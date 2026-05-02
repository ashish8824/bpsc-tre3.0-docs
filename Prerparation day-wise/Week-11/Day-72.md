# 📅 BPSC TRE 4.0 — DAY 72: I/O MANAGEMENT + FILE SYSTEMS + LOCAL GOVERNMENT
### Week 11 — Polling, DMA, Memory-Mapped I/O, PCI Bus, File Systems + Panchayati Raj + Urban Bodies
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): CS — I/O types (Polling, Interrupt, DMA), Memory-mapped I/O, PCI Bus, File Systems
> - Afternoon (1 hr): GS — Local Government (73rd + 74th Amendment, Panchayati Raj, Urban Bodies)
> - Evening (1.5 hrs): Solve all 50 MCQs
> - Night (30 min): Read the Night Revision Sheet

---

# PART 1: CS CONCEPT NOTES
## 📘 I/O Management + File Systems — Complete Deep Dive

---

## 🔷 TOPIC 1: THE I/O PROBLEM — WHY I/O MANAGEMENT EXISTS

```
THE FUNDAMENTAL PROBLEM:
════════════════════════════════════════════════════════════════════

CPU operates at GHz speed (billions of operations per second).
I/O devices operate MUCH slower:
  Keyboard:   ~10 characters/second (human typing)
  HDD:        ~100–200 MB/second
  Network:    ~100 Mbps to 1 Gbps
  USB 2.0:    ~60 MB/second
  CPU:        ~tens of GB/second (memory bandwidth)

PROBLEM: If CPU waits every time an I/O device finishes,
         the CPU is IDLE 99.9% of the time → wasted performance.

SOLUTION: Three progressively better approaches:
  1. PROGRAMMED I/O (Polling)  → CPU keeps checking ("are you done yet?")
  2. INTERRUPT-DRIVEN I/O      → Device tells CPU when done
  3. DMA (Direct Memory Access) → Device transfers data DIRECTLY, CPU not involved

════════════════════════════════════════════════════════════════════

I/O SUBSYSTEM LAYERS (OS handles I/O in layers):
  ┌────────────────────────────────────────────────┐
  │         USER PROCESS (e.g., program reads file) │
  ├────────────────────────────────────────────────┤
  │    KERNEL I/O SUBSYSTEM (OS layer)              │
  │    (scheduling, buffering, caching, spooling)   │
  ├────────────────────────────────────────────────┤
  │    DEVICE DRIVERS (OS-device interface)         │
  │    (specific code for each device type)         │
  ├────────────────────────────────────────────────┤
  │    DEVICE CONTROLLER (hardware)                 │
  │    (small processor on device itself)           │
  ├────────────────────────────────────────────────┤
  │    I/O DEVICE (keyboard, disk, network, etc.)  │
  └────────────────────────────────────────────────┘

DEVICE CONTROLLER:
  → Small processor built into each I/O device
  → Contains: DATA registers, STATUS registers, COMMAND registers
  → STATUS register = CPU polls this to check if device is ready
    ← "STATUS FLAGS" = what polling checks ← PYQ EXACT PHRASE
  → CPU communicates with device via device controller
```

---

## 🔷 TOPIC 2: PROGRAMMED I/O (POLLING) — THE #1 PYQ TOPIC

```
DEFINITION:
════════════════════════════════════════════════════════════════════

PROGRAMMED I/O = I/O technique where the CPU REPEATEDLY CHECKS
                 (polls) the STATUS FLAGS of the I/O device controller
                 to see if the I/O operation has completed.

  ALSO CALLED: POLLING ← both names are tested in BPSC!
  ← TRE 1.0 DIRECT PYQ: "Program-controlled I/O = repeatedly checking STATUS FLAGS"
  ← EXACT PHRASE TO MEMORIZE: "repeatedly checking status flags"

════════════════════════════════════════════════════════════════════

HOW POLLING WORKS — STEP BY STEP:
  1. CPU sends I/O command to device controller
  2. CPU enters a BUSY-WAIT LOOP:
       while (status_register != DONE) {
           check status_register;  // poll again and again
       }
  3. CPU keeps checking the status flag in a loop
  4. NOTHING ELSE can happen — CPU is 100% occupied with polling
  5. When device sets status = DONE, CPU reads the data and continues

VISUAL:
  ┌─────────────────────────────────────────────────────────────┐
  │  CPU: "Are you done?" → Device: "Not yet."                  │
  │  CPU: "Are you done?" → Device: "Not yet."                  │
  │  CPU: "Are you done?" → Device: "Not yet."                  │
  │  CPU: "Are you done?" → Device: "Not yet."                  │
  │  CPU: "Are you done?" → Device: "DONE!"                     │
  │  CPU: reads data → continues                                │
  └─────────────────────────────────────────────────────────────┘

════════════════════════════════════════════════════════════════════

POLLING ADVANTAGES:              POLLING DISADVANTAGES:
  ✓ Simple to implement            ✗ CPU WASTED — busy-waiting (doing nothing useful)
  ✓ No interrupt hardware needed   ✗ No other work done while polling
  ✓ Predictable timing             ✗ CPU cycles completely wasted on checking
  ✓ Good for very fast devices     ✗ Bad for slow devices (keyboard, disk)
    (less overhead than interrupt)

WHEN IS POLLING ACCEPTABLE?
  → Very fast I/O devices (< few microseconds) where interrupt overhead > polling time
  → Simple embedded systems with no multitasking
  → Real-time systems needing deterministic response

KEY FACTS (PYQ SUMMARY):
  ★ Programmed I/O = POLLING ← both terms mean same thing
  ★ Polling = CPU REPEATEDLY CHECKS STATUS FLAGS ← exact phrase
  ★ CPU cannot do other work while polling (busy-wait loop)
  ★ Worst CPU utilization among three I/O methods
  ★ "Status flags" = bits in device controller STATUS REGISTER
```

---

## 🔷 TOPIC 3: INTERRUPT-DRIVEN I/O — THE EFFICIENT APPROACH

```
DEFINITION:
════════════════════════════════════════════════════════════════════

INTERRUPT-DRIVEN I/O = I/O technique where:
  → CPU sends I/O command to device controller
  → CPU IMMEDIATELY CONTINUES doing other useful work
  → When I/O completes, the device controller sends an INTERRUPT to CPU
  → CPU stops current work, handles the interrupt (reads data), resumes

  KEY INSIGHT: CPU does NOT wait. It gets notified when device is ready.
               CPU is free to run other processes while I/O is happening!

════════════════════════════════════════════════════════════════════

HOW INTERRUPT-DRIVEN I/O WORKS:
  ┌──────────────────────────────────────────────────────────────┐
  │                                                              │
  │  1. CPU → sends I/O command → Device Controller             │
  │  2. CPU → CONTINUES doing other work (Process B, Process C) │
  │  3. Device Controller → completes I/O operation             │
  │  4. Device Controller → sends INTERRUPT SIGNAL to CPU       │
  │  5. CPU → suspends current work → saves its state (context) │
  │  6. CPU → runs INTERRUPT SERVICE ROUTINE (ISR)              │
  │     (ISR = special code that handles the I/O completion)    │
  │  7. ISR → reads data from device controller                 │
  │  8. CPU → restores previous state → resumes interrupted work│
  │                                                              │
  └──────────────────────────────────────────────────────────────┘

INTERRUPT SERVICE ROUTINE (ISR):
  = Small piece of code executed when interrupt arrives
  = Handles the specific interrupt (reads data, updates buffers)
  = Also called: Interrupt Handler

INTERRUPT VECTOR TABLE (IVT):
  = Table in memory that maps interrupt numbers to ISR addresses
  = When interrupt N occurs → CPU looks up IVT → jumps to ISR for N

════════════════════════════════════════════════════════════════════

INTERRUPT-DRIVEN vs POLLING COMPARISON:
  ────────────────────────────────────────────────────────────────
  FEATURE           POLLING                  INTERRUPT-DRIVEN
  CPU while I/O     BUSY-WAITING (wasted)    Does useful other work
  CPU utilization   Very LOW (wasted cycles) HIGH (productive)
  Notification      CPU keeps asking         Device TELLS CPU
  Overhead          Low per poll cycle       Interrupt handling overhead
  Suitability       Fast devices             Slow/medium speed devices
  Complexity        Simple                   More complex (ISR needed)
  ────────────────────────────────────────────────────────────────

INTERRUPT-DRIVEN KEY FACTS:
  ★ CPU does OTHER WORK while I/O is in progress
  ★ Device NOTIFIES CPU (not CPU checking device)
  ★ Much better CPU utilization than polling
  ★ BUT: still involves CPU for EVERY data transfer (byte/word)
  ★ For very high-speed I/O (like disk) → still too slow (too many interrupts)
  → Solution: DMA (next topic)
```

---

## 🔷 TOPIC 4: DMA — DIRECT MEMORY ACCESS

```
DEFINITION:
════════════════════════════════════════════════════════════════════

DMA = Direct Memory Access = A technique where a DEDICATED HARDWARE
      CONTROLLER (DMA Controller) transfers data DIRECTLY between
      an I/O device and MAIN MEMORY WITHOUT CPU involvement.

  KEY PHRASE: DMA BYPASSES the CPU for data transfer ← exact PYQ phrase

  Why needed?
  → Interrupt-driven I/O: CPU handles EVERY data transfer (byte by byte)
  → For a disk transfer of 1MB at 1 byte/interrupt = 1,048,576 interrupts!
  → This would completely overwhelm the CPU with interrupt handling
  → DMA lets a special controller do the bulk transfer while CPU is free

════════════════════════════════════════════════════════════════════

HOW DMA WORKS — STEP BY STEP:
  ┌──────────────────────────────────────────────────────────────┐
  │                                                              │
  │  1. CPU programs DMA Controller:                            │
  │     → Source: device (e.g., disk)                           │
  │     → Destination: RAM address (where data should go)       │
  │     → Count: how many bytes to transfer                     │
  │                                                              │
  │  2. DMA Controller takes over the SYSTEM BUS                │
  │     (CPU is temporarily disconnected from bus)              │
  │     This is called "CYCLE STEALING" or "BUS STEALING"       │
  │                                                              │
  │  3. DMA Controller transfers data:                          │
  │     Device → DMA Controller → directly to RAM               │
  │     (word by word or block by block)                        │
  │     CPU does NOT touch each data unit!                      │
  │                                                              │
  │  4. When transfer COMPLETE:                                 │
  │     DMA Controller sends ONE INTERRUPT to CPU               │
  │     "Hey, I'm done! All 1MB is now in RAM."                 │
  │                                                              │
  │  5. CPU processes the data from RAM                         │
  │     (only ONE interrupt total, not millions!)               │
  │                                                              │
  └──────────────────────────────────────────────────────────────┘

CYCLE STEALING:
  = DMA controller "steals" memory bus cycles from CPU
  = CPU is paused briefly for each memory access by DMA
  = CPU is NOT completely stopped — just briefly paused each bus cycle
  = CPU still executes instructions from CPU cache during stolen cycles

════════════════════════════════════════════════════════════════════

DMA KEY FACTS (PYQ SUMMARY):
  ★ DMA = bypasses CPU for data transfer ← exact exam phrase
  ★ DMA transfers data DIRECTLY between I/O device and RAM
  ★ Only ONE interrupt sent at end (not one per byte like interrupt I/O)
  ★ CYCLE STEALING = DMA temporarily takes control of memory bus
  ★ Much faster than interrupt-driven I/O for large transfers (disk, network)
  ★ Requires dedicated DMA CONTROLLER hardware
  ★ CPU is FREE during DMA transfer (doing useful work)

THREE I/O METHODS — MASTER COMPARISON:
════════════════════════════════════════════════════════════════════

METHOD           HOW CPU INVOLVED         INTERRUPTS  BEST FOR
─────────────────────────────────────────────────────────────────
Polling          CPU checks continuously  0           Very fast devices,
(Programmed I/O) (busy-wait loop)                     simple embedded systems

Interrupt-Driven Device notifies CPU       1 per byte  Medium speed devices
I/O              CPU handles each xfer    (or word)    keyboard, mouse, serial

DMA              DMA controller does xfer 1 per BLOCK  Fast/large transfers
                 CPU free during xfer     (not per byte) disk, network, USB

─────────────────────────────────────────────────────────────────
EFFICIENCY: Polling < Interrupt-Driven < DMA (best CPU utilization)
INTERRUPTS: DMA = fewest interrupts per data volume (1 per block)
════════════════════════════════════════════════════════════════════
```

---

## 🔷 TOPIC 5: MEMORY-MAPPED I/O vs I/O-MAPPED I/O

```
THE FUNDAMENTAL QUESTION: How does the CPU communicate with I/O devices?
  → Every I/O device has REGISTERS (data register, status register, command register)
  → CPU must READ/WRITE these registers to control the device
  → The question is: WHERE ARE THESE REGISTERS IN THE ADDRESS SPACE?

════════════════════════════════════════════════════════════════════

METHOD 1: MEMORY-MAPPED I/O
════════════════════════════════════════════════════════════════════

DEFINITION: I/O device registers are mapped into the SAME ADDRESS SPACE
            as main memory. I/O and memory SHARE THE SAME address space.

            ← TRE 1.0 DIRECT PYQ: "Memory-mapped I/O = I/O and memory SHARE SAME address space"
            ← EXACT PHRASE: "share same address space"

ADDRESS MAP:
  ┌────────────────────────────────────────────────────────────┐
  │                    ADDRESS SPACE (32-bit = 4GB)            │
  │                                                            │
  │  0x00000000 ─── 0xBFFFFFFF  │  Main Memory (RAM) 3GB      │
  │                             │                             │
  │  0xC0000000 ─── 0xDFFFFFFF  │  I/O Device Registers       │
  │                             │  (mapped here)              │
  │  0xE0000000 ─── 0xFFFFFFFF  │  More RAM or other devices  │
  └────────────────────────────────────────────────────────────┘

HOW CPU ACCESSES DEVICE:
  → CPU uses NORMAL MEMORY INSTRUCTIONS (LOAD/STORE, MOV)
  → To read keyboard: MOV AX, [0xC0000100] (read from keyboard address)
  → To write display: MOV [0xD0000200], AX (write to display address)
  → No special I/O instructions needed!

ADVANTAGES:
  ✓ Simple — use same instructions for memory AND I/O
  ✓ Any instruction that works on memory works on I/O
  ✓ Can use powerful addressing modes for I/O access
DISADVANTAGES:
  ✗ Uses up some of the precious memory address space for I/O
  ✗ Cache must handle I/O addresses carefully (I/O shouldn't be cached)

════════════════════════════════════════════════════════════════════

METHOD 2: I/O-MAPPED I/O (PORT-MAPPED I/O / ISOLATED I/O)
════════════════════════════════════════════════════════════════════

DEFINITION: I/O devices have a COMPLETELY SEPARATE address space from memory.
            CPU uses SPECIAL I/O INSTRUCTIONS (IN/OUT) to access devices.

ADDRESS MAP:
  ┌─────────────────────────┐  ┌─────────────────────────────┐
  │  MEMORY ADDRESS SPACE   │  │  I/O ADDRESS SPACE (separate)│
  │                         │  │                             │
  │  0x00000000–0xFFFFFFFF  │  │  Port 0x00–0xFF             │
  │  (4GB for RAM only)     │  │  (e.g., 256 I/O ports)      │
  │  NOT contaminated       │  │  accessed ONLY by IN/OUT    │
  │  by I/O device addrs    │  │  instructions               │
  └─────────────────────────┘  └─────────────────────────────┘

HOW CPU ACCESSES DEVICE:
  → CPU uses SPECIAL INSTRUCTIONS: IN (read from port), OUT (write to port)
  → To read keyboard: IN AL, 0x60 (port 0x60 = keyboard data port on x86)
  → To write: OUT 0x60, AL

ADVANTAGES:
  ✓ Full memory address space available for RAM
  ✓ Clear separation between memory and I/O accesses
  ✓ Hardware can distinguish memory vs I/O cycle easily
DISADVANTAGES:
  ✗ Need special IN/OUT instructions (limited instruction set)
  ✗ Can't use all addressing modes that work on memory
  ✗ Fewer available I/O addresses (usually 16-bit I/O space)

════════════════════════════════════════════════════════════════════

COMPARISON TABLE:
  FEATURE             MEMORY-MAPPED I/O        I/O-MAPPED I/O
  ────────────────────────────────────────────────────────────────
  Address space       SHARED (mem + I/O)       SEPARATE for I/O
  CPU instructions    Normal LOAD/STORE         Special IN/OUT
  Memory space used   Some used by I/O          Full memory available
  Architecture        RISC, ARM, most modern    x86 legacy
  Access              Any instruction           Only IN/OUT
  PYQ phrase          "share same address"      "separate address space"
  ────────────────────────────────────────────────────────────────

★ PYQ: Memory-mapped I/O = I/O and memory SHARE SAME address space ← TRE 1.0
★ PYQ: I/O-mapped I/O = SEPARATE address spaces for I/O and memory
```

---

## 🔷 TOPIC 6: BUS ARCHITECTURE — PCI BUS

```
WHAT IS A BUS?
════════════════════════════════════════════════════════════════════

BUS = A set of communication lines (wires) that connects components
      inside a computer and transfers DATA, ADDRESSES, and CONTROL SIGNALS.

TYPES OF SIGNALS ON A BUS:
  DATA BUS:     carries actual data (bidirectional)
  ADDRESS BUS:  carries memory addresses (unidirectional, CPU→memory)
  CONTROL BUS:  carries control signals (read/write, interrupt, clock)

BUS HIERARCHY (inside a typical computer):
  ┌──────────────────────────────────────────────────────────────┐
  │                                                              │
  │  CPU ◄──────────────── PROCESSOR BUS (Front-Side Bus) ─────► │
  │                         (fastest bus, CPU to chipset)       │
  │                                ↕ (via bridge chip)          │
  │                        MEMORY BUS (to RAM)                  │
  │                                ↕                            │
  │                        SYSTEM BUS / EXPANSION BUS           │
  │                                ↕                            │
  │                         PCI BUS                             │
  │                    ┌────┴────────┴────┐                     │
  │               Graphics          Network/Sound               │
  │               Card              Cards                       │
  └──────────────────────────────────────────────────────────────┘

════════════════════════════════════════════════════════════════════

PCI BUS (Peripheral Component Interconnect):
════════════════════════════════════════════════════════════════════

PCI = Peripheral Component Interconnect

DEFINITION: PCI bus is a standard bus that EXTENDS the CONNECTIVITY
            of the PROCESSOR BUS to peripheral devices.

← TRE 1.0 / BPSC DIRECT PYQ: "PCI bus extends the connectivity of PROCESSOR BUS"
← EXACT PHRASE: "extends connectivity of processor bus"

WHAT PCI BUS DOES:
  → Connects peripheral devices (graphics card, sound card, network card,
    USB controller, SATA controller) to the main system
  → Provides a standardized interface for expansion cards
  → Multiple devices can share the PCI bus

PCI BUS CHARACTERISTICS:
  Speed:    Original PCI: 33 MHz × 32-bit = ~133 MB/s
  Slots:    Physical expansion slots on motherboard
  Sharing:  Multiple devices share one bus (can cause contention)

PCI EXPRESS (PCIe) — MODERN SUCCESSOR:
  → PCIe replaced original PCI (backward compatible with PCI concept)
  → Uses SERIAL LANES (1x, 4x, 8x, 16x lanes)
  → PCIe 4.0 × 16: ~32 GB/s bandwidth
  → Graphics cards use PCIe × 16 slot
  → SSDs use PCIe × 4 (NVMe SSDs)
  → PCIe = NOT the same as PCI but PCI concept was foundation

════════════════════════════════════════════════════════════════════

OTHER BUS TYPES:
  ─────────────────────────────────────────────────────────────────
  BUS NAME        PURPOSE                          SPEED
  ISA bus         Old expansion bus (pre-PCI)      8 MB/s (obsolete)
  PCI             Extends processor bus to periph  133 MB/s
  PCIe            Modern serial lane bus            up to 32 GB/s
  USB             Universal Serial Bus             USB 2.0: 60MB/s
                  (connects external devices)      USB 3.2: 2 GB/s
  SATA            Connects disk drives to system   600 MB/s
  IDE/ATA         Old disk interface (obsolete)    133 MB/s
  AGP             Old graphics port (replaced PCIe) 2 GB/s
  ─────────────────────────────────────────────────────────────────

BUS KEY FACTS (PYQ SUMMARY):
  ★ PCI bus = extends connectivity of PROCESSOR BUS ← exact BPSC PYQ phrase
  ★ PCI = Peripheral Component Interconnect
  ★ Bus = communication pathway connecting computer components
  ★ PCIe = modern successor to PCI (uses serial lanes)
  ★ USB = Universal Serial Bus (for external devices)
```

---

## 🔷 TOPIC 7: SPOOLING — SIMULTANEOUS PERIPHERAL OPERATIONS ONLINE

```
DEFINITION:
  SPOOL = Simultaneous Peripheral Operations OnLine

  SPOOLING = Technique where data is temporarily stored (queued)
             in a SPOOL (buffer on disk) before being sent to a
             device that cannot immediately process it.

  CLASSIC EXAMPLE: PRINTER SPOOLING
  ┌──────────────────────────────────────────────────────────────┐
  │  Process A sends print job → SPOOL (stored on disk)          │
  │  Process B sends print job → SPOOL (queued behind A)         │
  │  Process C sends print job → SPOOL (queued behind B)         │
  │                                                              │
  │  Printer reads from SPOOL one job at a time:                 │
  │  Prints A → prints B → prints C                             │
  │                                                              │
  │  Processes A, B, C DON'T WAIT for printer → they continue!  │
  └──────────────────────────────────────────────────────────────┘

WHY SPOOLING MATTERS:
  → Printer is MUCH SLOWER than CPU
  → Without spooling: each process WAITS for printer to finish before continuing
  → With spooling: process dumps data to spool file (fast) → continues
  → OS manages printer queue independently

SPOOLING vs BUFFERING:
  BUFFER:  Temporary RAM storage for data in TRANSIT (between two operations)
           → Small, in RAM, holds data briefly
  SPOOL:   Disk-based queue for data WAITING to be processed
           → Large, on disk, holds data longer (entire print jobs)

SPOOLING KEY FACTS:
  ★ SPOOL = Simultaneous Peripheral Operations OnLine
  ★ Classic use case = PRINTER SPOOLING
  ★ Allows multiple processes to "print" simultaneously (via queue)
  ★ Printer daemon/service reads from spool, manages queue
  ★ Improves CPU utilization (processes don't wait for slow printer)
```

---

## 🔷 TOPIC 8: FILE SYSTEMS — COMPLETE DEEP DIVE

```
DEFINITION:
════════════════════════════════════════════════════════════════════

FILE SYSTEM = The method and data structures used by the OS to
              organize, store, retrieve, and manage files on
              secondary storage (disk).

  → Without a file system, disk is just raw bytes — no structure
  → File system provides: files, directories, permissions, metadata

SECONDARY MEMORY ORGANIZATION = LOGICAL
  ← BPSC DIRECT PYQ: Secondary memory = LOGICAL organization
  → Because files and directories are LOGICAL structures on disk
  → The actual physical storage (sectors, tracks) is handled transparently

════════════════════════════════════════════════════════════════════

FILE — THE BASIC UNIT:
  FILE = A named collection of related data stored on secondary storage
  FILE ATTRIBUTES (metadata):
    → Name (human-readable identifier)
    → Identifier (unique inode number or file ID in OS)
    → Type (text, binary, executable, directory)
    → Size (bytes)
    → Location (physical address on disk)
    → Timestamps (created, modified, accessed)
    → Protection (read/write/execute permissions)
    → Owner (user who owns the file)

════════════════════════════════════════════════════════════════════

FILE OPERATIONS — THE BPSC-TESTED LIST:
  ← DIRECT PYQ: "Common file operations: Create, Delete, Rename (all valid)"

  ┌─────────────────────────────────────────────────────────────┐
  │  BASIC FILE OPERATIONS (all are valid OS file operations):  │
  │                                                             │
  │  1. CREATE    → Make a new empty file                       │
  │  2. DELETE    → Remove a file permanently                   │
  │  3. OPEN      → Load file info into memory (prepare to use) │
  │  4. CLOSE     → Release file from memory (done using it)    │
  │  5. READ      → Read data from file into memory buffer      │
  │  6. WRITE     → Write data from buffer to file              │
  │  7. RENAME    → Change the file's name                      │
  │  8. SEEK      → Move read/write pointer to specific position│
  │  9. APPEND    → Write data at end of file (special write)   │
  │  10. TRUNCATE → Shorten file to specified size              │
  │  11. COPY     → Make duplicate of a file                    │
  │  12. MOVE     → Change file location (cut + paste)          │
  └─────────────────────────────────────────────────────────────┘

  ★ Create, Delete, Rename = all VALID operations ← direct PYQ fact
  ★ Open/Close = must do before/after reading/writing (pair operations)
  ★ SEEK = repositions file pointer (for random access)

FILE POINTER:
  → Integer tracking CURRENT POSITION in file during read/write
  → After READ(n bytes) → pointer advances n bytes
  → SEEK moves pointer to specific byte position
  → Sequential access: pointer moves linearly
  → Random access: SEEK then READ/WRITE at any position

════════════════════════════════════════════════════════════════════

FILE TYPES:
  TEXT FILE:    Human-readable characters (ASCII/Unicode)
  BINARY FILE:  Raw bytes (machine-readable: executables, images)
  DIRECTORY:    Special file containing list of other files
  LINK:         Pointer to another file (hard link or soft link)
  DEVICE FILE:  Represents hardware device (Linux: /dev/sda = disk)
  SOCKET:       IPC (inter-process communication) endpoint

FILE EXTENSIONS (common examples):
  .txt    → Text file
  .exe    → Windows executable
  .com    → Windows command/executable
  .dll    → Dynamic Link Library (Windows)
  .so     → Shared Object (Linux equivalent of .dll)
  .c      → C source code
  .cpp    → C++ source code
  .java   → Java source code
  .class  → Java bytecode (compiled)
  .pdf    → Portable Document Format
  .jpg    → JPEG image
  .mp4    → MPEG-4 video
```

---

## 🔷 TOPIC 9: FILE SYSTEM TYPES — BPSC EXAM TABLE

```
COMMON FILE SYSTEMS:
════════════════════════════════════════════════════════════════════

← DIRECT BPSC PYQ: "File system types: NTFS, FAT32, HFS+ (all valid)"
← Exact PYQ: "Common file operations: Create, Delete, Rename — all correct"

FILE SYSTEM  FULL NAME              OS / USE          KEY FACTS
─────────────────────────────────────────────────────────────────────
FAT16        File Allocation Table  Old Windows,      Max file: 2GB
             (16-bit)               USB drives         Max vol: 4GB

FAT32        File Allocation Table  Windows, USB,     Max file: 4GB
             (32-bit)               memory cards       Max vol: 2TB
                                                       ← very common!

NTFS         New Technology File    Windows XP/7/10/  Max file: 16EB
             System                 11                 Journaling ✓
                                                       Encryption ✓
                                                       Permissions ✓
                                                       ← Windows standard

exFAT        Extended FAT           USB drives,       Max file: 16EB
                                    SD cards           No journaling
                                    (>4GB files)

ext2/3/4     Extended File System   Linux              ext4 = current
             (2nd/3rd/4th gen)                         standard for Linux
                                                       Journaling in ext3/4

HFS+         Hierarchical File      macOS (older)      Replaced by APFS
             System Plus                               in newer macOS

APFS         Apple File System      macOS 10.13+,      SSD-optimized
                                    iOS                 Encryption ✓

ZFS          Z File System          Solaris, BSD       Checksums, snapshots
                                    (enterprise)        Very reliable

CDFS/ISO9660 CD File System         CD/DVD-ROMs        Read-only
─────────────────────────────────────────────────────────────────────

JOURNALING FILE SYSTEMS (IMPORTANT):
  = File system that keeps a LOG (journal) of changes BEFORE making them
  = If crash occurs mid-write, OS replays journal to recover consistency
  = NTFS, ext3, ext4 all have journaling
  = FAT32 does NOT have journaling → crash can corrupt data

WINDOWS FILE SYSTEM EVOLUTION:
  FAT16 → FAT32 → NTFS (current standard)

LINUX FILE SYSTEM EVOLUTION:
  ext2 → ext3 (added journaling) → ext4 (current standard)

════════════════════════════════════════════════════════════════════

DIRECTORY STRUCTURE:
  SINGLE-LEVEL:  All files in ONE directory (simplest, naming conflicts)
  TWO-LEVEL:     Separate directory per user
  TREE-STRUCTURED: Hierarchical (subdirectories) ← most common (C:\, /home/)
  ACYCLIC GRAPH:  Directories can share subdirectories (links allowed)
  GENERAL GRAPH:  Cycles allowed (requires garbage collection)

ABSOLUTE vs RELATIVE PATH:
  ABSOLUTE: Full path from root → /home/user/documents/file.txt
  RELATIVE: Path from current directory → ../documents/file.txt
  ROOT:     / (Linux) or C:\ (Windows) = top of directory tree
```

---

## 🔷 TOPIC 10: FILE ALLOCATION METHODS

```
HOW ARE FILES STORED ON DISK?
The OS must decide HOW to allocate disk blocks to files.
Three main methods:
════════════════════════════════════════════════════════════════════

METHOD 1: CONTIGUOUS ALLOCATION
  → File occupies CONSECUTIVE blocks on disk
  → Simple and fast (sequential access excellent)
  ┌──────────────────────────────────────────────────────────┐
  │ File A: blocks [10, 11, 12, 13, 14]                      │
  │ File B: blocks [20, 21, 22]                              │
  └──────────────────────────────────────────────────────────┘
  ADVANTAGE: Fast sequential AND random access
  DISADVANTAGE: External fragmentation! (holes left when files deleted)
                Hard to grow files (need to move entire file)

METHOD 2: LINKED ALLOCATION (LINKED LIST)
  → File = linked list of disk blocks
  → Each block contains pointer to NEXT block
  ┌──────────────────────────────────────────────────────────┐
  │ Block 10 → Block 25 → Block 3 → Block 47 → NULL (end)   │
  └──────────────────────────────────────────────────────────┘
  ADVANTAGE: No external fragmentation (any free block can be used)
             Files can grow dynamically
  DISADVANTAGE: SLOW random access (must follow chain from start)
                Pointer space overhead in each block
                If one pointer corrupted → rest of file lost!
  USED IN: FAT (File Allocation Table) file system
           FAT stores ALL pointers in a separate table (not in each block)

METHOD 3: INDEXED ALLOCATION
  → One special INDEX BLOCK for each file
  → Index block contains addresses of ALL data blocks
  ┌──────────────────────────────────────────────────────────┐
  │ Index Block: [10, 25, 3, 47, 82, ...]                    │
  │   → Block 10 (data), Block 25 (data), Block 3 (data)...  │
  └──────────────────────────────────────────────────────────┘
  ADVANTAGE: Good random access (just look up index block)
             No external fragmentation
  DISADVANTAGE: Index block overhead (wastes space for small files)
                Limited file size (bounded by index block size)
  USED IN: UNIX/Linux (called INODE structure)

INODE (INDEX NODE):
  = The index structure used by UNIX/Linux (ext2/3/4)
  = Contains: file attributes + direct block pointers (12)
            + single indirect pointer (points to block of pointers)
            + double indirect pointer
            + triple indirect pointer
  = Can handle very large files efficiently

════════════════════════════════════════════════════════════════════

FILE ALLOCATION COMPARISON:
  METHOD          SEQUENTIAL  RANDOM   FRAG    GROW
  ────────────────────────────────────────────────────
  Contiguous      Excellent   Good     External  Hard
  Linked          Good        Poor     None      Easy
  Indexed         Good        Good     None      Medium
  ────────────────────────────────────────────────────
```

---

## 📊 CS DAY 72 — MASTER TRAP TABLE

```
TOPIC                   CORRECT FACT                          COMMON TRAP
──────────────────────────────────────────────────────────────────────────────
Programmed I/O          = POLLING = REPEATEDLY CHECKING       Students say "interrupt-
(TRE 1.0 PYQ)           STATUS FLAGS                          driven" or confuse both
                        CPU is in busy-wait loop

Memory-mapped I/O       I/O and memory SHARE SAME             Students say "separate
(TRE 1.0 PYQ)           ADDRESS SPACE                         address space"
                        Uses normal LOAD/STORE instructions

I/O-mapped I/O          SEPARATE address spaces               Students confuse with
                        Uses special IN/OUT instructions       memory-mapped

PCI bus                 EXTENDS CONNECTIVITY of               Students say "extends
(BPSC PYQ)              PROCESSOR BUS                         memory bus" or
                                                              "expands RAM"

DMA                     Bypasses CPU for data transfer         Students say "DMA
                        Only 1 interrupt per BLOCK             needs CPU for each byte"
                        (not 1 per byte)

Secondary memory        LOGICAL organization                   Students say "physical"
(BPSC PYQ)              (long-term storage = files/dirs)       or "sequential"

File operations         CREATE, DELETE, RENAME = all valid    Students think rename
(BPSC PYQ)              (not just read/write)                  is not an OS operation

File systems            NTFS, FAT32, HFS+ = ALL VALID         Students say only one
(BPSC PYQ)              file system types                      is "correct"

Spooling                SPOOL = Simultaneous Peripheral        Students confuse with
                        Operations OnLine = disk-based queue   buffering (RAM-based)

FAT32 file size limit   Maximum file size = 4GB               Students say unlimited
                        (cannot store files > 4GB on FAT32)

Journaling              NTFS, ext3, ext4 have journaling      FAT32 does NOT have
                        = log of changes before making them    journaling (crash risk)

Contiguous allocation   External fragmentation                 Students say internal frag
                        Files hard to grow
──────────────────────────────────────────────────────────────────────────────
```

---
---

# PART 2: GS CONCEPT NOTES
## 🏛️ Local Government — Panchayati Raj + Urban Local Bodies
### (73rd Amendment + 74th Amendment — Complete Deep Dive)

---

## 🔷 TOPIC 1: WHY LOCAL GOVERNMENT? — BACKGROUND

```
GANDHIAN VISION — GRAM SWARAJ:
════════════════════════════════════════════════════════════════════
Gandhi believed in "Gram Swaraj" = Village Self-Rule
→ True democracy = governance from the grassroots level
→ Every village must be self-sufficient and self-governing
→ "India lives in her villages"

BEFORE 73RD AMENDMENT (pre-1992):
  → Panchayats existed in some states but had no constitutional backing
  → No uniformity — each state had different structure, powers, elections
  → Panchayats were weak — no guaranteed funding, no regular elections
  → Power remained concentrated at state level

BALWANT RAI MEHTA COMMITTEE (1957):
  → FIRST committee to recommend Democratic Decentralization
  → Recommended 3-tier Panchayati Raj system ← PYQ tested
  → Led to establishment of Panchayati Raj in Rajasthan first (1959)
  → Rajasthan = FIRST STATE to implement Panchayati Raj (Oct 2, 1959)
    ← Inaugurated by PM Nehru at Nagaur (Rajasthan) ← BPSC PYQ

ASHOK MEHTA COMMITTEE (1977):
  → Recommended 2-tier Panchayati Raj instead of 3-tier
  → Recommendations not fully implemented

G.V.K. RAO COMMITTEE (1985):
  → Recommended revitalizing Panchayati Raj
  → Called PRIs "grass without roots" — weak and ineffective

L.M. SINGHVI COMMITTEE (1986):
  → Recommended CONSTITUTIONAL STATUS for Panchayati Raj
  → First committee to recommend constitutional recognition of PRIs
  ← KEY: Led to eventual 73rd Constitutional Amendment

════════════════════════════════════════════════════════════════════
```

---

## 🔷 TOPIC 2: 73RD CONSTITUTIONAL AMENDMENT — PANCHAYATI RAJ

```
73RD AMENDMENT:
════════════════════════════════════════════════════════════════════

Full Name:   The Constitution (73rd Amendment) Act, 1992
Passed:      December 1992
Came into
effect:      April 24, 1993
Significance: April 24 = celebrated as NATIONAL PANCHAYATI RAJ DAY
              ← BPSC tests this date!

Added to Constitution:
  PART IX:      "The Panchayats" (Articles 243 to 243-O)
  11th SCHEDULE: List of 29 subjects that Panchayats can manage

PYQ TRAP: 73rd Amendment = PART IX + 11th SCHEDULE
          74th Amendment = PART IX-A + 12th SCHEDULE
════════════════════════════════════════════════════════════════════

THREE-TIER PANCHAYATI RAJ SYSTEM:
════════════════════════════════════════════════════════════════════

  ┌─────────────────────────────────────────────────────────────┐
  │  TIER 3 (DISTRICT LEVEL)                                    │
  │  ZILA PARISHAD / DISTRICT PANCHAYAT                         │
  │  = Apex body at district level                              │
  │  = Coordinates all panchayats in a district                 │
  ├─────────────────────────────────────────────────────────────┤
  │  TIER 2 (INTERMEDIATE / BLOCK LEVEL)                        │
  │  PANCHAYAT SAMITI / TALUK PANCHAYAT / BLOCK PANCHAYAT       │
  │  = Covers a cluster of villages (block/mandal)              │
  │  = Links village panchayat to district panchayat            │
  ├─────────────────────────────────────────────────────────────┤
  │  TIER 1 (VILLAGE LEVEL)                                     │
  │  GRAM PANCHAYAT                                             │
  │  = Basic unit of local self-government                      │
  │  = Covers one or a few villages                             │
  │  GRAM SABHA = assembly of ALL voters in a village           │
  │             = FOUNDATION of democratic governance           │
  └─────────────────────────────────────────────────────────────┘

NOTE: Intermediate tier optional for states with population < 20 lakh
      (States can have 2-tier for small states)

GRAM SABHA vs GRAM PANCHAYAT:
  GRAM SABHA:     = Assembly of ALL registered voters in the village
                  = ALL adult villagers are members
                  = Meets at least TWICE a year
                  = CANNOT be dissolved (permanent body)
                  ← PYQ TRAP: Gram Sabha is the PRIMARY institution
  GRAM PANCHAYAT: = ELECTED body of representatives from the village
                  = Smaller group that manages day-to-day affairs
                  = Reports to Gram Sabha

════════════════════════════════════════════════════════════════════

KEY PROVISIONS OF 73RD AMENDMENT:
════════════════════════════════════════════════════════════════════

1. MANDATORY 3-TIER STRUCTURE:
   → All states (except small ones) must have village, intermediate, district levels

2. GRAM SABHA:
   → Article 243-A: Gram Sabha at village level = foundation of PRI
   → Must meet at least twice per year

3. ELECTIONS:
   → Regular elections every 5 YEARS ← fixed term
   → State Election Commission (SEC) conducts elections
   ← PYQ: STATE ELECTION COMMISSION (not Election Commission of India!)
   → If panchayat dissolved before 5 years → elections within 6 MONTHS

4. RESERVATION:
   → SEATS AND OFFICES reserved for:
     • Scheduled Castes (SCs) — proportional to SC population
     • Scheduled Tribes (STs) — proportional to ST population
     • WOMEN — NOT LESS THAN 1/3 (one-third) of seats
       ← BPSC PYQ: Women reservation in PRIs = NOT LESS THAN 1/3
   → Many states now have 50% reservation for women (Bihar, UP, etc.)
   → Bihar has 50% reservation for women in panchayats ← BPSC HIGH PRIORITY

5. STATE FINANCE COMMISSION (SFC):
   → Every 5 years, state must constitute SFC
   → Reviews financial position of panchayats
   → Recommends distribution of state funds to panchayats
   ← NOT to confuse with Finance Commission of India (central body)

6. STATE ELECTION COMMISSION (SEC):
   → Each state must have its own SEC
   → Superintends, directs, controls elections to panchayats
   ← PYQ: Elections to panchayats = STATE ELECTION COMMISSION

7. DURATION: FIXED 5-YEAR TERM
   → Panchayat can be dissolved before 5 years only by state government
   → If dissolved → fresh elections within 6 months
   → Newly elected panchayat serves REMAINDER of original term only

8. ELEVENTH SCHEDULE (PART OF 73RD AMENDMENT):
   → Contains 29 subjects that Panchayats MAY be assigned power over
   → These are subjects OPTIONAL for states to devolve (not mandatory)

11TH SCHEDULE — 29 SUBJECTS (important ones for BPSC):
  1. Agriculture + land reforms
  2. Land improvement, soil conservation
  3. Minor irrigation, water management
  4. Animal husbandry, dairying
  5. Fisheries
  6. Social forestry, farm forestry
  7. Minor forest produce
  8. Small-scale industries (including food processing)
  9. Khadi, village and cottage industries
  10. Rural housing
  11. Drinking water
  12. Fuel and fodder
  13. Roads, culverts, bridges (village level)
  14. Rural electrification
  15. Non-conventional energy sources
  16. Poverty alleviation programmes
  17. EDUCATION — primary and secondary ← tested
  18. Technical training + vocational education
  19. Adult and non-formal education
  20. Libraries
  21. Cultural activities
  22. Markets and fairs
  23. Health and sanitation (including hospitals, PHCs)
  24. Family welfare
  25. Women and child development
  26. Social welfare (disabled, mentally retarded)
  27. Welfare of weaker sections (SC/ST)
  28. Public distribution system
  29. Maintenance of community assets

════════════════════════════════════════════════════════════════════
```

---

## 🔷 TOPIC 3: 74TH CONSTITUTIONAL AMENDMENT — URBAN LOCAL BODIES

```
74TH AMENDMENT:
════════════════════════════════════════════════════════════════════

Full Name:   The Constitution (74th Amendment) Act, 1992
Passed:      December 1992 (same time as 73rd!)
Came into
effect:      June 1, 1993

Added to Constitution:
  PART IX-A:    "The Municipalities" (Articles 243-P to 243-ZG)
  12th SCHEDULE: List of 18 subjects for Urban Local Bodies

Significance: Gave CONSTITUTIONAL STATUS to Urban Local Bodies (ULBs)
              ← "Urban counterpart of Panchayati Raj"

════════════════════════════════════════════════════════════════════

THREE TYPES OF URBAN LOCAL BODIES:
════════════════════════════════════════════════════════════════════

  ┌─────────────────────────────────────────────────────────────┐
  │  NAGAR PANCHAYAT                                            │
  │  = For areas transitioning from rural to urban              │
  │  = Smaller towns, semi-urban areas                          │
  │  = Population: ~10,000 to ~20,000                           │
  ├─────────────────────────────────────────────────────────────┤
  │  MUNICIPAL COUNCIL (Nagar Parishad / Nagar Palika)          │
  │  = For smaller URBAN AREAS                                  │
  │  = Medium-sized towns                                       │
  │  = Population: typically 20,000 to 3 lakh                   │
  ├─────────────────────────────────────────────────────────────┤
  │  MUNICIPAL CORPORATION (Nagar Nigam / Mahanagar Palika)     │
  │  = For LARGE URBAN AREAS (cities)                           │
  │  = Examples: Delhi, Mumbai, Kolkata, Patna, Lucknow         │
  │  = Population: typically > 3–5 lakh                         │
  │  = Most powerful ULB; handles major city governance         │
  └─────────────────────────────────────────────────────────────┘

MUNICIPAL COMMISSIONER:
  = Head of administration for Municipal Corporation
  = IAS officer appointed by state government
  = Executes decisions of elected council
  = Mayor = ceremonial head; Municipal Commissioner = real executive

MAYOR vs MUNICIPAL COMMISSIONER:
  MAYOR:                = Elected head of Municipal Corporation
                          (representative of people)
  MUNICIPAL COMMISSIONER: = Appointed IAS officer
                            (real administrative executive)
  ← PYQ TRAP: Mayor = elected head (political); Commissioner = administrative head (IAS)

════════════════════════════════════════════════════════════════════

KEY PROVISIONS OF 74TH AMENDMENT:
  → Regular elections every 5 YEARS
  → STATE ELECTION COMMISSION conducts elections (same as Panchayats)
  → RESERVATION: 1/3 seats for WOMEN (same as Panchayats)
  → SC/ST reservation proportional to their population
  → STATE FINANCE COMMISSION reviews ULB finances
  → WARD COMMITTEES for cities with > 3 lakh population
  → 12TH SCHEDULE: 18 subjects for ULBs

12TH SCHEDULE — 18 SUBJECTS (important ones):
  1. Urban planning (town planning)
  2. Regulation of land use and building construction
  3. Planning for economic and social development
  4. Roads and bridges
  5. Water supply for domestic, industrial, commercial
  6. PUBLIC HEALTH, sanitation, conservancy, solid waste management
  7. Fire services
  8. Urban forestry, environmental protection
  9. Safeguarding interests of weaker sections (SCs, STs, women, disabled)
  10. Slum improvement and upgradation
  11. Urban poverty alleviation
  12. Provision of urban amenities (parks, gardens, playgrounds)
  13. Promotion of cultural, educational, aesthetic aspects
  14. Burials and burial grounds / cremations
  15. Cattle pounds
  16. Vital statistics (birth, death)
  17. Public amenities (street lighting, parking, bus stops, public conveniences)
  18. Regulation of slaughterhouses and tanneries

════════════════════════════════════════════════════════════════════
```

---

## 🔷 TOPIC 4: 73RD vs 74TH AMENDMENT — MASTER COMPARISON

```
COMPARISON: 73RD vs 74TH AMENDMENT
════════════════════════════════════════════════════════════════════

FEATURE              73RD AMENDMENT          74TH AMENDMENT
─────────────────────────────────────────────────────────────────
Year enacted         1992 (effect: Apr 24,   1992 (effect: Jun 1,
                     1993)                   1993)
Area covered         RURAL                   URBAN
Bodies covered       PANCHAYATS              MUNICIPALITIES
Part added           PART IX (243–243-O)     PART IX-A (243-P–243-ZG)
Schedule added       11TH SCHEDULE           12TH SCHEDULE
No. of subjects      29 subjects             18 subjects
Tiers                3-tier system           3 types of ULBs
Village tier         Gram Panchayat          Nagar Panchayat (small)
Intermediate tier    Panchayat Samiti        Municipal Council (medium)
District tier        Zila Parishad           Municipal Corporation (large)
Basic unit           GRAM SABHA (all voters) WARD COMMITTEES (>3L pop)
Election authority   STATE ELECTION COMM.    STATE ELECTION COMM.
Women reservation    ≥ 1/3 seats             ≥ 1/3 seats
Term                 5 YEARS                 5 YEARS
Finance review       STATE FINANCE COMM.     STATE FINANCE COMMISSION
National day         April 24 = National     No specific national day
                     Panchayati Raj Day
−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−
★ Both passed in December 1992
★ Both have same women reservation (1/3)
★ Both have STATE ELECTION COMMISSION for elections
★ Both have STATE FINANCE COMMISSION for finances
★ Both gave constitutional status for first time
════════════════════════════════════════════════════════════════════
```

---

## 🔷 TOPIC 5: BIHAR SPECIFIC — PANCHAYATI RAJ FACTS

```
BIHAR AND PANCHAYATI RAJ:
════════════════════════════════════════════════════════════════════

1. WOMEN RESERVATION IN BIHAR:
   → Bihar has 50% reservation for women in Panchayats
     ← 50% (MORE than constitutional minimum of 1/3)
   → Bihar was one of the first states to implement 50% women reservation
   → Result: Large number of women Mukhiyas (Panchayat heads) in Bihar

2. BIHAR PANCHAYAT STRUCTURE:
   Gram Panchayat level: MUKHIYA (elected head) + Panchayat Sewak
   Block level: PANCHAYAT SAMITI
   District level: ZILA PARISHAD

3. BIHAR PANCHAYATI RAJ ACT:
   → Bihar Panchayati Raj Act 2006 (amended version)
   → Governs elections, structure, powers of panchayats in Bihar

4. URBAN LOCAL BODIES IN BIHAR:
   → Patna Municipal Corporation (PMC) = largest ULB in Bihar
   → Mayor of Patna = directly elected by voters in Patna
     ← Bihar has DIRECT ELECTION of Mayor ← PYQ trap
   → Municipal Commissioner = IAS officer, appointed by state govt
   → Bihar Municipal Act 2007 governs urban bodies

5. FIRST PANCHAYATI RAJ STATE:
   → RAJASTHAN = first state to implement Panchayati Raj (Oct 2, 1959)
   → Inaugurated at NAGAUR, Rajasthan, by PM JAWAHARLAL NEHRU
   ← BPSC PYQ: First state = Rajasthan, inaugurated by Nehru, location = Nagaur

════════════════════════════════════════════════════════════════════
```

---

## 🔷 TOPIC 6: STATE ELECTION COMMISSION + STATE FINANCE COMMISSION

```
STATE ELECTION COMMISSION (SEC):
════════════════════════════════════════════════════════════════════

  → Established by 73rd AND 74th Amendments
  → Article 243-K (Panchayats) and 243-ZA (Municipalities)
  → One SEC per state (not same as Election Commission of India!)
  → Headed by: STATE ELECTION COMMISSIONER
  → Appointed by: GOVERNOR of the state
  → Removal: Same as removal of a High Court JUDGE (difficult — protects independence)

FUNCTIONS:
  → Superintends, directs, controls ALL elections to Panchayats and Municipalities
  → Determines election schedule
  → Resolves election disputes
  → Can issue model code of conduct

SEC vs ELECTION COMMISSION OF INDIA (ECI):
  SEC (State):  Handles panchayat + municipal elections ONLY
                Separate for each state
                Appointed by Governor
  ECI (Central): Handles Lok Sabha, Rajya Sabha, State Legislative elections
                 One for whole India
                 Appointed by President

STATE FINANCE COMMISSION (SFC):
════════════════════════════════════════════════════════════════════

  → Established every 5 years by state government
  → Article 243-I (Panchayats) and 243-Y (Municipalities)
  → Reviews financial position of local bodies
  → Recommends:
    a) Distribution of state tax revenues between state + local bodies
    b) Determination of taxes, fees, tolls local bodies can levy
    c) Grants-in-aid from state consolidated fund to local bodies
  → NOT the same as Finance Commission of India (central)

SFC vs FINANCE COMMISSION OF INDIA:
  SFC:  State body → reviews local body (panchayat + ULB) finances
  FCI:  Central body → reviews centre-state financial relations
        (Article 280, constituted every 5 years by President)
```

---

## 🔷 TOPIC 7: DECENTRALIZATION — KEY CONCEPTS

```
DECENTRALIZATION = Transfer of power from higher levels to lower levels
                   of government

TYPES OF DECENTRALIZATION:
  POLITICAL:   Transfer of political authority (elected local bodies)
               → 73rd and 74th amendments = political decentralization
  ADMINISTRATIVE: Transfer of administrative functions (field offices)
  FISCAL:      Transfer of financial resources (grants, devolution)

3 Fs OF EFFECTIVE DECENTRALIZATION:
  → FUNCTIONS (what powers/subjects they handle)
  → FUNDS (how much money they get)
  → FUNCTIONARIES (who implements: staff, officers)
  ← BPSC likes this 3F framework for decentralization questions

GRASSROOTS DEMOCRACY:
  → Concept that democracy must reach village level
  → Panchayati Raj = grassroots democracy in practice
  → Key to India's federal structure

FIFTH AND SIXTH SCHEDULE (related to tribal areas):
  FIFTH SCHEDULE:  Tribal areas in 10 states (excluding Northeast)
                   Governor has special powers for tribal welfare
  SIXTH SCHEDULE:  Tribal areas in 4 NE states (Assam, Meghalaya, Tripura, Mizoram)
                   Autonomous District Councils with legislative powers
  ← These tribal areas have MODIFIED Panchayati Raj (PESA Act applies to 5th Schedule)

PESA ACT (1996):
  = Provisions of the Panchayati Raj Extension to Scheduled Areas Act
  → Extends Panchayati Raj to tribal (Fifth Schedule) areas
  → Gives tribal communities special powers (consent for land acquisition,
    management of minor forest produce, dispute resolution)
  ← BPSC tests this in tribal governance context
```

---
---

# PART 3: PRACTICE QUESTIONS
## 📝 MIXED PYQ + CONCEPT MCQs — Day 72 (CS + GS)

---

### COMPUTER SCIENCE — 25 MCQs (I/O Management + File Systems)

---

**Q1.** PROGRAM-CONTROLLED I/O is also called:
(A) Interrupt-driven I/O
(B) POLLING — CPU repeatedly checks STATUS FLAGS of device controller
(C) DMA — Direct Memory Access
(D) More than one of the above
(E) None of the above

---

**Q2.** In POLLING (programmed I/O), what does the CPU do while waiting for I/O completion?
(A) Executes other processes (multitasking)
(B) Sends an interrupt to the device and sleeps
(C) REPEATEDLY CHECKS the STATUS FLAGS in a busy-wait loop — doing no other work
(D) More than one of the above
(E) None of the above

---

**Q3.** MEMORY-MAPPED I/O means:
(A) I/O device registers have a SEPARATE address space from main memory
(B) I/O devices and main memory SHARE THE SAME address space
(C) Memory is mapped to disk (virtual memory)
(D) More than one of the above
(E) None of the above

---

**Q4.** The PCI bus (Peripheral Component Interconnect) is used to:
(A) Replace the CPU in data processing tasks
(B) EXTEND THE CONNECTIVITY of the PROCESSOR BUS to peripheral devices
(C) Connect two different computers over a network
(D) More than one of the above
(E) None of the above

---

**Q5.** DMA (Direct Memory Access) is superior to interrupt-driven I/O for large data transfers because:
(A) DMA requires more CPU interrupts than interrupt-driven I/O
(B) DMA BYPASSES the CPU and sends only ONE interrupt per BLOCK (not per byte)
(C) DMA uses a software routine that runs faster than hardware interrupts
(D) More than one of the above
(E) None of the above

---

**Q6.** The organization of SECONDARY MEMORY is best described as:
(A) Physical organization (sectors, tracks, cylinders)
(B) Structural organization (hardware layout)
(C) LOGICAL organization (files and directories — long-term storage)
(D) More than one of the above
(E) None of the above

---

**Q7.** Which of the following is a VALID file system type?
(A) NTFS only
(B) FAT32 only
(C) NTFS, FAT32, and HFS+ are ALL valid file system types
(D) More than one of the above
(E) None of the above

---

**Q8.** Which of the following are VALID file operations in an operating system?
(A) Create and Delete only
(B) Read and Write only
(C) Create, Delete, Rename, Open, Close, Read, Write — ALL are valid operations
(D) More than one of the above
(E) None of the above

---

**Q9.** In I/O-MAPPED I/O (Port-Mapped I/O), the CPU accesses I/O devices using:
(A) Normal LOAD/STORE memory instructions (same as memory access)
(B) Special IN/OUT instructions and a SEPARATE I/O address space
(C) DMA controller commands sent via memory writes
(D) More than one of the above
(E) None of the above

---

**Q10.** SPOOLING (Simultaneous Peripheral Operations OnLine) is best described as:
(A) A technique for directly connecting CPU to printer bypassing OS
(B) Storing output data in a DISK-BASED QUEUE so devices can be used asynchronously
(C) A method of increasing CPU clock speed using peripheral feedback
(D) More than one of the above
(E) None of the above

---

**Q11.** What is CYCLE STEALING in the context of DMA?
(A) CPU steals memory cycles from the DMA controller
(B) DMA controller temporarily takes control of the memory bus (steals cycles from CPU)
(C) Operating system steals CPU cycles to handle I/O interrupts
(D) More than one of the above
(E) None of the above

---

**Q12.** The INTERRUPT SERVICE ROUTINE (ISR) is:
(A) A hardware component that generates interrupt signals
(B) A piece of code that handles a specific interrupt when it arrives
(C) A register in the CPU that stores interrupt priority
(D) More than one of the above
(E) None of the above

---

**Q13.** FAT32 (File Allocation Table 32-bit) has a MAXIMUM FILE SIZE limitation of:
(A) 2 GB
(B) 4 GB
(C) 2 TB
(D) More than one of the above
(E) None of the above

---

**Q14.** Which of the following CORRECTLY describes CONTIGUOUS FILE ALLOCATION?
(A) File blocks are linked by pointers — random access is slow
(B) File occupies CONSECUTIVE blocks — excellent sequential access but external fragmentation
(C) An index block stores addresses of all file blocks
(D) More than one of the above
(E) None of the above

---

**Q15.** NTFS (New Technology File System) supports which of the following features?
(A) Journaling (log of changes for crash recovery)
(B) File encryption and permissions
(C) Files larger than 4GB
(D) More than one of the above
(E) None of the above

---

**Q16.** Compared to POLLING, INTERRUPT-DRIVEN I/O improves performance because:
(A) It completely eliminates I/O time
(B) CPU can do other useful work while waiting for I/O to complete
(C) It requires no hardware support
(D) More than one of the above
(E) None of the above

---

**Q17.** An INODE in UNIX/Linux file systems contains:
(A) The file name and its directory path only
(B) File attributes (size, timestamps, permissions) AND pointers to data blocks
(C) A linked list of all file names in the directory
(D) More than one of the above
(E) None of the above

---

**Q18.** USB stands for:
(A) Universal System Bus
(B) Unified Serial Broadband
(C) Universal Serial Bus
(D) More than one of the above
(E) None of the above

---

**Q19.** In LINKED FILE ALLOCATION, which of the following is a DISADVANTAGE?
(A) Files cannot grow dynamically
(B) External fragmentation is a serious problem
(C) RANDOM ACCESS is very slow (must follow pointer chain from start)
(D) More than one of the above
(E) None of the above

---

**Q20.** Which I/O method requires the CPU to do the LEAST WORK during data transfer?
(A) Polling (programmed I/O)
(B) Interrupt-driven I/O
(C) DMA (Direct Memory Access)
(D) More than one of the above
(E) None of the above

---

**Q21.** The STATUS REGISTER of a device controller is primarily used for:
(A) Storing the data being transferred to/from the device
(B) POLLING — CPU reads this register to check if device operation is complete
(C) Storing the DMA transfer count
(D) More than one of the above
(E) None of the above

---

**Q22.** JOURNALING in a file system means:
(A) Keeping a log of file names for faster directory search
(B) Keeping a LOG OF CHANGES before making them — enables crash recovery
(C) Compressing file data for storage efficiency
(D) More than one of the above
(E) None of the above

---

**Q23.** In INDEXED FILE ALLOCATION:
(A) All file blocks are stored consecutively on disk
(B) Each block has a pointer to the next block
(C) ONE INDEX BLOCK contains addresses of ALL data blocks of the file
(D) More than one of the above
(E) None of the above

---

**Q24.** Which of the following CORRECTLY pairs file system with its operating system?
(A) NTFS → macOS; HFS+ → Windows; ext4 → Linux
(B) NTFS → Windows; ext4 → Linux; HFS+/APFS → macOS
(C) FAT32 → Linux only; NTFS → macOS only
(D) More than one of the above
(E) None of the above

---

**Q25.** A DEVICE DRIVER in an operating system is:
(A) A hardware chip that physically drives current to devices
(B) OS-specific software that provides an interface between OS and a specific device
(C) A DMA controller program stored in ROM
(D) More than one of the above
(E) None of the above

---
---

### GENERAL STUDIES — 25 MCQs (Local Government)

---

**Q26.** The 73rd Constitutional Amendment gave constitutional status to:
(A) Urban Local Bodies (Municipalities)
(B) PANCHAYATS (Rural Local Self-Government)
(C) State Finance Commissions only
(D) More than one of the above
(E) None of the above

---

**Q27.** The 73rd Amendment added which PART and SCHEDULE to the Indian Constitution?
(A) Part IX-A and 12th Schedule
(B) Part IX and 11th Schedule
(C) Part IV and 10th Schedule
(D) More than one of the above
(E) None of the above

---

**Q28.** National Panchayati Raj Day is celebrated on:
(A) January 26
(B) October 2 (Gandhi Jayanti)
(C) April 24 (date 73rd Amendment came into effect in 1993)
(D) More than one of the above
(E) None of the above

---

**Q29.** Under the 73rd Amendment, ELECTIONS to Panchayats are conducted by:
(A) Election Commission of India (ECI)
(B) STATE ELECTION COMMISSION (SEC) — separate body for each state
(C) State Government directly (through district collectors)
(D) More than one of the above
(E) None of the above

---

**Q30.** The minimum reservation for WOMEN in Panchayat seats under 73rd Amendment is:
(A) One-fourth (1/4) of all seats
(B) NOT LESS THAN ONE-THIRD (1/3) of all seats
(C) Half (1/2) of all seats
(D) More than one of the above
(E) None of the above

---

**Q31.** GRAM SABHA is:
(A) The elected committee of representatives who manage the village panchayat
(B) Assembly of ALL REGISTERED VOTERS in the village — the primary democratic unit
(C) The district-level apex body of Panchayati Raj
(D) More than one of the above
(E) None of the above

---

**Q32.** The BALWANT RAI MEHTA COMMITTEE (1957) is associated with:
(A) Recommending constitutional status for urban local bodies
(B) Recommending Democratic Decentralization — FIRST to recommend 3-tier Panchayati Raj
(C) Drafting the 73rd Constitutional Amendment provisions
(D) More than one of the above
(E) None of the above

---

**Q33.** Which state was the FIRST to implement Panchayati Raj after Balwant Rai Mehta Committee?
(A) Bihar
(B) Uttar Pradesh
(C) Rajasthan (at Nagaur, inaugurated by PM Nehru, October 2, 1959)
(D) More than one of the above
(E) None of the above

---

**Q34.** The 11th Schedule of the Indian Constitution (added by 73rd Amendment) contains:
(A) 18 subjects for Urban Local Bodies
(B) 29 subjects that may be devolved to Panchayats
(C) Fundamental Duties of citizens
(D) More than one of the above
(E) None of the above

---

**Q35.** The STATE FINANCE COMMISSION (SFC) is constituted every:
(A) 3 years
(B) 5 YEARS — to review financial position of local bodies
(C) 10 years
(D) More than one of the above
(E) None of the above

---

**Q36.** The 74th Constitutional Amendment relates to:
(A) Panchayati Raj (rural)
(B) URBAN LOCAL BODIES (Municipalities)
(C) State Finance Commission only
(D) More than one of the above
(E) None of the above

---

**Q37.** The 12th Schedule (74th Amendment) contains how many subjects for Urban Local Bodies?
(A) 29 subjects
(B) 18 subjects
(C) 22 subjects
(D) More than one of the above
(E) None of the above

---

**Q38.** MUNICIPAL COMMISSIONER of a Municipal Corporation is:
(A) Directly elected by citizens of the city
(B) Elected by the councillors of the Municipal Corporation
(C) An IAS officer APPOINTED by the state government — real executive head
(D) More than one of the above
(E) None of the above

---

**Q39.** Which of the following CORRECTLY describes a NAGAR PANCHAYAT?
(A) Largest urban local body for major metropolitan cities
(B) Body for areas in TRANSITION from rural to urban (semi-urban small towns)
(C) Another name for District Panchayat (Zila Parishad)
(D) More than one of the above
(E) None of the above

---

**Q40.** PESA Act (1996) relates to:
(A) Extending Panchayati Raj to SCHEDULED (TRIBAL) AREAS (Fifth Schedule)
(B) Providing pensions to Panchayat members
(C) Allocating funds to Panchayats from central finance commission
(D) More than one of the above
(E) None of the above

---

**Q41.** Bihar has what percentage of seat RESERVATION FOR WOMEN in Panchayats?
(A) 33% (as per constitutional minimum)
(B) 40%
(C) 50% (Bihar gives more than constitutional minimum)
(D) More than one of the above
(E) None of the above

---

**Q42.** The L.M. SINGHVI COMMITTEE (1986) was the FIRST to recommend:
(A) 3-tier Panchayati Raj structure
(B) Abolition of intermediary panchayat tier
(C) CONSTITUTIONAL STATUS for Panchayati Raj Institutions
(D) More than one of the above
(E) None of the above

---

**Q43.** Both 73rd and 74th Amendments require that dissolved local bodies must have fresh elections within:
(A) 3 months
(B) 6 MONTHS of dissolution
(C) 1 year
(D) More than one of the above
(E) None of the above

---

**Q44.** Which of the following is a THREE-TIER structure under Panchayati Raj?
(A) Gram Panchayat → Panchayat Samiti → Zila Parishad (Village→Block→District)
(B) Ward → Municipal Council → Municipal Corporation
(C) Gram Sabha → Gram Panchayat → Zila Parishad (skipping intermediate tier)
(D) More than one of the above
(E) None of the above

---

**Q45.** The concept of "GRAM SWARAJ" (Village Self-Rule) is associated with:
(A) Dr. B.R. Ambedkar
(B) Jawaharlal Nehru
(C) Mahatma Gandhi — who believed true democracy must be at village level
(D) More than one of the above
(E) None of the above

---

**Q46.** WARD COMMITTEES are to be constituted in municipalities with population exceeding:
(A) 1 lakh
(B) 2 lakh
(C) 3 LAKH (Article 243-S)
(D) More than one of the above
(E) None of the above

---

**Q47.** The STATE ELECTION COMMISSIONER is appointed by and can be removed like:
(A) Appointed by President; removed like Supreme Court judge
(B) Appointed by GOVERNOR; removed like HIGH COURT JUDGE
(C) Appointed by Chief Minister; removed by state legislature
(D) More than one of the above
(E) None of the above

---

**Q48.** MATCH THE FOLLOWING — Amendment and its addition:
```
Amendment      What it added
1. 73rd        A. Part IX-A + 12th Schedule (Municipalities)
2. 74th        B. Fundamental Duties (Art 51A)
3. 42nd        C. Part IX + 11th Schedule (Panchayats)
4. 44th        D. Removed Right to Property from FRs
```
(A) 1-C, 2-A, 3-B, 4-D
(B) 1-A, 2-C, 3-D, 4-B
(C) 1-B, 2-D, 3-C, 4-A
(D) More than one of the above
(E) None of the above

---

**Q49.** The 3 "Fs" essential for effective decentralization are:
(A) Finance, Freedom, Federation
(B) FUNCTIONS, FUNDS, FUNCTIONARIES
(C) Federal, Fair, Firm
(D) More than one of the above
(E) None of the above

---

**Q50.** Which of the following CORRECTLY identifies subjects in the 11th Schedule (Panchayats)?
(A) Urban planning and regulation of land use in cities
(B) Fire services and public amenities (street lighting, parking)
(C) Agriculture, primary education, drinking water, and poverty alleviation
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY

## ⚠️ MANDATORY: Attempt ALL 50 questions BEFORE checking!

---

### CS Answers (Q1–Q25):

| Q  | Answer | Reason (one-line) |
|----|--------|-------------------|
| 1  | (B)    | Programmed I/O = POLLING = CPU repeatedly checks status flags ← TRE 1.0 exact PYQ |
| 2  | (C)    | Polling = CPU in busy-wait loop, checking status flags, doing NO other work |
| 3  | (B)    | Memory-mapped I/O = I/O and memory SHARE THE SAME address space ← TRE 1.0 PYQ |
| 4  | (B)    | PCI bus = EXTENDS CONNECTIVITY of PROCESSOR BUS ← exact BPSC PYQ phrase |
| 5  | (B)    | DMA bypasses CPU; only ONE interrupt per BLOCK (not per byte = far fewer interrupts) |
| 6  | (C)    | Secondary memory = LOGICAL organization (files/directories) ← direct PYQ |
| 7  | (C)    | NTFS, FAT32, HFS+ = ALL valid file system types ← direct BPSC PYQ |
| 8  | (C)    | ALL file operations are valid: Create, Delete, Rename, Open, Close, Read, Write ← PYQ |
| 9  | (B)    | I/O-mapped = special IN/OUT instructions + SEPARATE I/O address space |
| 10 | (B)    | Spooling = disk-based queue; devices used asynchronously (e.g., printer spool) |
| 11 | (B)    | Cycle stealing = DMA takes control of memory bus temporarily from CPU |
| 12 | (B)    | ISR (Interrupt Service Routine) = code that handles a specific interrupt |
| 13 | (B)    | FAT32 maximum file size = 4GB (cannot store files >4GB) ← common PYQ trap |
| 14 | (B)    | Contiguous = consecutive blocks; excellent sequential access; external fragmentation |
| 15 | (D)    | NTFS supports ALL three: journaling + encryption + files >4GB |
| 16 | (B)    | Interrupt I/O = CPU does other work while I/O in progress (vs polling busy-wait) |
| 17 | (B)    | Inode = file attributes (size, timestamps, permissions) + pointers to data blocks |
| 18 | (C)    | USB = Universal Serial Bus |
| 19 | (C)    | Linked allocation = SLOW random access (must follow pointer chain from beginning) |
| 20 | (C)    | DMA requires LEAST CPU involvement (device controller does the transfer) |
| 21 | (B)    | Status register = polled by CPU to check if device operation is complete |
| 22 | (B)    | Journaling = log of changes before making them → crash recovery possible |
| 23 | (C)    | Indexed allocation = ONE index block contains addresses of ALL data blocks |
| 24 | (B)    | NTFS→Windows; ext4→Linux; HFS+/APFS→macOS ← correct OS-filesystem pairing |
| 25 | (B)    | Device driver = OS software providing interface between OS and specific device |

---

### GS Answers (Q26–Q50):

| Q  | Answer | Reason (one-line) |
|----|--------|-------------------|
| 26 | (B)    | 73rd Amendment = PANCHAYATS (rural local self-government) |
| 27 | (B)    | 73rd Amendment = PART IX + 11TH SCHEDULE (29 subjects) |
| 28 | (C)    | National Panchayati Raj Day = APRIL 24 (when 73rd came into force, 1993) |
| 29 | (B)    | Elections to Panchayats = STATE ELECTION COMMISSION (not ECI) ← PYQ trap |
| 30 | (B)    | Women reservation = NOT LESS THAN 1/3 (one-third) of seats ← constitutional minimum |
| 31 | (B)    | Gram Sabha = ALL registered voters in village = primary democratic unit |
| 32 | (B)    | Balwant Rai Mehta 1957 = FIRST to recommend Democratic Decentralization + 3-tier PRIs |
| 33 | (C)    | Rajasthan = FIRST state; Nagaur; October 2, 1959; inaugurated by Nehru ← PYQ |
| 34 | (B)    | 11th Schedule = 29 subjects for Panchayats ← key fact |
| 35 | (B)    | State Finance Commission = every 5 YEARS |
| 36 | (B)    | 74th Amendment = URBAN LOCAL BODIES (Municipalities) |
| 37 | (B)    | 12th Schedule = 18 subjects for ULBs |
| 38 | (C)    | Municipal Commissioner = IAS officer appointed by state govt = real executive |
| 39 | (B)    | Nagar Panchayat = transitional area from rural to urban (small semi-urban towns) |
| 40 | (A)    | PESA Act 1996 = extends Panchayati Raj to Scheduled (tribal) areas (5th Schedule) |
| 41 | (C)    | Bihar = 50% women reservation in Panchayats (more than constitutional 1/3 minimum) |
| 42 | (C)    | L.M. Singhvi Committee 1986 = FIRST to recommend constitutional status for PRIs |
| 43 | (B)    | Dissolved local bodies must hold fresh elections within 6 MONTHS |
| 44 | (A)    | 3-tier: Gram Panchayat (village) → Panchayat Samiti (block) → Zila Parishad (district) |
| 45 | (C)    | Gram Swaraj = GANDHI's vision of village self-rule (foundation of democracy) |
| 46 | (C)    | Ward Committees = mandatory for municipalities with population > 3 LAKH |
| 47 | (B)    | State Election Commissioner = appointed by GOVERNOR; removed like HIGH COURT JUDGE |
| 48 | (A)    | 73rd→C (Part IX+11th Sch), 74th→A (Part IX-A+12th Sch), 42nd→B (FDs), 44th→D (property) |
| 49 | (B)    | 3 Fs = FUNCTIONS, FUNDS, FUNCTIONARIES (essential for decentralization) |
| 50 | (C)    | Agriculture, primary education, drinking water, poverty alleviation = 11th Schedule items |

---
---

# 🔁 NIGHT REVISION SHEET
## 📌 Day 72 — Ultra-Crisp "Last 30 Minutes Before Sleep"

---

### ⚡ CS — I/O MANAGEMENT + FILE SYSTEMS: 20 MUST-KNOW FACTS

```
I/O TYPES (3 PYQ FACTS):
1.  POLLING = Program-controlled I/O = CPU REPEATEDLY CHECKS STATUS FLAGS
    ← TRE 1.0 PYQ: EXACT PHRASE = "repeatedly checking status flags"
    CPU in busy-wait loop → worst CPU utilization
2.  Interrupt I/O = device NOTIFIES CPU → CPU free to do other work meanwhile
3.  DMA = BYPASSES CPU for data transfer → only 1 interrupt per BLOCK
    DMA = Cycle Stealing (DMA takes memory bus from CPU temporarily)

I/O ADDRESS SPACE (2 PYQ FACTS):
4.  Memory-mapped I/O = I/O and memory SHARE SAME address space ← TRE 1.0 PYQ
    Uses normal LOAD/STORE instructions
5.  I/O-mapped I/O = SEPARATE address spaces; uses special IN/OUT instructions

BUS:
6.  PCI bus = EXTENDS CONNECTIVITY of PROCESSOR BUS ← BPSC direct PYQ phrase
7.  USB = Universal Serial Bus (external devices)

SPOOLING:
8.  SPOOL = Simultaneous Peripheral Operations OnLine
9.  Spooling = disk-based queue (printer spooling = most classic example)

SECONDARY MEMORY + FILE SYSTEM:
10. Secondary memory = LOGICAL organization ← direct BPSC PYQ
11. File system types: NTFS, FAT32, HFS+ = ALL valid ← PYQ
12. File operations: Create, Delete, Rename = ALL valid ← PYQ (not just read/write)
13. FULL list: Create, Delete, Open, Close, Read, Write, Rename, Seek, Append

FILE SYSTEM FACTS:
14. FAT32 max file size = 4GB (cannot store files >4GB)
15. NTFS = Windows standard; supports journaling, encryption, >4GB files
16. ext4 = Linux standard (journaling)
17. HFS+ / APFS = macOS
18. Journaling = log of changes BEFORE making them → crash recovery

FILE ALLOCATION:
19. Contiguous = consecutive blocks; fast; external fragmentation problem
20. Linked = linked list; no fragmentation; SLOW random access ← weakness
21. Indexed = index block with all addresses; good random access; inode in Linux
```

---

### ⚡ GS — LOCAL GOVERNMENT: 15 MUST-KNOW FACTS

```
73RD AMENDMENT (Panchayats):
1.  73rd Amendment = 1992; effective April 24, 1993
    April 24 = NATIONAL PANCHAYATI RAJ DAY
2.  Added: PART IX + 11th SCHEDULE (29 subjects)
3.  3-tier: Gram Panchayat (village) → Panchayat Samiti (block) → Zila Parishad (district)
4.  Gram Sabha = ALL voters in village = CANNOT be dissolved (permanent body)
5.  Women reservation = NOT LESS THAN 1/3 of seats ← constitutional minimum
    Bihar = 50% (more than minimum) ← Bihar-specific BPSC fact
6.  Elections = STATE ELECTION COMMISSION (NOT ECI) ← PYQ trap
7.  Dissolved panchayat → fresh election within 6 MONTHS
8.  State Finance Commission = every 5 years (reviews panchayat finances)

74TH AMENDMENT (Urban):
9.  74th Amendment = 1992; effective June 1, 1993
10. Added: PART IX-A + 12th SCHEDULE (18 subjects)
11. 3 ULB types: Nagar Panchayat → Municipal Council → Municipal Corporation
12. Mayor = elected (political head); Municipal Commissioner = IAS (executive head)

KEY COMMITTEES:
13. Balwant Rai Mehta (1957) = FIRST to recommend 3-tier Panchayati Raj
14. L.M. Singhvi (1986) = FIRST to recommend CONSTITUTIONAL STATUS for PRIs
15. Rajasthan = FIRST state to implement PRIs (Oct 2, 1959, Nagaur, PM Nehru)

KEY CONCEPTS:
16. PESA Act 1996 = extends PRIs to Scheduled (tribal) areas (5th Schedule areas)
17. 3 Fs of decentralization = FUNCTIONS + FUNDS + FUNCTIONARIES
18. State Election Commissioner = appointed by GOVERNOR; removed like HC JUDGE
```

---

### ⚡ TOMORROW — DAY 73 PREVIEW

```
CS:  Threads + CPU Scheduling + Deadlocks
     KEY FACTS:
     → Thread shares: CODE SECTION + DATA SECTION ← PYQ
     → Thread does NOT share: STACK (each thread has OWN STACK) ← PYQ
     → Deadlock = ALL 4 conditions MUST hold: Mutual Exclusion + Hold & Wait
       + No Preemption + Circular Wait
     → Round Robin = preemptive + time quantum based
     → Context switch = saving + loading process state (PCB)

GS:  Indian Geography — Plateaus, Soils, Agriculture
     KEY FACTS:
     → Black soil = found in Karnataka + Gujarat (BOTH correct) ← BPSC PYQ
     → Malnad region = Karnataka Plateau ← BPSC PYQ
     → South Peninsular Upland = part of Gondwana Land ← BPSC PYQ
     → Highest peak Eastern Ghats = Mahendragiri ← BPSC PYQ
```

---

## 🎯 WEEK 11 PROGRESS TRACKER

```
Day 68: OS Introduction & Types             ✅ DONE
Day 69: Paging (Complete)                   ✅ DONE
Day 70: Segmentation + Virtual Memory       ✅ DONE
Day 71: Disk Scheduling (Complete)          ✅ DONE
Day 72: I/O Management + File Systems       ← TODAY ✅
Day 73: Threads + CPU Scheduling + Deadlocks
Day 74: OS Complete Revision + 25 PYQ MCQs
```

---

*Day 72 Complete | Week 11 of 25 | Phase 2: Depth | Target: TOP 50 RANK*
