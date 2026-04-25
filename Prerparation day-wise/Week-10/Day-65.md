# 📅 BPSC TRE 4.0 — DAY 65 COMPLETE STUDY MODULE
### Digital Electronics: Number Systems — Binary, Octal, Hexadecimal, BCD, Booth's Algorithm + History — INC Sessions & Viceroys of India
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Number Systems — All conversions (Decimal↔Binary↔Octal↔Hex), fractional binary, BCD, Booth's algorithm, PYQ key values (1234, 1011.1101)
> - Afternoon (1 hr): History — Indian National Congress Sessions (key sessions 1885–1947) + Viceroys of India (key facts, policies, events)
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Number Systems — Binary, Octal, Hexadecimal & Conversions

---

## 🔷 SECTION 1: Why Number Systems Matter

### Real-Life Analogy — Languages for the Same Idea:

The number "twelve" can be written as 12 (decimal), 1100 (binary), 14 (octal), or C (hexadecimal). Same value, different languages. Computers speak binary; humans prefer decimal; programmers use hex as shorthand for binary. A computer scientist must be fluent in all four.

> **A Number System is a mathematical notation for representing numbers using a set of digits and a base (radix). The base determines how many unique digits are used.**

### The Four Number Systems:
```
┌──────────────┬────────┬────────────────────┬──────────────────────────────┐
│    SYSTEM    │  BASE  │   DIGITS USED       │   PRIMARY USE                │
├──────────────┼────────┼────────────────────┼──────────────────────────────┤
│ Decimal      │  10    │ 0,1,2,3,4,5,6,7,8,9│ Human everyday counting      │
├──────────────┼────────┼────────────────────┼──────────────────────────────┤
│ Binary       │   2    │ 0, 1               │ Computer hardware (circuits) │
├──────────────┼────────┼────────────────────┼──────────────────────────────┤
│ Octal        │   8    │ 0,1,2,3,4,5,6,7    │ Shorthand for binary (older) │
├──────────────┼────────┼────────────────────┼──────────────────────────────┤
│ Hexadecimal  │  16    │ 0–9, A,B,C,D,E,F   │ Memory addresses, colors,    │
│              │        │                    │ compact binary shorthand     │
└──────────────┴────────┴────────────────────┴──────────────────────────────┘

POSITIONAL NOTATION:
  In any base-r system, a number d_n d_{n-1} ... d_1 d_0 has value:
  = d_n × r^n + d_{n-1} × r^{n-1} + ... + d_1 × r^1 + d_0 × r^0

EXAMPLE (Decimal 1234):
  1×10³ + 2×10² + 3×10¹ + 4×10⁰
  = 1000 + 200 + 30 + 4 = 1234

🎯 PYQ FACT: Binary = Base 2; Octal = Base 8; Hex = Base 16; Decimal = Base 10.
```

### Hexadecimal Digit Table (Must Memorize):
```
┌───────────────────────────────────────────────────┐
│         HEXADECIMAL DIGIT EQUIVALENTS              │
├────────────┬────────────┬────────────┬────────────┤
│  Decimal   │   Binary   │   Octal    │    Hex     │
├────────────┼────────────┼────────────┼────────────┤
│     0      │    0000    │     0      │     0      │
│     1      │    0001    │     1      │     1      │
│     2      │    0010    │     2      │     2      │
│     3      │    0011    │     3      │     3      │
│     4      │    0100    │     4      │     4      │
│     5      │    0101    │     5      │     5      │
│     6      │    0110    │     6      │     6      │
│     7      │    0111    │     7      │     7      │
│     8      │    1000    │    10      │     8      │
│     9      │    1001    │    11      │     9      │
│    10      │    1010    │    12      │     A      │
│    11      │    1011    │    13      │     B      │
│    12      │    1100    │    14      │     C      │
│    13      │    1101    │    15      │     D      │
│    14      │    1110    │    16      │     E      │
│    15      │    1111    │    17      │     F      │
└────────────┴────────────┴────────────┴────────────┘

MEMORY TRICK for Hex letters:
  A=10, B=11, C=12, D=13, E=14, F=15
  "After 9 in Hex: A B C D E F = 10 11 12 13 14 15"
  Count: A-B-C-D-E-F matches 10-11-12-13-14-15

🎯 PYQ FACT: In Hexadecimal, A=10, B=11, C=12, D=13, E=14, F=15.
🚨 TRAP: "Hex has digits 0–15 as 0,1,2...15" → FALSE!
         Hex uses letters A–F for 10–15 (single characters only).
```

---

## 🔷 SECTION 2: Decimal to Binary Conversion

### Method: Repeated Division by 2

```
PROCEDURE:
  Step 1: Divide the decimal number by 2
  Step 2: Record the REMAINDER (0 or 1)
  Step 3: Divide the QUOTIENT by 2 again
  Step 4: Repeat until quotient = 0
  Step 5: Read remainders from BOTTOM to TOP → that's the binary number!

MEMORY AID: "Divide by 2, read remainders upward"
```

### ⭐ KEY EXAMPLE: Decimal 1234 → Binary

```
STEP-BY-STEP DIVISION:

  1234 ÷ 2 = 617  remainder  0   ← LSB (Least Significant Bit — written last/bottom)
   617 ÷ 2 = 308  remainder  1
   308 ÷ 2 = 154  remainder  0
   154 ÷ 2 =  77  remainder  0
    77 ÷ 2 =  38  remainder  1
    38 ÷ 2 =  19  remainder  0
    19 ÷ 2 =   9  remainder  1
     9 ÷ 2 =   4  remainder  1
     4 ÷ 2 =   2  remainder  0
     2 ÷ 2 =   1  remainder  0
     1 ÷ 2 =   0  remainder  1   ← MSB (Most Significant Bit — written first/top)

READ REMAINDERS BOTTOM TO TOP (MSB first):
  1  0  0  1  1  0  1  0  0  1  0
  ↑                               ↑
 MSB                             LSB

RESULT: (1234)₁₀ = (10011010010)₂

VERIFICATION (Binary → Decimal):
  10011010010
  = 1×2¹⁰ + 0×2⁹ + 0×2⁸ + 1×2⁷ + 1×2⁶ + 0×2⁵ + 1×2⁴ + 0×2³ + 0×2² + 1×2¹ + 0×2⁰
  = 1024 + 0 + 0 + 128 + 64 + 0 + 16 + 0 + 0 + 2 + 0
  = 1024 + 128 + 64 + 16 + 2
  = 1234 ✅

🎯 PYQ FACT: (1234)₁₀ = (10011010010)₂  ← MEMORIZE THIS DIRECTLY!
```

### Powers of 2 — Quick Reference (Must Know):
```
2⁰  = 1        2⁵  = 32       2¹⁰ = 1024
2¹  = 2        2⁶  = 64       2¹¹ = 2048
2²  = 4        2⁷  = 128      2¹²  = 4096
2³  = 8        2⁸  = 256      2¹³  = 8192
2⁴  = 16       2⁹  = 512      2¹⁶  = 65536

MEMORY TRICK:  1, 2, 4, 8, 16, 32, 64, 128, 256, 512, 1024 ...
               Each value = DOUBLE the previous.
```

---

## 🔷 SECTION 3: Binary to Decimal Conversion

### Method: Positional Value (Powers of 2)

```
PROCEDURE:
  Step 1: Write the binary number with position numbers (rightmost = position 0)
  Step 2: For each bit = 1, multiply by 2^(position)
  Step 3: Add all the values

EXAMPLE: (10011010010)₂ → Decimal

  Position: 10  9  8  7  6  5  4  3  2  1  0
  Bit:       1  0  0  1  1  0  1  0  0  1  0

  1×2¹⁰ = 1×1024 = 1024
  0×2⁹  = 0
  0×2⁸  = 0
  1×2⁷  = 1×128  = 128
  1×2⁶  = 1×64   = 64
  0×2⁵  = 0
  1×2⁴  = 1×16   = 16
  0×2³  = 0
  0×2²  = 0
  1×2¹  = 1×2    = 2
  0×2⁰  = 0

  SUM = 1024 + 128 + 64 + 16 + 2 = 1234 ✅
```

---

## 🔷 SECTION 4: Decimal to Octal Conversion

### Method: Repeated Division by 8

```
PROCEDURE:
  Divide by 8 (instead of 2), read remainders bottom to top.
  Digits used: 0, 1, 2, 3, 4, 5, 6, 7 (no 8 or 9!)
```

### ⭐ KEY EXAMPLE: Decimal 1234 → Octal

```
STEP-BY-STEP DIVISION:

  1234 ÷ 8 = 154  remainder  2   ← LSD (written last/bottom)
   154 ÷ 8 =  19  remainder  2
    19 ÷ 8 =   2  remainder  3
     2 ÷ 8 =   0  remainder  2   ← MSD (written first/top)

READ REMAINDERS BOTTOM TO TOP:
  2  3  2  2

RESULT: (1234)₁₀ = (2322)₈

VERIFICATION (Octal → Decimal):
  2×8³ + 3×8² + 2×8¹ + 2×8⁰
  = 2×512 + 3×64 + 2×8 + 2×1
  = 1024 + 192 + 16 + 2
  = 1234 ✅

🎯 PYQ FACT: (1234)₁₀ = (2322)₈  ← MEMORIZE THIS DIRECTLY!
```

---

## 🔷 SECTION 5: Decimal to Hexadecimal Conversion

### Method: Repeated Division by 16

```
PROCEDURE:
  Divide by 16, record remainders (convert 10–15 to A–F), read bottom to top.
```

### ⭐ KEY EXAMPLE: Decimal 1234 → Hexadecimal

```
STEP-BY-STEP DIVISION:

  1234 ÷ 16 = 77  remainder  2   ← LSD (written last)
    77 ÷ 16 =  4  remainder 13   → D  (13 = D in hex!)
     4 ÷ 16 =  0  remainder  4   ← MSD (written first)

READ REMAINDERS BOTTOM TO TOP:
  4   D   2

RESULT: (1234)₁₀ = (4D2)₁₆

VERIFICATION (Hex → Decimal):
  4×16² + D×16¹ + 2×16⁰
  = 4×256 + 13×16 + 2×1
  = 1024 + 208 + 2
  = 1234 ✅

🎯 PYQ FACT: (1234)₁₀ = (4D2)₁₆  ← MEMORIZE THIS DIRECTLY!
🚨 TRAP: Students write "D2" as "132" forgetting that D=13 in hex context.
         In hex, D is a SINGLE digit representing decimal 13.
```

---

## 🔷 SECTION 6: Summary — All Conversions for 1234

```
┌──────────────────────────────────────────────────────────────────┐
│             THE FAMOUS 1234 CONVERSION — BPSC TRE PYQ            │
├──────────────┬───────────────────────────────────────────────────┤
│   SYSTEM     │              VALUE                                 │
├──────────────┼───────────────────────────────────────────────────┤
│ Decimal      │  1234                                             │
├──────────────┼───────────────────────────────────────────────────┤
│ Binary       │  10011010010  (11 bits)                           │
├──────────────┼───────────────────────────────────────────────────┤
│ Octal        │  2322                                             │
├──────────────┼───────────────────────────────────────────────────┤
│ Hexadecimal  │  4D2                                              │
└──────────────┴───────────────────────────────────────────────────┘

MEMORY TRICK to lock in 1234's hex value:
  1234 → "Four D Two" → 4D2
  "D" is the KEY — it's 13 in decimal (middle of A=10 to F=15)
  And 4 × 256 = 1024 is the anchor (2¹⁰ = 1024, close to 1234)
```

---

## 🔷 SECTION 7: Binary to Octal and Hex (Shortcut Method) ⭐

### Binary → Octal: Group by 3 bits

```
SHORTCUT: Every 3 binary bits = 1 octal digit (because 2³ = 8)

PROCEDURE:
  Step 1: Group binary digits in sets of 3 from RIGHT to LEFT
  Step 2: Add leading zeros if needed to complete groups
  Step 3: Convert each 3-bit group to its octal digit (0–7)

EXAMPLE: (10011010010)₂ → Octal

  Group from right in 3s:
  10  011  010  010
  ↓    ↓    ↓    ↓
  Add leading zero: 010
  010  011  010  010
   2    3    2    2
  
  RESULT: (2322)₈  ✅ (matches our earlier calculation!)

EXAMPLE 2: (1101110)₂ → Octal
  Group: 1  101  110
  Add 0: 001  101  110
          1    5    6
  RESULT: (156)₈
```

### Binary → Hex: Group by 4 bits

```
SHORTCUT: Every 4 binary bits = 1 hex digit (because 2⁴ = 16)

PROCEDURE:
  Step 1: Group binary digits in sets of 4 from RIGHT to LEFT
  Step 2: Add leading zeros if needed
  Step 3: Convert each 4-bit group to its hex digit (0–9, A–F)

EXAMPLE: (10011010010)₂ → Hex

  Group from right in 4s:
  100  1101  0010
  ↓      ↓     ↓
  Add leading zero: 0100
  0100  1101  0010
    4     D     2
  
  RESULT: (4D2)₁₆  ✅ (matches!)

EXAMPLE 2: (11111110)₂ → Hex
  Group: 1111  1110
          F     E
  RESULT: (FE)₁₆
```

### Octal → Hex (via Binary bridge):
```
SHORTCUT: Octal → Binary (3 bits each) → Hex (4 bits each)
There is NO direct octal-to-hex formula — always go through binary!

EXAMPLE: (2322)₈ → Hex
  2  3  2  2
  ↓  ↓  ↓  ↓ (each octal digit → 3 binary bits)
  010 011 010 010
  = 010011010010 (binary)
  Group in 4s from right: 0100 1101 0010
                            4    D    2
  RESULT: (4D2)₁₆  ✅

🎯 PYQ FACT: Binary → Octal: group 3 bits; Binary → Hex: group 4 bits.
🎯 PYQ FACT: Octal → Hex: always convert via binary (no direct shortcut).
```

---

## 🔷 SECTION 8: Fractional Binary Conversions ⭐ HIGH PYQ WEIGHT

### Binary Fraction to Decimal:

```
PROCEDURE:
  For digits AFTER the binary point:
  Position -1 → multiply by 2⁻¹ = 1/2 = 0.5
  Position -2 → multiply by 2⁻² = 1/4 = 0.25
  Position -3 → multiply by 2⁻³ = 1/8 = 0.125
  Position -4 → multiply by 2⁻⁴ = 1/16 = 0.0625

FRACTIONAL POWERS OF 2:
  2⁻¹ = 0.5
  2⁻² = 0.25
  2⁻³ = 0.125
  2⁻⁴ = 0.0625
  2⁻⁵ = 0.03125
  2⁻⁶ = 0.015625

MEMORY TRICK: Each is HALF the previous:
  0.5 → 0.25 → 0.125 → 0.0625 → 0.03125 → ...
```

### ⭐ KEY EXAMPLE: Binary 1011.1101 → Decimal

```
NUMBER: 1011.1101
         ↑↑↑↑ ↑↑↑↑
         Integer.Fraction

INTEGER PART (1011):
  Position:  3  2  1  0
  Bit:       1  0  1  1

  1×2³ + 0×2² + 1×2¹ + 1×2⁰
  = 8 + 0 + 2 + 1
  = 11

FRACTIONAL PART (.1101):
  Position: -1  -2  -3  -4
  Bit:        1   1   0   1

  1×2⁻¹ + 1×2⁻² + 0×2⁻³ + 1×2⁻⁴
  = 1×0.5 + 1×0.25 + 0×0.125 + 1×0.0625
  = 0.5 + 0.25 + 0 + 0.0625
  = 0.8125

TOTAL: Integer + Fraction = 11 + 0.8125 = 11.8125

RESULT: (1011.1101)₂ = (11.8125)₁₀

🎯 PYQ FACT: (1011.1101)₂ = (11.8125)₁₀  ← MEMORIZE THIS DIRECTLY!

VERIFICATION (quick check):
  Integer: 1011 binary = 8+2+1 = 11 ✅
  Fraction: .1101 = 0.5+0.25+0.0625 = 0.8125 ✅
  Total: 11.8125 ✅
```

### Decimal Fraction to Binary:

```
PROCEDURE (for fractional part only):
  Step 1: Multiply the fractional part by 2
  Step 2: Record the INTEGER part (0 or 1) — this is the next binary bit
  Step 3: Keep only the FRACTIONAL part of the result
  Step 4: Repeat until fraction = 0 or desired precision reached
  Step 5: Read bits from TOP to BOTTOM (left to right after binary point)

EXAMPLE: Convert 0.8125 to Binary

  0.8125 × 2 = 1.625  → integer part = 1, fraction = 0.625
  0.625  × 2 = 1.25   → integer part = 1, fraction = 0.25
  0.25   × 2 = 0.5    → integer part = 0, fraction = 0.5
  0.5    × 2 = 1.0    → integer part = 1, fraction = 0.0 (STOP!)

  Read integer parts top to bottom: 1, 1, 0, 1

  RESULT: (0.8125)₁₀ = (0.1101)₂  ✅ (confirms our earlier work!)
```

---

## 🔷 SECTION 9: Hexadecimal to Decimal

```
PROCEDURE:
  Each hex digit × 16^(position) — same as any base conversion.

EXAMPLE: (4D2)₁₆ → Decimal
  4×16² + D×16¹ + 2×16⁰
  = 4×256 + 13×16 + 2×1
  = 1024 + 208 + 2
  = 1234  ✅

EXAMPLE: (FF)₁₆ → Decimal
  F×16¹ + F×16⁰
  = 15×16 + 15×1
  = 240 + 15
  = 255

EXAMPLE: (A3)₁₆ → Decimal
  A×16¹ + 3×16⁰
  = 10×16 + 3
  = 160 + 3
  = 163

🎯 PYQ FACT: (FF)₁₆ = 255 in decimal. (FF)₁₆ is 8 bits all set to 1.
🎯 PYQ FACT: Maximum value of 8-bit binary = 11111111 = FF hex = 255 decimal.
```

---

## 🔷 SECTION 10: BCD — Binary Coded Decimal ⭐

### What is BCD?

```
BCD = Binary Coded Decimal

DEFINITION:
  BCD is a method of representing each DECIMAL DIGIT (0–9) separately
  using its 4-bit binary equivalent.

  It is NOT a pure base-2 system. It encodes decimal digit-by-digit.

RULE: Each decimal digit (0–9) → represented by exactly 4 binary bits.

ENCODING:
  Decimal 0 → BCD: 0000
  Decimal 1 → BCD: 0001
  Decimal 2 → BCD: 0010
  Decimal 3 → BCD: 0011
  Decimal 4 → BCD: 0100
  Decimal 5 → BCD: 0101
  Decimal 6 → BCD: 0110
  Decimal 7 → BCD: 0111
  Decimal 8 → BCD: 1000
  Decimal 9 → BCD: 1001

  ← ONLY these 10 codes are VALID BCD codes (0000 to 1001)!
  
INVALID BCD codes: 1010, 1011, 1100, 1101, 1110, 1111
  (These represent 10–15 which are NOT single decimal digits!)
```

### BCD vs Pure Binary — Key Difference:

```
PURE BINARY representation of 1234:
  (1234)₁₀ = (10011010010)₂   ← 11 bits, continuous binary

BCD representation of 1234:
  Digit by digit:  1     2     3     4
  BCD encoding: 0001  0010  0011  0100
  Full BCD: 0001 0010 0011 0100   ← 16 bits (4 bits per decimal digit)

PURE BINARY uses fewer bits but treats the entire number as binary.
BCD preserves decimal digit boundaries — easier for decimal display but uses more bits.

APPLICATIONS OF BCD:
  → Digital calculators (display shows decimal digits — BCD is natural)
  → Seven-segment displays
  → Bank ATMs and financial systems (avoid floating-point decimal errors)
  → Older digital systems

🎯 PYQ FACT: BCD encodes each decimal digit as 4 bits.
🎯 PYQ FACT: Maximum VALID BCD digit = 9 (code: 1001). NOT 15 (1111)!
🎯 PYQ FACT: BCD codes 1010 to 1111 (10–15) are INVALID — they do not represent any decimal digit.
🚨 TRAP: "BCD maximum digit = 15" → FALSE! BCD max = 9!
🚨 TRAP: "BCD and binary are the same thing" → FALSE! BCD encodes each decimal digit separately.
```

### BCD Addition — Key Concept:

```
BCD ADDITION RULE:
  When adding two BCD digits, if result > 9 or if there is a carry:
  ADD 6 (0110) to the result to skip the 6 invalid codes (1010–1111).

EXAMPLE: Add BCD 7 + 8
  7 = 0111
  8 = 1000
  Sum = 0111 + 1000 = 1111 = 15 (decimal)
  
  But 15 is NOT a valid BCD digit (max is 9)!
  So ADD 6: 1111 + 0110 = 10101 → carry 1, remainder 0101 = 5
  Result: BCD sum = 1 (carry) and 0101 (5) = decimal 15 ✅

🎯 PYQ FACT: In BCD addition, if result > 9, add 6 (correction factor).
```

---

## 🔷 SECTION 11: Booth's Algorithm ⭐

```
DEFINITION:
  Booth's Algorithm is an efficient algorithm for BINARY MULTIPLICATION
  of signed (positive and negative) binary numbers using 2's complement.

  Developed by: Andrew Donald Booth (1950)

PURPOSE:
  → Multiplies two binary numbers
  → Works for BOTH positive and negative numbers (signed multiplication)
  → Reduces the number of operations compared to simple binary multiplication
  → Uses a combination of addition, subtraction, and arithmetic right shifts

HOW IT WORKS (conceptual):
  For each bit in the multiplier, the algorithm:
  → If current bit = 1 and previous bit = 0: SUBTRACT multiplicand from accumulator
  → If current bit = 0 and previous bit = 1: ADD multiplicand to accumulator
  → If both bits same (0,0 or 1,1): just SHIFT (no add/subtract)

KEY FACTS FOR BPSC TRE:
  ✅ Booth's algorithm = used for BINARY MULTIPLICATION
  ✅ Works on SIGNED binary numbers (2's complement)
  ✅ Reduces number of additions needed
  ✅ Uses arithmetic RIGHT SHIFTS

🎯 PYQ FACT: Booth's algorithm is used for BINARY MULTIPLICATION of signed numbers.
🚨 TRAP: "Booth's algorithm is for binary DIVISION" → FALSE! It's for MULTIPLICATION.
🚨 TRAP: "Booth's algorithm only works for positive numbers" → FALSE! Works for signed (+ and −).
```

---

## 🔷 SECTION 12: Number System Conversions — Master Formula Table

```
┌────────────────────────────────────────────────────────────────────────┐
│               COMPLETE CONVERSION METHODS SUMMARY                      │
├─────────────────────────────┬──────────────────────────────────────────┤
│         CONVERSION          │              METHOD                       │
├─────────────────────────────┼──────────────────────────────────────────┤
│ Decimal → Binary            │ Divide by 2; read remainders bottom→top  │
├─────────────────────────────┼──────────────────────────────────────────┤
│ Decimal → Octal             │ Divide by 8; read remainders bottom→top  │
├─────────────────────────────┼──────────────────────────────────────────┤
│ Decimal → Hex               │ Divide by 16; replace 10–15 with A–F;   │
│                             │ read remainders bottom→top               │
├─────────────────────────────┼──────────────────────────────────────────┤
│ Binary → Decimal            │ Positional value: sum of bit × 2^pos    │
├─────────────────────────────┼──────────────────────────────────────────┤
│ Octal → Decimal             │ Positional value: sum of digit × 8^pos  │
├─────────────────────────────┼──────────────────────────────────────────┤
│ Hex → Decimal               │ Positional value: sum of digit × 16^pos │
├─────────────────────────────┼──────────────────────────────────────────┤
│ Binary → Octal (SHORTCUT)   │ Group 3 bits from right; each → 1 octal │
├─────────────────────────────┼──────────────────────────────────────────┤
│ Binary → Hex (SHORTCUT)     │ Group 4 bits from right; each → 1 hex   │
├─────────────────────────────┼──────────────────────────────────────────┤
│ Octal → Binary              │ Each octal digit → 3 binary bits        │
├─────────────────────────────┼──────────────────────────────────────────┤
│ Hex → Binary                │ Each hex digit → 4 binary bits          │
├─────────────────────────────┼──────────────────────────────────────────┤
│ Octal → Hex (or vice versa) │ Via binary (no direct shortcut)         │
├─────────────────────────────┼──────────────────────────────────────────┤
│ Decimal fraction → Binary   │ Multiply by 2; collect integer parts    │
│                             │ top→bottom                               │
├─────────────────────────────┼──────────────────────────────────────────┤
│ Binary fraction → Decimal   │ Each bit × 2^(-position) ; sum all      │
└─────────────────────────────┴──────────────────────────────────────────┘
```

---

## 🔷 SECTION 13: Additional Practice Conversions

### Quick Conversions to Practice:

```
EXAMPLE SET A — Powers of 2 (common in PYQs):
  (16)₁₀  = (10000)₂   = (20)₈  = (10)₁₆
  (32)₁₀  = (100000)₂  = (40)₈  = (20)₁₆
  (64)₁₀  = (1000000)₂ = (100)₈ = (40)₁₆
  (128)₁₀ = (10000000)₂= (200)₈ = (80)₁₆
  (255)₁₀ = (11111111)₂= (377)₈ = (FF)₁₆  ← Very important! Max 8-bit value
  (256)₁₀ = (100000000)₂=(400)₈ = (100)₁₆ ← Next after max 8-bit

EXAMPLE SET B — Common Hex values:
  (A)₁₆   = 10 decimal
  (F)₁₆   = 15 decimal
  (FF)₁₆  = 255 decimal
  (100)₁₆ = 256 decimal
  (1A)₁₆  = 1×16 + 10 = 26 decimal

EXAMPLE SET C — Fractional binary:
  (0.5)₁₀    = (0.1)₂     [1×2⁻¹ = 0.5]
  (0.25)₁₀   = (0.01)₂    [1×2⁻² = 0.25]
  (0.125)₁₀  = (0.001)₂   [1×2⁻³ = 0.125]
  (0.75)₁₀   = (0.11)₂    [0.5 + 0.25]
  (0.375)₁₀  = (0.011)₂   [0.25 + 0.125]
```

---

## 🔷 SECTION 14: PYQ Traps — Number Systems

```
🚨 TRAP 1: "(1234)₁₀ = (4D2)₁₆ is wrong — the correct answer is (4E2)" → FALSE!
   (1234)₁₀ = (4D2)₁₆ is CORRECT. Verify: 4×256 + 13×16 + 2 = 1024+208+2 = 1234.
   The middle digit is D (=13), not E (=14).

🚨 TRAP 2: "BCD maximum digit is 15 (1111 binary)" → FALSE!
   BCD max digit = 9 (1001 binary). Codes 1010 to 1111 are INVALID in BCD.

🚨 TRAP 3: "Booth's algorithm is for binary DIVISION" → FALSE!
   Booth's algorithm = binary MULTIPLICATION (of signed numbers).

🚨 TRAP 4: "To convert binary to octal, group 4 bits" → FALSE!
   Binary → Octal: group 3 bits (because 2³ = 8)
   Binary → Hex:   group 4 bits (because 2⁴ = 16)
   3 for Octal, 4 for Hex — don't swap!

🚨 TRAP 5: "1011.1101 in binary = 13.8125 decimal" → FALSE!
   Integer part: 1011 = 8+2+1 = 11 (not 13!)
   Correct: (1011.1101)₂ = 11.8125 decimal.

🚨 TRAP 6: "(4D2)₁₆ means 4×D×2 = some product" → FALSE!
   Hex numbers are positional: 4D2 = 4×256 + D×16 + 2 = 1234.
   D is not a multiplication — it's the hexadecimal digit for 13.

🚨 TRAP 7: "In BCD, the number 1234 is stored as (10011010010) binary" → FALSE!
   Pure binary: (10011010010)₂ = 1234.
   BCD: 0001 0010 0011 0100 (each digit encoded separately — 16 bits total).
   BCD ≠ pure binary!

🚨 TRAP 8: "Octal uses digits 0–8" → FALSE!
   Octal uses digits 0–7 only (base 8 means 8 digits: 0,1,2,3,4,5,6,7).
   There is NO digit "8" in octal!

🚨 TRAP 9: "Reading remainders top-to-bottom in division method" → FALSE!
   Read remainders BOTTOM TO TOP (last remainder = MSB, first = LSB).
   Reading top-to-bottom gives the REVERSED (wrong) answer!

🚨 TRAP 10: "Hexadecimal uses G, H instead of A, B for large values" → FALSE!
   Hex only goes up to F (=15). No G or H.
   Hex digits: 0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,F — exactly 16 symbols.
```

---

# PART 2: GENERAL STUDIES
## 📜 History — INC Sessions & Viceroys of India

---

## 🔷 SECTION 1: Indian National Congress — Formation & Background

```
FOUNDED:        28 December 1885
FOUNDER:        A.O. Hume (Allan Octavian Hume) — a retired British ICS officer
FIRST SESSION:  Bombay (Mumbai), December 1885
FIRST PRESIDENT: Womesh Chandra Bonnerjee (W.C. Banerjee)
VENUE:          Gokuldas Tejpal Sanskrit College, Bombay

WHY HUME FOUNDED INC:
  → Hume wanted to create a "safety valve" for Indian discontent
    (channel grievances peacefully, prevent another 1857-type revolt)
  → Nationalists later used INC as a platform for independence movement

PHASES OF INC:
  1885–1905 → MODERATE PHASE (petitions, prayers, constitutional methods)
              Leaders: Gopal Krishna Gokhale, Dadabhai Naoroji, Pherozeshah Mehta
  1905–1919 → EXTREMIST PHASE (mass agitation, Swaraj demand, Swadeshi)
              Leaders: Bal Gangadhar Tilak, Bipin Chandra Pal, Lala Lajpat Rai (Lal-Bal-Pal)
  1919–1947 → GANDHIAN PHASE (mass movements, non-violence, civil disobedience)

🎯 PYQ FACT: INC founded 28 December 1885 by A.O. Hume in Bombay.
🎯 PYQ FACT: First INC President = W.C. Banerjee (Womesh Chandra Bonnerjee).
```

---

## 🔷 SECTION 2: Key INC Sessions — Complete Reference ⭐

```
┌──────────┬─────────────┬──────────────────────┬──────────────────────────────────────────┐
│   YEAR   │    PLACE    │     PRESIDENT         │           KEY DECISION / SIGNIFICANCE    │
├──────────┼─────────────┼──────────────────────┼──────────────────────────────────────────┤
│  1885    │ Bombay      │ W.C. Bonnerjee        │ FIRST SESSION — INC founded              │
├──────────┼─────────────┼──────────────────────┼──────────────────────────────────────────┤
│  1886    │ Calcutta    │ Dadabhai Naoroji      │ First session outside Bombay;            │
│          │             │                       │ Naoroji = "Grand Old Man of India"       │
├──────────┼─────────────┼──────────────────────┼──────────────────────────────────────────┤
│  1888    │ Allahabad   │ George Yule           │ First NON-INDIAN president of INC        │
├──────────┼─────────────┼──────────────────────┼──────────────────────────────────────────┤
│  1896    │ Calcutta    │ Rahimtullah Sayani    │ Vande Mataram sung for the first time    │
│          │             │                       │ at an INC session (by Rabindranath       │
│          │             │                       │ Tagore)                                  │
├──────────┼─────────────┼──────────────────────┼──────────────────────────────────────────┤
│  1905    │ Banaras     │ G.K. Gokhale          │ Partition of Bengal announced            │
│          │             │                       │ (backdrop — Curzon's Bengal partition)   │
├──────────┼─────────────┼──────────────────────┼──────────────────────────────────────────┤
│  1906    │ Calcutta    │ Dadabhai Naoroji      │ SWARAJ demanded for the FIRST TIME       │
│          │             │                       │ ("Self-rule" — Naoroji used the word!)   │
├──────────┼─────────────┼──────────────────────┼──────────────────────────────────────────┤
│  1907    │ Surat       │ Rash Behari Ghosh     │ SURAT SPLIT — INC split into             │
│          │             │                       │ Moderates vs Extremists                  │
│          │             │                       │ (Historic — Tilak's extremists expelled) │
├──────────┼─────────────┼──────────────────────┼──────────────────────────────────────────┤
│  1911    │ Calcutta    │ Bishan Narayan Dhar   │ Jana Gana Mana sung for first time       │
│          │             │                       │ (by Rabindranath Tagore)                 │
├──────────┼─────────────┼──────────────────────┼──────────────────────────────────────────┤
│  1916    │ Lucknow     │ Ambika Charan         │ LUCKNOW PACT — INC + Muslim League       │
│          │             │ Mazumdar              │ united; Moderates + Extremists reunite   │
│          │             │                       │ (Tilak + Annie Besant lead this)         │
├──────────┼─────────────┼──────────────────────┼──────────────────────────────────────────┤
│  1917    │ Calcutta    │ Annie Besant          │ FIRST WOMAN PRESIDENT of INC             │
├──────────┼─────────────┼──────────────────────┼──────────────────────────────────────────┤
│  1920    │ Nagpur      │ C. Vijayaraghavacharlu│ Non-Cooperation Movement launched        │
│  (Special│             │                       │ Tilak's death; Gandhi takes leadership  │
│  session │ Calcutta)   │                       │ Drastic change in INC constitution      │
├──────────┼─────────────┼──────────────────────┼──────────────────────────────────────────┤
│  1924    │ Belgaum     │ Mahatma Gandhi        │ ONLY TIME Gandhi was President of INC   │
├──────────┼─────────────┼──────────────────────┼──────────────────────────────────────────┤
│  1927    │ Madras      │ M.A. Ansari           │ Complete Independence resolution (first  │
│          │             │                       │ proposed by Nehru — not yet passed)      │
│          │             │                       │ Simon Commission boycott decided         │
├──────────┼─────────────┼──────────────────────┼──────────────────────────────────────────┤
│  1929    │ Lahore      │ Jawaharlal Nehru      │ PURNA SWARAJ (Complete Independence)     │
│          │             │                       │ declared on 31 December 1929             │
│          │             │                       │ 26 January 1930 = Independence Day       │
│          │             │                       │ (Later became Republic Day 1950)         │
├──────────┼─────────────┼──────────────────────┼──────────────────────────────────────────┤
│  1931    │ Karachi     │ Vallabhbhai Patel     │ Karachi Resolution — Fundamental Rights  │
│          │             │                       │ and economic policy defined              │
│          │             │                       │ Ratified Gandhi-Irwin Pact               │
├──────────┼─────────────┼──────────────────────┼──────────────────────────────────────────┤
│  1936    │ Lucknow     │ Jawaharlal Nehru      │ Nehru elected president; socialist       │
│          │             │                       │ agenda; provincial elections preparation │
├──────────┼─────────────┼──────────────────────┼──────────────────────────────────────────┤
│  1938    │ Haripura    │ Subhas Chandra Bose   │ Bose elected president                   │
├──────────┼─────────────┼──────────────────────┼──────────────────────────────────────────┤
│  1939    │ Tripuri     │ Subhas Chandra Bose   │ Bose re-elected but RESIGNED due to      │
│          │             │                       │ conflict with Gandhi; formed Forward      │
│          │             │                       │ Bloc later                               │
└──────────┴─────────────┴──────────────────────┴──────────────────────────────────────────┘

🎯 TOP PYQ FACTS — INC Sessions:
  ✅ 1885 Bombay = First session; W.C. Bonnerjee = first president
  ✅ 1906 Calcutta = Swaraj demanded first time (Dadabhai Naoroji)
  ✅ 1907 Surat = Famous split (Moderates vs Extremists)
  ✅ 1917 Calcutta = Annie Besant = first woman president
  ✅ 1924 Belgaum = Gandhi's ONLY presidency of INC
  ✅ 1929 Lahore = PURNA SWARAJ declared (Nehru presiding)
  ✅ 1931 Karachi = Karachi Resolution (Fundamental Rights + Economic Policy)
  ✅ 1939 Tripuri = Subhas Bose resigned as president
```

---

## 🔷 SECTION 3: Viceroys of India — Complete Reference ⭐

### Understanding Viceroys:
```
VICEROY = The representative of the British Crown in India.
          Governed India on behalf of the British government.
          Position created after 1858 (end of East India Company rule).

BEFORE 1858: Governors-General of India (East India Company)
AFTER 1858:  Viceroys of India (British Crown, post-Revolt of 1857)

FIRST VICEROY: Lord Canning (1858–1862)
  → Queen's Proclamation 1858 — Company rule ended
  → Indian Councils Act 1861

LAST VICEROY: Lord Mountbatten (1947)
  → Oversaw Indian Independence and Partition
  → India independence: 15 August 1947
```

### Key Viceroys and Their Associations ⭐:

```
┌────────────────────────────┬──────────────────────────────────────────────────────┐
│        VICEROY             │         KEY EVENTS / POLICIES / ASSOCIATION          │
├────────────────────────────┼──────────────────────────────────────────────────────┤
│ LORD CANNING               │ First Viceroy (1858–62); Queen's Proclamation 1858;  │
│ (1856–1862)                │ Indian Councils Act 1861; Sepoy Mutiny 1857          │
│                            │ Called "Clemency Canning" for lenient policy         │
├────────────────────────────┼──────────────────────────────────────────────────────┤
│ LORD DALHOUSIE             │ Doctrine of Lapse (annexed Jhansi, Satara, Nagpur)  │
│ (1848–1856)                │ Wood's Education Despatch 1854; first railway (1853) │
│ (Governor-General, not     │ Electric telegraph; Public Works Dept established    │
│  Viceroy technically)      │ Annexation of Punjab (1849), Lower Burma             │
│                            │ His policies triggered the 1857 Revolt!              │
├────────────────────────────┼──────────────────────────────────────────────────────┤
│ LORD LYTTON                │ Vernacular Press Act 1878 (to suppress Indian press) │
│ (1876–1880)                │ Arms Act 1878 (disarmed Indians)                     │
│                            │ Grand Delhi Durbar 1877 (Queen Victoria = Empress)   │
│                            │ Afghan War (Second)                                  │
│                            │ Known for PRO-BRITISH policies                       │
├────────────────────────────┼──────────────────────────────────────────────────────┤
│ LORD RIPON                 │ Repeal of Vernacular Press Act 1882                  │
│ (1880–1884)                │ Local Self-Government introduced (1882)              │
│                            │ Factory Act 1881 (child labour reforms)              │
│                            │ Hunter Commission on Education (1882)                │
│                            │ Ilbert Bill controversy                              │
│                            │ Known as PRO-INDIAN / LIBERAL viceroy               │
├────────────────────────────┼──────────────────────────────────────────────────────┤
│ LORD DUFFERIN              │ INC founded (1885) during his tenure                 │
│ (1884–1888)                │ Third Burma War (annexed Upper Burma 1885)           │
├────────────────────────────┼──────────────────────────────────────────────────────┤
│ LORD LANSDOWNE             │ Indian Councils Act 1892                             │
│ (1888–1894)                │ Factory Act 1891                                     │
│                            │ Age of Consent Act 1891 (raised marriage age to 12) │
├────────────────────────────┼──────────────────────────────────────────────────────┤
│ LORD CURZON                │ Partition of Bengal 1905 ← MOST IMPORTANT            │
│ (1899–1905)                │ Ancient Monuments Preservation Act 1904              │
│                            │ Indian Universities Act 1904                         │
│                            │ Delhi Durbar 1903                                    │
│                            │ Calcutta Corporation Act                             │
│                            │ Known for REACTIONARY / ANTI-INDIA policies         │
│                            │ Partition of Bengal triggered Swadeshi Movement     │
├────────────────────────────┼──────────────────────────────────────────────────────┤
│ LORD MINTO II              │ Indian Councils Act 1909 (Morley-Minto Reforms)     │
│ (1905–1910)                │ Separate electorate for Muslims (communal politics) │
│                            │ Working with Secretary of State John Morley          │
├────────────────────────────┼──────────────────────────────────────────────────────┤
│ LORD HARDINGE II           │ Annulment of Bengal Partition 1911                  │
│ (1910–1916)                │ Transfer of Capital: Calcutta → Delhi 1911          │
│                            │ Delhi Durbar 1911 (King George V visited India)     │
│                            │ Delhi Conspiracy Case (Hardinge bombed at Delhi     │
│                            │ Durbar procession)                                   │
├────────────────────────────┼──────────────────────────────────────────────────────┤
│ LORD CHELMSFORD            │ Montagu-Chelmsford Reforms 1919                     │
│ (1916–1921)                │ (Government of India Act 1919 — Dyarchy introduced) │
│                            │ Rowlatt Act 1919 (oppressive — no jury trials)      │
│                            │ Jallianwala Bagh massacre 1919 (during his tenure)  │
├────────────────────────────┼──────────────────────────────────────────────────────┤
│ LORD READING               │ Prince of Wales visit and boycott 1921              │
│ (1921–1926)                │ Non-Cooperation Movement (Gandhi arrested 1922)     │
│                            │ Moplah Rebellion 1921                                │
├────────────────────────────┼──────────────────────────────────────────────────────┤
│ LORD IRWIN                 │ Simon Commission 1927                               │
│ (1926–1931)                │ Lahore Session 1929 (Purna Swaraj during his time) │
│                            │ Civil Disobedience Movement / Salt March 1930       │
│                            │ Gandhi-Irwin Pact 1931                              │
│                            │ First Round Table Conference                        │
├────────────────────────────┼──────────────────────────────────────────────────────┤
│ LORD WILLINGDON            │ Second and Third Round Table Conferences            │
│ (1931–1936)                │ Gandhi-Irwin Pact broken; Gandhi re-arrested        │
│                            │ Government of India Act 1935 (during his tenure)   │
├────────────────────────────┼──────────────────────────────────────────────────────┤
│ LORD LINLITHGOW            │ Government of India Act 1935 implemented            │
│ (1936–1944)                │ Longest serving Viceroy (8 years)                  │
│                            │ WWII — India declared at war by Viceroy (1939)     │
│                            │ August Offer 1940; Cripps Mission 1942             │
│                            │ Quit India Movement 1942 (Gandhi arrested)          │
│                            │ Bengal Famine 1943 (3 million deaths)               │
├────────────────────────────┼──────────────────────────────────────────────────────┤
│ LORD WAVELL                │ Shimla Conference 1945                              │
│ (1944–1947)                │ Cabinet Mission 1946                                │
│                            │ INA trials (1945–46)                                │
│                            │ Great Calcutta Killings (communal riots 1946)       │
├────────────────────────────┼──────────────────────────────────────────────────────┤
│ LORD MOUNTBATTEN           │ LAST VICEROY (and first Governor-General of India)  │
│ (1947)                     │ Mountbatten Plan (3 June 1947) — Partition plan     │
│                            │ Indian Independence Act 1947                        │
│                            │ India: 15 August 1947; Pakistan: 14 August 1947    │
└────────────────────────────┴──────────────────────────────────────────────────────┘

🎯 TOP PYQ FACTS — Viceroys:
  ✅ First Viceroy = Lord Canning (1858)
  ✅ Last Viceroy = Lord Mountbatten (1947)
  ✅ Partition of Bengal 1905 = Lord Curzon
  ✅ Annulment of Bengal Partition 1911 = Lord Hardinge II
  ✅ Capital moved Calcutta → Delhi = Lord Hardinge II (1911)
  ✅ Montagu-Chelmsford Reforms 1919 = Lord Chelmsford
  ✅ Rowlatt Act + Jallianwala Bagh 1919 = Lord Chelmsford's tenure
  ✅ Gandhi-Irwin Pact 1931 = Lord Irwin
  ✅ Longest serving Viceroy = Lord Linlithgow (8 years, 1936–44)
  ✅ Local Self-Government + Repeal of VPA = Lord Ripon (liberal)
  ✅ Vernacular Press Act + Arms Act = Lord Lytton (anti-India)
  ✅ Doctrine of Lapse + First Railway = Lord Dalhousie
  ✅ INC Founded (1885) = during Lord Dufferin's tenure
  ✅ Bengal Famine 1943 = Lord Linlithgow's tenure
```

---

## 🔷 SECTION 4: PYQ Traps — INC Sessions & Viceroys

```
🚨 TRAP 1: "INC was founded by Bal Gangadhar Tilak" → FALSE!
   INC founded by A.O. Hume (1885).
   Tilak was a key leader later — but not the founder.

🚨 TRAP 2: "Purna Swaraj was declared at the 1929 Karachi session" → FALSE!
   Purna Swaraj = Lahore Session 1929 (not Karachi!).
   Karachi session (1931) = Karachi Resolution on Fundamental Rights.

🚨 TRAP 3: "Annie Besant was the first woman and first Indian woman president of INC" → PARTIAL TRAP!
   Annie Besant was the first woman president (1917) but she was NOT Indian — she was British/Irish!
   First INDIAN WOMAN president = Sarojini Naidu (1925, Kanpur session).

🚨 TRAP 4: "Gandhi was INC president multiple times" → FALSE!
   Gandhi was president of INC ONLY ONCE — Belgaum session, 1924.

🚨 TRAP 5: "Partition of Bengal was reversed by Lord Curzon" → FALSE!
   Curzon CAUSED the partition (1905).
   Lord Hardinge II REVERSED it (1911).

🚨 TRAP 6: "Rowlatt Act was passed during Lord Irwin's tenure" → FALSE!
   Rowlatt Act 1919 = Lord Chelmsford's tenure.
   Lord Irwin's tenure = Gandhi-Irwin Pact (1931), Salt March (1930).

🚨 TRAP 7: "Montagu-Chelmsford Reforms introduced separate electorates for Muslims" → FALSE!
   Separate electorates = Morley-Minto Reforms 1909 (Lord Minto II).
   Montagu-Chelmsford 1919 = Dyarchy (dual government) in provinces.

🚨 TRAP 8: "INC was founded at Calcutta in 1885" → FALSE!
   INC first session = BOMBAY (Mumbai), December 1885.
   Calcutta was the venue of the second session (1886).

🚨 TRAP 9: "Surat Split happened between INC and Muslim League" → FALSE!
   Surat Split (1907) = split WITHIN INC between Moderates and Extremists.
   Nothing to do with Muslim League.

🚨 TRAP 10: "Lord Linlithgow was the shortest-serving viceroy" → FALSE!
   Lord Linlithgow was the LONGEST-serving viceroy (8 years: 1936–1944).
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Number System Conversions, BCD, Booth's Algorithm, Fractional Binary

---

**Q1.** What is the decimal number 1234 in binary?
(A) 10011010100
(B) 10011010010
(C) 10001010010
(D) More than one of the above
(E) None of the above

---

**Q2.** What is the decimal number 1234 in octal?
(A) 2232
(B) 2223
(C) 2322
(D) More than one of the above
(E) None of the above

---

**Q3.** What is the decimal number 1234 in hexadecimal?
(A) 4E2
(B) 4D2
(C) 4C2
(D) More than one of the above
(E) None of the above

---

**Q4.** What is the decimal value of binary 1011.1101?
(A) 13.8125
(B) 11.75
(C) 11.8125
(D) More than one of the above
(E) None of the above

---

**Q5.** In hexadecimal, the letter D represents which decimal value?
(A) 12
(B) 14
(C) 13
(D) More than one of the above
(E) None of the above

---

**Q6.** In hexadecimal, the digit F represents which decimal value?
(A) 14
(B) 16
(C) 15
(D) More than one of the above
(E) None of the above

---

**Q7.** To convert a binary number to octal, you group binary digits in sets of:
(A) 2 bits
(B) 4 bits
(C) 3 bits
(D) More than one of the above
(E) None of the above

---

**Q8.** To convert a binary number to hexadecimal, you group binary digits in sets of:
(A) 3 bits
(B) 4 bits
(C) 8 bits
(D) More than one of the above
(E) None of the above

---

**Q9.** What is the decimal value of hexadecimal FF?
(A) 250
(B) 256
(C) 255
(D) More than one of the above
(E) None of the above

---

**Q10.** In decimal to binary conversion (repeated division method), the binary result is obtained by reading the remainders in which order?
(A) Top to bottom (first remainder = MSB)
(B) Bottom to top (last remainder = MSB)
(C) Either order — both give the same result
(D) More than one of the above
(E) None of the above

---

**Q11.** BCD stands for:
(A) Binary Coded Data
(B) Binary Coded Decimal
(C) Base Coded Decimal
(D) More than one of the above
(E) None of the above

---

**Q12.** What is the maximum decimal DIGIT that can be represented in BCD?
(A) 15 (1111 in binary)
(B) 7 (0111 in binary)
(C) 9 (1001 in binary)
(D) More than one of the above
(E) None of the above

---

**Q13.** Which of the following 4-bit codes is INVALID in BCD?
(A) 1001 (= decimal 9)
(B) 0101 (= decimal 5)
(C) 1010 (= decimal 10)
(D) More than one of the above
(E) None of the above

---

**Q14.** Booth's algorithm is used for:
(A) Binary addition of unsigned numbers
(B) Binary multiplication of signed numbers
(C) Binary division using repeated subtraction
(D) More than one of the above
(E) None of the above

---

**Q15.** What is the binary equivalent of decimal 255?
(A) 11110000
(B) 11111110
(C) 11111111
(D) More than one of the above
(E) None of the above

---

**Q16.** Convert binary 1111 to hexadecimal:
(A) E
(B) F
(C) 15
(D) More than one of the above
(E) None of the above

---

**Q17.** What is the octal equivalent of binary 11011010?
(A) 312
(B) 332
(C) 332 (3×64+3×8+2=218... let's verify: 11 011 010 = 3 3 2)
(D) More than one of the above
(E) None of the above

---

**Q18.** Convert hexadecimal A3 to decimal:
(A) 153
(B) 163
(C) 173
(D) More than one of the above
(E) None of the above

---

**Q19.** The BCD representation of decimal 9 is:
(A) 1111
(B) 1001
(C) 1010
(D) More than one of the above
(E) None of the above

---

**Q20.** In BCD addition, if the sum of two BCD digits exceeds 9, what correction is applied?
(A) Subtract 6 (0110) from the result
(B) Add 6 (0110) to the result
(C) Add 10 (1010) to the result
(D) More than one of the above
(E) None of the above

---

**Q21.** What is the decimal value of binary 1000?
(A) 6
(B) 8
(C) 10
(D) More than one of the above
(E) None of the above

---

**Q22.** The binary number system uses which base (radix)?
(A) 8
(B) 16
(C) 2
(D) More than one of the above
(E) None of the above

---

**Q23.** Convert decimal 0.5 to binary:
(A) 0.01
(B) 0.1
(C) 0.11
(D) More than one of the above
(E) None of the above

---

**Q24.** Octal number system uses digits from:
(A) 0 to 8 (nine digits)
(B) 0 to 7 (eight digits)
(C) 1 to 8 (eight digits)
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following statements about number systems is CORRECT?
(A) Booth's algorithm works for binary DIVISION
(B) BCD maximum digit value is 15 (1111)
(C) Binary 1011.1101 = decimal 11.8125 AND Decimal 1234 = Hex 4D2
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: INC Sessions, Viceroys of India

---

**Q26.** The Indian National Congress was founded in:
(A) 26 January 1885
(B) 28 December 1885
(C) 15 August 1885
(D) More than one of the above
(E) None of the above

---

**Q27.** Who founded the Indian National Congress?
(A) Bal Gangadhar Tilak
(B) Dadabhai Naoroji
(C) A.O. Hume
(D) More than one of the above
(E) None of the above

---

**Q28.** The first president of the Indian National Congress was:
(A) Dadabhai Naoroji
(B) Gopal Krishna Gokhale
(C) Womesh Chandra Bonnerjee
(D) More than one of the above
(E) None of the above

---

**Q29.** The historic Surat Split (1907) of INC was between:
(A) INC and Muslim League
(B) Moderates and Extremists within INC
(C) INC and the British government
(D) More than one of the above
(E) None of the above

---

**Q30.** Purna Swaraj (Complete Independence) was declared at which INC Session?
(A) Karachi Session, 1931
(B) Lahore Session, 1929
(C) Calcutta Session, 1928
(D) More than one of the above
(E) None of the above

---

**Q31.** Who presided over the historic 1929 Lahore Session of INC?
(A) Mahatma Gandhi
(B) Subhas Chandra Bose
(C) Jawaharlal Nehru
(D) More than one of the above
(E) None of the above

---

**Q32.** The first woman president of the Indian National Congress was:
(A) Sarojini Naidu (1925)
(B) Annie Besant (1917)
(C) Vijaya Lakshmi Pandit (1930)
(D) More than one of the above
(E) None of the above

---

**Q33.** Mahatma Gandhi served as president of INC at which session?
(A) Nagpur Session, 1920
(B) Belgaum Session, 1924
(C) Haripura Session, 1938
(D) More than one of the above
(E) None of the above

---

**Q34.** The Karachi Session of INC (1931) is famous for:
(A) Declaring Purna Swaraj
(B) The Surat Split between Moderates and Extremists
(C) Karachi Resolution on Fundamental Rights and Economic Policy
(D) More than one of the above
(E) None of the above

---

**Q35.** Vande Mataram was sung for the first time at an INC session in:
(A) 1885 (First Bombay Session)
(B) 1896 (Calcutta Session)
(C) 1906 (Calcutta Session)
(D) More than one of the above
(E) None of the above

---

**Q36.** The first Viceroy of India (after the Crown took over from East India Company) was:
(A) Lord Dalhousie
(B) Lord Canning
(C) Lord Ripon
(D) More than one of the above
(E) None of the above

---

**Q37.** Which Viceroy partitioned Bengal in 1905?
(A) Lord Minto
(B) Lord Hardinge
(C) Lord Curzon
(D) More than one of the above
(E) None of the above

---

**Q38.** The annulment (cancellation) of the Partition of Bengal was announced during which Viceroy's tenure?
(A) Lord Curzon
(B) Lord Hardinge II
(C) Lord Chelmsford
(D) More than one of the above
(E) None of the above

---

**Q39.** The transfer of India's capital from Calcutta to Delhi (1911) happened during whose tenure?
(A) Lord Curzon
(B) Lord Minto
(C) Lord Hardinge II
(D) More than one of the above
(E) None of the above

---

**Q40.** The Rowlatt Act (1919) and Jallianwala Bagh massacre (1919) occurred during which Viceroy's term?
(A) Lord Irwin
(B) Lord Reading
(C) Lord Chelmsford
(D) More than one of the above
(E) None of the above

---

**Q41.** The Gandhi-Irwin Pact (1931) was signed between Gandhi and which Viceroy?
(A) Lord Reading
(B) Lord Irwin
(C) Lord Willingdon
(D) More than one of the above
(E) None of the above

---

**Q42.** Which Viceroy was the LONGEST serving in India?
(A) Lord Curzon
(B) Lord Irwin
(C) Lord Linlithgow
(D) More than one of the above
(E) None of the above

---

**Q43.** The Vernacular Press Act (1878) was passed by which Viceroy to suppress the Indian press?
(A) Lord Ripon
(B) Lord Lytton
(C) Lord Dufferin
(D) More than one of the above
(E) None of the above

---

**Q44.** Which Viceroy is credited with introducing Local Self-Government and repealing the Vernacular Press Act?
(A) Lord Lytton
(B) Lord Curzon
(C) Lord Ripon
(D) More than one of the above
(E) None of the above

---

**Q45.** The Doctrine of Lapse and the introduction of the first railway (1853) in India are associated with:
(A) Lord Canning
(B) Lord Dalhousie
(C) Lord Ripon
(D) More than one of the above
(E) None of the above

---

**Q46.** During whose viceroyalty was the Indian National Congress founded in 1885?
(A) Lord Ripon
(B) Lord Dufferin
(C) Lord Lansdowne
(D) More than one of the above
(E) None of the above

---

**Q47.** The Morley-Minto Reforms (Indian Councils Act 1909), which introduced separate electorates for Muslims, were associated with Viceroy:
(A) Lord Chelmsford
(B) Lord Hardinge II
(C) Lord Minto II
(D) More than one of the above
(E) None of the above

---

**Q48.** The last Viceroy of India was:
(A) Lord Wavell
(B) Lord Linlithgow
(C) Lord Mountbatten
(D) More than one of the above
(E) None of the above

---

**Q49.** Consider the following INC sessions and their significance:
I. 1906 Calcutta — Swaraj demanded for the first time
II. 1907 Surat — INC split (Moderates vs Extremists)
III. 1917 Calcutta — Annie Besant became first woman president
IV. 1924 Belgaum — Gandhi's only presidency of INC

Which of these are CORRECTLY matched?
(A) I and II only
(B) I, II, and III only
(C) All of I, II, III, and IV
(D) More than one of the above
(E) None of the above

---

**Q50.** Consider these Viceroy associations:
I.   Partition of Bengal 1905 → Lord Curzon
II.  Annulment of Bengal Partition 1911 → Lord Hardinge II
III. Salt March / Gandhi-Irwin Pact → Lord Irwin
IV.  Bengal Famine 1943 → Lord Linlithgow

Which pairs are CORRECTLY matched?
(A) I and II only
(B) I, II, and III only
(C) All of I, II, III, and IV
(D) More than one of the above
(E) None of the above

---

# ✅ ANSWER KEY

## ⚠️ ATTEMPT ALL 50 QUESTIONS BEFORE CHECKING ANSWERS

---

### CS Answers (Q1–Q25):

| Q  | Ans | Key Reason |
|----|-----|------------|
| 1  | (B) | (1234)₁₀ = (10011010010)₂ — direct PYQ fact, memorize |
| 2  | (C) | (1234)₁₀ = (2322)₈ — direct PYQ fact, memorize |
| 3  | (B) | (1234)₁₀ = (4D2)₁₆ — direct PYQ fact; D=13, 4×256+13×16+2=1234 |
| 4  | (C) | 1011=11, .1101=0.5+0.25+0.0625=0.8125 → total 11.8125 |
| 5  | (C) | D = 13 in hexadecimal (A=10,B=11,C=12,D=13,E=14,F=15) |
| 6  | (C) | F = 15 in hexadecimal (last hex digit) |
| 7  | (C) | Binary → Octal: group 3 bits (2³=8) |
| 8  | (B) | Binary → Hex: group 4 bits (2⁴=16) |
| 9  | (C) | FF = 15×16+15 = 240+15 = 255 |
| 10 | (B) | Read remainders BOTTOM to TOP (last remainder = MSB) |
| 11 | (B) | BCD = Binary Coded Decimal |
| 12 | (C) | BCD max digit = 9 (1001 binary); NOT 15 — that's a common trap! |
| 13 | (C) | 1010 = decimal 10, which is NOT a single decimal digit → invalid in BCD |
| 14 | (B) | Booth's algorithm = binary MULTIPLICATION of signed numbers |
| 15 | (C) | 255 = 11111111 (eight 1s = maximum 8-bit value) |
| 16 | (B) | 1111 binary = 15 decimal = F hex |
| 17 | (C) | 11011010 → group 3: 011 011 010 = 3 3 2 → (332)₈ |
| 18 | (B) | A3 hex: A=10, 3=3 → 10×16+3×1 = 160+3 = 163 |
| 19 | (B) | Decimal 9 in BCD = 1001 (9 = 8+1 = 2³+2⁰) |
| 20 | (B) | BCD correction: add 6 (0110) when sum > 9 or carry occurs |
| 21 | (B) | Binary 1000 = 1×2³ = 8 |
| 22 | (C) | Binary = base 2 |
| 23 | (B) | 0.5×2=1.0 → integer=1, stop → binary = 0.1 |
| 24 | (B) | Octal uses 0–7 (eight digits: 0,1,2,3,4,5,6,7) |
| 25 | (C) | Both facts correct: 1011.1101=11.8125 AND 1234=4D2 hex → answer is D but since the question asks which statement is correct and C states both facts correctly, C is correct; Answer = (C) since it states both PYQ key facts accurately |

---

### GS Answers (Q26–Q50):

| Q  | Ans | Key Reason |
|----|-----|------------|
| 26 | (B) | INC founded 28 December 1885 |
| 27 | (C) | A.O. Hume founded INC (retired British ICS officer) |
| 28 | (C) | W.C. Bonnerjee (Womesh Chandra Bonnerjee) = first INC president |
| 29 | (B) | Surat 1907 = split between Moderates and Extremists WITHIN INC |
| 30 | (B) | Purna Swaraj = Lahore Session 1929 (not Karachi 1931!) |
| 31 | (C) | Jawaharlal Nehru presided over Lahore Session 1929 |
| 32 | (B) | Annie Besant = first woman president (1917 Calcutta session) |
| 33 | (B) | Gandhi was INC president ONLY at Belgaum session, 1924 |
| 34 | (C) | Karachi 1931 = Karachi Resolution (Fundamental Rights + Economic Policy) |
| 35 | (B) | Vande Mataram first sung at INC = 1896 Calcutta session |
| 36 | (B) | Lord Canning = first Viceroy of India (1858) |
| 37 | (C) | Partition of Bengal 1905 = Lord Curzon |
| 38 | (B) | Bengal Partition annulled 1911 = Lord Hardinge II |
| 39 | (C) | Capital Calcutta→Delhi 1911 = Lord Hardinge II |
| 40 | (C) | Rowlatt Act + Jallianwala Bagh 1919 = Lord Chelmsford |
| 41 | (B) | Gandhi-Irwin Pact 1931 = Lord Irwin |
| 42 | (C) | Longest serving Viceroy = Lord Linlithgow (8 years, 1936–1944) |
| 43 | (B) | Vernacular Press Act 1878 = Lord Lytton |
| 44 | (C) | Local Self-Government + Repeal of VPA = Lord Ripon (liberal) |
| 45 | (B) | Doctrine of Lapse + First Railway = Lord Dalhousie |
| 46 | (B) | INC founded 1885 during Lord Dufferin's tenure |
| 47 | (C) | Morley-Minto Reforms 1909 (separate electorates) = Lord Minto II |
| 48 | (C) | Last Viceroy = Lord Mountbatten (1947) |
| 49 | (C) | All four pairs I, II, III, IV are correctly matched |
| 50 | (C) | All four Viceroy associations I, II, III, IV are correctly matched |

---

# 🔁 DAY 65 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Number Systems

### THE THREE KEY PYQ FACTS (Memorize Directly):
```
(1234)₁₀  =  (10011010010)₂  =  (2322)₈  =  (4D2)₁₆
(1011.1101)₂  =  (11.8125)₁₀
BCD maximum digit = 9  (NOT 15!)
```

### Conversion Methods:
```
Dec → Binary:  Divide by 2, read remainders BOTTOM→TOP
Dec → Octal:   Divide by 8, read remainders BOTTOM→TOP
Dec → Hex:     Divide by 16, replace 10–15 with A–F, read BOTTOM→TOP

Binary → Octal: Group 3 bits from right (2³=8)
Binary → Hex:   Group 4 bits from right (2⁴=16)
Octal  → Hex:   Always via binary (no direct shortcut)
```

### Hex Digits:
```
A=10, B=11, C=12, D=13, E=14, F=15
FF hex = 255 decimal = 11111111 binary (max 8-bit value)
```

### Fractional Binary → Decimal:
```
2⁻¹=0.5, 2⁻²=0.25, 2⁻³=0.125, 2⁻⁴=0.0625
.1101 = 0.5+0.25+0+0.0625 = 0.8125
1011.1101 = 11 + 0.8125 = 11.8125
```

### BCD & Booth's:
```
BCD = 4 bits per decimal digit; valid only 0000–1001 (0–9)
BCD invalid: 1010–1111 (10–15 — not decimal digits!)
BCD addition: result > 9 → add 6 (0110) correction
Booth's = BINARY MULTIPLICATION of signed numbers
```

### PYQ Trap List — Number Systems:
```
✅ 1234 hex = 4D2 (D=13, NOT E=14!)
✅ 1011.1101 binary = 11.8125 (NOT 13.8125 — integer part = 11!)
✅ BCD max = 9 (NOT 15!)
✅ Binary→Octal = group 3 bits; Binary→Hex = group 4 bits (don't swap!)
✅ Read remainders BOTTOM to TOP in division method
✅ Booth's = MULTIPLICATION (not division!)
✅ Octal uses 0–7 only (no digit 8 or 9!)
✅ Hex uses 0–9 and A–F (no single-digit for 10–15 except A–F)
```

---

## ⚡ RAPID FIRE — INC Sessions & Viceroys

### INC Sessions Core 7:
```
1885 Bombay      → First session; W.C. Bonnerjee (1st president); A.O. Hume founded
1906 Calcutta    → Swaraj demanded FIRST TIME (Dadabhai Naoroji)
1907 Surat       → Famous SPLIT (Moderates vs Extremists)
1917 Calcutta    → Annie Besant = FIRST WOMAN president
1924 Belgaum     → Gandhi's ONLY INC presidency
1929 Lahore      → PURNA SWARAJ declared (Nehru presiding)
1931 Karachi     → Karachi Resolution (Fundamental Rights + Economic Policy)
```

### Viceroys Core 8:
```
Lord Canning      → First Viceroy (1858)
Lord Dalhousie    → Doctrine of Lapse + First Railway (Governor-General)
Lord Lytton       → Vernacular Press Act 1878 (anti-India)
Lord Ripon        → Repealed VPA + Local Self-Government (pro-India)
Lord Dufferin     → INC founded during his tenure (1885)
Lord Curzon       → Partition of Bengal 1905
Lord Hardinge II  → Cancelled Partition + Capital to Delhi (1911)
Lord Chelmsford   → Rowlatt Act + Jallianwala Bagh + Montagu-Chelmsford 1919
Lord Irwin        → Salt March + Gandhi-Irwin Pact 1931
Lord Linlithgow   → Longest serving (8 yrs) + Bengal Famine 1943
Lord Mountbatten  → Last Viceroy + Indian Independence 1947
```

### PYQ Trap List — INC/Viceroys:
```
✅ INC founded by A.O. HUME (not Tilak, not Gokhale!)
✅ Purna Swaraj = LAHORE 1929 (not Karachi 1931!)
✅ Karachi 1931 = Karachi RESOLUTION (Fundamental Rights)
✅ Annie Besant = first WOMAN president (not first Indian woman)
✅ Sarojini Naidu = first INDIAN woman president (1925 Kanpur)
✅ Gandhi was INC president ONLY ONCE at Belgaum 1924
✅ Partition of Bengal = Curzon; ANNULMENT = Hardinge II
✅ Rowlatt Act = Lord CHELMSFORD (not Irwin!)
✅ Longest Viceroy = Lord LINLITHGOW (8 years)
✅ Last Viceroy = Lord MOUNTBATTEN
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **The 3 PYQ Key Facts**: (1234)₁₀ = (10011010010)₂ = (2322)₈ = (4D2)₁₆. Binary 1011.1101 = 11.8125 decimal (integer 1011=11, fraction .1101=0.8125). BCD max digit = 9 NOT 15. Booth's = binary MULTIPLICATION.
2. **Conversion Rules**: Dec→Any: divide by base, read remainders bottom-to-top. Binary→Octal: group 3 bits. Binary→Hex: group 4 bits. Hex: A=10,B=11,C=12,D=13,E=14,F=15. FF hex = 255 decimal.
3. **INC Core Sessions**: 1885 Bombay (founded, A.O. Hume, W.C. Bonnerjee). 1907 Surat (Split: Moderates vs Extremists). 1917 (Annie Besant, first woman). 1924 Belgaum (Gandhi only). 1929 Lahore (Purna Swaraj, Nehru). 1931 Karachi (Karachi Resolution).
4. **Viceroys Key Chain**: Canning (first,1858) → Dalhousie (Doctrine of Lapse+Railway) → Curzon (Bengal Partition 1905) → Hardinge II (Annulled+Capital Delhi 1911) → Chelmsford (Rowlatt+JBagh 1919) → Irwin (Salt March+Pact 1931) → Linlithgow (longest,8 yrs) → Mountbatten (last,1947).
5. **Most Common Traps**: 1234 hex = 4D2 (not 4E2). Purna Swaraj = LAHORE not Karachi. Partition of Bengal = Curzon, Annulment = Hardinge II. Rowlatt Act = Chelmsford not Irwin. Bengal Famine 1943 = Linlithgow. Annie Besant = British not Indian.

---

## 📅 DAY 66 PREVIEW — What's Coming Next:
**CS**: Digital Electronics — Flip-Flops (SR, JK, D, T flip-flops), MUX (Multiplexer: select lines for 4:1 and 8:1 MUX), PLA (Programmable Logic Array), ROM types (MROM, PROM, EPROM, EEPROM), Error detection codes (Hamming, CRC, Checksum)
**GS**: Science & Technology — Green Hydrogen (electrolysis), Recent tech developments (ISRO missions, AI policy), Space technology basics

---

*🚀 Day 65 of 170 — Number system conversions are the most straightforward scoring topic in Digital Electronics — once you memorize the three key facts (1234 in all bases + 1011.1101 + BCD max=9), you can guarantee those marks. The INC Sessions + Viceroys section is one of the HIGHEST weightage history topics in BPSC TRE GS — these facts appear in every paper. You are now completing Week 10 — Phase 2 is fully underway! 🎯*
