# 📅 BPSC TRE 4.0 — DAY 69: PAGING + CHAMPARAN SATYAGRAHA (DEEP DIVE)
### Week 11 — Memory Management: Paging, TLB, Address Translation, Internal Fragmentation
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): CS — Paging, Page Table, TLB, Address Translation, Offset Calculation
> - Afternoon (1 hr): GS — Champaran Satyagraha 1917 (Complete Deep Dive)
> - Evening (1.5 hrs): Solve all 50 MCQs
> - Night (30 min): Read the Night Revision Sheet

---

# PART 1: CS CONCEPT NOTES
## 📘 Memory Management — PAGING (Complete Deep Dive)

---

## 🔷 TOPIC 1: WHY DO WE NEED MEMORY MANAGEMENT AT ALL?

Before understanding paging, you MUST understand the PROBLEM it solves.

```
THE PROBLEM WITHOUT MEMORY MANAGEMENT:
═══════════════════════════════════════════════════════════════════

Imagine RAM has 100 MB free in three scattered chunks:
  ┌──────────────────────────────────────────────────────┐
  │ [Process A: 20MB] [FREE: 15MB] [Process B: 30MB]     │
  │ [FREE: 25MB] [Process C: 10MB] [FREE: 10MB]          │
  └──────────────────────────────────────────────────────┘

Total free = 15 + 25 + 10 = 50 MB

Now a Process D needs 40 MB.
Can it load? → NO! Even though 50 MB is free, no CONTIGUOUS 40 MB block exists.

This is called EXTERNAL FRAGMENTATION = free memory is present but SCATTERED.

PAGING SOLVES THIS.
How? By NOT requiring the process to be in contiguous memory!
A process can be split into pieces and stored in scattered physical memory locations.
```

---

## 🔷 TOPIC 2: WHAT IS PAGING? — The Core Concept

```
PAGING = A memory management technique that:
  → Divides LOGICAL (virtual) memory into fixed-size blocks called PAGES
  → Divides PHYSICAL memory into fixed-size blocks called FRAMES
  → Maps each PAGE to a FRAME using a PAGE TABLE

KEY RULE: Page size = Frame size (they are ALWAYS equal!)

VISUAL DIAGRAM:
═══════════════════════════════════════════════════════════════════

LOGICAL MEMORY                    PHYSICAL MEMORY (RAM)
(Process's view)                  (Actual hardware)

┌──────────────────┐              ┌──────────────────┐
│  Page 0 (4KB)    │──────────►  │  Frame 3 (4KB)   │  ← Page 0 stored in Frame 3
├──────────────────┤              ├──────────────────┤
│  Page 1 (4KB)    │──────────►  │  Frame 7 (4KB)   │  ← Page 1 stored in Frame 7
├──────────────────┤              ├──────────────────┤
│  Page 2 (4KB)    │──────────►  │  Frame 1 (4KB)   │  ← Page 2 stored in Frame 1
├──────────────────┤              ├──────────────────┤
│  Page 3 (4KB)    │──────────►  │  Frame 9 (4KB)   │  ← Page 3 stored in Frame 9
└──────────────────┘              └──────────────────┘

Notice: Pages 0,1,2,3 are NOT in sequential frames (3,7,1,9)!
The process sees CONTIGUOUS logical memory,
but physically it is stored SCATTERED across RAM.
This is the MAGIC of paging — process doesn't know or care.

═══════════════════════════════════════════════════════════════════

KEY DEFINITIONS:
  PAGE  = fixed-size block of LOGICAL (virtual) memory
  FRAME = fixed-size block of PHYSICAL memory (RAM)
  Page size = Frame size (always equal — this is fundamental!)
  Page Table = data structure that maps Page Number → Frame Number
```

---

## 🔷 TOPIC 3: PAGE TABLE — The Heart of Paging

```
PAGE TABLE = A per-process data structure maintained by the OS
             Maps each logical page number to a physical frame number

STRUCTURE OF A PAGE TABLE ENTRY (PTE):
═══════════════════════════════════════════════════════════════════

  Each entry in the page table contains:

  ┌─────────┬────────┬───────────┬──────────┬───────────────────┐
  │  Frame  │ Valid  │  Modified │  Access  │    Protection     │
  │ Number  │  Bit   │   Bit (M) │  Bit (R) │    Bits (R/W/X)   │
  └─────────┴────────┴───────────┴──────────┴───────────────────┘

  Frame Number  = actual frame in RAM where this page is stored
  Valid Bit (V) = 1 → page is in memory | 0 → page is on disk (causes page fault!)
  Modified Bit  = 1 → page has been modified (dirty page) — needs write-back
  Access Bit    = 1 → page has been recently accessed (for page replacement)
  Protection    = Read/Write/Execute permissions

═══════════════════════════════════════════════════════════════════

EXAMPLE PAGE TABLE:

  Page Number │ Frame Number │ Valid Bit
  ────────────┼──────────────┼──────────
       0      │      3       │    1      ← Page 0 is in Frame 3, in memory
       1      │      7       │    1      ← Page 1 is in Frame 7, in memory
       2      │      1       │    1      ← Page 2 is in Frame 1, in memory
       3      │      —       │    0      ← Page 3 is NOT in memory (on disk!)
                                            Accessing this → PAGE FAULT

PAGE TABLE IS STORED IN MAIN MEMORY (RAM).
  → The page table base register (PTBR) points to the page table in RAM.
  → This means EVERY memory access requires TWO memory accesses:
      First access:  Read page table from RAM (to find frame number)
      Second access: Access actual data in the frame
  → This is SLOW → TLB solves this (see Topic 5)
```

---

## 🔷 TOPIC 4: LOGICAL ADDRESS STRUCTURE — How Addresses Work

```
LOGICAL ADDRESS = Address generated by CPU (what the program uses)
PHYSICAL ADDRESS = Actual address in RAM (what hardware uses)

THE KEY INSIGHT:
  Logical Address = Page Number  +  Page Offset
                   (which page?) (where within the page?)

LOGICAL ADDRESS STRUCTURE:
═══════════════════════════════════════════════════════════════════

  ┌─────────────────────────────┬──────────────────────────────┐
  │      Page Number (p)        │      Page Offset (d)         │
  │  (upper bits of address)    │   (lower bits of address)    │
  └─────────────────────────────┴──────────────────────────────┘

HOW ADDRESS TRANSLATION WORKS:
  Step 1: Extract Page Number from logical address (upper bits)
  Step 2: Look up Page Table using Page Number → get Frame Number
  Step 3: Physical Address = Frame Number + same Page Offset (d)

  ┌──────────────────────────────────────────────────────────┐
  │  Logical Address: [Page Number p | Offset d]             │
  │         ↓ (use p to index into page table)               │
  │  Page Table: p → Frame Number f                          │
  │         ↓                                                │
  │  Physical Address: [Frame Number f | Offset d]           │
  └──────────────────────────────────────────────────────────┘

IMPORTANT: The OFFSET (d) is NEVER changed during translation!
           Only the page number part changes to frame number.
           The offset tells "where within the page/frame" and stays the same.
```

---

## 🔷 TOPIC 5: PAGE OFFSET CALCULATION — THE #1 PYQ TOPIC

```
THIS IS THE MOST TESTED CALCULATION IN BPSC TRE — MASTER IT!

FORMULA:
  If Page Size = 2ⁿ bytes  →  Offset requires n bits
  Number of offset bits = log₂(Page Size in bytes)

STANDARD CALCULATIONS (ALL MEMORIZE!):
═══════════════════════════════════════════════════════════════════

  Page Size    │  2^? = Size  │  Offset Bits  │  Reason
  ─────────────┼──────────────┼───────────────┼──────────────────
  1 KB (1024)  │  2¹⁰ = 1024  │    10 bits    │  2¹⁰ = 1024 = 1KB
  2 KB (2048)  │  2¹¹ = 2048  │    11 bits    │  2¹¹ = 2048 = 2KB
  4 KB (4096)  │  2¹² = 4096  │    12 bits    │  2¹² = 4096 = 4KB  ← MOST TESTED!
  8 KB (8192)  │  2¹³ = 8192  │    13 bits    │  2¹³ = 8192 = 8KB
  16 KB        │  2¹⁴ = 16384 │    14 bits    │  2¹⁴ = 16384 = 16KB
  64 KB        │  2¹⁶ = 65536 │    16 bits    │  2¹⁶ = 65536 = 64KB

  ★ MUST MEMORIZE: 4KB page → 12-bit offset (2¹² = 4096)
  ★ MUST MEMORIZE: 1KB page → 10-bit offset (2¹⁰ = 1024)
  ★ MUST MEMORIZE: 8KB page → 13-bit offset (2¹³ = 8192)

═══════════════════════════════════════════════════════════════════

WHY DOES PAGE SIZE = POWER OF 2?
  Because offset bits are lower bits of binary address.
  If page size = 4KB = 4096 = 2¹², then the last 12 bits of any
  logical address automatically give the offset within the page.
  The remaining higher bits give the page number.
  This makes hardware address translation VERY FAST (just bit splitting).

WORKED EXAMPLE:
  Logical address space = 32-bit, Page size = 4KB (2¹²)
  
  Offset bits = 12 (for 4KB page)
  Page number bits = 32 - 12 = 20 bits
  
  Number of pages = 2²⁰ = 1,048,576 pages
  
  For logical address = 0x00003A2F (binary: 0000 0000 0000 0000 0011 1010 0010 1111)
    Lower 12 bits (offset) = 1010 0010 1111 = A2F (hex)
    Upper 20 bits (page number) = 0000 0000 0000 0000 0011 = page 3
  
  Look up page table: Page 3 → Frame 5 (say)
  Physical address = Frame 5 at offset A2F = 0x005A2F
```

---

## 🔷 TOPIC 6: TLB — Translation Lookaside Buffer (THE #1 PYQ TRAP)

```
THE PROBLEM WITH PAGE TABLES:
  Page table is stored in RAM.
  Every memory access = 2 RAM accesses (1 for page table + 1 for actual data).
  This DOUBLES the memory access time → very slow!

SOLUTION: TLB (Translation Lookaside Buffer)
═══════════════════════════════════════════════════════════════════

TLB = A small, ultra-fast HARDWARE CACHE that stores
      RECENTLY USED page table entries (page → frame mappings)

  → Located INSIDE the CPU (or very close to it)
  → Much faster than RAM (typically ~1-2 nanoseconds vs ~100ns for RAM)
  → Stores only a subset of page table entries (typically 32–1024 entries)

TLB ORGANIZATION = ASSOCIATIVE CACHE (not direct-mapped or set-associative RAM!)
  ← THIS IS THE #1 BPSC TRE PYQ TRAP! ALWAYS "ASSOCIATIVE CACHE"

WHY "ASSOCIATIVE"?
  In a regular cache, you look up by INDEX (like an array index).
  In an ASSOCIATIVE cache, you look up by CONTENT (match the page number).
  All TLB entries are searched SIMULTANEOUSLY (parallel lookup) using the page number.
  This is called CONTENT ADDRESSABLE MEMORY (CAM).

TLB STRUCTURE:
  ┌─────────────────┬────────────────┐
  │   Page Number   │  Frame Number  │
  ├─────────────────┼────────────────┤
  │       0         │       3        │
  │       1         │       7        │
  │       5         │       2        │
  │       8         │      11        │
  └─────────────────┴────────────────┘
  (All entries searched simultaneously when looking up a page number)

═══════════════════════════════════════════════════════════════════

HOW TLB WORKS — STEP BY STEP:

  CPU generates logical address with page number p and offset d.

  STEP 1: Search TLB for page number p
  
      TLB HIT (page found in TLB):
        → Get frame number f directly from TLB
        → Physical address = f + d
        → FAST: only 1 memory access (TLB access is near-zero time)
      
      TLB MISS (page NOT in TLB):
        → Go to page table in RAM
        → Get frame number f from page table
        → Load this entry into TLB (for future use)
        → Physical address = f + d
        → SLOW: 2 memory accesses (page table in RAM + actual data)

  DIAGRAM:
  ════════════════════════════════════════════════════════
  CPU generates address [p | d]
         │
         ▼
  ┌─────────────┐    HIT (found!)
  │   TLB       │─────────────────────────────────► Frame f
  │  (search p) │                                      │
  └─────────────┘                                      │ combine with offset d
         │ MISS (not found)                            │
         ▼                                             ▼
  ┌─────────────┐                             Physical Address [f | d]
  │  Page Table │──────────────────────────►       (access RAM)
  │  in RAM     │ (also load into TLB)
  └─────────────┘
  ════════════════════════════════════════════════════════

TLB KEY FACTS (PYQ SUMMARY):
  ★ TLB = organized as ASSOCIATIVE CACHE ← exact phrase used in PYQ
  ★ TLB = fast-access hardware cache for page table entries
  ★ TLB hit → only 1 memory access needed (very fast)
  ★ TLB miss → 2 memory accesses (page table + data)
  ★ TLB uses parallel (associative) lookup — searches ALL entries simultaneously
  ★ TLB is inside/near CPU; page table is in main memory (RAM)
  ★ TLB is small (limited entries); page table is large (all pages)

EFFECTIVE ACCESS TIME (EAT) WITH TLB:
  Let:
    h = TLB hit ratio (e.g., 0.9 = 90% of pages found in TLB)
    t = TLB access time (near zero, usually ignored)
    m = RAM access time

  EAT = h × (t + m) + (1-h) × (t + 2m)
      ≈ h × m + (1-h) × 2m   (if t ≈ 0)
      = m × (2 - h)

  Example: If hit ratio = 90%, RAM access = 100ns
    EAT = 0.9 × 100 + 0.1 × 200 = 90 + 20 = 110 ns
    Without TLB: always 200ns → TLB saves 45% time!
```

---

## 🔷 TOPIC 7: PAGE FAULT — What Happens When a Page is Not in RAM

```
PAGE FAULT = An interrupt/exception raised when the CPU tries to access
             a page that is NOT currently in physical memory (RAM)
             (i.e., the VALID BIT in the page table entry is 0)

The page exists — it's just on the DISK (secondary memory), not in RAM.

PAGE FAULT HANDLING STEPS:
═══════════════════════════════════════════════════════════════════

  1. CPU accesses logical address → looks up page table
  2. Valid bit = 0 → PAGE FAULT INTERRUPT is raised
  3. OS page fault handler takes over (traps to OS)
  4. OS finds the needed page on DISK (in swap space)
  5. OS finds a FREE FRAME in RAM
     (If no free frame → must EVICT an existing page using a replacement algorithm)
  6. OS loads the page from disk into the free frame in RAM
  7. OS updates the page table:
       - Frame number set to new frame
       - Valid bit set to 1
  8. TLB updated with new mapping
  9. CPU RESTARTS the instruction that caused the page fault
  10. This time: page table entry is valid → normal execution continues

WHY PAGE FAULT IS EXPENSIVE:
  → Disk access is 1,000,000× slower than RAM access
  → Each page fault can take milliseconds
  → If too many page faults → THRASHING (covered in Day 70)

PAGE REPLACEMENT ALGORITHMS (brief intro):
  When all frames are full and a new page must be loaded:
  
  FIFO  = Replace the page that has been in memory the LONGEST
  LRU   = Replace the page that was LEAST RECENTLY USED
  OPT   = Replace the page that will NOT be used for the LONGEST TIME in future
          (Optimal but impractical — we can't predict the future)
  LRU approximation: Second-Chance algorithm (uses reference bit)

BELADY'S ANOMALY:
  → Occurs with FIFO page replacement only
  → More frames → MORE page faults (counter-intuitive!)
  → LRU and OPT do NOT suffer from Belady's anomaly
  ← PYQ TRAP: "Belady's anomaly" = FIFO algorithm
```

---

## 🔷 TOPIC 8: INTERNAL FRAGMENTATION IN PAGING

```
INTERNAL FRAGMENTATION = Wasted space INSIDE an allocated page/frame
                         because the process doesn't need the full page

HOW IT HAPPENS:
═══════════════════════════════════════════════════════════════════

  Process needs 13 KB.
  Page size = 4 KB.

  Pages needed = ceil(13 / 4) = 4 pages (= 16 KB allocated)
  Space actually used = 13 KB
  WASTED space = 16 - 13 = 3 KB

  This 3 KB is INSIDE the last page (Page 3) — hence INTERNAL fragmentation.

  ┌──────────────────────┐
  │ Page 0: 4KB (full)   │  ← all used
  ├──────────────────────┤
  │ Page 1: 4KB (full)   │  ← all used
  ├──────────────────────┤
  │ Page 2: 4KB (full)   │  ← all used
  ├──────────────────────┤
  │ Page 3: 4KB          │  ← only 1 KB used
  │  [1KB USED | 3KB WASTED] ← INTERNAL FRAGMENTATION
  └──────────────────────┘

═══════════════════════════════════════════════════════════════════

KEY RELATIONSHIP:
  SMALLER page size → LESS internal fragmentation
                    → BUT MORE pages → LARGER page table!

  LARGER page size  → MORE internal fragmentation (up to page_size - 1)
                    → BUT FEWER pages → SMALLER page table!

  Designers choose page size to balance these trade-offs (typically 4KB).

INTERNAL vs EXTERNAL FRAGMENTATION COMPARISON:
  ─────────────────────────────────────────────────────────────────
  INTERNAL FRAGMENTATION:
    → Occurs INSIDE allocated memory blocks
    → Memory is ALLOCATED but partially UNUSED
    → Caused by: FIXED-SIZE allocation (pages, fixed partitions)
    → Present in: PAGING (always some in last page)
    → Solution: Smaller page size (reduces waste per page)

  EXTERNAL FRAGMENTATION:
    → Occurs OUTSIDE allocated memory (between processes)
    → Memory is FREE but SCATTERED (non-contiguous)
    → Caused by: Variable-size allocation (contiguous allocation)
    → Present in: SEGMENTATION, contiguous memory allocation
    → Solution: COMPACTION (move processes together)
    → Also solved by: PAGING (eliminates external fragmentation entirely!)
  ─────────────────────────────────────────────────────────────────

  ★ PAGING: Eliminates external fragmentation, but causes internal fragmentation
  ★ SEGMENTATION: May cause external fragmentation, no internal fragmentation
```

---

## 🔷 TOPIC 9: TYPES OF PAGING

```
1. SIMPLE PAGING (Single-Level Paging):
   → One page table per process
   → Page table itself can be VERY LARGE
   
   Problem: For 32-bit address space with 4KB pages:
     Number of pages = 2³² / 2¹² = 2²⁰ = ~1 million entries
     If each entry = 4 bytes → Page table = 4MB per process!
     For 100 processes → 400MB just for page tables!

2. MULTI-LEVEL PAGING (Hierarchical Paging):
   → Page table split into multiple levels
   → Most common: 2-level or 3-level
   → Only levels that are actually USED are loaded into memory
   → Saves memory for page tables (sparse address spaces)
   
   2-level: Outer Page Table → Inner Page Table → Frame
   Used in: Intel x86 (2-level), x86-64 (4-level)

3. INVERTED PAGE TABLE:
   → Instead of one page table per process (which grows huge),
     ONE page table for the ENTIRE SYSTEM
   → Indexed by FRAME NUMBER (not page number)
   → Entry: (process ID, page number) → frame index
   → Much smaller table size
   → But searching is SLOWER (must search whole table for a match)
   → Used in: IBM's older systems
   
   ← PYQ TRAP: Inverted page table → indexed by frame number (not page number)

4. DEMAND PAGING:
   → Pages loaded into RAM ONLY WHEN NEEDED (on demand)
   → Process starts with 0 pages in memory
   → Pages brought in as page faults occur
   → Advantage: Less memory used (only active pages in RAM)
   → This is how modern OS (Linux, Windows) works
   ← PYQ TRAP: Demand paging → pages loaded only when accessed
```

---

## 🔷 TOPIC 10: COMPLETE NUMERICAL WORKED EXAMPLES

```
EXAMPLE 1: Page offset calculation
═══════════════════════════════════════════════════════════════════
Q: A system has 4KB pages. How many offset bits are needed?

  4KB = 4 × 1024 = 4096 bytes = 2¹²
  Offset bits = 12

A: 12 bits ← answer

───────────────────────────────────────────────────────────────────

EXAMPLE 2: Number of pages in a process
═══════════════════════════════════════════════════════════════════
Q: A process is 18 KB. Page size = 4KB. How many pages?

  Pages = ceil(18 / 4) = ceil(4.5) = 5 pages
  (4 full pages = 16KB, 1 partial page holds remaining 2KB)
  Internal fragmentation = 5 × 4 - 18 = 20 - 18 = 2 KB

A: 5 pages; internal fragmentation = 2 KB

───────────────────────────────────────────────────────────────────

EXAMPLE 3: Physical address from logical address
═══════════════════════════════════════════════════════════════════
Q: Page size = 4KB. Logical address = 20500.
   Page Table: Page 0→Frame 5, Page 1→Frame 3, Page 2→Frame 8, Page 3→Frame 2.
   Find physical address.

  Step 1: Page size = 4KB = 4096 bytes
  Step 2: Page number  = floor(20500 / 4096) = floor(5.005) = 5
          Wait — page 5 not in given table, let me recalculate:
          
  Let me use: Logical address = 8300
  Page number = floor(8300 / 4096) = floor(2.026) = 2
  Offset      = 8300 mod 4096 = 8300 - 2×4096 = 8300 - 8192 = 108

  Page 2 → Frame 8 (from page table)
  Physical address = Frame 8 × 4096 + 108 = 32768 + 108 = 32876

A: Physical address = 32876

───────────────────────────────────────────────────────────────────

EXAMPLE 4: Effective Access Time (EAT)
═══════════════════════════════════════════════════════════════════
Q: TLB hit ratio = 80%, RAM access time = 200ns. TLB access ≈ 0.
   Find Effective Access Time.

  EAT = h × (m) + (1-h) × (2m)
      = 0.8 × 200 + 0.2 × 400
      = 160 + 80
      = 240 ns

  Without TLB: always 2m = 400ns
  With TLB at 80% hit: 240ns → 40% improvement

A: EAT = 240 ns
```

---

## 📊 CS PAGING — MASTER TRAP TABLE

```
TOPIC                   CORRECT FACT                        COMMON TRAP
────────────────────────────────────────────────────────────────────────────
TLB organization        ASSOCIATIVE CACHE                   Students write "general cache"
                        (Content Addressable Memory)        or "direct-mapped cache"

4KB page offset         12 bits (2¹² = 4096)                Students write 10 or 16 bits

1KB page offset         10 bits (2¹⁰ = 1024)                Students write 8 or 12 bits

8KB page offset         13 bits (2¹³ = 8192)                Students write 12 or 14 bits

Internal fragmentation  Waste INSIDE last page              Students confuse with
                        (fixed-size allocation)             external fragmentation

External fragmentation  Scattered free memory               Students confuse with
                        (not caused by paging!)             internal fragmentation

Paging vs External frag Paging ELIMINATES external frag     Students think paging
                        but CAUSES internal frag            has both types

TLB hit                 Only 1 memory access (fast)         Students say 2 accesses

TLB miss                2 memory accesses (slow)            Students say 1 access

Page fault              Valid bit = 0 in page table         Students say it means
                        Page is on disk, not in RAM         the page doesn't exist

Belady's anomaly        Occurs in FIFO replacement only     Students apply to LRU/OPT

Inverted page table     Indexed by FRAME NUMBER             Students say page number

Demand paging           Pages loaded ONLY when needed       Students say all pages
                        (on first page fault)               loaded at process start

Page size vs frag       Larger page → more internal frag    Students think larger
                        Smaller page → less internal frag   page = less fragmentation

Offset in translation   NEVER changes during translation    Students change offset
                        Only page number → frame number     along with page number
────────────────────────────────────────────────────────────────────────────
```

---
---

# PART 2: GS CONCEPT NOTES
## 🏛️ Champaran Satyagraha 1917 — COMPLETE DEEP DIVE
### (Bihar's Most Important Freedom Struggle Event — BPSC HIGHEST PRIORITY)

---

## 🔷 TOPIC 1: BACKGROUND — Why Was Champaran Significant?

```
CHAMPARAN SATYAGRAHA = Gandhi's FIRST SATYAGRAHA IN INDIA (1917)
                     = Beginning of Gandhian Era in India's Freedom Struggle

WHY CHAMPARAN? The Indigo Problem:
═══════════════════════════════════════════════════════════════════

LOCATION:
  Champaran = district in Bihar (now divided into East & West Champaran)
  Motihari = headquarters of East Champaran

THE OPPRESSION — THE TINKATHIA SYSTEM:
  British planters (Nilhe Sahebs = Indigo Planters) forced Indian farmers to:
  → Grow INDIGO (a blue dye plant — not food!) on 3/20 of their land
  → "3 Katha per Bigha" = 3 out of 20 kathas per bigha for indigo
  → Tinkathia = "three katha" (tin = three in Hindi, katha = unit of land)
  → Farmers could NOT refuse — it was COMPULSORY

WHY INDIGO?
  → Europeans needed blue dye for textiles
  → Synthetic dye discovered in Germany (1897) → indigo prices CRASHED
  → British planters now wanted COMPENSATION from farmers to let them out of contracts
  → Farmers were extorted — some had to pay even though the contracts were ending

═══════════════════════════════════════════════════════════════════

WHAT THE FARMERS FACED:
  1. Forced to grow indigo (took best land away from food crops)
  2. Low payment for indigo that barely covered costs
  3. Various illegal taxes and extortion by planters
  4. Violence and intimidation if they resisted
  5. No legal protection — courts favored British planters
  6. Extreme poverty and near-starvation conditions
```

---

## 🔷 TOPIC 2: HOW GANDHI CAME TO CHAMPARAN — The Chain of Events

```
THE JOURNEY TO CHAMPARAN:
═══════════════════════════════════════════════════════════════════

STEP 1: Raj Kumar Shukla's persistence
  → Raj Kumar Shukla = a simple indigo farmer from Champaran
  → He heard about Gandhi's successes in South Africa
  → Attended Lucknow Congress (December 1916) to find Gandhi
  → Followed Gandhi to Kanpur, to Ahmedabad, kept requesting him to come
  → Gandhi was busy, kept saying "come to Cawnpore (Kanpur), I'll decide"
  → Shukla was illiterate but PERSISTENT — Gandhi was moved by his determination
  → Gandhi agreed: "Meet me in Calcutta, I'll come with you"

STEP 2: Arrival at Patna
  → Gandhi arrived at PATNA RAILWAY STATION
  → Was received there by DR. RAJENDRA PRASAD
    ← BPSC HIGH PROBABILITY FACT: Rajendra Prasad received Gandhi in Patna
  → Rajendra Prasad was a prominent lawyer and INC leader in Bihar
  → Gandhi stayed briefly at Rajendra Prasad's residence in Patna

STEP 3: Journey to Motihari
  → Gandhi proceeded to Motihari (East Champaran headquarters)
  → Date of arrival in Motihari: APRIL 15, 1917
    ← BPSC EXAM: Specific date often asked
  → Accompanied by Raj Kumar Shukla and other local workers

STEP 4: The Summons and Defiance
  → British District Magistrate issued a notice to Gandhi:
    "Leave Champaran immediately — you are disturbing the peace"
  → Gandhi REFUSED to leave → "I am here to investigate conditions of farmers"
  → Gandhi wrote to the magistrate: "I will peacefully accept any legal punishment
    but cannot in conscience leave Champaran"
  → The case went to court in Motihari
  → Unprecedented happening: thousands of farmers gathered at the courthouse
  → British authorities were FRIGHTENED by the peaceful mass support for Gandhi
  → Government withdrew the case against Gandhi
  → THIS WAS THE FIRST VICTORY OF SATYAGRAHA IN INDIA

PEOPLE WHO JOINED GANDHI IN CHAMPARAN:
  → Rajendra Prasad (Bihar) — organized volunteers, became Gandhi's right-hand in Bihar
  → Brij Kishore Prasad — senior lawyer from Bihar, organized legal help
  → Mazharul Haque — prominent Bihar lawyer and INC leader
  → J.B. Kripalani (Acharya Kripalani) — later became INC president
  → Anugrah Narayan Sinha — joined as volunteer (later Bihar's first Deputy CM)
  ← Bihar-specific: ALL these were Bihar figures who came together for Champaran
```

---

## 🔷 TOPIC 3: THE INVESTIGATION AND GANDHIAN METHODS

```
GANDHI'S INVESTIGATION PROCESS:
═══════════════════════════════════════════════════════════════════

Gandhi conducted a SYSTEMATIC INQUIRY:
  → Walked from village to village in scorching summer heat
  → Personally interviewed THOUSANDS of farmers
  → Documented cases of exploitation, extortion, violence
  → Trained volunteers (including Rajendra Prasad) to record testimonies
  → Established temporary offices in Motihari and nearby areas

THE SCHOOL PROGRAM:
  → Gandhi also opened PRIMARY SCHOOLS in Champaran villages
  → Brought educated volunteers from other states to teach
  → Focus: basic literacy + hygiene awareness for villagers
  → Gandhi's wife KASTURBA GANDHI also came to Champaran
  → Kasturba conducted health and hygiene workshops for women
  → These schools were among the first village-level educational initiatives

CONSTRUCTIVE PROGRAM IN CHAMPARAN:
  → Village sanitation improvement
  → Women's health and literacy
  → Establishment of schools
  → Organization of farmers into a united body
  ← BPSC CONTEXT: Gandhi's constructive program = key innovation of his movement style

THE REPORT TO GOVERNMENT:
  → British government formed an INQUIRY COMMISSION
  → Due to Gandhi's pressure + mass support + documented evidence
  → Gandhi was appointed as MEMBER of the Champaran Agrarian Committee
    ← Significant: British government included Gandhi in their own inquiry!
  → The committee found widespread exploitation by planters
  → Resulted in the CHAMPARAN AGRARIAN ACT, 1918
```

---

## 🔷 TOPIC 4: CHAMPARAN AGRARIAN ACT 1918 — The Outcome

```
CHAMPARAN AGRARIAN ACT 1918:
═══════════════════════════════════════════════════════════════════

KEY PROVISIONS:
  1. TINKATHIA SYSTEM ABOLISHED ← MOST IMPORTANT RESULT
     → Farmers no longer forced to grow indigo on 3/20 of land
     → The compulsory indigo cultivation contract was legally ended

  2. COMPENSATION TO FARMERS:
     → Farmers who had paid "compensation" to planters (to get out of contracts)
       were to receive 25% REFUND (not 100%, not 50% — exactly 25%)
     ← BPSC TRAP: The refund was 25% of what farmers paid — memorize this
     → This was a compromise (Gandhi originally demanded 50% but accepted 25%)

  3. RIGHT TO GROW FOOD CROPS:
     → Farmers could now freely choose what to grow on their own land
     → British planters could no longer force them to grow indigo

WHAT GANDHI'S VICTORY MEANT:
  → First time British administration was FORCED TO ACT by Indian protest
  → Proved that organized NON-VIOLENT resistance could force the British to retreat
  → Rajendra Prasad later wrote that Champaran changed everything
  → Gandhi became a mass leader — ordinary people could now identify with him
  → Champaran = template for all future Gandhian satyagrahas in India
```

---

## 🔷 TOPIC 5: SIGNIFICANCE — WHY CHAMPARAN MATTERS

```
NATIONAL SIGNIFICANCE:
═══════════════════════════════════════════════════════════════════

1. FIRST SATYAGRAHA IN INDIA:
   → Gandhi had done satyagraha in SOUTH AFRICA before this (1906–1914)
   → But Champaran = first time he applied it on INDIAN SOIL
   ← PYQ TRAP: "First Satyagraha in India" ≠ "First Satyagraha by Gandhi"
   → Gandhi's satyagraha chronology:
     1906 → First satyagraha in SOUTH AFRICA (against registration law)
     1917 → First satyagraha IN INDIA = CHAMPARAN

2. PROOF OF CONCEPT:
   → Proved non-violent civil resistance WORKS against British power
   → Gave Gandhi credibility with Indian masses
   → Showed ordinary farmers could be political actors

3. RAJENDRA PRASAD'S TRANSFORMATION:
   → Before Champaran: Western-educated lawyer, somewhat detached
   → After Champaran: Completely devoted follower of Gandhi
   → Gave up Western clothes, adopted Indian dress
   → Became key organizer of Bihar's freedom movement

4. MASS MOBILIZATION MODEL:
   → First time a nationalist leader came to the VILLAGE and lived with farmers
   → Previous leaders (Tilak, Gokhale) operated mostly in cities
   → Gandhi showed the freedom struggle must involve RURAL INDIA

5. NATIONAL-RURAL CONNECTION:
   → Established that the freedom struggle must address ECONOMIC EXPLOITATION
     not just political rights
   → Combined national freedom with economic justice for farmers

BIHAR-SPECIFIC SIGNIFICANCE:
  → Became a symbol of Bihar's pride in freedom struggle
  → Motihari = pilgrimage site for Congress workers
  → Raj Kumar Shukla became a folk hero of Bihar
  → Rajendra Prasad → from Champaran activist to First President of India
  ← BPSC loves this trajectory: from Champaran to Rashtrapati Bhavan
```

---

## 🔷 TOPIC 6: KEY PEOPLE — COMPLETE FACT TABLE

```
CHAMPARAN KEY PEOPLE — EVERY FACT FOR BPSC
═══════════════════════════════════════════════════════════════════

PERSON              ROLE & KEY FACTS
─────────────────────────────────────────────────────────────────────
Raj Kumar Shukla    → Simple illiterate indigo farmer from Champaran
                    → Heard about Gandhi, tracked him down at Lucknow Congress (1916)
                    → Followed Gandhi to multiple cities, persistently requesting help
                    → Finally convinced Gandhi to come to Champaran
                    → "The man who brought Gandhi to Bihar" ← key description
                    → Symbol of the power of ordinary people in the freedom movement

Mahatma Gandhi      → Arrived Motihari: April 15, 1917
                    → Defied British order to leave Champaran
                    → Conducted village-to-village investigation
                    → Applied satyagraha (non-violent resistance) for first time in India
                    → Was member of Champaran Agrarian Committee
                    → Also established schools and constructive program

Dr. Rajendra Prasad → Received Gandhi at Patna Railway Station ← PYQ FACT
                    → Born: Zeradei, Siwan, Bihar
                    → Initially a Western-educated lawyer
                    → Joined Gandhi's investigation team as volunteer
                    → Champaran transformed him into Gandhi's devoted follower
                    → Later: First President of India (1950–1962)
                    → Founded Bihar Vidyapeeth (1921) during NCM
                    → Book: "India Divided" (against Partition, 1946)

Brij Kishore Prasad → Senior Bihar lawyer who joined Gandhi
                    → Organized legal defense and documentation
                    → Key organizer of Champaran inquiry

J.B. Kripalani      → Educated volunteer who came from another state
                    → Ran schools established by Gandhi in Champaran
                    → Later became President of INC (1946)
                    → Also known as Acharya Kripalani

Kasturba Gandhi     → Gandhi's wife; came to Champaran
                    → Conducted hygiene and health workshops for village women
                    → Died: Aga Khan Palace, Pune, February 22, 1944 (during QIM)

Mazharul Haque      → Prominent Bihar Muslim lawyer and INC leader
                    → Supported Gandhi's investigation
                    → Later founded Sadaqat Ashram, Patna (where Rajendra Prasad died)
                    ← BPSC connection: Rajendra Prasad died at Sadaqat Ashram, Patna (1963)
─────────────────────────────────────────────────────────────────────
```

---

## 🔷 TOPIC 7: COMPLETE TIMELINE — CHAMPARAN 1917

```
COMPLETE CHAMPARAN TIMELINE:
═══════════════════════════════════════════════════════════════════

1860s     Tinkathia system begins as British planters establish
          indigo cultivation contracts in Champaran

1897      Synthetic indigo discovered in Germany → demand for
          natural indigo crashes → planters demand compensation
          from farmers to let them out of contracts → NEW EXTORTION

December  Lucknow Congress Session
1916      → Raj Kumar Shukla meets Gandhi, begs him to come to Champaran
          → Gandhi initially reluctant, tells Shukla to meet him in Calcutta

Early     Shukla meets Gandhi in Calcutta (persisting)
1917      → Gandhi agrees to accompany Shukla to Champaran

April 10, Gandhi arrives in Calcutta; travels toward Bihar
1917

April     Gandhi and Shukla arrive in PATNA
1917      → DR. RAJENDRA PRASAD receives Gandhi at Patna Railway Station
          → Gandhi stays briefly in Patna

April 15, GANDHI ARRIVES IN MOTIHARI (East Champaran)
1917      ← EXACT DATE — frequently tested in BPSC

Same day  British District Magistrate serves notice:
          "Leave Champaran immediately"
          Gandhi writes back: refuses to leave, accepts any legal consequence

Next day  Case filed against Gandhi in Motihari court
          Thousands of farmers arrive at court in spontaneous solidarity
          British administration is alarmed by the peaceful mass support

Days      Government withdraws case against Gandhi
later     → FIRST VICTORY of Satyagraha on Indian soil

April–    Gandhi conducts systematic village-to-village investigation
June      Records testimonies of thousands of farmers
1917      Establishes schools, runs constructive program
          Kasturba arrives, conducts women's workshops
          Rajendra Prasad, Brij Kishore Prasad, J.B. Kripalani all join

Mid-1917  British government forms Champaran Agrarian Committee
          Gandhi appointed as MEMBER of the committee
          (unprecedented: British government including the protesting Indian in their own inquiry)

1918      CHAMPARAN AGRARIAN ACT passed:
          → Tinkathia system ABOLISHED
          → Farmers to receive 25% REFUND of compensation paid to planters
          → Farmers free to grow food crops on their own land

═══════════════════════════════════════════════════════════════════
```

---

## 🔷 COMPARISON: GANDHI'S THREE EARLY SATYAGRAHAS IN INDIA

```
GANDHI'S EARLY INDIA SATYAGRAHAS (1917–1918):
═══════════════════════════════════════════════════════════════════

FEATURE          CHAMPARAN (1917)   KHEDA (1917–18)    AHMEDABAD (1918)
─────────────────────────────────────────────────────────────────────────
Location         Bihar (Motihari)   Gujarat (Kheda)    Gujarat (Ahmedabad)
Issue            Indigo farmers     Crop failure;       Mill workers' wages
                 oppressed by       govt refused to     (textile strike)
                 Tinkathia system   suspend taxes
Against whom     British indigo     British tax         Indian mill owners
                 planters + Govt    collectors          (Ambalal Sarabhai)
Gandhi's role    Investigator,      Led farmers in      Mediated; first
                 organized inquiry  tax non-payment     HUNGER STRIKE by
                                                        Gandhi in India
Result           Tinkathia          Taxes suspended;    Wages increased;
                 abolished;         farmers not         arbitration accepted
                 25% refund         punished
Significance     First Satyagraha   Satyagraha for      First hunger strike
                 IN INDIA           farmers against     by Gandhi
                                    economic injustice
─────────────────────────────────────────────────────────────────────────

SEQUENCE to REMEMBER:
  1917 = Champaran (Bihar) = First Satyagraha in India
  1918 = Kheda (Gujarat) = Farmers' tax protest
  1918 = Ahmedabad (Gujarat) = Mill workers' wages + Gandhi's first hunger strike
```

---

## 🔷 GS MASTER TRAP TABLE — CHAMPARAN

```
STATEMENT                           CORRECT?  EXPLANATION
──────────────────────────────────────────────────────────────────────
"Champaran = Gandhi's first satyagraha"  ✗   First in INDIA only; he did
                                              satyagraha in South Africa from 1906

"Gandhi arrived Champaran in 1917"       ✓   April 15, 1917 specifically

"Raj Kumar Shukla was Gandhi's disciple" ✗   He was a farmer who BROUGHT Gandhi;
                                              not a disciple relationship

"Champaran Agrarian Act gave 50% refund" ✗   Only 25% refund — common error

"Tinkathia = 3/20 of land"              ✓   3 katha per bigha = 3/20

"Rajendra Prasad received Gandhi         ✓   Exact PYQ-tested fact
in Patna"

"Gandhi was arrested at Motihari"        ✗   He was summoned to court (not arrested)
                                              and the case was WITHDRAWN

"Champaran = CDM"                        ✗   Champaran = separate satyagraha (1917)
                                              CDM = 1930 (Salt March/Dandi)

"J.B. Kripalani later became INC        ✓   He was 1946 INC President
president"

"Kasturba Gandhi came to Champaran"      ✓   She conducted women's health workshops
──────────────────────────────────────────────────────────────────────
```

---
---

# PART 3: PRACTICE QUESTIONS
## 📝 MIXED PYQ + CONCEPT MCQs — Day 69 (CS + GS)

---

### COMPUTER SCIENCE — 25 MCQs (Paging & Memory Management)

---

**Q1.** The TLB (Translation Lookaside Buffer) is organized as which type of cache?
(A) Direct-mapped cache
(B) Set-associative cache
(C) Associative cache (Content Addressable Memory)
(D) More than one of the above
(E) None of the above

---

**Q2.** For a system with a page size of 4KB, how many bits are needed for the page offset?
(A) 10 bits
(B) 16 bits
(C) 12 bits
(D) More than one of the above
(E) None of the above

---

**Q3.** In paging, which of the following CORRECTLY defines a FRAME?
(A) A fixed-size block of logical (virtual) memory
(B) A fixed-size block of physical memory (RAM)
(C) A data structure that maps page numbers to frame numbers
(D) More than one of the above
(E) None of the above

---

**Q4.** A process is 22 KB in size. If page size = 4 KB, how much internal fragmentation occurs?
(A) 0 KB
(B) 4 KB
(C) 2 KB
(D) More than one of the above
(E) None of the above

---

**Q5.** What happens when a TLB MISS occurs during address translation?
(A) The process is terminated immediately
(B) The OS looks up the page table in RAM to find the frame number
(C) A page fault is always raised
(D) More than one of the above
(E) None of the above

---

**Q6.** What is a PAGE FAULT?
(A) An error because a page number exceeds the page table size
(B) An interrupt raised when a required page is not in RAM (is on disk)
(C) A memory error because the page is corrupted
(D) More than one of the above
(E) None of the above

---

**Q7.** For a 1KB page size, how many offset bits are needed?
(A) 8 bits
(B) 12 bits
(C) 10 bits
(D) More than one of the above
(E) None of the above

---

**Q8.** What type of fragmentation is caused by PAGING?
(A) External fragmentation (scattered free memory)
(B) Internal fragmentation (wasted space inside pages)
(C) Both internal and external fragmentation equally
(D) More than one of the above
(E) None of the above

---

**Q9.** In the VALID BIT of a page table entry, what does a value of 0 indicate?
(A) The page is in RAM and ready to use
(B) The page has not been modified since loading
(C) The page is NOT in RAM — it is on disk
(D) More than one of the above
(E) None of the above

---

**Q10.** What is the PRIMARY purpose of the TLB in a paging system?
(A) To store the entire page table for fast access
(B) To reduce the number of memory accesses needed for address translation
(C) To handle page faults automatically without OS involvement
(D) More than one of the above
(E) None of the above

---

**Q11.** In address translation using paging, what part of the logical address remains UNCHANGED in the physical address?
(A) The page number
(B) The frame number
(C) The page offset
(D) More than one of the above
(E) None of the above

---

**Q12.** An 8KB page size requires how many offset bits?
(A) 12 bits
(B) 14 bits
(C) 13 bits
(D) More than one of the above
(E) None of the above

---

**Q13.** Which page replacement algorithm suffers from Belady's Anomaly?
(A) LRU (Least Recently Used)
(B) OPT (Optimal)
(C) FIFO (First In First Out)
(D) More than one of the above
(E) None of the above

---

**Q14.** In demand paging, pages are loaded into memory:
(A) All at once when the process is first scheduled
(B) Only when they are actually accessed (on page fault)
(C) Periodically in batches by a background process
(D) More than one of the above
(E) None of the above

---

**Q15.** What does the MODIFIED BIT (dirty bit) in a page table entry indicate?
(A) The page has been recently accessed
(B) The page contains executable code
(C) The page has been modified since it was loaded from disk
(D) More than one of the above
(E) None of the above

---

**Q16.** Paging ELIMINATES which type of fragmentation but CAUSES which type?
(A) Eliminates internal; causes external
(B) Eliminates external; causes internal
(C) Eliminates both types completely
(D) More than one of the above
(E) None of the above

---

**Q17.** In an INVERTED PAGE TABLE, the table is indexed by:
(A) Page number
(B) Process ID
(C) Frame number
(D) More than one of the above
(E) None of the above

---

**Q18.** If TLB hit ratio = 90% and main memory access time = 100ns (TLB access ≈ 0), the Effective Access Time (EAT) is:
(A) 190 ns
(B) 100 ns
(C) 110 ns
(D) More than one of the above
(E) None of the above

---

**Q19.** The page table is stored in:
(A) CPU registers
(B) TLB only
(C) Main memory (RAM)
(D) More than one of the above
(E) None of the above

---

**Q20.** What is the relationship between page size and internal fragmentation?
(A) Larger page size → less internal fragmentation per page
(B) Smaller page size → more internal fragmentation per page
(C) Larger page size → more internal fragmentation (up to page_size - 1 bytes wasted)
(D) More than one of the above
(E) None of the above

---

**Q21.** Multi-level paging is used primarily to:
(A) Increase the speed of TLB lookups
(B) Reduce the memory consumed by storing large page tables
(C) Eliminate the need for address translation entirely
(D) More than one of the above
(E) None of the above

---

**Q22.** For a 32-bit address space with 4KB pages, how many bits are used for the page number?
(A) 12 bits
(B) 32 bits
(C) 20 bits
(D) More than one of the above
(E) None of the above

---

**Q23.** In paging, page size is ALWAYS:
(A) Larger than frame size
(B) Smaller than frame size
(C) Equal to frame size
(D) More than one of the above
(E) None of the above

---

**Q24.** Which of the following CORRECTLY describes external fragmentation?
(A) Wasted space inside allocated memory blocks/pages
(B) Free memory that exists but is scattered in non-contiguous chunks
(C) Memory lost because the page table is too large
(D) More than one of the above
(E) None of the above

---

**Q25.** The PTBR (Page Table Base Register) contains:
(A) The size of each page
(B) The starting address of the page table in main memory
(C) The number of frames in physical memory
(D) More than one of the above
(E) None of the above

---
---

### GENERAL STUDIES — 25 MCQs (Champaran Satyagraha 1917)

---

**Q26.** The Champaran Satyagraha of 1917 was significant because it was:
(A) Gandhi's first satyagraha anywhere in the world
(B) Gandhi's first satyagraha on Indian soil
(C) The first time indigo cultivation was introduced in Bihar
(D) More than one of the above
(E) None of the above

---

**Q27.** Who brought Mahatma Gandhi to Champaran to highlight the plight of indigo farmers?
(A) Rajendra Prasad
(B) Brij Kishore Prasad
(C) Raj Kumar Shukla
(D) More than one of the above
(E) None of the above

---

**Q28.** On which EXACT DATE did Gandhi arrive at Motihari (East Champaran)?
(A) April 6, 1917
(B) April 15, 1917
(C) December 9, 1917
(D) More than one of the above
(E) None of the above

---

**Q29.** The TINKATHIA SYSTEM in Champaran required farmers to cultivate indigo on what fraction of their land?
(A) 1/4 (one-fourth) of their land
(B) 1/2 (one-half) of their land
(C) 3/20 (three-twentieth) — 3 katha per bigha
(D) More than one of the above
(E) None of the above

---

**Q30.** Who received Mahatma Gandhi at Patna when he arrived for the Champaran Satyagraha?
(A) Raj Kumar Shukla
(B) Brij Kishore Prasad
(C) Dr. Rajendra Prasad
(D) More than one of the above
(E) None of the above

---

**Q31.** Which of the following CORRECTLY describes the Tinkathia system?
(A) A system where farmers paid taxes in the form of indigo crops
(B) A system where farmers were forced to grow indigo on 3/20 of their land
(C) A rental arrangement where British planters rented land from farmers
(D) More than one of the above
(E) None of the above

---

**Q32.** The Champaran Agrarian Act of 1918 provided for:
(A) Complete abolition of Tinkathia system AND 50% refund to farmers
(B) Abolition of Tinkathia system AND 25% refund of compensation paid by farmers
(C) Abolition of Tinkathia system only (no refund was given)
(D) More than one of the above
(E) None of the above

---

**Q33.** Where did Raj Kumar Shukla first meet Mahatma Gandhi to request his help for Champaran?
(A) Champaran itself
(B) Ahmedabad (Sabarmati Ashram)
(C) Lucknow Congress Session (December 1916)
(D) More than one of the above
(E) None of the above

---

**Q34.** When the British District Magistrate ordered Gandhi to leave Champaran, Gandhi:
(A) Immediately obeyed and left to avoid legal trouble
(B) Defied the order and peacefully accepted any legal consequence
(C) Called for a mass strike against British authority
(D) More than one of the above
(E) None of the above

---

**Q35.** Which of the following persons JOINED Gandhi's investigation team in Champaran?
(A) Rajendra Prasad
(B) J.B. Kripalani (Acharya Kripalani)
(C) Brij Kishore Prasad
(D) More than one of the above
(E) None of the above

---

**Q36.** What was the OUTCOME when the British filed a case against Gandhi in the Motihari court?
(A) Gandhi was convicted and jailed for 6 months
(B) The government withdrew the case, unable to proceed due to mass farmer support
(C) Gandhi paid a fine and was allowed to continue his work
(D) More than one of the above
(E) None of the above

---

**Q37.** What was the ROLE OF KASTURBA GANDHI in the Champaran Satyagraha?
(A) She led the indigo farmers in marches against planters
(B) She conducted health and hygiene workshops for village women
(C) She represented Gandhi in negotiations with British planters
(D) More than one of the above
(E) None of the above

---

**Q38.** Gandhi was appointed as a MEMBER of which committee formed by the British to investigate Champaran conditions?
(A) Rowlatt Committee
(B) Champaran Agrarian Committee
(C) Simon Commission
(D) More than one of the above
(E) None of the above

---

**Q39.** What did the SYNTHETIC INDIGO discovery in Germany (1897) lead to in Champaran?
(A) British planters INCREASED indigo cultivation to compete with synthetic dye
(B) Demand for natural indigo CRASHED → planters began extorting compensation from farmers
(C) Farmers willingly stopped growing indigo after seeing prices fall
(D) More than one of the above
(E) None of the above

---

**Q40.** What is the CORRECT chronological order of Gandhi's three early satyagrahas in India?
(A) Ahmedabad Mill Strike → Champaran → Kheda
(B) Kheda → Champaran → Ahmedabad
(C) Champaran (1917) → Kheda (1918) → Ahmedabad Mill Strike (1918)
(D) More than one of the above
(E) None of the above

---

**Q41.** Dr. Rajendra Prasad later described Champaran as the event that:
(A) Convinced him to join the Congress Party for the first time
(B) Transformed him from a Western-educated lawyer into Gandhi's devoted follower
(C) Made him realize British rule was permanently unshakeable
(D) More than one of the above
(E) None of the above

---

**Q42.** The term "NILHE SAHEBS" in the context of Champaran referred to:
(A) Indian landlords who collaborated with the British
(B) British indigo planters who exploited Champaran farmers
(C) British police officers who enforced the Tinkathia system
(D) More than one of the above
(E) None of the above

---

**Q43.** In which DISTRICT is Motihari located — the headquarters of the Champaran Satyagraha?
(A) West Champaran
(B) East Champaran
(C) Saran
(D) More than one of the above
(E) None of the above

---

**Q44.** J.B. Kripalani's role in Champaran was:
(A) He led the indigo farmers in petitions to the District Magistrate
(B) He came as an educated volunteer to run the schools Gandhi established
(C) He organized the legal defense for Gandhi's case in Motihari court
(D) More than one of the above
(E) None of the above

---

**Q45.** Which of the following statements about the Champaran Satyagraha is FALSE?
(A) Gandhi arrived at Motihari on April 15, 1917
(B) Raj Kumar Shukla was an educated lawyer who brought Gandhi to Champaran
(C) The Tinkathia system required farmers to grow indigo on 3/20 of their land
(D) More than one of the above
(E) None of the above

---

**Q46.** The Champaran Agrarian Act was passed in which year?
(A) 1917
(B) 1918
(C) 1919
(D) More than one of the above
(E) None of the above

---

**Q47.** Raj Kumar Shukla is described as an ILLITERATE farmer. This detail is historically important because:
(A) It shows Gandhi helped only educated classes during the freedom struggle
(B) It demonstrates that ordinary, uneducated people played crucial roles in freedom movement
(C) It means Shukla could not have attended the Lucknow Congress
(D) More than one of the above
(E) None of the above

---

**Q48.** What constructive activities did Gandhi undertake IN ADDITION to the inquiry in Champaran?
(A) He opened primary schools and ran health/sanitation programs in villages
(B) He organized a hartaal (strike) of all farmers against British planters
(C) He launched a non-cooperation campaign specifically for Bihar in 1917
(D) More than one of the above
(E) None of the above

---

**Q49.** MATCH THE FOLLOWING — Person and their CORRECT role in Champaran:
```
Person                Role
1. Raj Kumar Shukla   A. Received Gandhi at Patna railway station
2. Rajendra Prasad    B. Ran schools for village children
3. J.B. Kripalani     C. Brought Gandhi to Champaran (illiterate farmer)
4. Kasturba Gandhi    D. Conducted health workshops for village women
```
(A) 1-C, 2-A, 3-B, 4-D
(B) 1-A, 2-C, 3-D, 4-B
(C) 1-B, 2-D, 3-A, 4-C
(D) More than one of the above
(E) None of the above

---

**Q50.** Which of the following CORRECTLY identifies the COMPLETE result of Champaran Satyagraha?
(A) Only the Tinkathia system was abolished — nothing more
(B) Tinkathia abolished + farmers received 25% refund + freedom to grow food crops
(C) Full refund of all money paid to planters + Tinkathia abolished + British planters expelled
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY

## ⚠️ MANDATORY: Attempt ALL 50 questions BEFORE checking answers!

---

### CS Answers (Q1–Q25):

| Q  | Answer | Reason (one-line) |
|----|--------|-------------------|
| 1  | (C)    | TLB = ASSOCIATIVE CACHE (Content Addressable Memory) — exact PYQ phrase |
| 2  | (C)    | 4KB = 2¹² → 12 offset bits ← most tested calculation |
| 3  | (B)    | FRAME = fixed-size block of PHYSICAL memory (RAM) |
| 4  | (C)    | 22KB / 4KB = 5.5 → 6 pages needed (24KB) → waste = 24-22 = 2KB |
| 5  | (B)    | TLB miss → go to page table in RAM to find frame number |
| 6  | (B)    | Page fault = page NOT in RAM; interrupt raised; OS loads from disk |
| 7  | (C)    | 1KB = 2¹⁰ → 10 offset bits |
| 8  | (B)    | Paging causes INTERNAL fragmentation (waste inside last page) |
| 9  | (C)    | Valid bit = 0 → page is NOT in RAM (is on disk → page fault if accessed) |
| 10 | (B)    | TLB reduces memory accesses for address translation (avoids 2 RAM accesses) |
| 11 | (C)    | Page OFFSET never changes — only page number changes to frame number |
| 12 | (C)    | 8KB = 2¹³ → 13 offset bits |
| 13 | (C)    | Belady's Anomaly = FIFO only (more frames → more faults in FIFO) |
| 14 | (B)    | Demand paging = pages loaded ONLY when accessed (on first page fault) |
| 15 | (C)    | Modified/dirty bit = page was modified since loading → needs write-back to disk |
| 16 | (B)    | Paging ELIMINATES external fragmentation, CAUSES internal fragmentation |
| 17 | (C)    | Inverted page table indexed by FRAME NUMBER (not page number) |
| 18 | (C)    | EAT = 0.9×100 + 0.1×200 = 90+20 = 110 ns |
| 19 | (C)    | Page table stored in MAIN MEMORY (RAM); PTBR register points to it |
| 20 | (C)    | Larger page → more wasted space (up to page_size - 1 bytes in last page) |
| 21 | (B)    | Multi-level paging reduces memory for storing large page tables |
| 22 | (C)    | 32 - 12 (offset) = 20 bits for page number |
| 23 | (C)    | Page size is ALWAYS EQUAL to frame size (fundamental rule of paging) |
| 24 | (B)    | External fragmentation = free memory exists but scattered non-contiguously |
| 25 | (B)    | PTBR = Page Table Base Register = points to page table's starting address in RAM |

---

### GS Answers (Q26–Q50):

| Q  | Answer | Reason (one-line) |
|----|--------|-------------------|
| 26 | (B)    | First satyagraha ON INDIAN SOIL (he did first satyagraha in South Africa 1906) |
| 27 | (C)    | RAJ KUMAR SHUKLA = illiterate farmer who brought Gandhi to Champaran |
| 28 | (B)    | Gandhi arrived Motihari: April 15, 1917 |
| 29 | (C)    | Tinkathia = 3/20 (3 katha per bigha) |
| 30 | (C)    | DR. RAJENDRA PRASAD received Gandhi at Patna railway station |
| 31 | (B)    | Tinkathia = forced indigo on 3/20 of land — compulsory, not voluntary |
| 32 | (B)    | Tinkathia abolished + 25% refund (not 50%, not nothing) |
| 33 | (C)    | Shukla met Gandhi at LUCKNOW CONGRESS SESSION, December 1916 |
| 34 | (B)    | Gandhi DEFIED the order — peacefully accepted any legal consequence |
| 35 | (D)    | All three (Rajendra Prasad, Kripalani, Brij Kishore) joined the investigation team |
| 36 | (B)    | Govt WITHDREW the case — could not proceed facing massive peaceful crowd |
| 37 | (B)    | Kasturba conducted health and hygiene workshops for village women |
| 38 | (B)    | Champaran Agrarian Committee — Gandhi was a member (unprecedented) |
| 39 | (B)    | Synthetic dye → natural indigo prices crashed → planters extorted compensation |
| 40 | (C)    | Champaran (1917) → Kheda (1918) → Ahmedabad mill strike (1918) |
| 41 | (B)    | Champaran transformed Rajendra Prasad from lawyer to Gandhi's devoted follower |
| 42 | (B)    | Nilhe Sahebs = British indigo planters (nilha = indigo in local language) |
| 43 | (B)    | Motihari = headquarters of EAST CHAMPARAN district |
| 44 | (B)    | Kripalani ran the schools Gandhi established in Champaran villages |
| 45 | (B)    | FALSE: Raj Kumar Shukla was ILLITERATE (not an educated lawyer) |
| 46 | (B)    | Champaran Agrarian Act passed in 1918 (not 1917 — investigation was 1917) |
| 47 | (B)    | Shows ordinary, uneducated people were crucial to freedom movement |
| 48 | (A)    | Gandhi opened primary schools + ran health/sanitation programs |
| 49 | (A)    | Shukla-C, Rajendra Prasad-A, Kripalani-B, Kasturba-D |
| 50 | (B)    | Tinkathia abolished + 25% refund + freedom to grow food crops — all three |

---
---

# 🔁 NIGHT REVISION SHEET
## 📌 Day 69 — Ultra-Crisp "Last 30 Minutes Before Sleep"

---

### ⚡ CS — PAGING: 18 MUST-KNOW FACTS

```
DEFINITIONS:
1.  PAGE  = fixed-size block of LOGICAL (virtual) memory
    FRAME = fixed-size block of PHYSICAL memory (= same size as page)
2.  Page table = maps Page Number → Frame Number (stored in RAM)

PAGE OFFSET BITS (MEMORIZE ALL):
3.  4KB page  → 12-bit offset (2¹² = 4096) ← MOST TESTED
4.  1KB page  → 10-bit offset (2¹⁰ = 1024)
5.  8KB page  → 13-bit offset (2¹³ = 8192)
6.  In address translation: OFFSET NEVER CHANGES; only p→f

TLB:
7.  TLB = organized as ASSOCIATIVE CACHE ← exact PYQ phrase
8.  TLB hit  → only 1 memory access (fast)
9.  TLB miss → 2 memory accesses (page table + data)
10. TLB uses PARALLEL (simultaneous) lookup of all entries
11. TLB is near/inside CPU; page table is in RAM

FRAGMENTATION:
12. Paging ELIMINATES external fragmentation
13. Paging CAUSES internal fragmentation (wasted space inside last page)
14. Smaller page size → less internal fragmentation per page
                      → but MORE pages → larger page table (trade-off)

PAGE FAULT:
15. Page fault = valid bit = 0 → page is on DISK, not in RAM
16. OS loads page from disk → updates page table → restarts instruction

OTHERS:
17. Belady's Anomaly = FIFO replacement only
    (more frames can cause MORE page faults)
18. Inverted page table → indexed by FRAME NUMBER (not page number)
19. Demand paging → pages loaded ONLY when accessed (on page fault)
20. PTBR = register pointing to page table's location in RAM
```

---

### ⚡ GS — CHAMPARAN: 15 MUST-KNOW FACTS

```
KEY PEOPLE:
1.  Raj Kumar Shukla  = illiterate farmer; brought Gandhi to Champaran
                      = met Gandhi at LUCKNOW CONGRESS, Dec 1916
2.  Rajendra Prasad  = received Gandhi at PATNA RAILWAY STATION
                      = Bihar-born; First President of India (Siwan)
3.  J.B. Kripalani   = ran schools established by Gandhi in villages
4.  Kasturba Gandhi  = conducted health workshops for women

KEY FACTS:
5.  Champaran = Gandhi's FIRST SATYAGRAHA IN INDIA (not first ever — South Africa was 1906)
6.  Gandhi arrived Motihari: April 15, 1917 ← exact date
7.  Tinkathia = 3 katha per bigha = 3/20 of land for forced indigo cultivation
8.  British issued notice: "Leave Champaran" → Gandhi REFUSED peacefully
9.  Case against Gandhi WITHDRAWN (couldn't proceed — massive farmer support)
10. Gandhi was MEMBER of Champaran Agrarian Committee (unprecedented)

OUTCOME — CHAMPARAN AGRARIAN ACT 1918:
11. Tinkathia system ABOLISHED ← main result
12. Farmers received 25% REFUND (not 50%) ← PYQ trap
13. Farmers free to grow food crops

SIGNIFICANCE:
14. Proved non-violent resistance can force British to act
15. Transformed Rajendra Prasad from lawyer → Gandhi's devoted follower
    Champaran (1917) → Kheda (1918) → Ahmedabad Mill Strike (1918)
    ← Gandhi's three early India satyagrahas in order
```

---

### ⚡ TOMORROW — DAY 70 PREVIEW

```
CS:  Segmentation + Virtual Memory + Compaction + Thrashing
     KEY FACTS:
     → Compaction = shifts processes → ALL free memory in ONE BLOCK
     → Fragmentation = PROBLEM (not a technique)
     → Thrashing = excessive paging activity
     → Buffer registers = overcome SPEED DIFFERENCE between devices

GS:  Indian Parliament + Elections + Constitutional Bodies
```

---

## 🎯 WEEK 11 PROGRESS TRACKER

```
Day 68: OS Introduction & Types            ✅ DONE
Day 69: Paging (Complete)                  ← TODAY ✅
Day 70: Segmentation + Virtual Memory
Day 71: Disk Scheduling (FCFS calculation)
Day 72: I/O Management + File Systems
Day 73: Threads + CPU Scheduling + Deadlocks
Day 74: OS Complete Revision + 25 PYQ MCQs
```

---

*Day 69 Complete | Week 11 of 25 | Phase 2: Depth | Target: TOP 50 RANK*
