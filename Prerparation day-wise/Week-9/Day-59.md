# 📅 BPSC TRE 4.0 — DAY 59 COMPLETE STUDY MODULE
### Computer Networks: Subnetting, Multiplexing & I/O Addressing + Indian History — Salt Satyagraha & Civil Disobedience Movement
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): CS — Subnetting, VLSM, TDM/FDM/WDM, Memory-Mapped I/O vs I/O-Mapped I/O
> - Afternoon (1 hr): GS — Salt Satyagraha 1930, Civil Disobedience Movement, Purna Swaraj, Round Table Conferences, Bihar's role
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Computer Networks — Subnetting, Multiplexing & I/O Addressing

---

## 🔷 SECTION 1: IP Addressing — Quick Recap Before Subnetting

Before subnetting makes sense, these foundations must be solid:

```
IPv4 ADDRESS:
  → 32 bits total, written as 4 octets separated by dots
  → Example: 192.168.10.5
  → Each octet = 8 bits = values from 0 to 255

TWO PARTS OF AN IP ADDRESS:
  ┌────────────────────────────────────────────────┐
  │  IP Address  =  NETWORK PART  +  HOST PART     │
  │                                                │
  │  192.168.10.5  with subnet mask 255.255.255.0  │
  │  Network part: 192.168.10  (first 24 bits)     │
  │  Host part:    .5          (last 8 bits)        │
  └────────────────────────────────────────────────┘

SUBNET MASK:
  → Identifies which portion of the IP is NETWORK and which is HOST
  → Written in same dotted notation: 255.255.255.0
  → Or in CIDR notation: /24 (means first 24 bits = network)
  
  255.255.255.0 in binary:
  11111111.11111111.11111111.00000000
  ←────── NETWORK (24 bits) ──────→←HOST→

  The 1s in the subnet mask = NETWORK bits
  The 0s in the subnet mask = HOST bits

🎯 PYQ FACT: Subnet mask identifies the NETWORK PORTION of an IP address.
```

### IPv4 Address Classes (Quick Reference):

```
┌───────┬─────────────────────┬──────────────────┬───────────────────┬──────────────┐
│ CLASS │   RANGE (First Oct) │  DEFAULT MASK    │    NETWORK BITS   │   USE        │
├───────┼─────────────────────┼──────────────────┼───────────────────┼──────────────┤
│   A   │   1 – 126           │  255.0.0.0  (/8) │  8 bits           │  Large orgs  │
├───────┼─────────────────────┼──────────────────┼───────────────────┼──────────────┤
│   B   │  128 – 191          │ 255.255.0.0 (/16)│  16 bits          │  Medium orgs │
├───────┼─────────────────────┼──────────────────┼───────────────────┼──────────────┤
│   C   │  192 – 223          │255.255.255.0(/24)│  24 bits          │  Small orgs  │
├───────┼─────────────────────┼──────────────────┼───────────────────┼──────────────┤
│   D   │  224 – 239          │  (no mask)       │  Multicast        │  Multicasting│
├───────┼─────────────────────┼──────────────────┼───────────────────┼──────────────┤
│   E   │  240 – 255          │  (no mask)       │  Experimental     │  Reserved    │
└───────┴─────────────────────┴──────────────────┴───────────────────┴──────────────┘

SPECIAL ADDRESSES:
  127.x.x.x  → Loopback (localhost) — used for testing on same machine
  0.0.0.0    → Represents "this host" / default route
  255.255.255.255 → Limited broadcast (sends to all hosts on local network)

🎯 PYQ FACT: 127.0.0.1 = loopback address (localhost)
🎯 PYQ FACT: Class A starts at 1 (NOT 0); 127 is reserved for loopback
```

---

## 🔷 SECTION 2: Subnetting — Dividing a Network

### Why Subnetting?

Imagine a large organization gets a Class B network — giving them **65,534 host addresses** in ONE network. Problems arise:

```
PROBLEMS WITH ONE LARGE NETWORK:
  → Too much broadcast traffic (every device hears every broadcast)
  → No security isolation between departments (HR, Finance, Engineering)
  → Wasted IP addresses (Engineering has 100 computers, but 65,000 IPs wasted)
  → Difficult to manage and troubleshoot

SUBNETTING SOLUTION:
  → DIVIDE one large network into multiple smaller sub-networks
  → Each sub-network (subnet) = separate broadcast domain
  → Better security, efficiency, and management
```

### How Subnetting Works — The Core Idea:

```
SUBNETTING = BORROWING bits from the HOST portion and using them
             as SUBNET bits to create multiple smaller networks.

ORIGINAL NETWORK: 192.168.1.0 /24 (Class C, 254 usable hosts)

  IP:   192.168.1.  [xxxxxxxx]   ← last 8 bits = host bits
  Mask: 255.255.255.0

AFTER BORROWING 2 HOST BITS FOR SUBNETTING (new mask = /26):
  IP:   192.168.1.  [xx|xxxxxx]  ← 2 subnet bits | 6 host bits
  Mask: 255.255.255.192

  This creates 2² = 4 subnets:
  
  Subnet 0: 192.168.1.0   to 192.168.1.63   (hosts: .1 to .62)
  Subnet 1: 192.168.1.64  to 192.168.1.127  (hosts: .65 to .126)
  Subnet 2: 192.168.1.128 to 192.168.1.191  (hosts: .129 to .190)
  Subnet 3: 192.168.1.192 to 192.168.1.255  (hosts: .193 to .254)
  
  Each subnet: 64 total addresses, 62 USABLE (first = network, last = broadcast)
```

### Key Subnetting Formulas:

```
FORMULAS TO MEMORIZE:

  Number of SUBNETS created  = 2^(subnet bits borrowed)
  
  Total addresses per subnet = 2^(host bits remaining)
  
  USABLE hosts per subnet    = 2^(host bits remaining) - 2
  (subtract 2: one for NETWORK address, one for BROADCAST address)

EXAMPLE WALKTHROUGH:
  Network: 192.168.10.0 /24  → Borrow 3 bits for subnetting

  New prefix length: /24 + 3 = /27
  New subnet mask: 255.255.255.224

  Number of subnets: 2³ = 8 subnets
  Host bits remaining: 32 - 27 = 5 host bits
  Addresses per subnet: 2⁵ = 32
  Usable hosts per subnet: 32 - 2 = 30

TABLE OF SUBNET SIZES (CIDR → Hosts):
  /24  → 2⁸  = 256 total → 254 usable
  /25  → 2⁷  = 128 total → 126 usable
  /26  → 2⁶  =  64 total →  62 usable
  /27  → 2⁵  =  32 total →  30 usable
  /28  → 2⁴  =  16 total →  14 usable
  /29  → 2³  =   8 total →   6 usable
  /30  → 2²  =   4 total →   2 usable  ← point-to-point links
  /32  → 2⁰  =   1 total →   0 usable  ← single host route

NETWORK ADDRESS (first address in range) = ALL HOST BITS = 0
BROADCAST ADDRESS (last address in range) = ALL HOST BITS = 1

🎯 PYQ FACT: Usable hosts = 2^(host bits) - 2 (subtract network + broadcast addresses)
🎯 PYQ FACT: /30 subnet = 2 usable hosts (used for router-to-router point-to-point links)
```

### CIDR Notation:

```
CIDR = Classless Inter-Domain Routing
  → Replaces the old Class A/B/C system
  → Written as IP/prefix_length  (e.g., 192.168.1.0/24)
  → More flexible — doesn't force class boundaries

EXAMPLE: 10.0.0.0/8
  → First 8 bits = network portion
  → Last 24 bits = host portion
  → This is equivalent to old Class A

EXAMPLE: 172.16.0.0/20
  → First 20 bits = network
  → This does NOT fit cleanly into Class A/B/C — this is CLASSLESS!

🎯 PYQ FACT: CIDR allows flexible network sizes (not restricted to Class A/B/C boundaries)
```

---

## 🔷 SECTION 3: VLSM — Variable Length Subnet Masking

### The Problem with Fixed Subnetting:

```
SCENARIO: A company needs three subnets:
  → Engineering dept: needs 100 hosts
  → HR dept: needs 20 hosts
  → WAN link between routers: needs only 2 hosts

FIXED SUBNETTING PROBLEM:
  If you use /26 (62 usable hosts) for ALL subnets:
  → Engineering: 62 hosts allocated → fits but wastes some
  → HR: 62 hosts allocated → only 20 used, 42 WASTED
  → WAN link: 62 hosts allocated → only 2 used, 60 WASTED!

THIS IS INEFFICIENT. VLSM solves this.
```

### VLSM Solution:

```
VLSM = Variable Length Subnet Masking
  → Allows DIFFERENT subnet sizes within the same network
  → Each subnet gets EXACTLY the size it needs
  → No more wasted IP addresses

VLSM SOLUTION FOR SAME SCENARIO (from 192.168.1.0/24):
  
  Engineering (100 hosts needed) → /25 → 126 usable  ← 192.168.1.0/25
  HR (20 hosts needed)           → /27 →  30 usable  ← 192.168.1.128/27
  WAN link (2 hosts needed)      → /30 →   2 usable  ← 192.168.1.160/30

  RESULT: Much less wasted space!

VLSM KEY RULE: To use VLSM, the routing protocol MUST support it.
  → Protocols that SUPPORT VLSM:  OSPF, EIGRP, BGP, RIPv2, IS-IS
  → Protocols that DON'T support: RIPv1 (uses classful routing only)

🎯 PYQ FACT: VLSM = Variable Length Subnet Masking = different sized subnets in same network
🎯 PYQ FACT: RIPv1 does NOT support VLSM; RIPv2 and OSPF DO support VLSM
🚨 TRAP: "VLSM uses the same mask for all subnets" → FALSE! VLSM = VARIABLE length masks.
```

---

## 🔷 SECTION 4: Multiplexing — Sharing a Single Channel

### What is Multiplexing?

```
REAL-LIFE ANALOGY — The Highway:
  A highway is an expensive resource. Rather than building a separate road
  for every single vehicle, ALL vehicles SHARE the same highway.
  
  Multiplexing does the same for data transmission:
  → Multiple signals SHARE one physical transmission channel
  → Saves cost (only need one cable/medium for many signals)
  → A MULTIPLEXER (MUX) combines multiple signals at the sender
  → A DEMULTIPLEXER (DEMUX) separates them at the receiver

MUX                     TRANSMISSION           DEMUX
─────────               CHANNEL                ─────────
Signal 1 ──┐                                   ┌── Signal 1
Signal 2 ──┼──► [MUX] ═══════════════► [DEMUX] ┼── Signal 2
Signal 3 ──┘                                   └── Signal 3
  (3 signals share one channel)
```

### THREE MAIN TYPES OF MULTIPLEXING:

---

### TYPE 1: FDM — Frequency Division Multiplexing

```
CONCEPT: Each signal is assigned a DIFFERENT FREQUENCY BAND.
         All signals transmit SIMULTANEOUSLY — at different frequencies.
         The total bandwidth is DIVIDED into frequency slots.

DIAGRAM:
  Bandwidth (Hz)
  ┌────────────────────────────────────────────────────────────┐
  │  Channel 1  │  Guard  │  Channel 2  │  Guard  │  Channel 3 │
  │  (freq f1)  │  Band   │  (freq f2)  │  Band   │  (freq f3) │
  └────────────────────────────────────────────────────────────┘
  f1 < f2 < f3 (each signal uses different frequency range)
  
  GUARD BANDS: Small unused frequency gaps between channels
               (prevent interference between adjacent channels)

HOW IT WORKS:
  → Sender modulates each signal onto a CARRIER FREQUENCY
  → All modulated signals combined and sent over the same medium
  → Receiver uses FILTERS to extract each signal at its frequency

USED FOR:
  → Cable TV (each channel on different frequency)
  → FM Radio (each station at different frequency)
  → Traditional telephone systems (landlines)
  → Older analog cellular networks (AMPS)
  → DSL (phone calls + internet on same wire at different frequencies)

MEDIUM: Works for BOTH wired and wireless transmission

KEY PROPERTIES:
  → All users transmit SIMULTANEOUSLY (no time-sharing)
  → Bandwidth is divided (each user gets a slice of bandwidth)
  → Guard bands required between channels (slight inefficiency)
  → Analog technique (originally designed for analog signals)

🎯 PYQ FACT: FDM = different frequencies; used in cable TV, FM radio
🎯 PYQ FACT: FDM uses GUARD BANDS between channels to prevent interference
```

---

### TYPE 2: TDM — Time Division Multiplexing

```
CONCEPT: All signals share the SAME FREQUENCY (full bandwidth).
         BUT each signal gets the channel for a SPECIFIC TIME SLOT.
         Users take TURNS — only one transmits at any instant.

DIAGRAM:
  Time ──────────────────────────────────────────────────────►
  ┌──────┬──────┬──────┬──────┬──────┬──────┬──────┬──────┐
  │ Ch 1 │ Ch 2 │ Ch 3 │ Ch 1 │ Ch 2 │ Ch 3 │ Ch 1 │ Ch 2 │  ← TIME SLOTS
  └──────┴──────┴──────┴──────┴──────┴──────┴──────┴──────┘
  │◄─────────── FRAME 1 ──────────────►│◄── FRAME 2 ──────►│

FRAME:
  → A FRAME = one complete cycle of time slots (one slot per channel)
  → TDM time slots are grouped into FRAMES ← 🎯 CONFIRMED PYQ FACT
  → Frame duration = sum of all time slots in one cycle

TWO TYPES OF TDM:

  SYNCHRONOUS TDM:
  → Fixed time slots assigned to each user
  → Slot assigned EVEN IF that user has no data to send
  → Results in WASTED capacity when a user is idle
  → Used in: T1/E1 telephone lines, SONET/SDH
  → Simple to implement; predictable timing

  STATISTICAL TDM (STDM / Asynchronous TDM):
  → Time slots assigned ONLY WHEN a user has data to send
  → No wastage — idle users don't occupy slots
  → More efficient but more complex
  → Each slot must carry the USER'S ADDRESS (to identify sender)
  → Can serve MORE users than Synchronous TDM on same channel

USED FOR:
  → Digital telephone networks (T1, E1 lines)
  → SONET / SDH (Synchronous Optical Networking)
  → ISDN (Integrated Services Digital Network)

KEY PROPERTIES:
  → Digital technique (designed for digital signals)
  → Users share full bandwidth, but in different time slots
  → Synchronous TDM: fixed slots (may waste capacity)
  → Statistical TDM: slots on demand (more efficient)

🎯 PYQ FACT: TDM time slots are organized/divided into FRAMES ← MOST TESTED
🎯 PYQ FACT: Synchronous TDM = fixed slots (may be wasted if idle)
🎯 PYQ FACT: Statistical TDM = dynamic slots (only allocated when data exists)
🚨 TRAP: "TDM assigns different frequencies to different users" → FALSE! That is FDM.
          TDM = same channel, DIFFERENT TIME SLOTS.
```

---

### TYPE 3: WDM — Wavelength Division Multiplexing

```
CONCEPT: Like FDM but specifically for OPTICAL FIBER.
         Each signal is carried on a DIFFERENT WAVELENGTH (colour) of light.
         Multiple light wavelengths travel simultaneously in ONE fiber.

DIAGRAM:
  ┌──────────────────────────────────────────────────────────┐
  │  λ1 (red) + λ2 (green) + λ3 (blue) + λ4 (infrared)      │ ← FIBER
  │  ──────────────────────────────────────────────────────  │
  │  All different wavelengths travel in the SAME fiber      │
  └──────────────────────────────────────────────────────────┘
  (λ = lambda = wavelength symbol)

VARIANT:
  DWDM (Dense Wavelength Division Multiplexing):
  → Very closely spaced wavelengths (100+ channels in one fiber)
  → Used in long-haul (long distance) backbone networks
  → Achieves TERABIT-level throughput

USED FOR:
  → Long-haul optical fiber backbone networks
  → Submarine (undersea) fiber optic cables
  → High-capacity metro networks

KEY PROPERTIES:
  → Designed EXCLUSIVELY for optical fiber (light-based medium)
  → Conceptually similar to FDM, but for light wavelengths
  → Extremely high capacity (modern WDM: 100+ Tbps)
  → Each wavelength = independent logical channel

🎯 PYQ FACT: WDM = used for OPTICAL FIBER (different wavelengths of light)
🎯 PYQ FACT: WDM is essentially FDM applied to optical fiber
🚨 TRAP: "WDM is used for copper cables" → FALSE! WDM is for OPTICAL FIBER only.
```

---

### Multiplexing Comparison Table:

```
┌────────────────┬────────────────────────┬────────────────────────┬────────────────────────┐
│    FEATURE     │         FDM            │         TDM            │         WDM            │
├────────────────┼────────────────────────┼────────────────────────┼────────────────────────┤
│ Full Form      │ Frequency Division     │ Time Division          │ Wavelength Division    │
│                │ Multiplexing           │ Multiplexing           │ Multiplexing           │
├────────────────┼────────────────────────┼────────────────────────┼────────────────────────┤
│ Division basis │ FREQUENCY (Hz)         │ TIME (time slots)      │ WAVELENGTH (light, λ)  │
├────────────────┼────────────────────────┼────────────────────────┼────────────────────────┤
│ All transmit?  │ Simultaneously         │ Take turns             │ Simultaneously         │
├────────────────┼────────────────────────┼────────────────────────┼────────────────────────┤
│ Signal type    │ Analog (originally)    │ Digital                │ Optical (light)        │
├────────────────┼────────────────────────┼────────────────────────┼────────────────────────┤
│ Medium         │ Wired or Wireless      │ Wired or Wireless      │ Optical Fiber ONLY     │
├────────────────┼────────────────────────┼────────────────────────┼────────────────────────┤
│ Usage examples │ Cable TV, FM radio,    │ T1/E1 lines, SONET,    │ Fiber backbone,        │
│                │ telephone, DSL         │ ISDN, digital phone    │ submarine cables       │
├────────────────┼────────────────────────┼────────────────────────┼────────────────────────┤
│ Guard bands?   │ YES (between channels) │ NO                     │ YES (channel spacing)  │
├────────────────┼────────────────────────┼────────────────────────┼────────────────────────┤
│ Key feature    │ Different frequencies  │ Slots grouped in FRAMES│ Different wavelengths  │
└────────────────┴────────────────────────┴────────────────────────┴────────────────────────┘
```

---

### Fourth Type: CDM (Code Division Multiplexing)

```
CDM / CDMA (Code Division Multiple Access):
  → All users share SAME frequency AND SAME time
  → Users are distinguished by UNIQUE CODES (spread spectrum)
  → Each signal is spread across the entire bandwidth using a unique code
  → Receiver uses the correct code to extract the desired signal
  
  ANALOGY: A party where everyone speaks at once, but in different languages.
           You understand only the language (code) you know.
  
  USED FOR: 3G mobile networks, GPS, military communications

🎯 PYQ FACT: CDMA = same frequency + same time but different UNIQUE CODES
```

---

## 🔷 SECTION 5: Memory-Mapped I/O vs I/O-Mapped I/O

### The Central Problem — How Does CPU Talk to Devices?

A computer has TWO types of resources:
1. **Memory** (RAM, ROM) — stores programs and data
2. **I/O Devices** (keyboard, printer, hard disk, network card) — external devices

The CPU needs to communicate with BOTH. The question is: **how does the CPU address and access each type?**

---

### TYPE 1: Memory-Mapped I/O

```
CONCEPT: I/O devices and memory SHARE THE SAME ADDRESS SPACE.
         I/O device registers are treated just like memory locations.
         The CPU uses the SAME instructions to access both memory AND I/O.

DIAGRAM:
  TOTAL ADDRESS SPACE (e.g., 0 to 0xFFFFFF):
  ┌─────────────────────────────────────────────────────┐
  │  0x000000 to 0x7FFFFF  → RAM (memory)              │
  │  0x800000 to 0x8000FF  → Keyboard controller       │ ← I/O mapped here
  │  0x800100 to 0x8001FF  → Display controller        │ ← I/O mapped here
  │  0x800200 to 0x8002FF  → Disk controller           │ ← I/O mapped here
  └─────────────────────────────────────────────────────┘
  Memory and I/O share the SAME address space.

HOW IT WORKS:
  → Each I/O device is assigned a memory address
  → CPU reads/writes to that address to communicate with the device
  → SAME LOAD/STORE instructions used for both memory and I/O
  → No separate I/O instructions needed

ADVANTAGES:
  → Simple programming — use standard MOV/LOAD/STORE instructions
  → Can use full range of CPU addressing modes for I/O
  → Less complex instruction set (no separate IN/OUT instructions)

DISADVANTAGES:
  → Reduces available memory address space (some addresses reserved for I/O)
  → Accidental writes to I/O addresses can damage hardware
  → Hardware must distinguish memory vs I/O accesses (no separate bus)

USED BY: ARM processors, most RISC architectures, Motorola 68000
         Modern microcontrollers (Arduino, Raspberry Pi use memory-mapped I/O)

🎯 PYQ FACT: Memory-mapped I/O = I/O and memory SHARE the same address space
🎯 PYQ FACT: Memory-mapped I/O = uses SAME instructions for memory AND I/O access
```

---

### TYPE 2: I/O-Mapped I/O (Port-Mapped I/O / Isolated I/O)

```
CONCEPT: I/O devices have a SEPARATE ADDRESS SPACE from memory.
         The CPU has TWO DISTINCT address spaces:
         1. Memory address space (for RAM/ROM)
         2. I/O port address space (for devices)
         
         DIFFERENT INSTRUCTIONS are used for each.

DIAGRAM:
  TWO SEPARATE ADDRESS SPACES:
  
  MEMORY SPACE:           I/O PORT SPACE:
  ┌──────────────┐        ┌───────────────────┐
  │ 0x00000 RAM  │        │ Port 0x60 Keyboard │
  │ 0x10000 ROM  │        │ Port 0x3F8 COM1    │
  │ 0x20000 ...  │        │ Port 0x378 Printer │
  └──────────────┘        └───────────────────┘
  ↑ accessed with         ↑ accessed with
  MOV, LOAD, STORE        IN and OUT instructions

SPECIAL INSTRUCTIONS:
  IN  port → reads data FROM an I/O port into CPU register
  OUT port → writes data FROM CPU register TO an I/O port

ADVANTAGES:
  → Full memory address space available (I/O doesn't steal memory addresses)
  → Clear separation — accidental writes to I/O ports don't corrupt memory
  → Hardware is simpler — separate I/O bus

DISADVANTAGES:
  → Requires special IN/OUT instructions (more complex instruction set)
  → Cannot use all addressing modes for I/O (limited instruction set)
  → Programmer must know which addresses are memory vs I/O ports

USED BY: Intel x86 architecture (the classic PC architecture!)
         8085, 8086 processors use port-mapped I/O

🎯 PYQ FACT: I/O-mapped I/O = SEPARATE address spaces for memory and I/O
🎯 PYQ FACT: I/O-mapped I/O uses special IN/OUT instructions
🎯 PYQ FACT: Intel x86 architecture uses I/O-mapped (port-mapped) I/O
```

---

### Side-by-Side Comparison:

```
┌──────────────────────────┬─────────────────────────────────┬─────────────────────────────────┐
│         FEATURE          │      MEMORY-MAPPED I/O          │      I/O-MAPPED I/O             │
│                          │    (also: unified I/O)          │  (also: port-mapped, isolated)  │
├──────────────────────────┼─────────────────────────────────┼─────────────────────────────────┤
│ Address Space            │ SHARED — I/O and memory use     │ SEPARATE — distinct address      │
│                          │ same address space              │ spaces for memory and I/O        │
├──────────────────────────┼─────────────────────────────────┼─────────────────────────────────┤
│ Instructions used        │ SAME as memory (MOV, LOAD,      │ DIFFERENT — special IN and OUT   │
│                          │ STORE instructions)             │ instructions for I/O             │
├──────────────────────────┼─────────────────────────────────┼─────────────────────────────────┤
│ Memory available to RAM  │ REDUCED (some addresses         │ FULL — no memory addresses       │
│                          │ reserved for I/O)               │ used by I/O                      │
├──────────────────────────┼─────────────────────────────────┼─────────────────────────────────┤
│ Programming complexity   │ Simpler (one instruction set)   │ More complex (two instruction    │
│                          │                                 │ sets — IN/OUT + memory)          │
├──────────────────────────┼─────────────────────────────────┼─────────────────────────────────┤
│ Architecture examples    │ ARM, Motorola 68000,            │ Intel x86, 8085, 8086           │
│                          │ most RISC processors            │ (IBM PC architecture)            │
├──────────────────────────┼─────────────────────────────────┼─────────────────────────────────┤
│ Hardware complexity      │ Higher (must distinguish I/O    │ Lower (separate buses/signals)   │
│                          │ vs memory on same bus)          │                                  │
└──────────────────────────┴─────────────────────────────────┴─────────────────────────────────┘

MEMORY AID:
  Memory-MAPPED = I/O is MAPPED INTO memory space = SHARED
  I/O-MAPPED    = I/O is MAPPED to its OWN space  = SEPARATE
```

---

## 🔷 SECTION 6: Additional Network Concepts (PYQ Confirmed)

### Program-Controlled I/O (Polling):

```
POLLING (Program-Controlled I/O):
  → CPU REPEATEDLY CHECKS the I/O device's STATUS REGISTER
  → "Are you done yet? Are you done yet? Are you done yet?"
  → CPU is busy-waiting — wastes CPU cycles checking status flags
  → Simple but inefficient (CPU can't do other work while polling)
  → Alternative to polling: INTERRUPTS (device signals CPU when ready)

🎯 PYQ FACT: Program-controlled I/O = repeatedly checking STATUS FLAGS = POLLING
🚨 TRAP: "Polling is efficient" → FALSE! Polling wastes CPU cycles.
```

### Socket:

```
SOCKET:
  → Software endpoint for INTER-PROCESS COMMUNICATION over a network
  → Combination of IP address + PORT number
  → Like a telephone: IP = phone number, Port = extension number
  → Example: 192.168.1.5:80 = web server socket (IP:port)

🎯 PYQ FACT: Socket = endpoint of inter-process communication
🎯 PYQ FACT: Socket = IP address + Port number combined
```

### Network Recap — PYQ-Confirmed Quick Facts:

```
PING:
  → Tests connectivity between two hosts
  → Summarizes: packet loss + round-trip delay (RTT)
  → Uses ICMP (Internet Control Message Protocol) — NOT TCP/UDP
  → "Packet Internet Groper" is a WRONG full form (just called "ping")

TCP THREE-WAY HANDSHAKE:
  SYN → SYN-ACK → ACK
  (Client sends SYN; Server replies SYN-ACK; Client confirms ACK)
  After this, connection is ESTABLISHED.

SNIFFER PREVENTION:
  → Network sniffers (packet capture tools) are prevented by:
    SWITCHED NETWORKS (switches send packets only to intended recipient)
  → Hubs BROADCAST to all → easy to sniff
  → Switches UNICAST to specific port → harder to sniff

ASYMMETRIC KEY CRYPTOGRAPHY:
  → Uses KEY PAIR: Public Key + Private Key
  → PUBLIC KEY: shared openly (anyone can encrypt with it)
  → PRIVATE KEY: kept SECRET by the RECEIVER (used to decrypt)
  → Example: SSL/TLS, HTTPS, Digital Signatures

🎯 PYQ FACT: In asymmetric cryptography, PRIVATE KEY is kept by RECEIVER
🚨 TRAP: "Private key is kept by sender" → FALSE! Receiver keeps the private key.
```

---

## 🔷 SECTION 7: PYQ Trap List — Networks Day 59

```
🚨 TRAP 1: "Subnet mask identifies the HOST portion of IP" → FALSE!
   Subnet mask identifies the NETWORK PORTION (the 1-bits = network; 0-bits = host).

🚨 TRAP 2: "TDM assigns different frequencies to users" → FALSE!
   TDM = same frequency, different TIME SLOTS. FDM uses different frequencies.

🚨 TRAP 3: "TDM time slots are called channels" → FALSE!
   TDM time slots are grouped into FRAMES (confirmed PYQ answer).

🚨 TRAP 4: "WDM can be used with copper cables" → FALSE!
   WDM is designed EXCLUSIVELY for optical fiber (uses wavelengths of light).

🚨 TRAP 5: "Memory-mapped I/O uses separate address spaces" → FALSE!
   Memory-mapped I/O = SHARED address space for I/O and memory.
   I/O-mapped I/O = SEPARATE address spaces.

🚨 TRAP 6: "Intel x86 uses memory-mapped I/O" → FALSE!
   Intel x86 = I/O-mapped (port-mapped) I/O.
   ARM, RISC = memory-mapped I/O.

🚨 TRAP 7: "VLSM uses the same subnet mask for all subnets" → FALSE!
   VLSM = VARIABLE length — different subnets get different mask lengths.

🚨 TRAP 8: "RIPv1 supports VLSM" → FALSE!
   RIPv1 does NOT support VLSM (classful routing only).
   RIPv2, OSPF, EIGRP, BGP DO support VLSM.

🚨 TRAP 9: "A /30 subnet gives 4 usable hosts" → FALSE!
   /30 = 4 total addresses - 2 (network + broadcast) = 2 usable hosts.

🚨 TRAP 10: "Polling is efficient because it doesn't need interrupts" → FALSE!
   Polling WASTES CPU cycles. Interrupts are more efficient.

🚨 TRAP 11: "In asymmetric cryptography, the sender keeps the private key" → FALSE!
   RECEIVER keeps the PRIVATE KEY.

🚨 TRAP 12: "FDM does not use guard bands" → FALSE!
   FDM uses GUARD BANDS between frequency channels to prevent interference.
```

---

# PART 2: GENERAL STUDIES
## 🏛️ Indian History — Salt Satyagraha, Civil Disobedience Movement & Related Events

---

## 🔷 SECTION 1: Background — The Road to Civil Disobedience

### Congress Lahore Session 1929 — Purna Swaraj Declaration:

```
LAHORE SESSION (December 1929):
  President: JAWAHARLAL NEHRU (his first Congress presidency)
  
  KEY DECISIONS:
  1. PURNA SWARAJ (Complete Independence) declared as the goal
     → Shifted from "Swaraj" (self-rule) to COMPLETE independence from British
     → This was a radicalization of the freedom struggle
  
  2. Tricolour flag hoisted on December 31, 1929 / January 1, 1930
     (at midnight, Nehru hoisted the flag on the banks of the Ravi river)
  
  3. January 26, 1930 declared as FIRST INDEPENDENCE DAY
     (later became Republic Day — January 26, 1950)
     Every year, January 26 was to be celebrated as Independence Day
     UNTIL actual independence was achieved.

🎯 KEY FACTS:
  ✅ Lahore Session 1929 = Purna Swaraj resolution
  ✅ President = Jawaharlal Nehru
  ✅ January 26, 1930 = first celebrated as Independence Day
  ✅ Why Republic Day = Jan 26? To honour this date
```

---

## 🔷 SECTION 2: The Dandi March / Salt Satyagraha (1930)

### Why Salt?

```
CONTEXT — THE SALT LAW:
  → British government had a MONOPOLY on salt production and sale
  → Indians could NOT make their own salt — even from the sea!
  → Heavy taxes on salt — affecting EVERY Indian (rich, poor, farmer, trader)
  → Salt was ESSENTIAL — no Indian could boycott it (unlike foreign cloth)
  → By targeting salt, Gandhi chose an issue that united ALL Indians
  
  GANDHI'S GENIUS: Salt was the PERFECT symbol:
  → Universally needed (everyone needs salt)
  → Made by nature (sea, salt flats) — who can own the sea?
  → Breaking the salt law = direct, peaceful, symbolic defiance
  → Easy for common people to understand and participate
```

### The Dandi March — Timeline:

```
DANDI MARCH (March 12 to April 6, 1930):

  START: March 12, 1930
  → Gandhi + 78 carefully selected volunteers (called the "78 satyagrahis")
  → Started from SABARMATI ASHRAM, Ahmedabad, Gujarat
  
  ROUTE: 385 km (240 miles) march through Gujarat villages
  → Duration: 24 days of marching
  
  END: April 6, 1930
  → Reached DANDI, a coastal village in Gujarat
  → Gandhi picked up a handful of SALT from the seashore
  → Broke the British Salt Law — first act of Civil Disobedience
  
  WHAT HAPPENED NEXT:
  → Thousands across India began making salt
  → Salt was made on beaches, in fields — mass violation of British law
  → British arrested thousands including Congress leaders
  → Movement spread across India spontaneously
  
  RAID ON DHARASANA SALT WORKS (May 1930):
  → Gandhi arrested before the raid
  → Sarojini Naidu led the raid on Dharasana Salt Works (Gujarat)
  → Unarmed marchers beaten by police with metal-tipped lathis
  → American journalist Webb Miller reported brutality to the world
  → International outrage against British rule

🎯 KEY FACTS (EXAM ESSENTIALS):
  ✅ Dandi March: March 12 – April 6, 1930
  ✅ Started from: Sabarmati Ashram, Ahmedabad
  ✅ Number of satyagrahis: 78
  ✅ Reached: Dandi village (coastal Gujarat)
  ✅ Distance: 385 km, 24 days
  ✅ Gandhi broke salt law on: April 6, 1930
  ✅ Dharasana Salt Works raid: Sarojini Naidu led (Gandhi was arrested)
```

---

## 🔷 SECTION 3: Civil Disobedience Movement (CDM)

### Launching the Movement:

```
CIVIL DISOBEDIENCE MOVEMENT (CDM):
  Formally launched: April 6, 1930 (when Gandhi broke salt law at Dandi)
  
  WHAT "CIVIL DISOBEDIENCE" MEANS:
  → Peacefully REFUSING to obey unjust laws
  → Non-violent but direct confrontation with the colonial system
  → Breaking specific laws as a political protest
  
  FORMS OF CIVIL DISOBEDIENCE:
  1. Making salt in violation of Salt Laws
  2. BOYCOTT of British goods (cloth, sugar, cigarettes)
  3. Refusal to pay taxes (especially forest laws in Bardoli, rent laws)
  4. Picketing of liquor shops and foreign cloth stores
  5. Violation of forest laws (cutting timber in reserved forests)
  6. Hartals (strikes) and non-cooperation with British administration
  
  WOMEN IN CDM:
  → Women participated in LARGE NUMBERS for the first time
  → Picketed liquor shops, participated in salt satyagraha
  → CDM marked a turning point in women's political participation
  → Sarojini Naidu, Aruna Asaf Ali, Kamala Nehru prominent leaders
```

### Gandhi-Irwin Pact (March 5, 1931):

```
GANDHI-IRWIN PACT (March 5, 1931):
  Parties: Mahatma Gandhi + Lord Irwin (Viceroy of India)
  
  WHY NEEDED:
  → Thousands arrested including Gandhi (arrested May 5, 1930)
  → British wanted CDM stopped; Congress wanted concessions
  → Negotiations led to pact
  
  KEY TERMS OF THE PACT:
  1. Congress would SUSPEND Civil Disobedience Movement
  2. British would RELEASE all political prisoners (non-violent)
  3. Indians living on the coast could make salt for personal use (not commercial)
  4. Congress would participate in SECOND ROUND TABLE CONFERENCE
  5. Confiscated property of satyagrahis to be returned
  
  SIGNIFICANCE:
  → British RECOGNIZED Congress as representative of Indian people
  → First time British negotiated with Gandhi as an EQUAL
  → Critics (like Bhagat Singh supporters) felt pact was a betrayal
    (Bhagat Singh was hanged March 23, 1931 — Gandhi couldn't save him)
  
🎯 KEY FACTS:
  ✅ Gandhi-Irwin Pact = March 5, 1931
  ✅ CDM suspended in exchange for concessions
  ✅ Congress agreed to attend Second Round Table Conference
  ✅ Political prisoners released
  ✅ Bhagat Singh hanged March 23, 1931 (NOT saved by this pact)
```

---

## 🔷 SECTION 4: Round Table Conferences

```
THREE ROUND TABLE CONFERENCES (1930–1932):

FIRST ROUND TABLE CONFERENCE (November 1930 – January 1931):
  Location: London
  Indian participation: YES (princes, Muslim League, Hindu Mahasabha)
  Congress participation: NO (boycotted — CDM ongoing, leaders in jail)
  Result: INCONCLUSIVE (Congress absence made it incomplete)
  
  🎯 KEY FACT: Congress BOYCOTTED First RTC

SECOND ROUND TABLE CONFERENCE (September – December 1931):
  Location: London
  Indian participation: Gandhi attended (representing Congress)
  Result: FAILED — communal issue (Hindu-Muslim representation) unresolved
  Gandhi returned to India in December 1931
  
  KEY MOMENT: B.R. Ambedkar demanded separate electorate for
              Untouchables — Gandhi strongly opposed this
  
  🎯 KEY FACT: Gandhi attended SECOND RTC (only conference he attended)

THIRD ROUND TABLE CONFERENCE (November – December 1932):
  Location: London
  Congress participation: NO (CDM resumed, boycott again)
  Result: Led to Government of India Act 1935
  
  🎯 KEY FACT: Congress boycotted Third RTC
  🎯 KEY FACT: Outcome → Government of India Act, 1935

POONA PACT (September 25, 1932):
  Background: Ramsay MacDonald's Communal Award (August 1932)
  → Awarded SEPARATE ELECTORATES to Depressed Classes (Untouchables)
  Gandhi's reaction: Went on a FAST UNTO DEATH in Yerawada Jail
  Result: B.R. Ambedkar and Gandhi reached agreement
  
  POONA PACT PROVISIONS:
  → Separate electorate DROPPED for Depressed Classes
  → Instead: RESERVED SEATS within JOINT ELECTORATE
  → 148 reserved seats in provincial legislatures (increased from 71)
  
  🎯 KEY FACT: Poona Pact = September 25, 1932 (Ambedkar + Gandhi)
  🎯 KEY FACT: Replaced communal award's separate electorate with reserved seats
```

---

## 🔷 SECTION 5: Suspension and Resumption of CDM

```
CDM TIMELINE:

PHASE 1 (April 1930 – March 1931):
  → Started with Dandi March (April 6, 1930)
  → Mass civil disobedience, arrests
  → Gandhi arrested May 5, 1930
  → SUSPENDED by Gandhi-Irwin Pact (March 5, 1931)

PHASE 2 (January 1932 – April 1934):
  → Gandhi returned from Second RTC (December 1931) — nothing achieved
  → RESUMED CDM (January 1932)
  → Gandhi again arrested January 4, 1932
  → Communal Award + Poona Pact controversy (1932)
  → CDM gradually WITHDREW — formally ended April 1934
  → Gandhi stated CDM was "the greatest experiment in world history"
  
  WHY WITHDRAWN (1934)?
  → Increasing violence in some areas (contradicted non-violent principles)
  → Organizational exhaustion
  → Focus shifted to constructive programme (village upliftment)
  → Congress electoral participation through Council Entry policy

🎯 KEY FACT: CDM formally ended 1934 (not 1931 with Gandhi-Irwin Pact — that was suspension)
```

---

## 🔷 SECTION 6: Bihar's Role in CDM and Salt Satyagraha

```
BIHAR IN THE CIVIL DISOBEDIENCE MOVEMENT:

KEY LEADERS FROM BIHAR:
  → DR. RAJENDRA PRASAD: Led CDM activities in Bihar;
    later first President of India
  → JAYAPRAKASH NARAYAN (JP): Active in CDM; later Gandhi's
    "true heir" for JP movement (1974)
  → SHRI KRISHNA SINHA: Bihar's first Chief Minister;
    active in CDM
  
PATNA SALT SATYAGRAHA:
  → Bihar had its own salt satyagraha at sites like Sitamarhi
  → Congress volunteers made salt in violation of salt laws
  → Thousands arrested across Bihar
  
CHAMPARAN AND CDM CONNECTION:
  → After successful Champaran Satyagraha (1917) established
    Gandhi's method in Bihar, the CDM built on that foundation
  → Bihar peasants already had experience with Gandhian methods

SPECIAL EVENTS IN BIHAR:
  → Bihar Student Federation actively participated
  → Women of Bihar participated in picketing and salt making
  → Bhagalpur, Gaya, Patna were major centres of CDM activities

🎯 KEY FACT: Rajendra Prasad was Bihar's principal CDM leader
🎯 KEY FACT: Bihar CDM built on foundation of Champaran (1917)
```

---

## 🔷 SECTION 7: Key Figures and Their Roles

```
┌───────────────────────────────┬─────────────────────────────────────────────────┐
│   PERSON                      │   ROLE / SIGNIFICANCE                           │
├───────────────────────────────┼─────────────────────────────────────────────────┤
│ Mahatma Gandhi                │ Led Dandi March; launched CDM; negotiated       │
│                               │ Gandhi-Irwin Pact; attended 2nd RTC             │
├───────────────────────────────┼─────────────────────────────────────────────────┤
│ Jawaharlal Nehru              │ Congress President 1929; Purna Swaraj           │
│                               │ resolution; hoisted tricolour                   │
├───────────────────────────────┼─────────────────────────────────────────────────┤
│ Lord Irwin                    │ Viceroy who negotiated Gandhi-Irwin Pact        │
│                               │ (March 1931)                                    │
├───────────────────────────────┼─────────────────────────────────────────────────┤
│ Sarojini Naidu                │ Led Dharasana Salt Works raid (May 1930)        │
│                               │ after Gandhi's arrest; "Nightingale of India"   │
├───────────────────────────────┼─────────────────────────────────────────────────┤
│ B.R. Ambedkar                 │ Opposed Gandhi's position at 2nd RTC;          │
│                               │ demanded separate electorate; Poona Pact        │
├───────────────────────────────┼─────────────────────────────────────────────────┤
│ Lord Chelmsford               │ Viceroy during Jallianwala Bagh (1919)         │
├───────────────────────────────┼─────────────────────────────────────────────────┤
│ Ramsay MacDonald              │ British PM who announced Communal Award (1932) │
│                               │ triggered Poona Pact crisis                     │
├───────────────────────────────┼─────────────────────────────────────────────────┤
│ Bhagat Singh                  │ Hanged March 23, 1931 (18 days after           │
│                               │ Gandhi-Irwin Pact — not saved by pact)         │
├───────────────────────────────┼─────────────────────────────────────────────────┤
│ Dr. Rajendra Prasad           │ Bihar's CDM leader; later 1st President India  │
├───────────────────────────────┼─────────────────────────────────────────────────┤
│ Vallabhbhai Patel             │ Led Bardoli Satyagraha (1928) — precursor      │
│                               │ to CDM; called "Sardar" after Bardoli          │
└───────────────────────────────┴─────────────────────────────────────────────────┘
```

---

## 🔷 SECTION 8: Government of India Act 1935

```
GOVERNMENT OF INDIA ACT 1935 (outcome of Round Table Conferences):

KEY PROVISIONS:
  1. PROVINCIAL AUTONOMY:
     → Provinces got full autonomy in provincial subjects
     → Governor's role reduced to constitutional head
     → Elected Indian ministers (from Congress) could form governments
  
  2. ALL-INDIA FEDERATION (proposed):
     → Federation of British India + Princely States (NOT implemented — states refused)
  
  3. BICAMERAL LEGISLATURES in 6 provinces
  
  4. SEPARATE ELECTORATE for Muslims, Sikhs, Anglo-Indians
  
  5. FEDERAL COURT established (precursor to Supreme Court)
  
  6. RBI (Reserve Bank of India) established under this Act
  
  7. Sindh separated from Bombay Province
  
CONGRESS AND ACT 1935:
  → Congress CRITICISED the Act (called it "thoroughly rotten, fundamentally bad")
  → But Congress PARTICIPATED in 1937 elections under this Act
  → Congress won in 7 out of 11 provinces in 1937 elections

🎯 KEY FACTS:
  ✅ Government of India Act 1935 = Provincial Autonomy
  ✅ RBI established by this Act
  ✅ Federal Court (precursor to Supreme Court) established
  ✅ Congress won 7/11 provinces in 1937 elections under this Act
  ✅ Sindh separated from Bombay under this Act
```

---

## 🔷 SECTION 9: PYQ Traps — Salt Satyagraha / CDM

```
🚨 TRAP 1: "Dandi March started from Wardha Ashram" → FALSE!
   Dandi March started from SABARMATI ASHRAM, Ahmedabad.
   Wardha (Sevagram Ashram) was Gandhi's later residence (from 1936).

🚨 TRAP 2: "Gandhi attended the First Round Table Conference" → FALSE!
   Gandhi attended ONLY the SECOND RTC (1931).
   Congress BOYCOTTED the First and Third RTC.

🚨 TRAP 3: "CDM ended with Gandhi-Irwin Pact in 1931" → FALSE!
   Gandhi-Irwin Pact only SUSPENDED CDM (Phase 1 ended).
   CDM RESUMED in 1932 and was FORMALLY WITHDRAWN in 1934.

🚨 TRAP 4: "Sarojini Naidu led the Dandi March" → FALSE!
   Gandhi led the Dandi March with 78 satyagrahis.
   Sarojini Naidu led the Dharasana Salt Works raid (AFTER Gandhi's arrest).

🚨 TRAP 5: "Poona Pact maintained separate electorates for Depressed Classes" → FALSE!
   Poona Pact REPLACED separate electorates with RESERVED SEATS in JOINT electorate.

🚨 TRAP 6: "Purna Swaraj was declared in the Calcutta Session 1928" → FALSE!
   Purna Swaraj declared at LAHORE SESSION 1929 (president: Nehru).
   Calcutta 1928 had a different resolution (Nehru Report deadline).

🚨 TRAP 7: "Bardoli Satyagraha was led by Gandhi directly" → FALSE!
   Bardoli Satyagraha (1928) was led by SARDAR VALLABHBHAI PATEL.

🚨 TRAP 8: "Bhagat Singh was saved by Gandhi-Irwin Pact" → FALSE!
   Bhagat Singh was hanged on March 23, 1931 — 18 days AFTER the Pact.
   The pact did not cover capital punishment cases.

🚨 TRAP 9: "Dandi March covered 285 km in 12 days" → FALSE!
   Dandi March = 385 km over 24 days (March 12 to April 6, 1930).

🚨 TRAP 10: "RBI was established by Government of India Act 1947" → FALSE!
   RBI established by Government of India Act 1935 (not 1947).
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Subnetting, VLSM, TDM, FDM, WDM, Memory-Mapped I/O, I/O-Mapped I/O

---

**Q1.** A subnet mask in IP networking is used to identify:
(A) The speed of the network connection
(B) The host's unique hardware (MAC) address
(C) The network portion of an IP address
(D) More than one of the above
(E) None of the above

---

**Q2.** A Class C network 192.168.5.0 is subnetted using a /26 mask. How many subnets are created and how many USABLE hosts does each subnet have?
(A) 2 subnets, 126 usable hosts each
(B) 4 subnets, 62 usable hosts each
(C) 8 subnets, 30 usable hosts each
(D) More than one of the above
(E) None of the above

---

**Q3.** Using CIDR notation, the subnet 192.168.10.0/30 provides how many USABLE host addresses?
(A) 4 usable hosts
(B) 6 usable hosts
(C) 2 usable hosts
(D) More than one of the above
(E) None of the above

---

**Q4.** VLSM (Variable Length Subnet Masking) allows:
(A) All subnets in a network to use the same subnet mask for uniformity
(B) Different subnets within the same network to use different mask lengths
(C) Only Class A networks to be subnetted
(D) More than one of the above
(E) None of the above

---

**Q5.** Which routing protocol does NOT support VLSM?
(A) OSPF
(B) RIPv2
(C) RIPv1
(D) More than one of the above
(E) None of the above

---

**Q6.** In a subnet, the FIRST address is the _______ address and the LAST address is the _______ address:
(A) Broadcast address … Network address
(B) Network (subnet) address … Broadcast address
(C) Gateway address … Host address
(D) More than one of the above
(E) None of the above

---

**Q7.** In TDM (Time Division Multiplexing), the time slots are organized/grouped into:
(A) Channels
(B) Frames
(C) Packets
(D) More than one of the above
(E) None of the above

---

**Q8.** Which multiplexing technique assigns a different FREQUENCY BAND to each signal, allowing all signals to transmit simultaneously?
(A) TDM (Time Division Multiplexing)
(B) WDM (Wavelength Division Multiplexing)
(C) FDM (Frequency Division Multiplexing)
(D) More than one of the above
(E) None of the above

---

**Q9.** WDM (Wavelength Division Multiplexing) is designed specifically for use with:
(A) Coaxial cables
(B) Twisted pair copper cables
(C) Optical fiber cables
(D) More than one of the above
(E) None of the above

---

**Q10.** The GUARD BANDS used in FDM serve the purpose of:
(A) Protecting the signal from electromagnetic interference
(B) Preventing interference between adjacent frequency channels
(C) Providing redundancy in case one channel fails
(D) More than one of the above
(E) None of the above

---

**Q11.** In Synchronous TDM, what happens to the time slot of a user who has NO DATA to send at that moment?
(A) The slot is given to another user who needs it
(B) The slot remains empty/idle — it cannot be reassigned
(C) The entire TDM frame is paused until that user has data
(D) More than one of the above
(E) None of the above

---

**Q12.** Which type of TDM allocates time slots ONLY when a user has data to transmit, making it more bandwidth-efficient than regular TDM?
(A) Synchronous TDM
(B) Frequency Division TDM
(C) Statistical TDM (Asynchronous TDM)
(D) More than one of the above
(E) None of the above

---

**Q13.** In Memory-Mapped I/O, which of the following is TRUE?
(A) I/O devices and memory have completely separate address spaces
(B) Special IN and OUT instructions are required to access I/O devices
(C) I/O devices are mapped into the same address space as memory; accessed with same instructions
(D) More than one of the above
(E) None of the above

---

**Q14.** In I/O-Mapped I/O (Port-Mapped I/O), which of the following is TRUE?
(A) I/O and memory share the same address space; same instructions used
(B) I/O has a separate address space; accessed via special IN and OUT instructions
(C) I/O addresses are part of the memory address range
(D) More than one of the above
(E) None of the above

---

**Q15.** Which processor architecture traditionally uses I/O-Mapped (Port-Mapped) I/O with separate IN/OUT instructions?
(A) ARM (used in mobile phones and embedded systems)
(B) Motorola 68000
(C) Intel x86 (IBM PC architecture)
(D) More than one of the above
(E) None of the above

---

**Q16.** Program-Controlled I/O (also known as Polling) involves:
(A) I/O devices interrupting the CPU when they are ready
(B) The CPU repeatedly checking the status register of an I/O device
(C) DMA (Direct Memory Access) transfers without CPU involvement
(D) More than one of the above
(E) None of the above

---

**Q17.** A SOCKET in computer networking is defined as:
(A) The physical connector on a network interface card
(B) The endpoint of inter-process communication; identified by IP address + port number
(C) A hardware device that connects two network segments
(D) More than one of the above
(E) None of the above

---

**Q18.** The loopback IP address 127.0.0.1 is used for:
(A) Broadcasting to all devices on the local network
(B) Testing the network stack on the SAME machine (localhost)
(C) Identifying the default gateway router
(D) More than one of the above
(E) None of the above

---

**Q19.** In asymmetric (public key) cryptography, the PRIVATE KEY is:
(A) Shared publicly so that anyone can encrypt messages
(B) Kept secret by the SENDER for signing outgoing messages
(C) Kept secret by the RECEIVER and used to decrypt incoming messages
(D) More than one of the above
(E) None of the above

---

**Q20.** Network packet sniffers can be prevented most effectively by using:
(A) Hub-based networks (which broadcast to all ports)
(B) Switched networks (which forward packets only to the intended recipient)
(C) Wireless-only networks (Wi-Fi cannot be sniffed)
(D) More than one of the above
(E) None of the above

---

**Q21.** How many host addresses are in the range represented by the IP block 192.168.1.64/26?
(A) 30 usable hosts (32 total - 2)
(B) 62 usable hosts (64 total - 2)
(C) 126 usable hosts (128 total - 2)
(D) More than one of the above
(E) None of the above

---

**Q22.** What is the main ADVANTAGE of Statistical TDM over Synchronous TDM?
(A) Statistical TDM is simpler to implement
(B) Statistical TDM is more bandwidth efficient — slots only allocated when data exists
(C) Statistical TDM uses guard bands between time slots
(D) More than one of the above
(E) None of the above

---

**Q23.** The PING command uses which protocol to test network connectivity?
(A) TCP (Transmission Control Protocol)
(B) UDP (User Datagram Protocol)
(C) ICMP (Internet Control Message Protocol)
(D) More than one of the above
(E) None of the above

---

**Q24.** A network engineer needs to provide IP connectivity for 3 router-to-router WAN links. Each link needs exactly 2 host addresses. Which subnet size is MOST efficient?
(A) /28 (14 usable hosts — wasteful)
(B) /29 (6 usable hosts — wasteful)
(C) /30 (2 usable hosts — exactly right)
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following correctly distinguishes FDM from TDM?
(A) FDM = users take turns in time; TDM = users share different frequencies simultaneously
(B) FDM = different frequencies simultaneously; TDM = same frequency, different time slots
(C) FDM is used only for optical fiber; TDM is used only for copper cables
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: Salt Satyagraha, Dandi March, CDM, Round Table Conferences, Poona Pact

---

**Q26.** The PURNA SWARAJ (complete independence) resolution was passed by the Indian National Congress at which session?
(A) Calcutta Session 1928
(B) Lahore Session 1929
(C) Karachi Session 1931
(D) More than one of the above
(E) None of the above

---

**Q27.** Who presided over the Indian National Congress Lahore Session 1929 where Purna Swaraj was declared?
(A) Mahatma Gandhi
(B) Lala Lajpat Rai
(C) Jawaharlal Nehru
(D) More than one of the above
(E) None of the above

---

**Q28.** The Dandi March began on March 12, 1930 from:
(A) Wardha Ashram, Maharashtra
(B) Sabarmati Ashram, Ahmedabad (Gujarat)
(C) Sevagram Ashram, Wardha
(D) More than one of the above
(E) None of the above

---

**Q29.** The Dandi March covered approximately what distance, and how long did it take?
(A) 285 km over 12 days
(B) 485 km over 30 days
(C) 385 km over 24 days
(D) More than one of the above
(E) None of the above

---

**Q30.** How many satyagrahis accompanied Mahatma Gandhi on the original Dandi March?
(A) 100 volunteers
(B) 78 volunteers
(C) 50 volunteers
(D) More than one of the above
(E) None of the above

---

**Q31.** After Gandhi was arrested before the Dharasana Salt Works raid (May 1930), who led the march of satyagrahis to the salt pans?
(A) Jawaharlal Nehru
(B) Sardar Vallabhbhai Patel
(C) Sarojini Naidu
(D) More than one of the above
(E) None of the above

---

**Q32.** The Gandhi-Irwin Pact was signed in:
(A) January 1930
(B) March 1931
(C) September 1932
(D) More than one of the above
(E) None of the above

---

**Q33.** As per the Gandhi-Irwin Pact, which of the following was agreed upon?
(A) British would grant complete independence (Purna Swaraj)
(B) Congress suspended CDM; political prisoners released; Indians allowed to make salt on coast for personal use
(C) British agreed to hold elections immediately under universal suffrage
(D) More than one of the above
(E) None of the above

---

**Q34.** Mahatma Gandhi represented the Indian National Congress at which Round Table Conference in London?
(A) First Round Table Conference (1930)
(B) Second Round Table Conference (1931)
(C) Third Round Table Conference (1932)
(D) More than one of the above
(E) None of the above

---

**Q35.** The Congress party's stance on the First Round Table Conference (1930) was:
(A) It actively participated and sent a large delegation
(B) It boycotted the conference because CDM was ongoing and leaders were in jail
(C) It sent Gandhi as the sole representative
(D) More than one of the above
(E) None of the above

---

**Q36.** The Communal Award (August 1932) given by British PM Ramsay MacDonald provided for:
(A) Reduction of land revenue for peasants
(B) Separate electorates for Depressed Classes (Untouchables/Scheduled Castes)
(C) Granting dominion status to India
(D) More than one of the above
(E) None of the above

---

**Q37.** Gandhi's fast unto death against the Communal Award was undertaken from:
(A) Sabarmati Ashram, Ahmedabad
(B) Yerawada (Yerwada) Jail, Pune
(C) Delhi's Birla House
(D) More than one of the above
(E) None of the above

---

**Q38.** The Poona Pact (September 1932) was an agreement between:
(A) Gandhi and Lord Irwin (Viceroy)
(B) Mahatma Gandhi and Dr. B.R. Ambedkar
(C) INC and the Muslim League
(D) More than one of the above
(E) None of the above

---

**Q39.** Under the Poona Pact, the Communal Award's SEPARATE ELECTORATE for Depressed Classes was replaced with:
(A) A separate legislature for Depressed Classes
(B) Reserved seats within a joint (common) electorate
(C) Proportional representation in all provinces
(D) More than one of the above
(E) None of the above

---

**Q40.** The Civil Disobedience Movement was FORMALLY WITHDRAWN by Gandhi in:
(A) 1931 (after Gandhi-Irwin Pact)
(B) 1932 (after Poona Pact)
(C) 1934
(D) More than one of the above
(E) None of the above

---

**Q41.** Bhagat Singh was hanged on March 23, 1931 — just 18 days AFTER the Gandhi-Irwin Pact (March 5, 1931). This is significant because:
(A) Gandhi personally ordered his execution
(B) Despite the pact, Gandhi could not prevent the execution — a major criticism from his contemporaries
(C) Bhagat Singh was released by the pact
(D) More than one of the above
(E) None of the above

---

**Q42.** The Government of India Act 1935 was a direct outcome of the Round Table Conferences. Which of the following was NOT a provision of this Act?
(A) Provincial Autonomy — provinces got self-governance
(B) Establishment of Reserve Bank of India (RBI)
(C) Grant of complete independence (Purna Swaraj) to India
(D) More than one of the above
(E) None of the above

---

**Q43.** In the 1937 provincial elections conducted under the Government of India Act 1935, Congress:
(A) Boycotted elections in all provinces
(B) Won in 7 out of 11 provinces
(C) Won in all 11 provinces
(D) More than one of the above
(E) None of the above

---

**Q44.** The Bardoli Satyagraha of 1928 (precursor to CDM) was led by:
(A) Mahatma Gandhi
(B) Jawaharlal Nehru
(C) Sardar Vallabhbhai Patel
(D) More than one of the above
(E) None of the above

---

**Q45.** "Sarojini Naidu" is also known as:
(A) "Mother of the Nation"
(B) "Nightingale of India"
(C) "Grand Old Lady of Congress"
(D) More than one of the above
(E) None of the above

---

**Q46.** January 26 is celebrated as REPUBLIC DAY in India because:
(A) India gained independence on January 26, 1947
(B) The Indian Constitution came into effect on January 26, 1950; this date also honoured January 26, 1930 when Purna Swaraj was first celebrated as Independence Day
(C) The Constituent Assembly was formed on January 26, 1946
(D) More than one of the above
(E) None of the above

---

**Q47.** The PRINCIPAL leader of the Civil Disobedience Movement in BIHAR was:
(A) Jayaprakash Narayan
(B) Rajendra Prasad
(C) Shri Krishna Sinha
(D) More than one of the above
(E) None of the above

---

**Q48.** Who among the following was the VICEROY during the Jallianwala Bagh massacre (1919)?
(A) Lord Curzon
(B) Lord Chelmsford
(C) Lord Irwin
(D) More than one of the above
(E) None of the above

---

**Q49.** The famous slogan "Simon Go Back" was raised during the visit of the Simon Commission (1928). The commission was boycotted because:
(A) It proposed complete independence for India
(B) It had NO Indian member — an all-British commission to review India's constitution
(C) It arrived without the Viceroy's permission
(D) More than one of the above
(E) None of the above

---

**Q50.** Consider these statements about the Salt Satyagraha and CDM:
I. Dandi March started from Sabarmati Ashram on March 12, 1930
II. Gandhi attended the Second Round Table Conference in London (1931)
III. CDM was formally withdrawn in 1934 (not 1931)
IV. Poona Pact replaced separate electorates with reserved seats in joint electorate

Which of the above statements are CORRECT?

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
|----|-----|-----------|
| 1  | (C) | Subnet mask identifies the NETWORK portion of an IP address |
| 2  | (B) | /26 borrows 2 bits from host: 2²=4 subnets; 6 host bits: 2⁶-2=62 usable |
| 3  | (C) | /30: 32-30=2 host bits; 2²=4 addresses; 4-2=2 usable hosts |
| 4  | (B) | VLSM = Variable Length = different mask lengths for different subnets |
| 5  | (C) | RIPv1 does NOT support VLSM (classful routing); RIPv2/OSPF/EIGRP do |
| 6  | (B) | First address = Network (subnet) address; Last = Broadcast address |
| 7  | (B) | TDM time slots are grouped into FRAMES (confirmed PYQ fact) |
| 8  | (C) | FDM = different frequencies; all transmit simultaneously |
| 9  | (C) | WDM is for OPTICAL FIBER only (uses wavelengths of light) |
| 10 | (B) | Guard bands prevent interference between adjacent frequency channels |
| 11 | (B) | Synchronous TDM: idle user's slot REMAINS EMPTY (wasted capacity) |
| 12 | (C) | Statistical (Asynchronous) TDM = dynamic slots only when data exists |
| 13 | (C) | Memory-mapped I/O = shared address space; same instructions for I/O+memory |
| 14 | (B) | I/O-mapped I/O = separate address space; uses IN/OUT instructions |
| 15 | (C) | Intel x86 (IBM PC) = I/O-mapped (port-mapped) I/O with IN/OUT |
| 16 | (B) | Polling = CPU repeatedly checks status register of I/O device |
| 17 | (B) | Socket = endpoint of inter-process communication (IP address + port) |
| 18 | (B) | 127.0.0.1 = loopback = testing network stack on SAME machine (localhost) |
| 19 | (C) | Private key = kept by RECEIVER; used to decrypt incoming messages |
| 20 | (B) | Switched networks prevent sniffing (unicast vs hub's broadcast) |
| 21 | (B) | /26: 6 host bits; 2⁶=64 addresses; 64-2=62 usable hosts |
| 22 | (B) | Statistical TDM = bandwidth efficient (no idle slot wastage) |
| 23 | (C) | PING uses ICMP (Internet Control Message Protocol) |
| 24 | (C) | /30 = exactly 2 usable hosts = perfect for router-to-router WAN links |
| 25 | (B) | FDM = different frequencies simultaneously; TDM = same freq, different time |

---

### GS Answers (Q26–Q50):

| Q  | Ans | Key Reason |
|----|-----|-----------|
| 26 | (B) | Purna Swaraj = Lahore Session 1929 |
| 27 | (C) | Jawaharlal Nehru = Congress President, Lahore 1929 |
| 28 | (B) | Dandi March started from Sabarmati Ashram, Ahmedabad |
| 29 | (C) | 385 km over 24 days (March 12 – April 6, 1930) |
| 30 | (B) | 78 satyagrahis accompanied Gandhi on Dandi March |
| 31 | (C) | Sarojini Naidu led Dharasana raid after Gandhi's arrest |
| 32 | (B) | Gandhi-Irwin Pact = March 5, 1931 |
| 33 | (B) | CDM suspended + prisoners released + coastal salt making for personal use |
| 34 | (B) | Gandhi attended ONLY the Second Round Table Conference (1931) |
| 35 | (B) | Congress boycotted First RTC (CDM ongoing, leaders in jail) |
| 36 | (B) | Communal Award = separate electorates for Depressed Classes |
| 37 | (B) | Gandhi fasted in Yerawada (Yerwada) Jail, Pune |
| 38 | (B) | Poona Pact = Gandhi + B.R. Ambedkar |
| 39 | (B) | Poona Pact = separate electorate replaced by reserved seats in JOINT electorate |
| 40 | (C) | CDM formally withdrawn 1934 (not 1931 — that was suspension) |
| 41 | (B) | Gandhi couldn't prevent Bhagat Singh's hanging — major criticism |
| 42 | (C) | Purna Swaraj was NOT granted by GoI Act 1935; it gave provincial autonomy |
| 43 | (B) | Congress won 7 out of 11 provinces in 1937 elections |
| 44 | (C) | Bardoli Satyagraha (1928) = Sardar Vallabhbhai Patel |
| 45 | (B) | Sarojini Naidu = "Nightingale of India" |
| 46 | (B) | Republic Day Jan 26 honours both Constitution (1950) and Purna Swaraj Day (1930) |
| 47 | (B) | Rajendra Prasad = Bihar's principal CDM leader (later 1st President) |
| 48 | (B) | Lord Chelmsford = Viceroy during Jallianwala Bagh 1919 |
| 49 | (B) | Simon Commission had NO Indian members — all-British → boycotted |
| 50 | (C) | All four statements I, II, III, IV are correct |

---

# 🔁 DAY 59 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Networks: Subnetting & Multiplexing

### Subnetting Key Formulas:
```
Subnets created     = 2^(bits borrowed from host)
Total addresses     = 2^(remaining host bits)
USABLE hosts        = 2^(remaining host bits) - 2   ← subtract network + broadcast

COMMON CIDR TABLE:
  /24 → 254 usable | /25 → 126 | /26 → 62 | /27 → 30 | /28 → 14 | /30 → 2
```

### Multiplexing Comparison:
```
FDM → Different FREQUENCIES; simultaneous; cable TV/radio; GUARD BANDS between channels
TDM → Same freq, different TIME SLOTS; slots grouped into FRAMES (PYQ!) 
      Synchronous = fixed (may waste); Statistical = dynamic (efficient)
WDM → Different WAVELENGTHS; OPTICAL FIBER only; like FDM for light
CDM → Same freq + same time; different CODES (CDMA = 3G networks)
```

### Memory-Mapped vs I/O-Mapped I/O:
```
MEMORY-MAPPED I/O:
  → SHARED address space (I/O + memory together)
  → Same LOAD/STORE instructions for both
  → Used by: ARM, Motorola, RISC processors

I/O-MAPPED I/O (Port-Mapped):
  → SEPARATE address spaces
  → Special IN/OUT instructions for I/O
  → Used by: Intel x86 (IBM PC)
```

### PYQ Traps — Networks:
```
✅ TDM slots grouped into FRAMES (not channels)
✅ WDM = optical fiber ONLY (not copper)
✅ Memory-mapped = SHARED space; I/O-mapped = SEPARATE space
✅ Intel x86 = I/O-mapped (port-mapped)
✅ /30 = 2 usable hosts (router-to-router WAN links)
✅ Private key = kept by RECEIVER (not sender)
✅ RIPv1 does NOT support VLSM; RIPv2, OSPF do
✅ Subnet mask identifies NETWORK portion (not host portion)
```

---

## ⚡ RAPID FIRE — Salt Satyagraha & CDM

### Key Dates (Exam-Critical):
```
Dec 1929     → Lahore Session; Purna Swaraj declared; Nehru president
Jan 26, 1930 → First Independence Day celebrated
Mar 12, 1930 → Dandi March BEGINS (Sabarmati Ashram, 78 satyagrahis)
Apr 6, 1930  → Gandhi breaks salt law at DANDI village (CDM begins)
May 1930     → Gandhi arrested; Sarojini Naidu leads Dharasana raid
Mar 5, 1931  → Gandhi-Irwin Pact (CDM suspended — Phase 1 ends)
Mar 23, 1931 → Bhagat Singh hanged (18 days after pact)
Sep 1931     → Gandhi attends 2nd RTC London (Congress boycotted 1st, 3rd)
Jan 1932     → CDM RESUMED (Phase 2) after failed RTC
Aug 1932     → Communal Award (Ramsay MacDonald) → separate electorates
Sep 25, 1932 → POONA PACT (Gandhi + Ambedkar) → reserved seats in joint electorate
1934         → CDM formally WITHDRAWN
1935         → Government of India Act (provincial autonomy, RBI, Federal Court)
1937         → Congress wins 7/11 provinces in elections
```

### Round Table Conferences:
```
1st RTC (1930) → Congress BOYCOTTED (CDM ongoing)
2nd RTC (1931) → Gandhi attended (only conference with Gandhi) → FAILED
3rd RTC (1932) → Congress BOYCOTTED → led to GoI Act 1935
```

### PYQ Traps — CDM:
```
✅ Dandi March: Sabarmati Ashram (NOT Wardha/Sevagram)
✅ Gandhi attended 2nd RTC ONLY (not 1st, not 3rd)
✅ CDM formally withdrawn 1934 (NOT 1931 — 1931 = suspended only)
✅ Sarojini Naidu led Dharasana raid (NOT Gandhi — he was arrested)
✅ Poona Pact = reserved seats in JOINT electorate (replaced separate electorate)
✅ Bhagat Singh hanged March 23, 1931 (NOT saved by Gandhi-Irwin pact)
✅ Bardoli Satyagraha = Sardar Patel (not Gandhi directly)
✅ GoI Act 1935: RBI established + Provincial Autonomy (NOT Purna Swaraj)
✅ Rajendra Prasad = Bihar's CDM leader (later 1st President)
✅ Purna Swaraj = Lahore 1929 (Nehru presided); NOT Calcutta 1928
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **Subnetting**: Usable hosts = 2^(host bits) - 2; /30 = 2 usable (WAN links); VLSM = variable masks in same network; RIPv1 doesn't support VLSM; Subnet mask identifies NETWORK portion.
2. **Multiplexing**: FDM = different frequencies (cable TV, radio, guard bands); TDM = same freq different time SLOTS grouped into FRAMES (PYQ!); Statistical TDM = dynamic slots (efficient); WDM = optical fiber only (wavelengths of light).
3. **I/O addressing**: Memory-mapped = SHARED address space + same instructions (ARM/RISC); I/O-mapped = SEPARATE space + IN/OUT instructions (Intel x86); Polling = CPU repeatedly checks status flags (inefficient).
4. **Dandi March**: March 12–April 6, 1930; Sabarmati Ashram → Dandi (385 km, 24 days, 78 satyagrahis); Gandhi arrested → Sarojini Naidu led Dharasana raid; CDM formally withdrawn 1934 (not 1931).
5. **Round Table Conferences + Pacts**: Gandhi attended ONLY 2nd RTC (1931); Poona Pact (Sep 25, 1932) = Gandhi + Ambedkar = reserved seats replaced separate electorate; GoI Act 1935 = RBI + Provincial Autonomy; Rajendra Prasad led Bihar's CDM.

---

## 📅 DAY 60 PREVIEW — What's Coming Next:
**Phase 1 Complete! Day 60 = FIRST FULL MOCK TEST**
- Full 150-question mock paper (Language 30 + GS 40 + CS 80)
- Target: 2.5 hours under simulated exam conditions
- After test: Score analysis, identify weak areas, adjust Phase 2 plan

*Prepare by doing a rapid 1-hour revision of all topics from Days 43–59 (Networks) tonight.*

---

*🚀 Day 59 of 170 — You're finishing Phase 1 strong! TDM "frames" and memory-mapped I/O are CONFIRMED PYQ traps. The Dandi March date (March 12, 1930) and Sabarmati Ashram are classic GS traps. Tomorrow is Mock Test Day — the first real measure of where you stand. Go in confident — you've built a solid foundation!*
