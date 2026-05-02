# 📅 BPSC TRE 4.0 — DAY 77: MEMORY TYPES + BIOLOGY (PLANT TOPICS)
### Week 12 — Computer Architecture + Software Engineering
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): CS — RAM, ROM variants, Buffer Registers, PCI Bus, SCSI, ASCII vs EBCDIC
> - Afternoon (1 hr): GS — Biology: Plant Topics (Photoperiodism, Ginger, Reproduction, Anther, Diaphragm)
> - Evening (1.5 hrs): Solve all 50 Mixed MCQs (25 CS + 25 GS)
> - Night (30 min): Read the "Last 1-Hour Before Exam" revision sheet

---

# PART 1: CS RAPID REVISION
## 📘 Memory Types, Buffer Registers & I/O Interfaces — All Concepts, One Place

---

## 🔷 TOPIC 1: RAM — Random Access Memory

### What is RAM?
```
RAM = Random Access Memory
    = Primary / Main Memory
    = VOLATILE (loses all data when power is off)
    = used to hold currently running programs and data

"Random Access" = any memory location can be accessed directly
                  in the SAME time, regardless of location
                  (unlike sequential storage like tape)
```

### SRAM vs DRAM — Master Comparison:
```
FEATURE            SRAM                        DRAM
──────────────────────────────────────────────────────────────────
Full Form          Static RAM                  Dynamic RAM
Speed              FASTER ← key fact           SLOWER
Cost               MORE EXPENSIVE              CHEAPER
Density            Lower density               Higher density
                   (fewer cells per chip)      (more cells per chip)
Refresh needed?    NO (static — holds data)    YES (must refresh
                                               periodically)
Power consumption  Higher                      Lower
Used for           CACHE memory                MAIN memory (RAM slots)
Construction       Uses flip-flops (6 transistors) Uses capacitors (1 T + 1 C)
Volatile?          YES (both are volatile)     YES (both are volatile)

EXAM MEMORY AID:
  SRAM = Static = Speedy = Specialty (expensive) = used in CACHE
  DRAM = Dynamic = needs refresh = Dense = cheap = used in RAM sticks
──────────────────────────────────────────────────────────────────

KEY PYQ TRAPS:
  TRAP 1: "SRAM is non-volatile" → FALSE (SRAM IS volatile)
  TRAP 2: "DRAM is faster than SRAM" → FALSE (SRAM is faster)
  TRAP 3: "Cache uses DRAM" → FALSE (Cache uses SRAM)
  TRAP 4: "Main memory uses SRAM" → FALSE (Main memory uses DRAM)
```

---

## 🔷 TOPIC 2: ROM — Read Only Memory

### What is ROM?
```
ROM = Read Only Memory
    = NON-VOLATILE (retains data even without power) ← key property
    = Contents set at manufacture or by special process
    = Used to store firmware and permanent instructions
    = CPU can READ from ROM but normally cannot WRITE to it
```

### ROM Types — Complete Reference:
```
TYPE     FULL NAME                        KEY PROPERTY
──────────────────────────────────────────────────────────────────────
MROM     Masked ROM                       Programmed at MANUFACTURE;
                                          cannot be changed EVER
                                          Cheapest for large quantities
                                          Example: early calculator chips

PROM     Programmable ROM                 Blank from factory;
                                          programmed ONCE by user
                                          (using PROM programmer / burner)
                                          Once written → PERMANENT (like MROM)
                                          Cannot be erased

EPROM    Erasable Programmable ROM        Can be ERASED using
                                          ULTRAVIOLET (UV) LIGHT ← PYQ trap
                                          Has a quartz window on chip (to let UV in)
                                          After UV erase → can be reprogrammed
                                          UV = Ultraviolet (NOT X-ray, NOT electricity)

EEPROM   Electrically Erasable            Can be erased using
         Programmable ROM                 ELECTRICAL SIGNALS ← key difference
                                          No UV light needed
                                          Can erase BYTE by BYTE (selective)
                                          More convenient than EPROM
                                          Flash memory = type of EEPROM
                                          Used in: USB drives, SSDs, BIOS chips

──────────────────────────────────────────────────────────────────────

EVOLUTION: MROM → PROM → EPROM → EEPROM (each more flexible than previous)

KEY PYQ FACT: EPROM erased by UV LIGHT | EEPROM erased by ELECTRICITY
```

### ROM Quick Reference Card:
```
ROM TYPE   WRITE once?   Erase method       Selective erase?
MROM       At factory    Cannot erase       NO
PROM       By user once  Cannot erase       NO
EPROM      Multiple      UV Light           NO (entire chip)
EEPROM     Multiple      Electrical signal  YES (byte by byte)
Flash      Multiple      Electrical signal  YES (block by block)
```

### Flash Memory (Special Note):
```
Flash Memory = advanced type of EEPROM
  → Erased electrically in BLOCKS (not byte by byte like EEPROM)
  → Faster than EEPROM for large-scale operations
  → Used in: USB drives, SSDs, memory cards (SD cards), smartphones
  → Combines benefits: non-volatile + electrically reprogrammable

PYQ TRAP: "Flash is same as EEPROM" → PARTIALLY true; flash IS a type
          of EEPROM but erases in BLOCKS, not bytes
```

---

## 🔷 TOPIC 3: Buffer Registers — Bridging Speed Gaps

### What Are Buffer Registers?
```
Buffer Register = Temporary storage register that holds data
                  during transfer between devices of DIFFERENT speeds

PRIMARY PURPOSE: Overcome the DIFFERENCE IN DATA TRANSFER SPEED
                 between two devices ← #1 PYQ FACT — exact language!

ANALOGY: Like a waiting room at a doctor's office
  → Fast CPU produces data faster than slow printer can print
  → Buffer holds the data until printer is ready
  → CPU doesn't have to wait — it can continue other work

WHERE USED:
  CPU ↔ Keyboard    (keyboard is very slow vs CPU)
  CPU ↔ Printer     (printer is slow vs CPU)
  CPU ↔ Hard disk   (disk I/O is slow vs CPU)
  Network buffers   (network speed varies)

TYPES OF BUFFERS:
  Hardware buffer = physical register on I/O device
  Software buffer = area in RAM reserved for buffering
```

### Buffer vs Cache — Exam Distinction:
```
BUFFER                           CACHE
──────────────────────────────────────────────────────────────
Overcomes SPEED DIFFERENCE       Reduces average ACCESS TIME
between two devices              for frequently used data
Temporary holding area           Stores COPIES of frequently
during transfer                  used data for fast reuse
Used at I/O interfaces           Used between CPU and RAM
Data passes THROUGH buffer       Data may STAY in cache for reuse
ONE-TIME use per data item        Data can be reused multiple times

PYQ TRAP: "Buffer register stores frequently used data for fast access"
          → FALSE — that describes CACHE, not buffer register!
          Buffer = speed difference | Cache = frequently used data
```

---

## 🔷 TOPIC 4: PCI Bus — Extending the Processor Bus

### What is PCI Bus?
```
PCI = Peripheral Component Interconnect

PURPOSE: Extends the CONNECTIVITY of the PROCESSOR BUS ← #1 PYQ FACT
         (exact exam language — memorize!)

FUNCTION:
  → Provides a standard interface for connecting peripheral devices
    to the CPU bus system
  → Connects: graphics cards, sound cards, network cards, storage
  → Bridges between the fast processor bus and slower peripherals

PROCESSOR BUS (Front-Side Bus):
  → Direct connection between CPU and main memory
  → Very fast but has limited connectivity for peripherals
  → PCI bus EXTENDS this connectivity to more devices

KEY HIERARCHY:
  CPU ←→ Processor Bus (FSB) ←→ PCI Bus ←→ Peripheral Devices
                                            (GPU, NIC, Sound, etc.)

PCI VERSIONS:
  PCI      → Original, 32-bit, 33 MHz, 133 MB/s
  PCI-X    → Extended PCI, 64-bit, up to 1 GB/s
  PCIe     → PCI Express; current standard; serial, much faster
```

### PCI vs Other Buses:
```
BUS TYPE    PURPOSE                                   EXAM KEY
────────────────────────────────────────────────────────────────
PCI bus     Extends connectivity of PROCESSOR BUS     ← PYQ fact
SCSI bus    Small Computer System Interface
            → for STORAGE DEVICES (HDD, tape drives)
            → Serial Attached SCSI (SAS) = modern version
USB         Universal Serial Bus → general peripherals
ISA         Industry Standard Architecture → legacy (older PCs)
AGP         Accelerated Graphics Port → for graphics cards (older)
────────────────────────────────────────────────────────────────

KEY PYQ: "Which bus extends processor bus connectivity?" → PCI
         "SCSI is used for?" → STORAGE devices
```

---

## 🔷 TOPIC 5: SCSI Bus

### What is SCSI?
```
SCSI = Small Computer System Interface

PURPOSE: Interface standard for connecting STORAGE DEVICES to a computer
         (Hard disk drives, tape drives, optical drives, scanners)

KEY FACTS:
  → Primarily used for STORAGE devices ← exam fact
  → Can connect multiple SCSI devices in a CHAIN (daisy-chain)
  → Each device has a unique SCSI ID (0–7 or 0–15)
  → Faster than older ATA/IDE interfaces
  → Serial Attached SCSI (SAS) = modern version used in servers

COMPARE:
  SCSI → storage devices (HDD, tape drives)
  USB  → general peripherals (keyboard, mouse, printer, drives)
  PCI  → expansion cards inside the computer (GPU, NIC)
```

---

## 🔷 TOPIC 6: ASCII vs EBCDIC vs ANSI — Character Encodings

### Complete Comparison Table:
```
ENCODING    FULL NAME                           KEY FACTS
──────────────────────────────────────────────────────────────────────
ASCII       American Standard Code for          7-BIT code
            Information Interchange             128 characters (2⁷)
                                                Converts KEYSTROKE → BITS
                                                'A'=65, 'a'=97, '0'=48
                                                Standard for modern PCs
                                                Subset of Unicode

Extended    Extended ASCII                      8-BIT code
ASCII                                           256 characters (2⁸)
                                                Adds special chars and symbols

EBCDIC      Extended Binary Coded Decimal       8-BIT code (IBM standard)
            Interchange Code                    Used on IBM MAINFRAMES
                                                DIFFERENT encoding from ASCII
                                                ('A' is NOT 65 in EBCDIC!)
                                                Older; rarely used today

ANSI        American National Standards         NOT an encoding itself!
            Institute                           Standards BODY / organization
                                                Sets standards (like ASCII)
                                                "ANSI encoding" loosely refers
                                                to Windows-1252 code page

Unicode     Universal Character Set             Variable-width (UTF-8, UTF-16)
                                                Supports ALL world languages
                                                ASCII is a SUBSET of Unicode
                                                UTF-8 = most common on internet

BCD         Binary Coded Decimal                4-bit representation of
                                                decimal digits 0–9 only
                                                Max digit = 9 (NOT 10 or F)
──────────────────────────────────────────────────────────────────────

KEY PYQ FACTS:
  1. ASCII = 7-bit (NOT 8-bit)
  2. EBCDIC = IBM 8-bit (different from ASCII)
  3. ANSI = standards organization (NOT a character encoding per se)
  4. ASCII converts KEYSTROKE into corresponding BITS
  5. Unicode is SUPERSET of ASCII
  6. BCD max = 9 (only 0–9 represented)
```

---

## 🔷 TOPIC 7: Multiple Buses — Extending Connectivity

### Bus Hierarchy in a Computer:
```
COMPUTER BUS SYSTEM — OVERVIEW

Level 1 (Fastest):
  PROCESSOR BUS (Front-Side Bus / FSB)
  → Connects CPU directly to RAM and chipset
  → Highest speed bus in system

Level 2:
  PCI BUS / PCI Express
  → EXTENDS processor bus connectivity ← PYQ language
  → Connects expansion cards (GPU, NIC, sound)
  → Multiple devices can share the bus

Level 3:
  PERIPHERAL BUSES
  → USB (general peripherals)
  → SATA / SCSI (storage devices)
  → I²C, SPI (embedded / sensor buses)

WHY MULTIPLE BUSES?
  → CPU bus is very fast but limited connections
  → Multiple buses EXTEND the number of devices CPU can communicate with
  → Different buses optimized for different speed requirements

KEY PYQ: "Multiple buses are used to ___?"
  → Extend PROCESSOR BUS CONNECTIVITY ← exact answer expected
```

---

## 📊 CS MASTER COMPARISON TABLE

```
TOPIC             KEY FACT                               COMMON TRAP
──────────────────────────────────────────────────────────────────────
SRAM              Faster; used in CACHE; expensive       NOT non-volatile
DRAM              Slower; needs refresh; used in RAM     NOT faster than SRAM
MROM              Programmed at factory; permanent       Cannot change at all
PROM              User programs ONCE; permanent          Only ONCE — then fixed
EPROM             Erase with UV LIGHT; has quartz window NOT electricity, NOT X-ray
EEPROM            Erase with ELECTRICITY; byte by byte   NOT UV light
Flash             Type of EEPROM; erases in BLOCKS       Blocks (not bytes like EEPROM)
Buffer register   Overcomes SPEED DIFFERENCE             NOT for frequently used data
Cache             Stores frequently used data            NOT for speed-gap bridging
PCI bus           Extends PROCESSOR BUS connectivity     NOT processor bus itself
SCSI bus          For STORAGE devices                    NOT general peripherals
ASCII             7-bit; keystroke → bits                NOT 8-bit
EBCDIC            IBM 8-bit; different from ASCII        NOT same as ASCII
ANSI              Standards BODY (organization)          NOT a character encoding
Unicode           Superset of ASCII                      ASCII is subset, not superset
──────────────────────────────────────────────────────────────────────
```

---
---

# PART 2: GS RAPID REVISION
## 🌿 Biology — Plant Topics (BPSC PYQ Coverage)

---

## 🔷 TOPIC 1: Photoperiodism — Garner & Allard

```
PHOTOPERIODISM = Response of plants to the DURATION OF LIGHT
                 (length of day / night) that triggers flowering

DISCOVERED BY: W.W. GARNER and H.A. ALLARD (1920) ← PYQ tested!
               (Scientists at USDA, USA)

THREE TYPES OF PLANTS based on photoperiodism:

TYPE                 DEFINITION                    EXAMPLE
────────────────────────────────────────────────────────────────────
Short-Day Plants     Flower when day length         Chrysanthemum,
(Long-Night Plants)  is SHORTER than a critical     Cotton, Tobacco,
                     period (long dark period)       Soybean, Rice
                     (need long nights to flower)

Long-Day Plants      Flower when day length          Wheat, Barley,
(Short-Night Plants) EXCEEDS critical period         Spinach, Pea,
                     (need short nights to flower)   Oats, Radish

Day-Neutral Plants   Flowering NOT affected by       Tomato, Cucumber,
                     day length (flower regardless   Corn/Maize, Sunflower
                     of light duration)              Cotton (some varieties)
────────────────────────────────────────────────────────────────────

KEY FACTS:
  → It is actually the DARK PERIOD (night length) that matters most
  → Short-day plants = need LONG NIGHTS (not necessarily short days)
  → Critical period = threshold day/night length for each plant type
  → Plant hormone PHYTOCHROME detects day/night length

PYQ TRAP: "Photoperiodism discovered by Darwin" → FALSE
          "Photoperiodism is response to temperature" → FALSE (that is VERNALIZATION)
          Photoperiodism = light duration | Vernalization = cold temperature
```

---

## 🔷 TOPIC 2: Ginger — Underground Stem

```
GINGER (Zingiber officinale)

KEY FACT: Ginger is an UNDERGROUND STEM ← PYQ tested!
          Specifically = RHIZOME (a type of underground stem)

HOW TO IDENTIFY AS STEM (not root):
  ✅ Has NODES and INTERNODES   ← main proof it's a stem, not root
  ✅ Has scale leaves (modified leaves at nodes)
  ✅ Has buds that can develop into new plants
  ✅ Can photosynthesize (turns green in light)
  ❌ Roots do NOT have nodes and internodes

OTHER EXAMPLES OF UNDERGROUND STEMS (rhizomes):
  Ginger, Turmeric (Haldi), Fern, Lotus (Kamal)

OTHER TYPES OF MODIFIED STEMS:
  Bulb    = Onion, Garlic (underground modified bud)
  Corm    = Colocasia/Arvi (solid, no distinct internodes)
  Tuber   = Potato (underground stem tuber) ← common trap!
  Stolon  = Strawberry (horizontal above-ground runner)

PYQ TRAP: "Ginger is a ROOT" → FALSE (it is an underground STEM / rhizome)
          "Potato is a root" → FALSE (potato is a STEM TUBER)
          Proof: both have NODES and INTERNODES = characteristic of STEM
```

---

## 🔷 TOPIC 3: Asexual Reproduction — Budding (Yeast)

```
ASEXUAL REPRODUCTION = Reproduction WITHOUT fusion of gametes
                      = Single parent; offspring genetically identical

BUDDING:
  → New organism grows as a BUD from the parent organism
  → Bud eventually detaches and becomes independent individual
  → Example: YEAST (unicellular fungus) ← PYQ tested!
  → Also in: Hydra (freshwater animal)

OTHER ASEXUAL REPRODUCTION TYPES:
TYPE          ORGANISM             MECHANISM
────────────────────────────────────────────────────────────
Budding       YEAST, Hydra         Bud grows, detaches
Binary fission Bacteria, Amoeba   Cell divides into 2 equal halves
Fragmentation  Spirogyra, Planaria Breaks into fragments, each grows
Spore formation Bread mould(Rhizopus), Fern  Spores germinate
Vegetative     Potato, Ginger     Underground stem parts grow
reproduction
Regeneration   Planaria, Starfish  Cut parts regenerate whole organism
────────────────────────────────────────────────────────────

PYQ TRAP: "Yeast reproduces by binary fission" → FALSE (BUDDING)
          "Bacteria reproduce by budding" → FALSE (BINARY FISSION)
```

---

## 🔷 TOPIC 4: Parts of a Flower — Anther & Pollen

```
FLOWER PARTS — REPRODUCTIVE STRUCTURES

STAMEN = MALE reproductive organ of flower
  → Consists of: FILAMENT (stalk) + ANTHER (tip)
  → ANTHER = part that CONTAINS POLLEN GRAINS ← PYQ tested!
  → Pollen grains = male gametophytes (contain male gametes)

PISTIL/CARPEL = FEMALE reproductive organ
  → Consists of: STIGMA (top) + STYLE (tube) + OVARY (base)
  → STIGMA = receives pollen grains during pollination
  → OVARY contains OVULES
  → OVULE contains the EGG CELL (female gamete)

DIAGRAM:
       ANTHER ← pollen grains here
          |
       FILAMENT      ← together = STAMEN (male)
          |
  STIGMA ← pollen lands here
     |
  STYLE
     |
  OVARY ← ovules here     ← together = PISTIL (female)
     |
  OVULE → contains egg cell

POLLINATION:
  Self-pollination  = pollen from same flower / same plant
  Cross-pollination = pollen from different plant of same species
  Agents: Wind, Insects, Water, Birds (WIIB)

FERTILIZATION:
  Pollen grain germinates on stigma → pollen tube grows down style
  → Male gamete travels through pollen tube to ovule
  → Fertilization in ovule → SEED forms
  → Ovary wall → becomes FRUIT

PYQ TRAPS:
  "Stigma contains pollen grains" → FALSE (ANTHER contains pollen)
  "Filament contains pollen" → FALSE (ANTHER does)
  "Ovary is part of stamen" → FALSE (ovary is part of PISTIL)
```

---

## 🔷 TOPIC 5: Diaphragm — Role in Respiration

```
DIAPHRAGM = Dome-shaped muscular sheet separating chest and abdomen

NORMAL BREATHING (Quiet Respiration):

INHALATION (breathing IN):
  → Diaphragm CONTRACTS and FLATTENS ← PYQ tested!
  → Ribcage moves up and out
  → Chest volume INCREASES
  → Air pressure inside lungs DECREASES
  → Air rushes IN (from high pressure outside)

EXHALATION (breathing OUT):
  → Diaphragm RELAXES and returns to DOME shape
  → Ribcage moves down and in
  → Chest volume DECREASES
  → Air pressure inside increases
  → Air pushed OUT

KEY PYQ FACT:
  During NORMAL INHALATION → Diaphragm is FLATTENED ← tested!
  "During normal respiration, the diaphragm is flattened" = TRUE ✅

PYQ TRAP: "Diaphragm is relaxed during inhalation" → FALSE
          (Diaphragm CONTRACTS / flattens during inhalation)
          "Diaphragm domes upward during inhalation" → FALSE
          (It domes upward during EXHALATION)
```

---

## 🔷 TOPIC 6: Additional Biology Facts (PYQ-Tested)

```
TOPIC                 FACT                              PYQ SOURCE
────────────────────────────────────────────────────────────────────
Immunity              LYMPHOCYTES are the most          TRE papers
                      important cells for immunity
                      (B-lymphocytes = antibodies;
                       T-lymphocytes = cellular immunity)

Silent Valley          Kerala; famous for rare           TRE papers
                      flora and fauna; tropical
                      rainforest; no dams built
                      due to conservation protests

Antacid               Medicine for INDIGESTION          TRE papers
                      Neutralizes excess stomach acid
                      (HCl) using bases like
                      Mg(OH)₂ or Al(OH)₃

Vas deferens          Part of MALE reproductive         TRE papers
                      system (NOT female)
                      Carries sperm from testis
                      to urethra

Stomata               Tiny pores on leaves              NCERT Class 10
                      Function: gas exchange + transpiration
                      Guard cells OPEN stomata in light
                      Guard cells CLOSE stomata in dark

Chlorophyll           Green pigment in chloroplasts     NCERT Class 10
                      Absorbs light for photosynthesis
                      Absorbs RED and BLUE light most
                      Reflects GREEN light (hence leaves appear green)

Photosynthesis        6CO₂ + 6H₂O → C₆H₁₂O₆ + 6O₂     NCERT Class 10
equation              Occurs in CHLOROPLASTS
                      Light-dependent stage: in thylakoid
                      Light-independent (Calvin cycle): in stroma

Root pressure         Force that pushes water upward    NCERT Class 10
                      in plants
                      Active process (uses energy)

Transpiration         Loss of water vapor from leaves   NCERT Class 10
                      Occurs through STOMATA mainly
                      Creates suction pulling water up
────────────────────────────────────────────────────────────────────
```

---

## 🔷 TOPIC 7: Plant Hormones — Quick Reference

```
HORMONE          FUNCTION                              KEY FACT
────────────────────────────────────────────────────────────────────
Auxin            Cell elongation; phototropism         Produced at shoot tip
                 (bending toward light)                IAA = Indole Acetic Acid
Gibberellin      Stem elongation; seed germination;    Promotes growth
                 breaks dormancy
Cytokinin        Cell DIVISION; delays leaf aging      Promotes cell division
Abscisic Acid    Inhibits growth; CLOSES STOMATA;      "Stress hormone"
(ABA)            induces dormancy                      Closes stomata in drought
Ethylene         Fruit ripening; leaf abscission       GAS hormone (only gaseous)
                 (falling)
────────────────────────────────────────────────────────────────────

PHYTOCHROME = pigment that detects light duration → role in photoperiodism
AUXIN causes phototropism: more auxin on shaded side → that side grows more
→ plant bends TOWARD light (positive phototropism)
```

---
---

# PART 3: PRACTICE QUESTIONS
## 📝 MIXED MCQs — Day 77 Topics

---

### COMPUTER SCIENCE — 25 MCQs

---

**Q1.** Which type of RAM is FASTER and used in CACHE memory?
(A) DRAM (Dynamic RAM)
(B) SRAM (Static RAM)
(C) EEPROM
(D) More than one of the above
(E) None of the above

---

**Q2.** DRAM (Dynamic RAM) requires periodic refreshing because:
(A) It uses flip-flops that need constant clock signals
(B) It stores charge in CAPACITORS which leak and need recharging
(C) It generates too much heat during operation
(D) More than one of the above
(E) None of the above

---

**Q3.** Which ROM type is erased using ULTRAVIOLET (UV) LIGHT?
(A) EEPROM
(B) PROM
(C) EPROM
(D) More than one of the above
(E) None of the above

---

**Q4.** Which ROM type can be erased using ELECTRICAL SIGNALS and supports byte-by-byte erasure?
(A) EPROM
(B) MROM
(C) EEPROM
(D) More than one of the above
(E) None of the above

---

**Q5.** The PRIMARY purpose of a buffer register is to:
(A) Store frequently accessed data for faster CPU access
(B) Overcome the difference in data transfer SPEED between two devices
(C) Extend the connectivity of the processor bus
(D) More than one of the above
(E) None of the above

---

**Q6.** Which of the following CORRECTLY describes the PCI bus?
(A) It is used to connect STORAGE devices like HDD and tape drives
(B) It extends the CONNECTIVITY of the PROCESSOR BUS
(C) It is a standard interface for USB peripherals
(D) More than one of the above
(E) None of the above

---

**Q7.** SCSI (Small Computer System Interface) is primarily used for:
(A) Connecting graphic cards and sound cards
(B) Connecting STORAGE DEVICES such as HDDs and tape drives
(C) Extending the processor bus to peripherals
(D) More than one of the above
(E) None of the above

---

**Q8.** ASCII is a _____-bit encoding standard that converts _____ into corresponding bits.
(A) 8-bit; keypresses
(B) 7-bit; keystrokes
(C) 6-bit; binary digits
(D) More than one of the above
(E) None of the above

---

**Q9.** EBCDIC is:
(A) A 7-bit encoding standard used in modern PCs
(B) Another name for Extended ASCII
(C) An 8-bit IBM character encoding standard (used on mainframes)
(D) More than one of the above
(E) None of the above

---

**Q10.** ANSI in the context of character encoding refers to:
(A) An 8-bit encoding similar to EBCDIC
(B) An American standards body / organization (not an encoding itself)
(C) A 16-bit Unicode-compatible encoding
(D) More than one of the above
(E) None of the above

---

**Q11.** Which of the following is TRUE about SRAM?
(A) SRAM is slower but cheaper than DRAM
(B) SRAM is used in main memory (RAM slots in a PC)
(C) SRAM is volatile and faster than DRAM; used in cache
(D) More than one of the above
(E) None of the above

---

**Q12.** Which ROM type is programmed permanently at the time of MANUFACTURE and cannot be changed?
(A) PROM
(B) EPROM
(C) MROM (Masked ROM)
(D) More than one of the above
(E) None of the above

---

**Q13.** Flash memory is best described as:
(A) A type of RAM that retains data without power
(B) A type of EEPROM that erases in BLOCKS (not byte by byte)
(C) A type of EPROM erased by UV light
(D) More than one of the above
(E) None of the above

---

**Q14.** Multiple buses in a computer system are used to:
(A) Reduce the speed of data transfer between components
(B) Extend the connectivity of the processor bus
(C) Replace the need for cache memory
(D) More than one of the above
(E) None of the above

---

**Q15.** Which of the following is NON-VOLATILE memory?
(A) SRAM
(B) DRAM
(C) ROM (all types)
(D) More than one of the above
(E) None of the above

---

**Q16.** The difference between BUFFER and CACHE can be stated as:
(A) Buffer = stores frequently used data; Cache = bridges speed gap
(B) Buffer = bridges speed gap between devices; Cache = stores frequently used data
(C) Both serve the same purpose with different names
(D) More than one of the above
(E) None of the above

---

**Q17.** PROM (Programmable ROM) differs from MROM in that:
(A) PROM is programmed at manufacture; MROM by the user
(B) PROM can be erased with UV light; MROM cannot
(C) PROM is programmed ONCE by the USER; MROM is programmed at manufacture
(D) More than one of the above
(E) None of the above

---

**Q18.** Unicode is related to ASCII in which way?
(A) ASCII is a superset of Unicode
(B) ASCII is a SUBSET of Unicode (Unicode includes ASCII)
(C) Unicode and ASCII use the same bit-length encoding
(D) More than one of the above
(E) None of the above

---

**Q19.** Which of the following correctly orders ROM types from LEAST to MOST flexible (reprogrammability)?
(A) MROM → PROM → EPROM → EEPROM
(B) EEPROM → EPROM → PROM → MROM
(C) PROM → MROM → EPROM → EEPROM
(D) More than one of the above
(E) None of the above

---

**Q20.** A hardware buffer at an I/O port is most useful when:
(A) The CPU and the I/O device operate at the same speed
(B) The CPU produces data FASTER than the I/O device can process it
(C) The I/O device is faster than the CPU
(D) More than one of the above
(E) None of the above

---

**Q21.** BCD (Binary Coded Decimal) can represent decimal digits from:
(A) 0 to 15 (0 to F in hex)
(B) 0 to 9 only
(C) 0 to 7 only
(D) More than one of the above
(E) None of the above

---

**Q22.** The EPROM chip has a quartz window because:
(A) It allows the user to view the stored data
(B) It allows ULTRAVIOLET LIGHT to pass through for erasure
(C) It provides ventilation to prevent overheating
(D) More than one of the above
(E) None of the above

---

**Q23.** Which of the following is TRUE about both SRAM and DRAM?
(A) Both are volatile (lose data when power is off)
(B) Both require periodic refreshing
(C) Both are used in cache memory
(D) More than one of the above
(E) None of the above

---

**Q24.** SCSI devices in a chain are differentiated using:
(A) MAC addresses
(B) IP addresses
(C) Unique SCSI IDs (0–7 or 0–15)
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following is the CORRECT relationship between PCI bus and the processor bus?
(A) PCI bus IS the processor bus
(B) PCI bus EXTENDS the connectivity of the processor bus
(C) PCI bus REPLACES the processor bus in modern systems
(D) More than one of the above
(E) None of the above

---
---

### GENERAL STUDIES — 25 MCQs
### Biology — Plant Topics

---

**Q26.** Photoperiodism was discovered by:
(A) Darwin and Wallace
(B) Garner and Allard
(C) Mendel and Morgan
(D) More than one of the above
(E) None of the above

---

**Q27.** Photoperiodism in plants refers to their response to:
(A) Temperature changes during seasons
(B) Duration of light (length of day/night) triggering flowering
(C) Availability of water and nutrients
(D) More than one of the above
(E) None of the above

---

**Q28.** Plants that flower when the day length is SHORTER than a critical period are called:
(A) Long-day plants
(B) Day-neutral plants
(C) Short-day plants
(D) More than one of the above
(E) None of the above

---

**Q29.** Which of the following is an example of a SHORT-DAY plant?
(A) Wheat
(B) Chrysanthemum
(C) Tomato
(D) More than one of the above
(E) None of the above

---

**Q30.** Ginger is botanically classified as:
(A) A root (taproot)
(B) An underground stem (rhizome)
(C) A modified leaf
(D) More than one of the above
(E) None of the above

---

**Q31.** Which feature PROVES that ginger is a STEM and not a root?
(A) It grows underground
(B) It has nodes and internodes
(C) It stores food
(D) More than one of the above
(E) None of the above

---

**Q32.** Which of the following is ALSO an underground stem (rhizome)?
(A) Carrot
(B) Radish
(C) Turmeric (Haldi)
(D) More than one of the above
(E) None of the above

---

**Q33.** Yeast reproduces asexually by:
(A) Binary fission
(B) Fragmentation
(C) Budding
(D) More than one of the above
(E) None of the above

---

**Q34.** Which part of the stamen CONTAINS POLLEN GRAINS?
(A) Filament
(B) Stigma
(C) Anther
(D) More than one of the above
(E) None of the above

---

**Q35.** Pollen grains land on which part of the pistil during pollination?
(A) Ovary
(B) Style
(C) Stigma
(D) More than one of the above
(E) None of the above

---

**Q36.** During normal INHALATION (breathing in), the diaphragm:
(A) Relaxes and moves upward (dome shape)
(B) Contracts and FLATTENS
(C) Remains unchanged; only ribs move
(D) More than one of the above
(E) None of the above

---

**Q37.** Which cells are MOST IMPORTANT for the body's IMMUNITY?
(A) Red Blood Cells (RBCs)
(B) Platelets
(C) Lymphocytes
(D) More than one of the above
(E) None of the above

---

**Q38.** Silent Valley National Park, famous for rare flora and fauna, is located in:
(A) Karnataka
(B) Tamil Nadu
(C) Kerala
(D) More than one of the above
(E) None of the above

---

**Q39.** Antacid medicines work by:
(A) Killing bacteria in the stomach
(B) Neutralizing excess stomach acid (HCl) using a base
(C) Stimulating more acid production
(D) More than one of the above
(E) None of the above

---

**Q40.** Vas deferens is part of which reproductive system?
(A) Female reproductive system
(B) Male reproductive system
(C) Both male and female
(D) More than one of the above
(E) None of the above

---

**Q41.** Stomata in leaves are primarily responsible for:
(A) Absorbing water from soil
(B) Gas exchange and transpiration (water vapor loss)
(C) Producing chlorophyll
(D) More than one of the above
(E) None of the above

---

**Q42.** Why do plant leaves appear GREEN?
(A) Chlorophyll absorbs green light and reflects all others
(B) Chlorophyll absorbs red and blue light but REFLECTS green light
(C) Chlorophyll produces green pigment as a waste product
(D) More than one of the above
(E) None of the above

---

**Q43.** Which plant hormone is responsible for CLOSING STOMATA during drought/stress?
(A) Auxin
(B) Ethylene
(C) Abscisic Acid (ABA)
(D) More than one of the above
(E) None of the above

---

**Q44.** Which is the ONLY GASEOUS plant hormone that promotes fruit ripening and leaf fall?
(A) Gibberellin
(B) Cytokinin
(C) Ethylene
(D) More than one of the above
(E) None of the above

---

**Q45.** Phototropism (bending of plant toward light) is caused by unequal distribution of which hormone?
(A) Gibberellin
(B) Cytokinin
(C) Auxin
(D) More than one of the above
(E) None of the above

---

**Q46.** In the equation: 6CO₂ + 6H₂O → C₆H₁₂O₆ + 6O₂, what process is represented?
(A) Respiration
(B) Transpiration
(C) Photosynthesis
(D) More than one of the above
(E) None of the above

---

**Q47.** The potato is a modified:
(A) Root (taproot tuber)
(B) Leaf (modified storage leaf)
(C) Stem (underground stem tuber)
(D) More than one of the above
(E) None of the above

---

**Q48.** Which organism reproduces by BINARY FISSION?
(A) Yeast
(B) Hydra
(C) Bacteria (e.g. Amoeba)
(D) More than one of the above
(E) None of the above

---

**Q49.** MATCH THE FOLLOWING — Plant parts and their type:
```
Plant Part      Type
1. Ginger       A. Underground stem tuber
2. Potato       B. Rhizome (underground stem)
3. Onion        C. Root (taproot)
4. Carrot       D. Bulb (modified bud)
```
(A) 1-B, 2-A, 3-D, 4-C
(B) 1-A, 2-B, 3-C, 4-D
(C) 1-B, 2-D, 3-A, 4-C
(D) More than one of the above
(E) None of the above

---

**Q50.** Which of the following correctly describes VERNALIZATION (to distinguish from photoperiodism)?
(A) Vernalization = response to LIGHT duration to trigger flowering
(B) Vernalization = response to prolonged COLD TEMPERATURE to trigger flowering
(C) Vernalization = response to WATER availability for germination
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY

## ⚠️ MANDATORY: Attempt all 50 questions BEFORE checking!

---

### CS Answers (Q1–Q25):

| Q  | Answer | Reason (one-line)                                                        |
|----|--------|--------------------------------------------------------------------------|
| 1  | (B)    | SRAM = faster, expensive, used in CACHE (DRAM = slower, used in main RAM)|
| 2  | (B)    | DRAM uses capacitors that leak charge → must be refreshed periodically   |
| 3  | (C)    | EPROM = Erasable Programmable ROM; erased by UV LIGHT (quartz window)    |
| 4  | (C)    | EEPROM = Electrically Erasable; erased by electricity, byte by byte      |
| 5  | (B)    | Buffer register = overcomes SPEED DIFFERENCE between devices             |
| 6  | (B)    | PCI bus = extends CONNECTIVITY of the PROCESSOR BUS ← exact PYQ language|
| 7  | (B)    | SCSI = Small Computer System Interface = for STORAGE devices             |
| 8  | (B)    | ASCII = 7-bit standard; converts KEYSTROKES into bits                    |
| 9  | (C)    | EBCDIC = IBM 8-bit character encoding used on mainframes                 |
| 10 | (B)    | ANSI = standards organization/body (not an encoding itself)              |
| 11 | (C)    | SRAM = volatile + faster than DRAM + used in cache memory                |
| 12 | (C)    | MROM = Masked ROM = programmed at manufacture, cannot be changed         |
| 13 | (B)    | Flash = type of EEPROM that erases in BLOCKS (not byte by byte)          |
| 14 | (B)    | Multiple buses = to EXTEND processor bus connectivity                    |
| 15 | (C)    | All ROM types = NON-VOLATILE (retain data without power)                 |
| 16 | (B)    | Buffer = speed difference between devices; Cache = frequently used data  |
| 17 | (C)    | PROM = programmed ONCE by user; MROM = programmed at manufacture         |
| 18 | (B)    | ASCII is a SUBSET of Unicode (Unicode is the superset)                   |
| 19 | (A)    | MROM(fixed)→PROM(once)→EPROM(UV)→EEPROM(electric) = increasing flex.    |
| 20 | (B)    | Buffer most useful when CPU is FASTER than the I/O device                |
| 21 | (B)    | BCD represents decimal digits 0–9 ONLY (not 0–15 like hex)              |
| 22 | (B)    | Quartz window on EPROM allows UV light to pass through for erasure       |
| 23 | (A)    | Both SRAM and DRAM are VOLATILE (lose data when power off)               |
| 24 | (C)    | SCSI devices differentiated by unique SCSI IDs (0–7 or 0–15)            |
| 25 | (B)    | PCI bus EXTENDS the connectivity of the processor bus                    |

---

### GS Answers (Q26–Q50):

| Q  | Answer | Reason (one-line)                                                      |
|----|--------|------------------------------------------------------------------------|
| 26 | (B)    | Photoperiodism discovered by GARNER and ALLARD (1920) ← PYQ tested    |
| 27 | (B)    | Photoperiodism = response to DURATION OF LIGHT triggering flowering    |
| 28 | (C)    | Short-day plants = flower when day < critical period (long nights)     |
| 29 | (B)    | Chrysanthemum = classic short-day plant (Wheat = long-day; Tomato = neutral)|
| 30 | (B)    | Ginger = underground STEM (rhizome) — NOT a root                       |
| 31 | (B)    | Nodes and internodes = proof it is a STEM not a root                   |
| 32 | (C)    | Turmeric (Haldi) = rhizome = underground stem (Carrot/Radish = roots)  |
| 33 | (C)    | Yeast = reproduces by BUDDING (not binary fission — that's bacteria)   |
| 34 | (C)    | ANTHER contains pollen grains (Filament = stalk; Stigma = female part) |
| 35 | (C)    | STIGMA receives pollen during pollination (top of pistil)              |
| 36 | (B)    | During inhalation = diaphragm CONTRACTS and FLATTENS                   |
| 37 | (C)    | LYMPHOCYTES = most important cells for immunity (B-cells + T-cells)    |
| 38 | (C)    | Silent Valley National Park = KERALA                                   |
| 39 | (B)    | Antacid = neutralizes excess HCl in stomach using a BASE               |
| 40 | (B)    | Vas deferens = MALE reproductive system (carries sperm)                |
| 41 | (B)    | Stomata = gas exchange AND transpiration (both functions)              |
| 42 | (B)    | Chlorophyll absorbs red+blue, REFLECTS green → leaves appear green     |
| 43 | (C)    | Abscisic Acid (ABA) = stress hormone; CLOSES stomata during drought    |
| 44 | (C)    | Ethylene = only GASEOUS hormone; promotes fruit ripening + leaf fall   |
| 45 | (C)    | AUXIN = causes phototropism (unequal distribution = bending toward light)|
| 46 | (C)    | 6CO₂ + 6H₂O → C₆H₁₂O₆ + 6O₂ = PHOTOSYNTHESIS equation               |
| 47 | (C)    | Potato = underground STEM TUBER (has nodes+internodes = proof of stem) |
| 48 | (C)    | Bacteria (and Amoeba) = BINARY FISSION (Yeast=budding; Hydra=budding)  |
| 49 | (A)    | Ginger=B(rhizome), Potato=A(stem tuber), Onion=D(bulb), Carrot=C(root)|
| 50 | (B)    | Vernalization = response to prolonged COLD to trigger flowering        |

---
---

# 🔁 FINAL REVISION NOTES
## 📌 "Last 1-Hour Before Exam" — Ultra-Crisp Format

---

### ⚡ CS — 30 MUST-KNOW FACTS (Memory Types + Buses)

```
RAM TYPES:
1.  SRAM = Static RAM = FASTER = used in CACHE = expensive = no refresh
2.  DRAM = Dynamic RAM = SLOWER = used in MAIN MEMORY = cheap = needs refresh
3.  BOTH SRAM and DRAM are VOLATILE (lose data at power-off)
4.  TRAP: "SRAM is non-volatile" → FALSE | "Cache uses DRAM" → FALSE

ROM TYPES (least to most flexible — memorize this order!):
5.  MROM   = Programmed at MANUFACTURE; cannot change EVER
6.  PROM   = Programmed ONCE by user; then permanent
7.  EPROM  = Erased by UV LIGHT (quartz window on chip); reprogrammable
8.  EEPROM = Erased by ELECTRICITY; byte-by-byte erasure; most flexible
9.  Flash  = Type of EEPROM; erases in BLOCKS (not bytes); used in USB/SSD
10. All ROM types = NON-VOLATILE (retain data without power)

BUFFER REGISTER:
11. Buffer = overcomes DIFFERENCE IN DATA TRANSFER SPEED ← exact PYQ language
12. Buffer vs Cache: Buffer = speed gap | Cache = frequently used data
13. TRAP: "Buffer stores frequently used data" → FALSE (that's CACHE)

PCI BUS:
14. PCI bus = EXTENDS CONNECTIVITY OF PROCESSOR BUS ← exact PYQ language
15. PCI connects: graphics cards, sound cards, network cards
16. SCSI = Small Computer System Interface = for STORAGE DEVICES (HDD, tape)
17. Multiple buses purpose = to EXTEND processor bus connectivity

CHARACTER ENCODINGS:
18. ASCII  = 7-bit (NOT 8-bit!) | 128 chars | 'A'=65 | 'a'=97 | '0'=48
19. EBCDIC = IBM 8-bit | mainframes | DIFFERENT from ASCII
20. ANSI   = standards ORGANIZATION (not an encoding itself)
21. Unicode = superset of ASCII | supports all world languages
22. ASCII converts KEYSTROKE into corresponding BITS ← PYQ language
23. Extended ASCII = 8-bit | BCD = 0–9 only (max digit = 9)

EXAM TRAPS (most tested):
24. "DRAM is faster than SRAM" → WRONG; SRAM is faster
25. "EPROM erased by electricity" → WRONG; UV LIGHT erases EPROM
26. "EEPROM erased by UV light" → WRONG; ELECTRICITY erases EEPROM
27. "Buffer stores frequently used data" → WRONG; that's CACHE
28. "SCSI extends processor bus" → WRONG; PCI does that; SCSI = storage
29. "ASCII is 8-bit" → WRONG; ASCII is 7-BIT
30. "ANSI is a character encoding" → WRONG; ANSI is a standards body
```

---

### ⚡ GS — 30 MUST-KNOW FACTS (Biology — Plant Topics)

```
PHOTOPERIODISM:
1.  Discovered by GARNER and ALLARD (1920) ← PYQ tested!
2.  = Response to DURATION OF LIGHT (day/night length) for flowering
3.  Short-day plants = flower when days SHORT (long nights needed)
    Examples: Chrysanthemum, Cotton, Tobacco, Rice, Soybean
4.  Long-day plants = flower when days LONG (short nights needed)
    Examples: Wheat, Barley, Spinach, Pea, Oats
5.  Day-neutral = not affected by light duration
    Examples: Tomato, Cucumber, Corn, Sunflower
6.  Vernalization = response to COLD (different from photoperiodism!)
7.  Phytochrome = pigment that detects light duration in leaves

UNDERGROUND STEMS:
8.  Ginger = UNDERGROUND STEM (rhizome) — NOT a root ← PYQ tested!
9.  Proof: has NODES and INTERNODES = characteristic of STEM not root
10. Turmeric (Haldi) = also rhizome | Lotus = also rhizome
11. Potato = STEM TUBER (underground stem) — also has nodes+internodes
12. Onion = BULB (modified bud with fleshy leaves)
13. Carrot, Radish = TRUE ROOTS (no nodes/internodes)

ASEXUAL REPRODUCTION:
14. Yeast = BUDDING ← PYQ tested!
15. Bacteria, Amoeba = BINARY FISSION
16. Spirogyra, Planaria = FRAGMENTATION
17. Bread mould (Rhizopus) = SPORE FORMATION

FLOWER PARTS:
18. ANTHER = contains POLLEN GRAINS ← PYQ tested!
19. Filament + Anther = STAMEN (male organ)
20. Stigma + Style + Ovary = PISTIL (female organ)
21. STIGMA receives pollen | OVARY contains ovules | OVULE → SEED

RESPIRATION:
22. During INHALATION → diaphragm CONTRACTS and FLATTENS ← PYQ tested!
23. During EXHALATION → diaphragm RELAXES and domes upward

IMMUNITY & MEDICINE:
24. LYMPHOCYTES = most important cells for immunity ← PYQ tested!
25. Silent Valley = KERALA (rare flora and fauna)
26. Antacid = neutralizes excess HCl (stomach acid)
27. Vas deferens = MALE reproductive system

PLANT HORMONES:
28. AUXIN = phototropism (bending toward light)
29. ABA (Abscisic Acid) = CLOSES stomata during drought (stress hormone)
30. ETHYLENE = only GASEOUS hormone; fruit ripening + leaf fall
```

---

### ⚡ LAST-MINUTE COMPARISON TABLES

```
RAM TYPE    SPEED      USED IN      REFRESH?    COST
────────────────────────────────────────────────────────
SRAM        Faster     CACHE        No          Expensive
DRAM        Slower     Main RAM     YES         Cheap
────────────────────────────────────────────────────────

ROM TYPE    Programmed by   Erased by        Selective?
────────────────────────────────────────────────────────
MROM        Factory         Cannot erase     NO
PROM        User (once)     Cannot erase     NO
EPROM       User            UV LIGHT         NO (whole chip)
EEPROM      User            Electricity      YES (byte by byte)
Flash       User            Electricity      YES (block by block)
────────────────────────────────────────────────────────

BUS        PURPOSE                          PYQ ANSWER
────────────────────────────────────────────────────────
PCI        Extends processor bus            ← connectivity
SCSI       Storage devices (HDD, tape)      ← storage
USB        General peripherals              ← universal
────────────────────────────────────────────────────────

ENCODING   BITS    USED BY              KEY FACT
────────────────────────────────────────────────────────
ASCII      7       Modern PCs           Keystroke → bits
Extended   8       Modern PCs           256 chars
EBCDIC     8       IBM Mainframes       Different from ASCII
Unicode    Var     All systems          Superset of ASCII
BCD        4       Digit 0–9 only       Max = 9
────────────────────────────────────────────────────────

PLANT         TYPE                    PROOF
────────────────────────────────────────────────────────
Ginger        Underground STEM        Nodes+internodes
Turmeric      Underground STEM        Nodes+internodes
Potato        Stem TUBER              Nodes+internodes (eyes!)
Onion         BULB                    Fleshy leaf scales
Carrot/Radish TRUE ROOT               No nodes/internodes
────────────────────────────────────────────────────────
```

---

## 🎯 DAY 77 COMPLETE — WHAT YOU'VE MASTERED TODAY

```
CS:   RAM (SRAM vs DRAM) | ROM (MROM, PROM, EPROM, EEPROM, Flash)
      Buffer Registers (speed difference) | PCI Bus (extends processor bus)
      SCSI (storage devices) | ASCII (7-bit) vs EBCDIC (IBM 8-bit) vs ANSI
      Multiple buses (extend connectivity) | Unicode (superset of ASCII)

GS:   Photoperiodism (Garner & Allard) — short/long/day-neutral plants
      Ginger = underground stem (nodes+internodes proof)
      Yeast = budding | Anther = pollen grains
      Diaphragm flattens on inhalation | Lymphocytes = immunity
      Plant hormones (Auxin, ABA, Ethylene) | Vernalization vs Photoperiodism

NEXT: Day 78 — TRE 2.0 FULL PYQ PAPER PRACTICE
      Solve all 80 CS questions from TRE 2.0 paper
      Compare results with TRE 1.0; note new/repeated topics
```

---

*Day 77 of 170 | Phase 2: Depth | Week 12: Computer Architecture + Software Engineering*
*BPSC TRE 4.0 Preparation | Target: TOP 50 RANK | Score: 130+/150*
