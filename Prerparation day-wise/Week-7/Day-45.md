# 📅 BPSC TRE 4.0 — DAY 45 COMPLETE STUDY MODULE
### Computer Networks: IP Addressing (IPv4 & IPv6), Subnetting & CIDR + Science & Technology — AI/ML Basics
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): IP Addressing — IPv4 Classes, Subnet Mask, CIDR, IPv6, Private IPs
> - Afternoon (1 hr): Science & Technology — AI, Machine Learning, Types, Applications
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 IP Addressing — IPv4, IPv6, Subnetting & CIDR

---

## 🔷 SECTION 1: What is an IP Address?

### Real-Life Analogy — The Postal Address System:

Every house in India has an address:
**"House No. 42, Street 5, Rajendra Nagar, Patna, Bihar — 800016"**

This address has layers:
- **PIN code (800016)** → identifies the city/area (like Network ID)
- **House No. (42)** → identifies the specific house (like Host ID)

Without this address, no letter can reach you. Similarly, without an IP address, no data packet can reach a device on the internet.

> **An IP Address (Internet Protocol Address) is a unique numerical label assigned to every device connected to a computer network that uses the Internet Protocol for communication.**

### Purpose of IP Address:
```
IP ADDRESS SERVES TWO FUNCTIONS:
  1. IDENTIFICATION:  "Who are you?" — Uniquely identifies a device on the network
  2. LOCATION:        "Where are you?" — Tells routers how to route data to you

ANALOGY:
  Your NAME         = identifies you as a person (like a MAC address — hardware identity)
  Your HOME ADDRESS = locates where to send your mail (like an IP address — logical location)
```

### Logical vs Physical Addressing:
```
┌──────────────────────────────────────────────────────────────────────────────┐
│              PHYSICAL vs LOGICAL ADDRESSING                                  │
├─────────────────────────┬────────────────────────────────────────────────────┤
│   PHYSICAL ADDRESS      │           LOGICAL ADDRESS                          │
│   (MAC Address)         │           (IP Address)                             │
├─────────────────────────┼────────────────────────────────────────────────────┤
│ Burned into NIC hardware│ Assigned by network administrator or DHCP         │
│ by manufacturer         │                                                    │
├─────────────────────────┼────────────────────────────────────────────────────┤
│ 48 bits, hexadecimal    │ IPv4: 32 bits | IPv6: 128 bits                    │
│ e.g.: 00:1A:2B:3C:4D:5E │ e.g.: 192.168.1.1 | 2001:db8::1                  │
├─────────────────────────┼────────────────────────────────────────────────────┤
│ Does NOT change         │ CAN change (dynamic IP via DHCP)                  │
│ (permanent)             │                                                    │
├─────────────────────────┼────────────────────────────────────────────────────┤
│ Used at Data Link Layer │ Used at Network Layer (OSI L3 / TCP/IP Internet)  │
│ (OSI Layer 2)           │                                                    │
├─────────────────────────┼────────────────────────────────────────────────────┤
│ Local delivery          │ End-to-end routing across networks                │
│ (within same network)   │ (across the entire Internet)                      │
├─────────────────────────┼────────────────────────────────────────────────────┤
│ Flat address space      │ Hierarchical (Network + Host portions)            │
│ (no hierarchy)          │                                                    │
└─────────────────────────┴────────────────────────────────────────────────────┘

KEY INSIGHT: When sending data across the Internet:
  → IP address routes the packet to the CORRECT NETWORK (like city address)
  → MAC address delivers it to the CORRECT DEVICE within that network (like door number)
  → ARP protocol bridges them: converts IP → MAC for final delivery

🎯 PYQ FACT: IP address = Logical address (Network Layer); MAC = Physical address (Data Link Layer)
```

---

## 🔷 SECTION 2: IPv4 Addressing — Deep Dive

### Basic Structure:
```
IPv4 = Internet Protocol version 4
SIZE: 32 BITS total
REPRESENTATION: DOTTED DECIMAL NOTATION
  → Divide 32 bits into 4 groups of 8 bits each (= 4 OCTETS)
  → Each octet converted to decimal (0–255)
  → Separated by dots

EXAMPLE:
  Binary:  11000000 . 10101000 . 00000001 . 00000001
  Decimal:    192   .   168   .    1    .    1
  → Written as: 192.168.1.1

RANGE OF EACH OCTET:
  8 bits → 2^8 = 256 possible values → 0 to 255
  So each part of IPv4 address: 0 to 255

TOTAL IPv4 ADDRESSES:
  32 bits → 2^32 = 4,294,967,296 ≈ 4.3 BILLION addresses
  (This sounds like a lot but the world has 8 billion people + billions of devices!)
  → IPv4 address EXHAUSTION is why IPv6 was created!

🎯 PYQ FACT: IPv4 = 32 bits = 4 octets = dotted decimal notation (e.g., 192.168.1.1)
🎯 PYQ FACT: Maximum value of any octet = 255 (2^8 - 1)
🎯 PYQ FACT: Total IPv4 addresses ≈ 4.3 billion (2^32)
```

### IPv4 Address Structure — Network ID and Host ID:
```
AN IPv4 ADDRESS HAS TWO PARTS:

┌────────────────────────────────────────────────────────────────┐
│                    IPv4 ADDRESS (32 bits)                       │
├────────────────────────────┬───────────────────────────────────┤
│      NETWORK ID            │           HOST ID                  │
│   (Network Portion)        │         (Host Portion)             │
├────────────────────────────┼───────────────────────────────────┤
│ Identifies WHICH NETWORK   │ Identifies WHICH DEVICE           │
│ the device belongs to      │ within that network               │
├────────────────────────────┼───────────────────────────────────┤
│ Like the CITY + AREA of    │ Like the specific HOUSE NUMBER    │
│ your address               │ within that area                  │
├────────────────────────────┼───────────────────────────────────┤
│ All devices on the SAME    │ Must be UNIQUE within the         │
│ network share the same     │ network (no two devices have      │
│ Network ID                 │ the same Host ID)                 │
└────────────────────────────┴───────────────────────────────────┘

EXAMPLE: 192.168.1.45 with subnet mask 255.255.255.0
  Network ID = 192.168.1   (first 3 octets / 24 bits)
  Host ID    = 45          (last octet / 8 bits)
  
  This means: Device is on network "192.168.1.0"
              And is specifically device number "45" in that network

VISUAL:
  192  .  168  .   1   .  45
  ┌────────────────────┐┌──────┐
  │    NETWORK ID      ││HOST  │
  │   (24 bits)        ││ID    │
  └────────────────────┘└──────┘
```

---

## 🔷 SECTION 3: IPv4 Classes — The Original Classification System

Before CIDR, IP addresses were divided into CLASSES based on the first octet. Each class defines how many bits are for the Network ID vs Host ID.

```
IPv4 CLASSES — OVERVIEW DIAGRAM:

First Octet    Class    Purpose
  0–127         A       Large networks (governments, ISPs)
128–191         B       Medium networks (universities, companies)
192–223         C       Small networks (most common — home/office)
224–239         D       Multicasting (no host addresses)
240–255         E       Experimental/Reserved (not for general use)

HOW TO IDENTIFY CLASS FROM FIRST OCTET:
  First bit = 0          → Class A  (0xxxxxxx → 0–127)
  First bits = 10        → Class B  (10xxxxxx → 128–191)
  First bits = 110       → Class C  (110xxxxx → 192–223)
  First bits = 1110      → Class D  (1110xxxx → 224–239)
  First bits = 11110     → Class E  (11110xxx → 240–255)
```

### Class A:
```
CLASS A — LARGE NETWORKS

FIRST OCTET RANGE:  1 to 126  (0 is reserved; 127 is loopback)
NETWORK BITS:       8 bits (first octet = Network ID)
HOST BITS:          24 bits (last 3 octets = Host ID)
DEFAULT SUBNET MASK: 255.0.0.0  (or /8 in CIDR)

FORMAT:  [Network(8)] . [Host(8)] . [Host(8)] . [Host(8)]
         NNN.HHH.HHH.HHH

NUMBER OF NETWORKS:  2^7 = 128 (but usable = 126, since 0 and 127 reserved)
HOSTS PER NETWORK:   2^24 - 2 = 16,777,214 hosts
                     (-2 because: network address + broadcast address reserved)

EXAMPLE:  10.0.0.1
  Network ID = 10
  Host ID    = 0.0.1
  
WHO USES CLASS A:
  Very large organisations — internet backbone ISPs, large governments
  Example: 10.0.0.0/8 is a private Class A network

SPECIAL: 127.0.0.1 = LOOPBACK ADDRESS ("localhost")
  When you ping 127.0.0.1, you're pinging YOUR OWN device!
  Used for testing network software on your own machine.
  
🎯 PYQ FACT: 127.0.0.1 = loopback/localhost address
🎯 PYQ FACT: Class A default subnet mask = 255.0.0.0 = /8
🎯 PYQ FACT: Class A can have ~16.7 million hosts per network!
```

### Class B:
```
CLASS B — MEDIUM NETWORKS

FIRST OCTET RANGE:  128 to 191
NETWORK BITS:       16 bits (first 2 octets = Network ID)
HOST BITS:          16 bits (last 2 octets = Host ID)
DEFAULT SUBNET MASK: 255.255.0.0  (or /16 in CIDR)

FORMAT:  [Network(8)] . [Network(8)] . [Host(8)] . [Host(8)]
         NNN.NNN.HHH.HHH

NUMBER OF NETWORKS:  2^14 = 16,384
HOSTS PER NETWORK:   2^16 - 2 = 65,534 hosts

EXAMPLE:  172.16.5.20
  Network ID = 172.16
  Host ID    = 5.20
  
WHO USES CLASS B:
  Medium-sized organisations — universities, large companies

🎯 PYQ FACT: Class B default subnet mask = 255.255.0.0 = /16
🎯 PYQ FACT: Class B can have ~65,534 hosts per network
```

### Class C:
```
CLASS C — SMALL NETWORKS (MOST COMMON!)

FIRST OCTET RANGE:  192 to 223
NETWORK BITS:       24 bits (first 3 octets = Network ID)
HOST BITS:          8 bits (last octet = Host ID)
DEFAULT SUBNET MASK: 255.255.255.0  (or /24 in CIDR)

FORMAT:  [Network(8)] . [Network(8)] . [Network(8)] . [Host(8)]
         NNN.NNN.NNN.HHH

NUMBER OF NETWORKS:  2^21 = 2,097,152
HOSTS PER NETWORK:   2^8 - 2 = 254 hosts

EXAMPLE:  192.168.1.50
  Network ID = 192.168.1
  Host ID    = 50
  
WHO USES CLASS C:
  Small networks — homes, small offices (most common type!)
  Your home Wi-Fi router almost certainly uses 192.168.x.x!

🎯 PYQ FACT: Class C default subnet mask = 255.255.255.0 = /24
🎯 PYQ FACT: Class C allows only 254 hosts per network (most limited)
🎯 PYQ FACT: 192.168.x.x is the MOST commonly seen private IP range (Class C private)
```

### Class D and Class E:
```
CLASS D — MULTICASTING

FIRST OCTET RANGE: 224 to 239
PURPOSE: MULTICAST — send data to a GROUP of devices simultaneously
         (not to a single device like unicast, not to all like broadcast)
NO SUBNET MASK: Not used for individual hosts
EXAMPLE: 224.0.0.1 (all hosts multicast), 239.x.x.x (organisation-local)
USE: Video conferencing, IPTV, live streaming to multiple subscribers simultaneously

CLASS E — EXPERIMENTAL / RESERVED

FIRST OCTET RANGE: 240 to 255
PURPOSE: Research and experimental use; NOT assigned to regular hosts
         255.255.255.255 = Limited Broadcast Address (send to ALL on local network)
EXAMPLE: 240.0.0.0 to 254.255.255.255 (experimental)
         255.255.255.255 (broadcast to everyone on local network)
```

### IPv4 Classes — Master Summary Table:
```
┌─────────┬───────────────┬──────────────────┬──────────────────┬────────────────────┬─────────────────┐
│  CLASS  │  FIRST OCTET  │  NETWORK BITS /  │  DEFAULT SUBNET  │  HOSTS PER         │  PURPOSE        │
│         │    RANGE      │   HOST BITS      │     MASK         │  NETWORK           │                 │
├─────────┼───────────────┼──────────────────┼──────────────────┼────────────────────┼─────────────────┤
│    A    │   1 – 126     │    8 / 24        │   255.0.0.0      │  16,777,214        │ Very large      │
│         │               │    (/8)          │                  │  (~16.7 million)   │ networks        │
├─────────┼───────────────┼──────────────────┼──────────────────┼────────────────────┼─────────────────┤
│    B    │  128 – 191    │   16 / 16        │  255.255.0.0     │  65,534            │ Medium          │
│         │               │    (/16)         │                  │  (~65K)            │ networks        │
├─────────┼───────────────┼──────────────────┼──────────────────┼────────────────────┼─────────────────┤
│    C    │  192 – 223    │   24 / 8         │ 255.255.255.0    │  254               │ Small networks  │
│         │               │    (/24)         │                  │                    │ (most common)   │
├─────────┼───────────────┼──────────────────┼──────────────────┼────────────────────┼─────────────────┤
│    D    │  224 – 239    │   N/A            │   No mask        │  N/A               │ Multicast only  │
├─────────┼───────────────┼──────────────────┼──────────────────┼────────────────────┼─────────────────┤
│    E    │  240 – 255    │   N/A            │   No mask        │  N/A               │ Experimental /  │
│         │               │                  │                  │                    │ Reserved        │
└─────────┴───────────────┴──────────────────┴──────────────────┴────────────────────┴─────────────────┘

MEMORY TRICK for first octet ranges:
"A Boys Can't Do Experiments"
  A → 1-126
  B → 128-191
  C → 192-223
  D → 224-239
  E → 240-255
  
EASY PATTERN:
  Class A: starts at 0 (first bit = 0) → 1 to 126
  Class B: starts at 128 (10000000) → 128 to 191
  Class C: starts at 192 (11000000) → 192 to 223
  Class D: starts at 224 (11100000) → 224 to 239
  Class E: starts at 240 (11110000) → 240 to 255
```

---

## 🔷 SECTION 4: Private IP Addresses — The "Home Use" Ranges

### Why Private IPs?
```
PROBLEM: IPv4 only has ~4.3 billion addresses.
         The world has BILLIONS more devices than that!

SOLUTION: PRIVATE IP RANGES — addresses used INSIDE private networks
          (home, office) that are NOT routed on the public Internet.

  HOME ROUTER gives private IPs to your devices (192.168.1.x)
  Your router has ONE PUBLIC IP from your ISP
  → This is called NAT (Network Address Translation):
    Many devices with private IPs share ONE public IP address!

ANALOGY:
  Private IP = Internal phone extension in an office (ext. 101, 102, 103...)
  Public IP  = The ONE external phone number of the entire office
  
  Internal calls: use extensions (private IPs — fast, free, internal)
  External calls: go through the main number (public IP — NAT)
```

### Three Private IP Ranges:
```
┌─────────────────────────────────────────────────────────────────────────────┐
│                      PRIVATE IP ADDRESS RANGES                               │
├──────────────────────┬─────────────────────────┬────────────────────────────┤
│    IP RANGE          │    CIDR NOTATION         │   CLASS / TYPICAL USE      │
├──────────────────────┼─────────────────────────┼────────────────────────────┤
│  10.0.0.0 to         │  10.0.0.0/8              │  Class A private           │
│  10.255.255.255       │                          │  Large enterprise networks │
│                      │                          │  16,777,214 hosts!         │
├──────────────────────┼─────────────────────────┼────────────────────────────┤
│  172.16.0.0 to       │  172.16.0.0/12           │  Class B private           │
│  172.31.255.255       │                          │  Medium networks           │
│                      │                          │  1,048,574 hosts           │
├──────────────────────┼─────────────────────────┼────────────────────────────┤
│  192.168.0.0 to      │  192.168.0.0/16          │  Class C private           │
│  192.168.255.255      │                          │  HOME NETWORKS! (most seen)│
│                      │                          │  65,534 hosts possible     │
└──────────────────────┴─────────────────────────┴────────────────────────────┘

MEMORY TRICK — Three Private Ranges:
"10 is A-class, 172 is B-range, 192.168 is my Home"
  10.x.x.x       = Class A private (one BIG network)
  172.16-31.x.x  = Class B private (medium)
  192.168.x.x    = Class C private (your home Wi-Fi!)

SPECIAL IP ADDRESSES:
  0.0.0.0         = This host / Unknown source
  127.0.0.1       = LOOPBACK (localhost — your own device)
  255.255.255.255 = Broadcast (send to ALL on local network)
  169.254.x.x     = APIPA (Auto IP when DHCP fails — link-local address)

🎯 PYQ FACT: 192.168.x.x = most common home network private range
🎯 PYQ FACT: 127.0.0.1 = loopback address (localhost)
🎯 PYQ FACT: Private IPs are NOT routable on the public Internet — need NAT
🚨 TRAP: "192.168.x.x is a public IP" → FALSE! It's a PRIVATE range!
```

---

## 🔷 SECTION 5: Subnet Mask — The Network vs Host Identifier

### What is a Subnet Mask?
```
PROBLEM: Given an IP address like 192.168.1.45, how do we know which part
         is the Network ID and which is the Host ID?

SOLUTION: SUBNET MASK!

> A SUBNET MASK is a 32-bit number that, when applied to an IP address,
> separates the NETWORK portion from the HOST portion.

RULE:
  → Bits set to 1 in subnet mask = NETWORK portion of IP address
  → Bits set to 0 in subnet mask = HOST portion of IP address

ANALOGY:
  Subnet mask = a TEMPLATE or STENCIL laid over the IP address
  Where the stencil has holes (1s) = Network ID shows through
  Where the stencil is solid (0s) = Host ID is hidden

EXAMPLE:
  IP Address:    192.168.1.45
  Subnet Mask:   255.255.255.0

  In binary:
  IP:      11000000.10101000.00000001.00101101
  Mask:    11111111.11111111.11111111.00000000
           ←────── NETWORK (24 bits) ────────→←HOST (8 bits)→

  Network ID = 192.168.1.0   (where mask bits = 1)
  Host ID    = 45            (where mask bits = 0)
  
  So this device is host #45 on network 192.168.1.0
```

### How Subnet Mask Works (AND Operation):
```
THE BITWISE AND OPERATION:
  Network Address = IP Address AND Subnet Mask
  
  IP:   192.168.1.45  = 11000000.10101000.00000001.00101101
  Mask: 255.255.255.0 = 11111111.11111111.11111111.00000000
  AND:                = 11000000.10101000.00000001.00000000
                      = 192.168.1.0  ← NETWORK ADDRESS!

RULE OF AND:
  1 AND 1 = 1  (both network bits → keeps network bit)
  1 AND 0 = 0  (network mask 1, but host bit → zeroes host)
  0 AND anything = 0
  
  Result: ALL the host bits become 0 → reveals pure network address!
```

### Common Subnet Masks:
```
┌───────────────────────────────┬──────────────────┬──────────────┬───────────────────┐
│      SUBNET MASK              │  CIDR NOTATION   │ NETWORK BITS │   HOST BITS       │
├───────────────────────────────┼──────────────────┼──────────────┼───────────────────┤
│   255.0.0.0                   │      /8          │     8 bits   │  24 bits          │
│   (11111111.00000000.00000000.00000000)            │              │  2^24-2 = ~16.7M hosts │
├───────────────────────────────┼──────────────────┼──────────────┼───────────────────┤
│   255.255.0.0                 │      /16         │    16 bits   │  16 bits          │
│   (11111111.11111111.00000000.00000000)            │              │  2^16-2 = 65,534 hosts │
├───────────────────────────────┼──────────────────┼──────────────┼───────────────────┤
│   255.255.255.0               │      /24         │    24 bits   │  8 bits           │
│   (11111111.11111111.11111111.00000000)            │              │  2^8-2 = 254 hosts│
├───────────────────────────────┼──────────────────┼──────────────┼───────────────────┤
│   255.255.255.128             │      /25         │    25 bits   │  7 bits           │
│                               │                  │              │  2^7-2 = 126 hosts│
├───────────────────────────────┼──────────────────┼──────────────┼───────────────────┤
│   255.255.255.192             │      /26         │    26 bits   │  6 bits           │
│                               │                  │              │  2^6-2 = 62 hosts │
├───────────────────────────────┼──────────────────┼──────────────┼───────────────────┤
│   255.255.255.224             │      /27         │    27 bits   │  5 bits           │
│                               │                  │              │  2^5-2 = 30 hosts │
└───────────────────────────────┴──────────────────┴──────────────┴───────────────────┘

FORMULA: Number of usable hosts = 2^(host bits) - 2
         (-2 because: network address + broadcast address are reserved, not assignable)

NETWORK ADDRESS (all host bits = 0):   e.g., 192.168.1.0 — identifies the network
BROADCAST ADDRESS (all host bits = 1): e.g., 192.168.1.255 — sends to ALL hosts on network
USABLE HOST RANGE: everything between network and broadcast address
```

---

## 🔷 SECTION 6: CIDR — Classless Inter-Domain Routing

### What is CIDR?
```
CIDR = Classless Inter-Domain Routing
Introduced in 1993 to REPLACE the rigid class system (A, B, C)

PROBLEM WITH CLASSES:
  A company needs 300 host addresses.
  → Class C allows only 254 hosts (too small!)
  → Class B allows 65,534 hosts (WAY too many — wastes 65,234 addresses!)
  → Rigid classes cause MASSIVE ADDRESS WASTE

CIDR SOLUTION:
  → Allows ANY number of network bits (not just 8, 16, or 24)
  → Written as: IP_address/prefix_length
  → Prefix length = number of NETWORK bits

CIDR NOTATION:
  192.168.1.0/24  → 24 network bits, 8 host bits → 254 hosts
  192.168.1.0/25  → 25 network bits, 7 host bits → 126 hosts
  192.168.1.0/26  → 26 network bits, 6 host bits → 62 hosts
  10.0.0.0/8      → 8 network bits, 24 host bits → ~16.7M hosts
  172.16.0.0/12   → 12 network bits, 20 host bits → ~1M hosts

FORMAT: IP Address / Prefix Length
  e.g., 192.168.1.0/24
         ─────────── ──
         Network Addr  └ 24 = first 24 bits are network portion
```

### CIDR to Subnet Mask Conversion — Must Know:
```
QUICK CONVERSION TABLE:

  /8  → 255.0.0.0       (/8 means first 8 bits are 1s)
  /16 → 255.255.0.0     (/16 means first 16 bits are 1s)
  /24 → 255.255.255.0   (/24 means first 24 bits are 1s)
  /25 → 255.255.255.128 (first 25 bits 1s → last octet = 10000000 = 128)
  /26 → 255.255.255.192 (first 26 bits 1s → last octet = 11000000 = 192)
  /27 → 255.255.255.224 (first 27 bits 1s → last octet = 11100000 = 224)
  /28 → 255.255.255.240 (first 28 bits 1s → last octet = 11110000 = 240)
  /30 → 255.255.255.252 (first 30 bits 1s → last octet = 11111100 = 252)
  /32 → 255.255.255.255 (all 32 bits 1s → single host, no host bits!)

MEMORY SHORTCUT for /24, /16, /8:
  /24 = 255.255.255.0   ← 3 full octets of 255 (24 = 3×8)
  /16 = 255.255.0.0     ← 2 full octets of 255 (16 = 2×8)
  /8  = 255.0.0.0       ← 1 full octet of 255  (8  = 1×8)

LAST OCTET VALUES for /25, /26, /27, /28:
  /25 → last octet 128 = 10000000 (one 1 in last octet)
  /26 → last octet 192 = 11000000 (two 1s in last octet)
  /27 → last octet 224 = 11100000 (three 1s in last octet)
  /28 → last octet 240 = 11110000 (four 1s in last octet)
  
  TRICK: 128, 192, 224, 240, 248, 252 — each adds half the remaining bits!
```

### Subnetting Concept (Conceptual — No Deep Calculation):
```
WHAT IS SUBNETTING?
  Subnetting = dividing a large network into SMALLER sub-networks (subnets)

WHY SUBNET?
  → Better network management (smaller, more organised networks)
  → Improved security (isolate departments)
  → Reduced broadcast traffic (broadcasts don't cross subnet boundaries)
  → Efficient IP address use

EXAMPLE:
  A company gets network 192.168.1.0/24 (254 usable IPs)
  They want 4 departments, each with ~50 computers
  
  WITHOUT subnetting: All 254 devices in one big network
                      → Broadcast traffic goes to ALL 254 devices
  
  WITH subnetting (/26 = 62 hosts each):
    Subnet 1 (HR):      192.168.1.0/26   → .1 to .62
    Subnet 2 (Finance): 192.168.1.64/26  → .65 to .126
    Subnet 3 (IT):      192.168.1.128/26 → .129 to .190
    Subnet 4 (Admin):   192.168.1.192/26 → .193 to .254
  
  → Each department in its own subnet
  → Broadcasts CONTAINED within each subnet (less traffic!)
  → Finance can't directly see HR's traffic (security!)

BORROWING BITS:
  To create subnets, you "borrow" bits from the HOST portion
  and add them to the NETWORK portion.
  
  More borrowed bits = More subnets BUT fewer hosts per subnet
  Fewer borrowed bits = Fewer subnets BUT more hosts per subnet

FORMULA:
  Number of subnets  = 2^(borrowed bits)
  Hosts per subnet   = 2^(remaining host bits) - 2
```

---

## 🔷 SECTION 7: IPv6 — The Future of IP Addressing

### Why IPv6?
```
IPv4 EXHAUSTION PROBLEM:
  IPv4 has 2^32 ≈ 4.3 billion addresses.
  By 2011, IANA (Internet Assigned Numbers Authority) had allocated
  ALL IPv4 address blocks to regional registries!
  
  IANA announced IPv4 EXHAUSTION on February 3, 2011.
  
  Solution: IPv6 — a much larger address space.
```

### IPv6 Basics:
```
IPv6 = Internet Protocol version 6
SIZE: 128 BITS (4 times longer than IPv4's 32 bits!)
TOTAL ADDRESSES: 2^128 = 340,282,366,920,938,463,463,374,607,431,768,211,456
                ≈ 340 UNDECILLION (340 trillion trillion trillion)
                
This is enough to give TRILLIONS of IP addresses to every single person on Earth!
We will NEVER run out of IPv6 addresses in any foreseeable future.

REPRESENTATION: HEXADECIMAL NOTATION
  → 128 bits divided into 8 GROUPS of 16 bits each
  → Each group written in HEXADECIMAL (0-9, A-F)
  → Groups separated by COLONS (:) — NOT dots like IPv4!

EXAMPLE IPv6 ADDRESS:
  2001:0db8:85a3:0000:0000:8a2e:0370:7334
  
  Breaking it down:
  2001 : 0db8 : 85a3 : 0000 : 0000 : 8a2e : 0370 : 7334
  ↑      ↑      ↑      ↑      ↑      ↑      ↑      ↑
  Grp1  Grp2  Grp3  Grp4  Grp5  Grp6  Grp7  Grp8
  (each group = 16 bits = 4 hex digits)
```

### IPv6 Address Shortening Rules:
```
IPv6 addresses can be SHORTENED for readability:

RULE 1: Leading zeros in each group can be omitted:
  0db8 → db8
  0000 → 0
  0370 → 370

RULE 2: One or more consecutive groups of ALL zeros can be replaced with ::
  (can only be used ONCE in an address)
  
EXAMPLE:
  Full:      2001:0db8:85a3:0000:0000:8a2e:0370:7334
  Step 1:    2001:db8:85a3:0:0:8a2e:370:7334    (removed leading zeros)
  Step 2:    2001:db8:85a3::8a2e:370:7334        (:: replaces :0:0:)
  
  Another example:
  Full:     FE80:0000:0000:0000:0202:B3FF:FE1E:8329
  Shortened: FE80::202:B3FF:FE1E:8329

SPECIAL IPv6 ADDRESSES:
  ::1          = Loopback address (equivalent to 127.0.0.1 in IPv4!)
  ::           = Unspecified address (all zeros)
  FE80::/10    = Link-local addresses (similar to 169.254.x.x in IPv4)
  FF00::/8     = Multicast addresses
  2001::/32    = Teredo tunneling
```

### IPv6 Key Features:
```
1. MASSIVE ADDRESS SPACE:
   2^128 ≈ 340 undecillion — virtually UNLIMITED for any future need!
   
2. NO NEED FOR NAT:
   Since every device can get a UNIQUE public IPv6 address,
   NAT (Network Address Translation) is no longer needed.
   → True end-to-end connectivity restored!
   
3. SIMPLIFIED HEADER:
   IPv6 header is SIMPLER than IPv4 (fewer fields, fixed size 40 bytes)
   → Faster processing by routers!
   → IPv4 header = variable length (20-60 bytes)
   
4. BUILT-IN IPSec (SECURITY):
   IPv6 was designed with IPSEC (Internet Protocol Security) as mandatory
   → Encryption and authentication BUILT IN
   → IPv4 had IPSec as an optional add-on only
   
5. AUTO-CONFIGURATION (SLAAC):
   Stateless Address Autoconfiguration — devices can AUTOMATICALLY
   configure their own IPv6 addresses without needing DHCP!
   
6. EFFICIENT ROUTING:
   Hierarchical addressing + elimination of broadcast
   (IPv6 uses MULTICAST instead of broadcast)
   → Routers process packets more efficiently
   
7. NO FRAGMENTATION AT ROUTERS:
   IPv6 handles fragmentation only at source, NOT at intermediate routers
   → Better router performance!
   
8. QUALITY OF SERVICE (QoS):
   IPv6 has a built-in Flow Label field for better QoS support
   → Prioritise video/voice traffic natively

🎯 PYQ FACT: IPv6 = 128 bits = 8 groups of 16 bits = hexadecimal, colon-separated
🎯 PYQ FACT: IPv6 loopback = ::1 (equivalent to IPv4's 127.0.0.1)
🎯 PYQ FACT: IPv6 removes need for NAT (every device gets unique public address)
🎯 PYQ FACT: IPv6 has built-in IPSec (IPv4 had it as optional)
```

---

## 🔷 SECTION 8: IPv4 vs IPv6 — Complete Comparison

```
┌──────────────────────────┬───────────────────────────────┬────────────────────────────────┐
│         FEATURE          │           IPv4                │             IPv6               │
├──────────────────────────┼───────────────────────────────┼────────────────────────────────┤
│ Full Name                │ Internet Protocol version 4   │ Internet Protocol version 6    │
├──────────────────────────┼───────────────────────────────┼────────────────────────────────┤
│ Address Size             │ 32 BITS                       │ 128 BITS                       │
├──────────────────────────┼───────────────────────────────┼────────────────────────────────┤
│ Total Addresses          │ 2^32 ≈ 4.3 billion            │ 2^128 ≈ 340 undecillion        │
├──────────────────────────┼───────────────────────────────┼────────────────────────────────┤
│ Address Format           │ Dotted DECIMAL                │ HEXADECIMAL with colons        │
│                          │ 4 octets (e.g., 192.168.1.1)  │ 8 groups (e.g., 2001:db8::1)  │
├──────────────────────────┼───────────────────────────────┼────────────────────────────────┤
│ Header Size              │ Variable (20-60 bytes)        │ Fixed (40 bytes)               │
├──────────────────────────┼───────────────────────────────┼────────────────────────────────┤
│ NAT Required             │ YES (private IPs share 1 pub) │ NO (every device unique IP)    │
├──────────────────────────┼───────────────────────────────┼────────────────────────────────┤
│ Security (IPSec)         │ OPTIONAL (add-on)             │ MANDATORY (built-in)           │
├──────────────────────────┼───────────────────────────────┼────────────────────────────────┤
│ Broadcast                │ YES (255.255.255.255)         │ NO — uses MULTICAST instead    │
├──────────────────────────┼───────────────────────────────┼────────────────────────────────┤
│ Loopback Address         │ 127.0.0.1                     │ ::1                            │
├──────────────────────────┼───────────────────────────────┼────────────────────────────────┤
│ Auto-configuration       │ DHCP required                 │ SLAAC — self-configures!       │
├──────────────────────────┼───────────────────────────────┼────────────────────────────────┤
│ Address Classes          │ A, B, C, D, E                 │ No classes (CIDR-like system)  │
├──────────────────────────┼───────────────────────────────┼────────────────────────────────┤
│ Fragmentation            │ At routers and source         │ ONLY at source                 │
├──────────────────────────┼───────────────────────────────┼────────────────────────────────┤
│ Checksum in header       │ YES                           │ NO (removed for speed)         │
├──────────────────────────┼───────────────────────────────┼────────────────────────────────┤
│ Subnet Mask              │ Uses subnet mask              │ Uses prefix length (/64 etc.)  │
├──────────────────────────┼───────────────────────────────┼────────────────────────────────┤
│ Status Today             │ Still MOST widely used        │ Adoption growing (dual-stack)  │
└──────────────────────────┴───────────────────────────────┴────────────────────────────────┘

🧠 MEMORY TRICK: IPv4 = "Four-dotted decimal" | IPv6 = "Six-colon-hex" (more complex, more space)
```

---

## 🔷 SECTION 9: Common PYQ Traps — IP Addressing

```
🚨 TRAP 1: "IPv4 has 128 bits" → FALSE! IPv4 = 32 bits. IPv6 = 128 bits.
🚨 TRAP 2: "IPv6 uses dotted decimal notation" → FALSE! IPv6 = hexadecimal with colons.
🚨 TRAP 3: "192.168.1.1 is a public IP address" → FALSE! 192.168.x.x = PRIVATE range.
🚨 TRAP 4: "Subnet mask 255.255.0.0 = /24" → FALSE! 255.255.0.0 = /16. /24 = 255.255.255.0.
🚨 TRAP 5: "127.0.0.1 is a private network address" → PARTIALLY MISLEADING.
           127.0.0.1 = LOOPBACK address (localhost) — reserved for self-testing.
           It's not a "private" range like 192.168.x.x but is reserved/special.
🚨 TRAP 6: "Class D is used for regular host assignment" → FALSE! Class D = multicast ONLY.
🚨 TRAP 7: "Class A starts from 0" → CAREFUL! Range is 1-126 (0 is reserved, 127 is loopback).
🚨 TRAP 8: "Subnet mask identifies the host portion" → MISLEADING.
           Subnet mask bits = 1 identify the NETWORK portion.
           Subnet mask bits = 0 identify the HOST portion.
🚨 TRAP 9: "CIDR /24 means 24 hosts" → FALSE! /24 means 24 network bits → 2^8-2 = 254 hosts.
🚨 TRAP 10: "IPv6 requires NAT like IPv4" → FALSE! IPv6 eliminates the need for NAT.
🚨 TRAP 11: "Class C allows more hosts than Class A" → FALSE!
            Class A = ~16.7 million hosts; Class C = only 254 hosts per network.
🚨 TRAP 12: "Network address and broadcast address are usable host addresses" → FALSE!
            These are RESERVED — network address (all host bits 0) and
            broadcast address (all host bits 1) cannot be assigned to hosts.
            Usable = Total addresses - 2.
```

---

# PART 2: GENERAL STUDIES
## 🤖 Science & Technology — Artificial Intelligence & Machine Learning Basics

---

## 🔷 SECTION 1: What is Artificial Intelligence (AI)?

### Real-Life Analogy — Teaching a Child vs Programming a Robot:

Old-style computers were like **calculators** — you give exact instructions, they follow exactly. But what if a task is too complex to write rules for? Teaching a child to recognize a cat doesn't involve saying "if has pointy ears AND whiskers AND is small AND meows, then it's a cat." The child just SEES many cats and learns automatically.

**AI gives computers the ability to learn and perform tasks that normally require human intelligence.**

> **Artificial Intelligence (AI) is the simulation of human intelligence processes by computer systems — including learning, reasoning, problem-solving, perception, and language understanding.**

### History of AI:
```
AI TIMELINE:
  1950 → Alan Turing proposes "Turing Test" 
         (Can a machine behave indistinguishably from a human?)
  1956 → Term "Artificial Intelligence" COINED by John McCarthy
         at Dartmouth Conference — considered the BIRTH OF AI
  1997 → IBM's Deep Blue defeats chess champion Garry Kasparov
  2011 → IBM Watson wins Jeopardy! (natural language understanding)
  2016 → Google DeepMind's AlphaGo defeats Go champion (complex strategy game)
  2022 → ChatGPT released (OpenAI) — mass public adoption of AI
  2023 → AI integrated into mainstream products everywhere

🎯 PYQ FACT: "Artificial Intelligence" coined by John McCarthy (1956)
🎯 PYQ FACT: Alan Turing proposed the Turing Test (1950)
🎯 PYQ FACT: First AI conference = Dartmouth Conference (1956)
```

### Types of AI (Narrow vs General vs Super):
```
TYPE 1: NARROW AI (Weak AI)
  → AI that performs ONE specific task very well
  → Does NOT understand the task — just pattern recognition
  → ALL current AI is Narrow AI!
  
  EXAMPLES:
  → Chess programs (Deep Blue) — only plays chess, can't drive a car
  → Face recognition (phone unlock) — only recognizes faces
  → Voice assistant (Siri, Alexa) — only answers queries
  → Spam filter — only classifies emails
  → Google Maps navigation — only finds routes
  → Recommendation engine (Netflix, YouTube) — only suggests content

TYPE 2: GENERAL AI (Strong AI / AGI)
  → AI that can perform ANY intellectual task that a human can
  → Can transfer knowledge between domains
  → Can reason, plan, learn, and understand language like humans
  → Does NOT EXIST yet — only theoretical!
  
  EXAMPLE (fictional): HAL 9000 from "2001: A Space Odyssey"
                        JARVIS from Iron Man

TYPE 3: SUPER AI (Artificial Superintelligence / ASI)
  → AI that SURPASSES human intelligence in ALL areas
  → Can improve itself, solve problems humans can't
  → Does NOT EXIST yet — only theoretical / hypothetical
  → Subject of AI safety concerns (Nick Bostrom's "Superintelligence")

🎯 PYQ FACT: All current AI (ChatGPT, Siri, etc.) = NARROW AI
🎯 PYQ FACT: AGI (General AI) does NOT exist yet — still theoretical
```

---

## 🔷 SECTION 2: What is Machine Learning (ML)?

### AI vs ML — The Relationship:
```
AI CONTAINS ML:

         ┌─────────────────────────────────────┐
         │       ARTIFICIAL INTELLIGENCE        │
         │  (Broad field — all intelligent machines)│
         │                                     │
         │   ┌───────────────────────────────┐ │
         │   │     MACHINE LEARNING          │ │
         │   │  (Subset of AI — learning    │ │
         │   │   from data)                 │ │
         │   │                              │ │
         │   │  ┌───────────────────────┐   │ │
         │   │  │   DEEP LEARNING       │   │ │
         │   │  │ (Subset of ML —       │   │ │
         │   │  │  neural networks)     │   │ │
         │   │  └───────────────────────┘   │ │
         │   └───────────────────────────────┘ │
         └─────────────────────────────────────┘

AI ⊃ ML ⊃ Deep Learning (each is a SUBSET of the one above)
```

> **Machine Learning (ML) is a subset of AI that enables computers to LEARN from data and improve their performance WITHOUT being explicitly programmed for each task.**

### Traditional Programming vs Machine Learning:
```
TRADITIONAL PROGRAMMING:
  Input: DATA + RULES (written by programmers)
  Output: ANSWERS
  
  Example: 
    Rule: "If price < ₹100 AND rating > 4, then recommend"
    Data: Product prices and ratings
    Output: List of recommended products
    PROBLEM: Can't handle complexity — too many rules needed!

MACHINE LEARNING:
  Input: DATA + ANSWERS (historical examples)
  Output: RULES (learned automatically by the algorithm!)
  
  Example:
    Data: 1 million past Amazon purchases + customer profiles
    Answers: What each customer bought
    ML learns: Patterns, correlations, what types of customers buy what
    Output: A MODEL that can predict what any new customer might buy!
```

---

## 🔷 SECTION 3: Types of Machine Learning

### TYPE 1 — SUPERVISED LEARNING (Learning with a Teacher)

```
CONCEPT: The algorithm learns from LABELLED training data
         (data where the correct answer is already provided)

"SUPERVISED" because: Like a teacher who tells the student whether the answer is 
                       right or wrong. The algorithm is "supervised" by labels.

HOW IT WORKS:
  1. Training data is provided WITH correct labels (answers)
  2. Algorithm learns the MAPPING from input → correct output
  3. Once trained, it can predict labels for NEW, unseen data

TYPES OF SUPERVISED LEARNING:
  
  CLASSIFICATION:
  → Predicts a CATEGORY (discrete label)
  → Output is a CLASS
  → Examples:
     ✅ Email = Spam or Not Spam?
     ✅ Photo = Cat or Dog?
     ✅ Patient = Diabetic or Not Diabetic?
     ✅ Loan = Approve or Reject?
     ✅ Message = Positive or Negative sentiment?
  
  REGRESSION:
  → Predicts a CONTINUOUS VALUE (number)
  → Output is a QUANTITY
  → Examples:
     ✅ House price prediction (₹ amount)
     ✅ Temperature forecast (degrees)
     ✅ Stock price prediction (₹ amount)
     ✅ Student score prediction (marks out of 100)

POPULAR SUPERVISED ALGORITHMS:
  → Linear Regression (predicts continuous values)
  → Logistic Regression (classification despite the name!)
  → Decision Tree (tree of yes/no questions)
  → Random Forest (many decision trees combined)
  → Support Vector Machine (SVM)
  → K-Nearest Neighbors (KNN)
  → Neural Networks

DECISION TREE — Explained:
  Like a FLOWCHART of yes/no questions:
  
                    "Is it raining?"
                    /              \
                 YES               NO
                 /                   \
        "Do you have          "Is it hot outside?"
         an umbrella?"         /              \
          /      \           YES               NO
        YES       NO         ↓                 ↓
         ↓         ↓      "Wear T-shirt"  "Wear jacket"
      "Go out    "Stay 
       with      inside"
       umbrella"
  
  In ML: Questions are based on FEATURES of the data
  → Used for both classification and regression
  → Easy to understand and explain (interpretable!)

🎯 PYQ FACT: Supervised learning = labelled data + learns mapping input → output
🎯 PYQ FACT: Decision Tree = Supervised learning algorithm
🎯 PYQ FACT: Classification = predicts category; Regression = predicts continuous value
```

---

### TYPE 2 — UNSUPERVISED LEARNING (Learning without a Teacher)

```
CONCEPT: The algorithm learns from UNLABELLED data
         (no correct answers provided — must find hidden patterns itself)

"UNSUPERVISED" because: Like a student exploring a library with NO teacher.
                         Must find patterns and structure independently.

HOW IT WORKS:
  1. Unlabelled data is provided (no correct answers!)
  2. Algorithm finds hidden PATTERNS, STRUCTURES, or GROUPINGS in data
  3. Discovers what the data "looks like" naturally

TYPES OF UNSUPERVISED LEARNING:

  CLUSTERING:
  → Groups similar data points together into CLUSTERS
  → No predefined labels — algorithm discovers natural groupings
  → Examples:
     ✅ Customer segmentation (group customers by buying patterns)
        "Cluster 1: young, tech-savvy shoppers"
        "Cluster 2: price-sensitive family shoppers"
     ✅ Document categorisation (group articles by topic)
     ✅ Gene expression analysis in biology
     ✅ Social network community detection
  
  POPULAR CLUSTERING ALGORITHM: K-Means Clustering
  → K = number of clusters (you decide)
  → Algorithm assigns each data point to nearest cluster centre
  → Iteratively improves until clusters stabilise

  DIMENSIONALITY REDUCTION:
  → Reduces the number of features while keeping important information
  → Makes data easier to visualise and process
  → Example: Compressing a 1000-feature dataset to 2 features for visualisation
  
  POPULAR ALGORITHM: PCA (Principal Component Analysis)

  ASSOCIATION:
  → Finds RULES about associations between variables in large datasets
  → "People who buy X also tend to buy Y"
  → Example: Amazon's "Customers who bought this also bought..."
             "Beer and diapers are often bought together on Fridays"
  
  POPULAR ALGORITHM: Apriori Algorithm (Market Basket Analysis)

🎯 PYQ FACT: Unsupervised learning = NO labels, finds hidden patterns
🎯 PYQ FACT: Clustering = unsupervised learning technique (e.g., K-Means)
🎯 PYQ FACT: Customer segmentation = classic unsupervised clustering application
```

---

### TYPE 3 — REINFORCEMENT LEARNING (Learning through Trial and Error)

```
CONCEPT: An AGENT learns by INTERACTING with an ENVIRONMENT
         Gets REWARDS for correct actions, PENALTIES for wrong ones
         Learns to maximise cumulative reward over time

ANALOGY: Training a dog:
  → Dog does a trick correctly → gets a treat (REWARD)
  → Dog misbehaves → no treat or scolding (PENALTY)
  → Over time, dog learns which actions earn treats (maximises reward!)

KEY COMPONENTS:
  AGENT:       The learner/decision-maker (the AI)
  ENVIRONMENT: Where the agent operates (the game, the road, the market)
  STATE:       Current situation the agent observes
  ACTION:      What the agent does
  REWARD:      Positive/negative feedback for each action
  POLICY:      Strategy agent develops — what to do in each state

EXAMPLES:
  → AlphaGo (Google DeepMind) — learned Go by playing millions of games
  → Game playing AI (chess, video games — beating human champions!)
  → Robotics (robot learns to walk by trial and error)
  → Self-driving cars (learns to navigate by receiving rewards for safe driving)
  → Stock trading algorithms

🎯 PYQ FACT: AlphaGo uses Reinforcement Learning
🎯 PYQ FACT: Reinforcement learning = reward/penalty based learning
```

### ML Types Summary Table:
```
┌──────────────────────┬───────────────────────┬───────────────────────────┬───────────────────────┐
│    TYPE              │   DATA NEEDED          │   WHAT IT LEARNS          │   EXAMPLES            │
├──────────────────────┼───────────────────────┼───────────────────────────┼───────────────────────┤
│ SUPERVISED           │ Labelled data          │ Mapping input → output    │ Spam filter,          │
│ LEARNING             │ (with correct answers) │ (with known answers)      │ Disease diagnosis,    │
│                      │                        │                           │ Price prediction      │
├──────────────────────┼───────────────────────┼───────────────────────────┼───────────────────────┤
│ UNSUPERVISED         │ Unlabelled data        │ Hidden patterns,          │ Customer clustering,  │
│ LEARNING             │ (NO correct answers)   │ natural groupings         │ Topic modelling,      │
│                      │                        │                           │ Anomaly detection     │
├──────────────────────┼───────────────────────┼───────────────────────────┼───────────────────────┤
│ REINFORCEMENT        │ Interaction with       │ Optimal actions via       │ AlphaGo, Game AI,     │
│ LEARNING             │ environment +          │ trial and error           │ Robotics,             │
│                      │ reward/penalty signals │ (maximise rewards)        │ Self-driving cars     │
└──────────────────────┴───────────────────────┴───────────────────────────┴───────────────────────┘
```

---

## 🔷 SECTION 4: Deep Learning — AI's Brain Simulation

```
DEEP LEARNING = A subset of Machine Learning that uses
                ARTIFICIAL NEURAL NETWORKS (ANNs) with
                MANY HIDDEN LAYERS (hence "DEEP")

INSPIRED BY: Human brain's neuron structure
  Human brain: ~86 billion neurons connected in networks
  ANN: Mathematical model with interconnected "artificial neurons"

STRUCTURE OF A NEURAL NETWORK:
  
  INPUT LAYER    HIDDEN LAYERS        OUTPUT LAYER
  ┌─────────┐   ┌──────────────────┐   ┌──────────┐
  │ Feature1│──▶│○  ○  ○  ○  ○  ○ │──▶│          │
  │ Feature2│──▶│○  ○  ○  ○  ○  ○ │──▶│ Output   │
  │ Feature3│──▶│○  ○  ○  ○  ○  ○ │──▶│          │
  └─────────┘   └──────────────────┘   └──────────┘
                Many "deep" layers
                = "Deep" Learning

WHY DEEP LEARNING WORKS SO WELL:
  → Automatically learns features from raw data
  → No manual feature engineering needed!
  → Given enough data + computation → matches or beats human performance

APPLICATIONS OF DEEP LEARNING:
  → IMAGE RECOGNITION: Face unlock, medical imaging (detecting cancer)
  → NATURAL LANGUAGE: ChatGPT, Google Translate, Siri, Alexa
  → SPEECH RECOGNITION: Voice assistants, transcription services
  → SELF-DRIVING CARS: Object detection, path planning
  → GAME PLAYING: AlphaGo, OpenAI Five (Dota 2)

FAMOUS DEEP LEARNING MODELS:
  → CNNs (Convolutional Neural Networks): Image recognition
  → RNNs (Recurrent Neural Networks): Sequential data (text, speech)
  → LSTMs (Long Short-Term Memory): Language understanding
  → Transformers: GPT (ChatGPT), BERT (Google Search)
  → GANs (Generative Adversarial Networks): Deepfakes, image generation

🎯 PYQ FACT: Deep Learning uses neural networks with MANY hidden layers
🎯 PYQ FACT: Deep Learning powers face recognition, ChatGPT, self-driving cars
🎯 PYQ FACT: CNN = images; RNN/LSTM = sequences (text/speech)
```

---

## 🔷 SECTION 5: Important AI/ML Terms for Exam

```
ALGORITHM:
  Step-by-step procedure for solving a problem or making a prediction.
  In ML, algorithms learn patterns from data.

TRAINING DATA:
  The historical data used to TEACH the ML model.
  More training data → usually better model!

TEST DATA:
  Data the model has NEVER seen — used to evaluate its performance.

MODEL:
  The OUTPUT of the ML training process — the "learned rules" encoded in math.
  
FEATURE:
  An individual measurable property of the data.
  Example: For predicting house price — features = area, rooms, location, age.

LABEL:
  The correct answer in supervised learning.
  Example: For email classification — label = "spam" or "not spam"

OVERFITTING:
  Model learns training data TOO well — even memorises noise.
  Result: Works great on training data but POORLY on new data.
  (Like a student who memorises answers without understanding concepts!)

UNDERFITTING:
  Model is too simple — doesn't learn patterns well enough.
  Result: Performs poorly even on training data.

NATURAL LANGUAGE PROCESSING (NLP):
  AI/ML applied to understanding and generating HUMAN LANGUAGE.
  Applications: Chatbots, translation, sentiment analysis, voice assistants.

COMPUTER VISION:
  AI/ML applied to understanding IMAGES and VIDEOS.
  Applications: Face recognition, medical imaging, autonomous vehicles.

CHATBOT / GENERATIVE AI:
  AI that generates text, images, or other content.
  Examples: ChatGPT (OpenAI), Gemini (Google), Copilot (Microsoft), Claude (Anthropic)
```

### India's AI Initiatives:
```
INDIA AND AI:
  → INDIA AI MISSION: Government initiative for AI infrastructure in India
  → NASSCOM AI initiative: Industry body promoting AI adoption
  → IIT Delhi, IIT Bombay — leading AI research institutions
  → AI used in Aarogya Setu (COVID contact tracing), BHIM (payments)
  → ISRO uses AI for satellite imagery analysis
  → AI in agriculture: crop disease detection using smartphone cameras
  → AI in education: adaptive learning platforms (BYJU's, etc.)

🎯 PYQ FACT: India AI Mission = Government's plan for AI development infrastructure
🎯 PYQ FACT: AI applications in India: healthcare, agriculture, finance, education
```

---

## 🔷 SECTION 6: PYQ Traps — AI/ML

```
🚨 TRAP 1: "Machine Learning = Artificial Intelligence" → FALSE (incomplete)!
   ML is a SUBSET of AI. AI is the broader field.
   All ML is AI but not all AI is ML.

🚨 TRAP 2: "Supervised learning uses unlabelled data" → FALSE!
   Supervised = LABELLED data.
   Unsupervised = UNLABELLED data.

🚨 TRAP 3: "Clustering is a supervised learning technique" → FALSE!
   Clustering = UNSUPERVISED (no predefined labels).

🚨 TRAP 4: "Deep Learning is the same as Machine Learning" → FALSE!
   Deep Learning is a SUBSET of Machine Learning (which itself is a subset of AI).

🚨 TRAP 5: "AlphaGo uses supervised learning to play Go" → FALSE (partially)!
   AlphaGo primarily uses REINFORCEMENT LEARNING (plus supervised for initial training).

🚨 TRAP 6: "AI was coined by Alan Turing" → FALSE!
   "Artificial Intelligence" coined by JOHN McCARTHY (1956).
   Alan Turing proposed the TURING TEST (1950).

🚨 TRAP 7: "Decision Tree is unsupervised learning" → FALSE!
   Decision Tree = SUPERVISED learning algorithm.

🚨 TRAP 8: "Reinforcement learning needs labelled training data" → FALSE!
   Reinforcement learning learns via REWARD/PENALTY signals, not labelled data.

🚨 TRAP 9: "General AI (AGI) currently exists" → FALSE!
   AGI does NOT exist yet. All current AI is NARROW AI.

🚨 TRAP 10: "NLP deals with computer vision tasks" → FALSE!
   NLP = Natural Language Processing (text/speech).
   Computer Vision = image/video understanding.
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: IPv4, IPv6, IP Classes, Subnet Mask, CIDR, Private IPs

---

**Q1.** An IPv4 address is how many bits long?
(A) 16 bits
(B) 64 bits
(C) 32 bits
(D) More than one of the above
(E) None of the above

---

**Q2.** An IPv6 address is how many bits long?
(A) 32 bits
(B) 64 bits
(C) 128 bits
(D) More than one of the above
(E) None of the above

---

**Q3.** An IPv4 address is represented in which notation?
(A) Hexadecimal with colons (e.g., 2001:db8::1)
(B) Dotted decimal (e.g., 192.168.1.1)
(C) Binary with slashes (e.g., 11000000/10101000)
(D) More than one of the above
(E) None of the above

---

**Q4.** The maximum value that any single OCTET in an IPv4 address can have is:
(A) 128
(B) 256
(C) 255
(D) More than one of the above
(E) None of the above

---

**Q5.** Which IPv4 address class has a default subnet mask of 255.255.255.0?
(A) Class A
(B) Class B
(C) Class C
(D) More than one of the above
(E) None of the above

---

**Q6.** The IPv4 address 172.20.5.10 belongs to which class?
(A) Class A
(B) Class B
(C) Class C
(D) More than one of the above
(E) None of the above

---

**Q7.** The IPv4 address 10.50.100.200 belongs to which class?
(A) Class A
(B) Class B
(C) Class C
(D) More than one of the above
(E) None of the above

---

**Q8.** Which of the following IPv4 address ranges is a PRIVATE address range?
(A) 8.8.8.0 to 8.8.8.255 (Google DNS)
(B) 192.168.0.0 to 192.168.255.255
(C) 20.0.0.0 to 20.255.255.255
(D) More than one of the above
(E) None of the above

---

**Q9.** The IPv4 address 127.0.0.1 is known as the:
(A) Default gateway address
(B) Broadcast address
(C) Loopback (localhost) address
(D) More than one of the above
(E) None of the above

---

**Q10.** A subnet mask is used to:
(A) Assign MAC addresses to devices
(B) Separate the Network portion from the Host portion of an IP address
(C) Encrypt data during transmission
(D) More than one of the above
(E) None of the above

---

**Q11.** The subnet mask 255.255.255.0 in CIDR notation is:
(A) /8
(B) /16
(C) /24
(D) More than one of the above
(E) None of the above

---

**Q12.** The CIDR notation /16 corresponds to which subnet mask?
(A) 255.0.0.0
(B) 255.255.0.0
(C) 255.255.255.0
(D) More than one of the above
(E) None of the above

---

**Q13.** For a network with subnet mask 255.255.255.0 (/24), how many USABLE host addresses are available?
(A) 256
(B) 255
(C) 254
(D) More than one of the above
(E) None of the above

---

**Q14.** In the address 192.168.1.100/24, what is the Network Address?
(A) 192.168.1.100
(B) 192.168.1.255
(C) 192.168.1.0
(D) More than one of the above
(E) None of the above

---

**Q15.** In the address 192.168.1.100/24, what is the Broadcast Address?
(A) 192.168.1.0
(B) 192.168.1.255
(C) 192.168.2.0
(D) More than one of the above
(E) None of the above

---

**Q16.** Which IPv4 address class is used EXCLUSIVELY for MULTICASTING?
(A) Class B
(B) Class C
(C) Class D
(D) More than one of the above
(E) None of the above

---

**Q17.** CIDR (Classless Inter-Domain Routing) was introduced primarily to:
(A) Replace IPv4 with IPv6
(B) Improve routing speed in Data Link Layer
(C) Overcome the rigid class system and reduce IP address waste
(D) More than one of the above
(E) None of the above

---

**Q18.** What is the total number of possible IPv4 addresses?
(A) 2^16 ≈ 65,536
(B) 2^32 ≈ 4.3 billion
(C) 2^128 ≈ 340 undecillion
(D) More than one of the above
(E) None of the above

---

**Q19.** An IPv6 address uses which notation format?
(A) Dotted decimal with 4 octets
(B) Hexadecimal with 8 groups separated by colons
(C) Binary with 32 bits separated by slashes
(D) More than one of the above
(E) None of the above

---

**Q20.** Which of the following is the LOOPBACK address in IPv6?
(A) FE80::1
(B) FF00::
(C) ::1
(D) More than one of the above
(E) None of the above

---

**Q21.** One key advantage of IPv6 over IPv4 is:
(A) IPv6 uses dotted decimal notation which is easier to remember
(B) IPv6 eliminates the need for NAT by providing enough unique addresses for every device
(C) IPv6 has a smaller header size making it more complex to process
(D) More than one of the above
(E) None of the above

---

**Q22.** The private IP range 10.0.0.0/8 corresponds to which IPv4 class?
(A) Class B private range
(B) Class C private range
(C) Class A private range
(D) More than one of the above
(E) None of the above

---

**Q23.** Which of the following correctly identifies the CLASS of IP addresses based on first octet?
(A) 128–191 = Class A; 1–126 = Class B
(B) 1–126 = Class A; 128–191 = Class B; 192–223 = Class C
(C) 192–255 = Class A; 128–191 = Class B; 1–127 = Class C
(D) More than one of the above
(E) None of the above

---

**Q24.** A company has the network 192.168.10.0/26. How many USABLE host addresses does this subnet provide?
(A) 64
(B) 62
(C) 30
(D) More than one of the above
(E) None of the above

---

**Q25.** Consider these statements about IP addressing:
I.   IPv4 = 32 bits; IPv6 = 128 bits
II.  Class C default subnet mask = 255.255.255.0 = /24
III. 192.168.x.x is a PUBLIC IP range
IV.  IPv6 uses colons; IPv4 uses dots

Which are CORRECT?
(A) I, II, and IV only
(B) I, II, III, and IV all correct
(C) I and IV only
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: Artificial Intelligence, Machine Learning, Deep Learning, Types & Applications

---

**Q26.** The term "Artificial Intelligence" was coined by:
(A) Alan Turing
(B) John McCarthy
(C) Marvin Minsky
(D) More than one of the above
(E) None of the above

---

**Q27.** The Turing Test was proposed by Alan Turing in 1950. Its purpose was to:
(A) Test the speed of early computers
(B) Determine if a machine can exhibit intelligent behaviour indistinguishable from a human
(C) Measure the memory capacity of computers
(D) More than one of the above
(E) None of the above

---

**Q28.** Machine Learning is BEST described as:
(A) Programming computers with explicit rules for every situation
(B) A subset of AI where computers learn from data without being explicitly programmed
(C) A hardware component that makes computers faster
(D) More than one of the above
(E) None of the above

---

**Q29.** Which of the following correctly describes the relationship between AI, ML, and Deep Learning?
(A) Deep Learning ⊃ Machine Learning ⊃ AI (Deep Learning is largest)
(B) AI ⊃ ML ⊃ Deep Learning (AI is broadest; DL is subset of subset)
(C) They are three separate, unrelated fields
(D) More than one of the above
(E) None of the above

---

**Q30.** SUPERVISED LEARNING is characterized by:
(A) Training on UNLABELLED data to find hidden patterns
(B) Learning through trial and error with rewards and penalties
(C) Training on LABELLED data where correct answers are provided
(D) More than one of the above
(E) None of the above

---

**Q31.** UNSUPERVISED LEARNING is characterized by:
(A) Training on labelled data with known correct outputs
(B) Learning patterns from UNLABELLED data without predefined correct answers
(C) Learning through reward and penalty signals
(D) More than one of the above
(E) None of the above

---

**Q32.** CLUSTERING is an example of which type of Machine Learning?
(A) Supervised Learning
(B) Reinforcement Learning
(C) Unsupervised Learning
(D) More than one of the above
(E) None of the above

---

**Q33.** A DECISION TREE algorithm is an example of:
(A) Unsupervised learning
(B) Reinforcement learning
(C) Supervised learning
(D) More than one of the above
(E) None of the above

---

**Q34.** Google DeepMind's AlphaGo, which defeated a world champion at the game of Go, primarily uses:
(A) Supervised learning with a database of winning moves
(B) Unsupervised clustering of game positions
(C) Reinforcement learning (learning through millions of self-play games with win/loss rewards)
(D) More than one of the above
(E) None of the above

---

**Q35.** REINFORCEMENT LEARNING involves:
(A) An agent learning optimal actions by receiving rewards for correct and penalties for wrong actions
(B) Finding clusters in unlabelled datasets
(C) Classifying emails as spam using labelled training data
(D) More than one of the above
(E) None of the above

---

**Q36.** DEEP LEARNING is distinguished from regular Machine Learning by:
(A) It uses DECISION TREES exclusively
(B) It uses artificial NEURAL NETWORKS with MANY hidden layers
(C) It only works for text data
(D) More than one of the above
(E) None of the above

---

**Q37.** NATURAL LANGUAGE PROCESSING (NLP) is a branch of AI that deals with:
(A) Processing and understanding HUMAN LANGUAGE (text and speech)
(B) Understanding and interpreting IMAGES and VIDEOS
(C) Training robots to walk and move
(D) More than one of the above
(E) None of the above

---

**Q38.** Which of the following is the BEST example of a NARROW AI application?
(A) A robot that can solve any intellectual problem a human can
(B) An AI that surpasses humans in all cognitive tasks
(C) A spam email filter that classifies emails as spam or not spam
(D) More than one of the above
(E) None of the above

---

**Q39.** In Machine Learning, OVERFITTING refers to:
(A) Model that is too simple and fails to learn even training data patterns
(B) Model that learns training data TOO perfectly, performing poorly on new unseen data
(C) Using too much computing power during training
(D) More than one of the above
(E) None of the above

---

**Q40.** The first conference where the term "Artificial Intelligence" was officially used was:
(A) MIT AI Conference, 1960
(B) Stanford AI Lab Meeting, 1970
(C) Dartmouth Conference, 1956
(D) More than one of the above
(E) None of the above

---

**Q41.** ChatGPT, developed by OpenAI, is an example of which type of AI?
(A) General AI (AGI) — can do anything a human can
(B) Super AI — surpasses human intelligence
(C) Narrow AI — a specific AI system for language generation tasks
(D) More than one of the above
(E) None of the above

---

**Q42.** Which of the following is an example of SUPERVISED LEARNING?
(A) Grouping customers into segments based on purchasing behaviour (no predefined groups)
(B) Training a spam filter with emails labelled "spam" and "not spam"
(C) A game AI that learns chess by playing millions of games against itself
(D) More than one of the above
(E) None of the above

---

**Q43.** "K-Means Clustering" is an algorithm used in:
(A) Supervised classification
(B) Reinforcement learning
(C) Unsupervised learning (clustering)
(D) More than one of the above
(E) None of the above

---

**Q44.** COMPUTER VISION in AI refers to:
(A) AI that processes and understands images and videos
(B) The physical display screen used for AI computing
(C) AI for text translation between languages
(D) More than one of the above
(E) None of the above

---

**Q45.** Which statement CORRECTLY distinguishes AI from ML?
(A) AI and ML are the same thing — different names for the same field
(B) ML is broader than AI — AI is a subset of ML
(C) AI is the broad field simulating human intelligence; ML is a subset of AI that learns from data
(D) More than one of the above
(E) None of the above

---

**Q46.** In supervised learning, REGRESSION is used when:
(A) The output is a discrete category (like "spam" or "not spam")
(B) The output is a CONTINUOUS VALUE (like house price or temperature)
(C) There are no labels in the training data
(D) More than one of the above
(E) None of the above

---

**Q47.** "IBM's Deep Blue" (1997) that defeated chess champion Garry Kasparov is an example of:
(A) General AI — it could handle any intellectual task
(B) Narrow AI — it was specifically designed to play chess only
(C) Reinforcement learning exclusively
(D) More than one of the above
(E) None of the above

---

**Q48.** Which of the following applications uses DEEP LEARNING most prominently?
(A) Sorting a list of numbers in ascending order
(B) Finding all files with a specific name on a computer
(C) Recognising faces in photos on a smartphone
(D) More than one of the above
(E) None of the above

---

**Q49.** Which of the following is NOT an example of Machine Learning application?
(A) Netflix recommending movies based on viewing history
(B) A calculator performing 2 + 2 = 4 based on programmed rules
(C) A hospital system predicting patient readmission risk
(D) More than one of the above
(E) None of the above

---

**Q50.** Consider these statements about AI and ML:
I.  Supervised learning requires labelled training data.
II. Clustering is an unsupervised learning technique.
III. AGI (General AI) currently exists in systems like ChatGPT.
IV. Deep Learning is a subset of Machine Learning.

Which statements are CORRECT?
(A) I, II, and III only
(B) I, II, and IV only
(C) II, III, and IV only
(D) More than one of the above
(E) None of the above

---

# ✅ ANSWER KEY

## ⚠️ ATTEMPT ALL 50 QUESTIONS BEFORE CHECKING ANSWERS

---

### CS Answers (Q1–Q25):

| Q  | Ans | Key Reason |
|----|-----|-----------|
| 1  | (C) | IPv4 = 32 bits (4 octets × 8 bits) |
| 2  | (C) | IPv6 = 128 bits (8 groups × 16 bits) |
| 3  | (B) | IPv4 = dotted decimal (e.g., 192.168.1.1); IPv6 uses hex with colons |
| 4  | (C) | Each octet = 8 bits → 2^8 - 1 = 255 maximum |
| 5  | (C) | Class C default subnet mask = 255.255.255.0 = /24 |
| 6  | (B) | 172 falls in 128–191 range → Class B |
| 7  | (A) | 10 falls in 1–126 range → Class A |
| 8  | (B) | 192.168.x.x = private Class C range; 8.8.8.x = Google public DNS |
| 9  | (C) | 127.0.0.1 = loopback (localhost) — testing your own device |
| 10 | (B) | Subnet mask identifies network vs host portion of IP address |
| 11 | (C) | 255.255.255.0 = 24 bits of 1s = /24 |
| 12 | (B) | /16 = 16 bits of 1s = 255.255.0.0 |
| 13 | (C) | /24 = 8 host bits → 2^8 - 2 = 256 - 2 = 254 usable hosts |
| 14 | (C) | Network address = IP with all host bits zeroed = 192.168.1.0 |
| 15 | (B) | Broadcast = IP with all host bits set to 1 = 192.168.1.255 |
| 16 | (C) | Class D (224–239) = multicast ONLY, not for host assignment |
| 17 | (C) | CIDR introduced to overcome rigid class system and reduce waste |
| 18 | (B) | IPv4 = 2^32 ≈ 4.3 billion addresses |
| 19 | (B) | IPv6 = hexadecimal, 8 groups of 16 bits, separated by colons |
| 20 | (C) | IPv6 loopback = ::1 (equivalent to 127.0.0.1 in IPv4) |
| 21 | (B) | IPv6 eliminates NAT by providing enough unique addresses for all devices |
| 22 | (C) | 10.0.0.0/8 = Class A private range (first octet 10 = Class A) |
| 23 | (B) | Correct: 1–126=A, 128–191=B, 192–223=C |
| 24 | (B) | /26 = 6 host bits → 2^6 - 2 = 64 - 2 = 62 usable hosts |
| 25 | (A) | I correct (32/128), II correct (C=/24), III WRONG (192.168=private), IV correct (IPv6 colons) |

---

### GS Answers (Q26–Q50):

| Q  | Ans | Key Reason |
|----|-----|-----------|
| 26 | (B) | "Artificial Intelligence" coined by John McCarthy (1956 Dartmouth) |
| 27 | (B) | Turing Test = can a machine behave indistinguishably from a human? |
| 28 | (B) | ML = subset of AI, learns from data without explicit programming |
| 29 | (B) | Hierarchy: AI ⊃ ML ⊃ Deep Learning |
| 30 | (C) | Supervised = labelled data with correct answers provided |
| 31 | (B) | Unsupervised = unlabelled data, finds hidden patterns |
| 32 | (C) | Clustering = unsupervised learning (no predefined labels) |
| 33 | (C) | Decision Tree = supervised learning algorithm |
| 34 | (C) | AlphaGo = reinforcement learning (self-play with win/loss reward) |
| 35 | (A) | Reinforcement learning = agent + rewards/penalties from environment |
| 36 | (B) | Deep Learning = neural networks with MANY hidden layers |
| 37 | (A) | NLP = processing and understanding human language (text + speech) |
| 38 | (C) | Spam filter = narrow AI (one specific task only) |
| 39 | (B) | Overfitting = model memorises training data, fails on new data |
| 40 | (C) | Dartmouth Conference 1956 = birth of AI as a field |
| 41 | (C) | ChatGPT = Narrow AI (language generation task only; not AGI) |
| 42 | (B) | Spam filter with labelled emails = classic supervised learning |
| 43 | (C) | K-Means = unsupervised clustering algorithm |
| 44 | (A) | Computer Vision = AI for understanding images and videos |
| 45 | (C) | AI = broad field; ML = subset of AI that learns from data |
| 46 | (B) | Regression = predicts continuous values (price, temperature) |
| 47 | (B) | Deep Blue = Narrow AI (chess only; couldn't do anything else) |
| 48 | (C) | Face recognition = deep learning (CNN-based neural networks) |
| 49 | (B) | Calculator doing 2+2=4 = rule-based programming, NOT machine learning |
| 50 | (B) | I correct (supervised = labelled), II correct (clustering = unsupervised), III WRONG (AGI doesn't exist; ChatGPT = Narrow AI), IV correct (DL ⊂ ML) |

---

# 🔁 DAY 45 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — IP Addressing

### IPv4 vs IPv6 — 3 Key Differences:
```
FEATURE      │  IPv4              │  IPv6
─────────────┼────────────────────┼──────────────────────
Bits         │  32 bits           │  128 bits
Format       │  Dotted decimal    │  Hex with colons
Addresses    │  ~4.3 billion      │  ~340 undecillion
NAT needed?  │  YES               │  NO
Security     │  Optional          │  Built-in (IPSec)
Loopback     │  127.0.0.1         │  ::1
```

### IPv4 Classes — Quick Reference:
```
CLASS  │ FIRST OCTET  │ SUBNET MASK       │ HOSTS/NETWORK
───────┼──────────────┼───────────────────┼──────────────
  A    │   1–126      │ 255.0.0.0   (/8)  │ ~16.7 million
  B    │  128–191     │ 255.255.0.0 (/16) │ 65,534
  C    │  192–223     │ 255.255.255.0(/24)│ 254
  D    │  224–239     │ N/A (multicast)   │ N/A
  E    │  240–255     │ N/A (reserved)    │ N/A
```

### Private IP Ranges:
```
10.x.x.x          → Class A private
172.16–31.x.x     → Class B private
192.168.x.x       → Class C private (HOME NETWORK!)
127.0.0.1         → Loopback (localhost)
255.255.255.255   → Broadcast (all hosts on local network)
```

### CIDR Shortcuts:
```
/8  → 255.0.0.0       → ~16.7M hosts
/16 → 255.255.0.0     → 65,534 hosts
/24 → 255.255.255.0   → 254 hosts
/25 → 255.255.255.128 → 126 hosts
/26 → 255.255.255.192 → 62 hosts
/27 → 255.255.255.224 → 30 hosts

FORMULA: Usable hosts = 2^(host bits) - 2
```

### PYQ Trap List — IP Addressing:
```
✅ IPv4 = 32 bits; IPv6 = 128 bits (not the other way!)
✅ IPv6 = hexadecimal with colons (NOT dotted decimal)
✅ 192.168.x.x = PRIVATE range (NOT public!)
✅ /24 = 255.255.255.0 (not /24 = 255.255.0.0)
✅ /16 = 255.255.0.0 (not /16 = 255.0.0.0)
✅ 127.0.0.1 = loopback (not a private "host" range)
✅ Class D = multicast ONLY (no host assignment)
✅ Class A = 1–126 (NOT 0–127; 0 reserved, 127 loopback)
✅ Usable hosts = 2^(host bits) - 2 (not 2^n)
✅ Network + Broadcast addresses are NOT usable host addresses
✅ IPv6 loopback = ::1 (NOT 127.0.0.1)
✅ IPv6 eliminates NAT (IPv4 requires NAT)
```

---

## ⚡ RAPID FIRE — AI / ML

### Hierarchy:
```
AI ⊃ Machine Learning ⊃ Deep Learning
(Broadest)  (Subset)      (Subset of subset)
```

### ML Types — 3 Lines:
```
SUPERVISED:    Labelled data → learns input-output mapping
               (Decision Tree, SVM, Neural Networks)
               Examples: spam filter, disease diagnosis, price prediction

UNSUPERVISED:  Unlabelled data → finds hidden patterns
               (K-Means Clustering, PCA)
               Examples: customer segmentation, topic discovery

REINFORCEMENT: Agent + rewards/penalties → optimal policy
               (Q-Learning, Policy Gradient)
               Examples: AlphaGo, game AI, robotics
```

### Key AI/ML Facts:
```
"AI" coined by:     John McCarthy, 1956 Dartmouth Conference
Turing Test:        Alan Turing, 1950
Deep Learning:      Neural networks with many hidden layers
NLP:                Language (text/speech) understanding
Computer Vision:    Image/video understanding
Current AI type:    ALL current AI = NARROW AI (AGI doesn't exist!)
ChatGPT by:         OpenAI | Claude by: Anthropic | Gemini by: Google
```

### PYQ Trap List — AI/ML:
```
✅ ML = subset of AI (not the same!)
✅ Clustering = UNSUPERVISED (no predefined labels)
✅ Decision Tree = SUPERVISED
✅ AlphaGo = Reinforcement Learning
✅ AGI (General AI) does NOT exist yet
✅ ChatGPT = Narrow AI (not AGI)
✅ "AI" term coined by John McCarthy (not Alan Turing)
✅ Alan Turing = Turing Test (1950)
✅ Supervised = labelled; Unsupervised = unlabelled
✅ Overfitting = too good on training data → fails on new data
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **IPv4 = 32 bits** (dotted decimal, e.g., 192.168.1.1); Classes: A=1–126(/8, 255.0.0.0), B=128–191(/16, 255.255.0.0), C=192–223(/24, 255.255.255.0); Private: 10.x.x.x, 172.16–31.x.x, 192.168.x.x; Loopback=127.0.0.1.
2. **IPv6 = 128 bits** (hex with colons, e.g., 2001:db8::1); ~340 undecillion addresses; no NAT needed; built-in IPSec; loopback = ::1; no broadcast (uses multicast).
3. **Subnet mask & CIDR**: /24=255.255.255.0=254 hosts; /16=255.255.0.0=65,534 hosts; /8=255.0.0.0=~16.7M hosts; usable hosts = 2^(host bits) - 2; network address + broadcast NOT usable.
4. **AI hierarchy**: AI ⊃ ML ⊃ Deep Learning; Supervised=labelled data (spam filter, decision tree); Unsupervised=unlabelled (clustering/K-means); Reinforcement=reward-penalty (AlphaGo); all current AI = Narrow AI.
5. **Key AI traps**: "AI" coined by John McCarthy (1956); Turing Test by Alan Turing (1950); AGI doesn't exist; ChatGPT = Narrow AI; Decision Tree = Supervised; Clustering = Unsupervised; Deep Learning = neural networks with many hidden layers.

---

## 📅 DAY 46 PREVIEW — What's Coming Next:
**CS**: Computer Networks — Network Topologies (Bus, Star, Ring, Mesh, Tree, Hybrid), Network Devices (Hub, Switch, Router, Bridge, Gateway, Repeater, Modem), Transmission Media (Twisted Pair, Coaxial, Fiber Optic, Wireless)
**GS**: Indian Economy — Inflation: Types (Demand-pull, Cost-push), Measurement (CPI, WPI), RBI's role, Monetary Policy basics

---

*🚀 Day 45 of 170 — You're 26.5% through the journey. IP addressing is one of the most calculation-heavy yet formula-easy topics — master the /24, /16, /8 CIDR shortcuts and the class ranges today. For AI/ML, the supervised vs unsupervised distinction is the #1 PYQ pattern. Stay focused!*
