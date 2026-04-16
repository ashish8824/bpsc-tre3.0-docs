# 📅 BPSC TRE 4.0 — DAY 44
## CS Topic: TCP/IP Model, Layer Mapping, IPv4/IPv6 & Network Protocols
## GS Topic: Indian Economy — GDP, National Income, RBI & Monetary Policy
### 🎯 Target: 130+/150 | TOP 50 RANK

---

> **Topper Benchmark for Today:**
> Networks = ~10% of CS paper. Today covers TCP/IP (the REAL protocol suite used on the internet),
> IP addressing, and key protocols. These topics combine for 5–7 guaranteed marks.
> Indian Economy (GDP + RBI) = 2–3 GS marks every exam. Easy, factual, predictable.

---

## ⏰ TODAY'S STUDY SCHEDULE

| Slot | Duration | Activity |
|------|----------|----------|
| Morning | 1.5 hrs | CS: TCP/IP Model + IP Addressing + Protocols |
| Afternoon | 1 hr | GS: Indian Economy — GDP, National Income, RBI |
| Evening | 1 hr | Solve all 50 MCQs (25 CS + 25 GS) |
| Night | 30 min | Write 5-bullet summary from memory for each section |

---

---

# 🖥️ PART A — COMPUTER SCIENCE
# TCP/IP MODEL, IPv4/IPv6 & KEY NETWORK PROTOCOLS

---

## 🔑 WHY TCP/IP IS MORE IMPORTANT THAN OSI FOR BPSC

| Point | OSI Model | TCP/IP Model |
|-------|-----------|--------------|
| Purpose | Conceptual/Reference | Practical (Internet actually uses this) |
| Layers | 7 | 4 |
| Origin | ISO (1984) | US DOD (1970s) |
| Usage | Exam theory | Real-world internet |
| BPSC focus | Layer names, PDUs | Layer mapping, protocols, IP addressing |

> **Key Insight:** OSI is the "textbook" model. TCP/IP is what your phone, computer, and every server on the internet actually uses. BPSC asks about BOTH — but TCP/IP questions are more "applied."

---

## 🌐 SECTION 1: TCP/IP MODEL — THE REAL INTERNET PROTOCOL SUITE

### TCP/IP = Transmission Control Protocol / Internet Protocol

Developed by the **US Department of Defense (DARPA/DoD)** in the **1970s** as part of the ARPANET project — the predecessor of the modern internet.

---

### 🏗️ TCP/IP MODEL — 4 LAYERS

```
┌──────────────────────────────────────────────────────────┐
│                   TCP/IP MODEL                           │
├────────┬─────────────────────┬────────────────────────────┤
│ Layer# │    Layer Name       │    Protocols               │
├────────┼─────────────────────┼────────────────────────────┤
│   4    │   APPLICATION       │  HTTP, HTTPS, FTP, SMTP,   │
│        │                     │  DNS, DHCP, Telnet, SSH,   │
│        │                     │  SNMP, POP3, IMAP, MQTT    │
├────────┼─────────────────────┼────────────────────────────┤
│   3    │   TRANSPORT         │  TCP, UDP, SCTP            │
│        │   (Host-to-Host)    │                            │
├────────┼─────────────────────┼────────────────────────────┤
│   2    │   INTERNET          │  IP (IPv4, IPv6), ICMP,    │
│        │                     │  ARP, RARP, OSPF, BGP, RIP │
├────────┼─────────────────────┼────────────────────────────┤
│   1    │   NETWORK ACCESS    │  Ethernet, Wi-Fi (802.11), │
│        │   (Link Layer)      │  PPP, Token Ring, FDDI     │
└────────┴─────────────────────┴────────────────────────────┘
```

---

### 🔗 OSI vs TCP/IP — COMPLETE MAPPING DIAGRAM

```
    OSI MODEL (7 layers)          TCP/IP MODEL (4 layers)
  ┌────────────────────┐        ┌────────────────────────┐
  │  7. Application    │        │                        │
  ├────────────────────┤   →    │    4. Application      │
  │  6. Presentation   │        │                        │
  ├────────────────────┤        │                        │
  │  5. Session        │        │                        │
  ├────────────────────┼────────┼────────────────────────┤
  │  4. Transport      │   →    │  3. Transport           │
  │  (Segments)        │        │     (Host-to-Host)      │
  ├────────────────────┼────────┼────────────────────────┤
  │  3. Network        │   →    │  2. Internet            │
  │  (Packets)         │        │     (Packets / IP)      │
  ├────────────────────┼────────┼────────────────────────┤
  │  2. Data Link      │        │                        │
  ├────────────────────┤   →    │  1. Network Access      │
  │  1. Physical       │        │     (Link Layer)        │
  │  (Bits)            │        │                        │
  └────────────────────┘        └────────────────────────┘

KEY MAPPINGS (BPSC DIRECT PYQ):
• OSI Layer 7+6+5 = TCP/IP Layer 4 (Application)
• OSI Layer 4     = TCP/IP Layer 3 (Transport / Host-to-Host)  ← MOST ASKED
• OSI Layer 3     = TCP/IP Layer 2 (Internet)
• OSI Layer 2+1   = TCP/IP Layer 1 (Network Access)
```

---

### ⭐ TOPPER TIP — THE ONE MAPPING BPSC LOVES MOST:

```
┌─────────────────────────────────────────────────────┐
│  TCP/IP "Host-to-Host" layer  =  OSI Transport Layer│
│  This has appeared in TRE 1.0, 2.0, and 3.0!       │
│  If you remember ONE mapping → remember THIS one.   │
└─────────────────────────────────────────────────────┘
```

---

## 📡 SECTION 2: IPv4 ADDRESSING (CRITICAL — HIGH PYQ FREQUENCY)

### What is an IP Address?
An **IP (Internet Protocol) address** is a **unique numerical label** assigned to every device connected to a network. It serves two purposes:
1. **Host identification** — who are you?
2. **Location addressing** — where are you?

---

### 🔢 IPv4 — THE CURRENT INTERNET STANDARD

```
IPv4 = 32-bit address = 4 octets (groups of 8 bits) separated by dots

Example:  192  .  168  .   1  .   1
Binary: 11000000.10101000.00000001.00000001

Total possible addresses = 2^32 = 4,294,967,296 ≈ 4.3 billion
Format: Dotted Decimal Notation
Range: 0.0.0.0 to 255.255.255.255
```

---

### 🏷️ IPv4 ADDRESS CLASSES — BPSC TOPPER TABLE

```
┌───────┬──────────────┬─────────────────────────────┬────────────────────┐
│ Class │ First Octet  │ Address Range               │ Purpose            │
│       │ Range        │                             │                    │
├───────┼──────────────┼─────────────────────────────┼────────────────────┤
│   A   │   1 – 126    │ 1.0.0.0 – 126.255.255.255  │ Large networks     │
│       │              │ Network: 8 bits             │ ISPs, Governments  │
│       │              │ Host: 24 bits               │ 16 million hosts   │
├───────┼──────────────┼─────────────────────────────┼────────────────────┤
│   B   │  128 – 191   │ 128.0.0.0 – 191.255.255.255│ Medium networks    │
│       │              │ Network: 16 bits            │ Universities,      │
│       │              │ Host: 16 bits               │ Companies          │
│       │              │                             │ 65,534 hosts       │
├───────┼──────────────┼─────────────────────────────┼────────────────────┤
│   C   │  192 – 223   │ 192.0.0.0 – 223.255.255.255│ Small networks     │
│       │              │ Network: 24 bits            │ Home, Small offices│
│       │              │ Host: 8 bits                │ 254 hosts          │
├───────┼──────────────┼─────────────────────────────┼────────────────────┤
│   D   │  224 – 239   │ 224.0.0.0 – 239.255.255.255│ MULTICAST          │
│       │              │ No host bits                │ (Group messaging)  │
├───────┼──────────────┼─────────────────────────────┼────────────────────┤
│   E   │  240 – 255   │ 240.0.0.0 – 255.255.255.255│ EXPERIMENTAL       │
│       │              │                             │ (Reserved)         │
└───────┴──────────────┴─────────────────────────────┴────────────────────┘

⚠️ EXAM TRAP: 127.x.x.x = LOOPBACK address (localhost)
              127.0.0.1 = Your own computer!
              NOT part of Class A for assignment!
```

---

### 🔒 PRIVATE IP RANGES — MEMORIZE THESE!

```
These are addresses reserved for PRIVATE networks (not routable on internet):

Class A Private: 10.0.0.0 – 10.255.255.255      (10.x.x.x)
Class B Private: 172.16.0.0 – 172.31.255.255    (172.16–31.x.x)
Class C Private: 192.168.0.0 – 192.168.255.255  (192.168.x.x)

Your home Wi-Fi router gives you an address like 192.168.1.x → Class C Private!
```

---

### 🎭 SUBNET MASK — WHAT IT DOES

```
Subnet Mask identifies the NETWORK portion vs HOST portion of an IP address.

Example:
IP Address:    192.168.1.100
Subnet Mask:   255.255.255.0

Network Part:  192.168.1  (first 3 octets = network)
Host Part:     .100       (last octet = specific device)

255 in binary = 11111111 (all 8 bits = NETWORK)
0   in binary = 00000000 (all 8 bits = HOST)

BPSC PYQ KEY FACT:
"Subnet mask identifies the NETWORK PORTION of an IP address"
```

---

### 🌐 CIDR NOTATION — CLASSLESS INTER-DOMAIN ROUTING

```
Instead of writing 255.255.255.0, we write /24

192.168.1.0/24  →  means first 24 bits are network portion
                   (= subnet mask 255.255.255.0)

/8  = 255.0.0.0      (Class A equivalent)
/16 = 255.255.0.0    (Class B equivalent)
/24 = 255.255.255.0  (Class C equivalent)
```

---

## 🌍 SECTION 3: IPv6 — THE FUTURE OF INTERNET ADDRESSING

### Why IPv6?
IPv4 gives only ~4.3 billion addresses. In 2011, the last IPv4 blocks were assigned. The world needed MORE addresses → **IPv6 was developed**.

```
┌─────────────────────────────────────────────────────────────┐
│              IPv4  vs  IPv6 — BPSC COMPARISON               │
├───────────────────────┬──────────────────┬──────────────────┤
│ Feature               │     IPv4         │     IPv6         │
├───────────────────────┼──────────────────┼──────────────────┤
│ Address size          │ 32 bits          │ 128 bits         │
│ Total addresses       │ ~4.3 billion     │ 3.4 × 10^38      │
│ Format                │ Dotted decimal   │ Hexadecimal      │
│                       │ 192.168.1.1      │ 2001:0db8::1     │
│ Separator             │ Dot (.)          │ Colon (:)        │
│ Header size           │ Variable (20–60B)│ Fixed (40 bytes) │
│ Checksum in header    │ Yes              │ No               │
│ NAT required          │ Yes              │ Not required     │
│ Security (IPSec)      │ Optional         │ Mandatory        │
│ Flow label            │ Not present      │ PRESENT          │
└───────────────────────┴──────────────────┴──────────────────┘

⚠️ BPSC PYQ TRAP:
IPv6 = 128 bits — NOT 32, NOT 64, NOT 256 bits.
If the option says "64 bits" or "256 bits" → WRONG.
```

---

### 🔑 IPv6 FLOW LABEL — DIRECT PYQ FACT!

```
During IPv6 header translation (converting between IPv4 and IPv6):
→ The FLOW LABEL field is CONSIDERED (taken into account)
→ It is NOT discarded/ignored

This exact fact appeared in TRE 3.0!
```

### IPv6 Address Format:
```
Full form:  2001:0db8:0000:0000:0000:0000:0000:0001
Short form: 2001:db8::1  (leading zeros dropped, consecutive zeros = ::)

IPv6 has 8 groups of 4 hexadecimal digits (16 bits each = 8 × 16 = 128 bits)
```

---

## 📬 SECTION 4: KEY NETWORK PROTOCOLS — BPSC EXAM ESSENTIALS

### 🔥 PROTOCOL QUICK REFERENCE TABLE

```
┌──────────┬──────────┬────────────┬──────────────────────────────────────┐
│ Protocol │  Layer   │  Port No.  │  Function                            │
├──────────┼──────────┼────────────┼──────────────────────────────────────┤
│ HTTP     │ App      │ 80         │ Web browsing (unsecure)               │
│ HTTPS    │ App      │ 443        │ Secure web browsing (SSL/TLS)         │
│ FTP      │ App      │ 20, 21     │ File transfer (20=data, 21=control)  │
│ SMTP     │ App      │ 25         │ Sending emails                        │
│ POP3     │ App      │ 110        │ Receiving emails (download & delete)  │
│ IMAP     │ App      │ 143        │ Receiving emails (server-side)        │
│ DNS      │ App      │ 53         │ Domain Name → IP resolution           │
│ DHCP     │ App      │ 67, 68     │ Auto IP address assignment            │
│ SSH      │ App      │ 22         │ Secure remote login                   │
│ Telnet   │ App      │ 23         │ Remote login (unsecure)               │
│ SNMP     │ App      │ 161        │ Network device management             │
│ MQTT     │ App      │ 1883       │ IoT device communication              │
│ TCP      │ Transport│ —          │ Reliable, connection-oriented         │
│ UDP      │ Transport│ —          │ Fast, connectionless                  │
│ IP       │ Internet │ —          │ Logical addressing, routing           │
│ ICMP     │ Internet │ —          │ Error reporting (Ping uses this!)     │
│ ARP      │ Internet │ —          │ IP → MAC address resolution           │
│ RARP     │ Internet │ —          │ MAC → IP address resolution           │
└──────────┴──────────┴────────────┴──────────────────────────────────────┘
```

---

### 📧 SMTP — THE MOST TRICKY PROTOCOL IN BPSC

```
SMTP = Simple Mail Transfer Protocol
Port = 25
Function = SENDING emails

THE CRITICAL DISTINCTION (appeared in PYQ!):

Scenario 1: YOUR email client (Gmail app) sends email to Gmail server
→ Gmail app is the SMTP CLIENT
→ Gmail server is the SMTP SERVER

Scenario 2: Gmail server sends email to Yahoo server (another mail server)
→ Gmail server acts as SMTP CLIENT
→ Yahoo server acts as SMTP SERVER

⭐ BPSC PYQ TRAP:
"When a mail server sends email to another mail server, it acts as ___?"
Answer: SMTP CLIENT (not SMTP server!)
The SENDING side is always the CLIENT.
The RECEIVING side is always the SERVER.
```

---

### 🌐 DNS — DOMAIN NAME SYSTEM

```
DNS = Phone book of the internet
Function: Converts human-readable domain names → IP addresses

You type: www.google.com
DNS resolves: 142.250.190.46 (IP address)

Without DNS, you'd need to memorize IP addresses for every website!

DNS hierarchy:
Root DNS → TLD DNS (.com, .in, .org) → Authoritative DNS → IP Address
```

---

### 📶 PING — COMMON BPSC TRAP!

```
PING is a network utility that:
✅ Summarizes PACKET LOSS
✅ Reports ROUND-TRIP DELAY (latency)
✅ Uses ICMP protocol (not TCP or UDP)

⚠️ BPSC TRAP: 
Wrong answer given in options: "Packet Internet Groper"
→ This is a BACKRONYM — Ping was NOT originally named this!
→ Ping tests reachability and measures round-trip time

Correct use: "ping google.com" → tells you if google.com is reachable
and how long packets take to travel there and back
```

---

### 📡 MQTT — IoT PROTOCOL (TRE 3.0 asked this!)

```
MQTT = Message Queuing Telemetry Transport
Purpose: Communication protocol for IoT (Internet of Things) devices
Why used for IoT: Lightweight, low bandwidth, works on unreliable networks
Architecture: Publish-Subscribe model (not request-response)

Example: Smart home devices, temperature sensors, industrial machines
→ All use MQTT to communicate with each other

BPSC Fact: IoT short-range wireless = Bluetooth; IoT protocol = MQTT
```

---

### 🔌 SOCKET — WHAT IS IT?

```
A SOCKET = endpoint of an inter-process communication flow across a network

Definition: Combination of IP address + Port number
Example: 192.168.1.1:80 (IP:Port)

One end: Client socket
Other end: Server socket

BPSC PYQ: "Socket is the _____ of inter-process communication"
Answer: ENDPOINT
```

---

## 🌉 SECTION 5: NETWORK DEVICES & TRANSMISSION MEDIA

### Network Devices Summary:

```
┌───────────────┬───────────────┬──────────────────────────────────────┐
│ Device        │ OSI Layer     │ Function                             │
├───────────────┼───────────────┼──────────────────────────────────────┤
│ Hub           │ Layer 1       │ Broadcasts to ALL ports; dumb device │
│ Repeater      │ Layer 1       │ Amplifies/regenerates signal         │
│ Bridge        │ Layer 2       │ Connects two LAN segments            │
│ Switch        │ Layer 2       │ Forwards data using MAC addresses    │
│               │               │ Connects devices in a LAN            │
│ Router        │ Layer 3       │ Routes packets between networks      │
│               │               │ Connects multiple networks           │
│ Gateway       │ Layer 4–7     │ Translates between different protocols│
│ Firewall      │ Layer 3–7     │ Security — filters traffic            │
└───────────────┴───────────────┴──────────────────────────────────────┘

BPSC FACTS:
• Switch connects devices in LAN (not router!)
• Router connects multiple networks together
• NOT a topology: Peer-to-peer (it's a network type, not topology)
```

---

### 📻 TRANSMISSION MEDIA — BPSC COMPARISON TABLE

```
┌──────────────────┬──────────────────────────────────────────────────┐
│ Medium           │ Key Characteristics (BPSC facts)                 │
├──────────────────┼──────────────────────────────────────────────────┤
│ Optical Fiber    │ • HIGHEST transmission speed                     │
│                  │ • BEST resistance to electrical interference     │
│                  │ • Expensive; uses light pulses                   │
│                  │ • Best for long distances                        │
├──────────────────┼──────────────────────────────────────────────────┤
│ Coaxial Cable    │ • Moderate speed and interference resistance     │
│                  │ • Used in cable TV, older networks               │
├──────────────────┼──────────────────────────────────────────────────┤
│ UTP (Unshielded  │ • MOST VULNERABLE to electrical interference    │
│ Twisted Pair)    │ • Cheapest; most widely used in offices         │
│                  │ • Ethernet cables (Cat5, Cat6 are UTP)          │
├──────────────────┼──────────────────────────────────────────────────┤
│ Wireless         │ • Radio waves, microwaves, infrared             │
│                  │ • No physical cable; mobile                     │
│                  │ • Susceptible to interference and eavesdropping │
└──────────────────┴──────────────────────────────────────────────────┘

BPSC PYQ: Sniffers (packet sniffing attacks) prevented by: SWITCHED NETWORK
(Switches send data only to intended recipient; hubs broadcast to all)
```

---

## 🔐 SECTION 6: NETWORK SECURITY BASICS

### Asymmetric Key Cryptography:

```
Also called: Public Key Cryptography

Each person has TWO keys:
• PUBLIC key  → shared openly with everyone
• PRIVATE key → kept secret, never shared

Encryption:  Sender uses RECEIVER'S PUBLIC key to encrypt
Decryption:  Receiver uses their OWN PRIVATE key to decrypt

BPSC PYQ FACT:
"In asymmetric key cryptography, the private key is kept by ___?"
Answer: The RECEIVER (not sender!)

Real example: HTTPS websites use SSL certificates (asymmetric crypto)
```

---

## 🌐 SECTION 7: IMPORTANT INTERNET CONCEPTS

```
WWW (World Wide Web):
= Collection of HYPERLINKED DOCUMENTS on the Internet
≠ The Internet itself (Internet is the infrastructure; WWW is a service on it)

TDM (Time Division Multiplexing):
= Slots divided into FRAMES
= Multiple signals share a channel by taking turns in time slots

VPN (Virtual Private Network):
= Creates encrypted tunnel over public internet
= Makes your traffic appear to come from a different location

NAT (Network Address Translation):
= Maps multiple private IPs to one public IP
= Allows home devices (192.168.x.x) to access the internet with one public IP
```

---

## ⚠️ COMPLETE BPSC TRAPS — NETWORKS (DAY 43 + 44 COMBINED)

| Question Framing | Wrong Option (Trap) | Correct Answer |
|------------------|---------------------|----------------|
| "TCP/IP Host-to-Host = ?" | Network Layer | **Transport Layer** |
| "IPv6 address size?" | 32, 64, or 256 bits | **128 bits** |
| "IPv6 flow label during translation?" | Discarded | **Considered** |
| "Ping stands for?" | Packet Internet Groper | **No full form; tests round-trip delay + packet loss** |
| "SMTP client when servers communicate?" | SMTP Server | **SMTP Client** |
| "IoT communication protocol?" | HTTP | **MQTT** |
| "Socket is _____ of communication?" | Entry point | **Endpoint** |
| "Optical fiber immune to ___?" | Physical damage | **Electrical interference** |
| "UTP is most vulnerable to ___?" | Physical cuts | **Electrical interference** |
| "NOT a topology?" | Star, Bus, Ring | **Peer-to-peer** |
| "Switch vs Router?" | Both connect networks | Switch = **LAN devices**; Router = **multiple networks** |
| "Private key in asymmetric crypto?" | Sender | **Receiver** |
| "Sniffers prevented by?" | Firewall | **Switched network** |
| "TCP/IP layers count?" | 7 or 5 | **4** |
| "Class D IPv4 addresses used for?" | Large organizations | **Multicast** |

---
---

# 💰 PART B — GENERAL STUDIES
# INDIAN ECONOMY: GDP, NATIONAL INCOME, RBI & MONETARY POLICY

---

## 🔑 WHY ECONOMY IS HIGH-SCORING IN BPSC TRE GS SECTION

- Economy questions are **purely factual** — no analysis needed
- Same 20–30 facts repeat across Bihar competitive exams every year
- RBI, GDP, National Income = **2–3 questions guaranteed** per BPSC exam
- Takes less time to prepare but gives big returns

---

## 📊 SECTION 1: NATIONAL INCOME — THE MOST ASKED ECONOMY TOPIC

### What is National Income?
National income is the **total money value of all final goods and services** produced by the residents of a country in a given period (usually one year).

---

### 🔑 KEY CONCEPTS — GDP, GNP, NNP

#### GDP — GROSS DOMESTIC PRODUCT

```
GDP = Total value of all final goods and services produced
      WITHIN the geographical boundaries of a country
      in a given time period (1 year)

KEY WORD: "WITHIN THE COUNTRY" (regardless of who produces it)

Example:
• Toyota factory in India → counted in India's GDP
• Indian IT company working in USA → NOT in India's GDP
• But YES in India's GNP

Formula (Expenditure Method):
GDP = C + I + G + (X - M)
Where:
C = Private Consumption (household spending)
I = Investment (business spending)
G = Government Spending
X = Exports
M = Imports
(X - M) = Net Exports
```

---

#### GNP — GROSS NATIONAL PRODUCT

```
GNP = GDP + Net Factor Income from Abroad (NFIA)

KEY WORD: "BY NATIONALS" (regardless of where they produce)

GNP = GDP + (Income earned by Indians abroad)
             - (Income earned by foreigners in India)

Example:
• Indian software engineer working in USA → in India's GNP but NOT GDP
• American banker working in Mumbai → in India's GDP but NOT GNP

NFIA = Net Factor Income from Abroad
     = Income earned by residents abroad - Income paid to non-residents
```

---

#### NNP — NET NATIONAL PRODUCT

```
NNP = GNP - Depreciation

Depreciation = Wear and tear of capital assets (machines, buildings etc.)
             = Also called "Capital Consumption Allowance"

NNP at Market Price = GNP - Depreciation
NNP at Factor Cost  = NNP at MP - Net Indirect Taxes
                    = Also called NATIONAL INCOME
```

---

### 📐 COMPLETE NATIONAL INCOME HIERARCHY DIAGRAM

```
GDP (Gross Domestic Product)
    + Net Factor Income from Abroad (NFIA)
    ↓
GNP (Gross National Product)
    - Depreciation
    ↓
NNP at Market Price
    - Net Indirect Taxes (Taxes - Subsidies)
    ↓
NNP at Factor Cost = NATIONAL INCOME (NI)
    ÷ Total Population
    ↓
Per Capita Income (PCI)

REMEMBER:
GNP = GDP + NFIA
NNP = GNP - Depreciation
NI  = NNP at Factor Cost
PCI = NI ÷ Population
```

---

### 🏷️ GDP vs GNP vs NNP — QUICK COMPARISON

```
┌─────────────┬────────────────────────────────────────────┐
│  Concept    │  Definition                                │
├─────────────┼────────────────────────────────────────────┤
│ GDP         │ Total production WITHIN country borders    │
│ GNP         │ Total production BY nationals (any country)│
│ NNP         │ GNP minus depreciation                     │
│ National    │ NNP at factor cost (net indirect taxes     │
│ Income      │ deducted)                                   │
│ Per Capita  │ National Income ÷ Population               │
│ Income      │ (measures standard of living)              │
└─────────────┴────────────────────────────────────────────┘
```

---

### 📏 METHODS OF MEASURING NATIONAL INCOME

```
THREE METHODS (all give same result theoretically):

1. OUTPUT METHOD (Product Method)
   = Sum of value added at each stage of production
   = Avoids double counting
   Used for: Agricultural sector, manufacturing

2. INCOME METHOD (Factor Income Method)
   = Sum of all incomes earned by factors of production
   = Wages + Rent + Interest + Profit
   Used for: Service sector, banking

3. EXPENDITURE METHOD (Spending Method)
   = GDP = C + I + G + (X-M)
   = Total spending in the economy
   Used for: National accounts

⚠️ BPSC TRAP: "Transfer payments" (pensions, scholarships) are
NOT included in National Income calculations
(No new production = no income)
```

---

### 📉 IMPORTANT GDP-RELATED TERMS

```
GDP at Market Price vs GDP at Factor Cost:
GDP at Factor Cost = GDP at MP - Net Indirect Taxes
                   = GDP at MP - (Taxes - Subsidies)

Real GDP vs Nominal GDP:
Nominal GDP = GDP calculated at CURRENT year prices
Real GDP    = GDP calculated at BASE YEAR prices (removes inflation effect)

GDP Deflator:
= (Nominal GDP ÷ Real GDP) × 100
= Measures price changes (like inflation measure for entire economy)

GVA (Gross Value Added):
= Value of output - Value of intermediate inputs
GDP = GVA + Net taxes on products
```

---

### 💡 FISCAL DEFICIT, REVENUE DEFICIT & CURRENT ACCOUNT

```
FISCAL DEFICIT = Total expenditure - Total revenue (excluding borrowings)
= Tells how much government needs to BORROW
= If high → government printing money → inflation risk

REVENUE DEFICIT = Revenue expenditure - Revenue receipts
= Deficit in day-to-day operations

CURRENT ACCOUNT DEFICIT (CAD):
= Imports of goods + services > Exports
= India's persistent problem (we import more than we export)

PRIMARY DEFICIT = Fiscal Deficit - Interest payments
```

---

## 🏦 SECTION 2: RESERVE BANK OF INDIA (RBI)

### Basic Facts:
```
Established: 1 April 1935 (based on Hilton-Young Commission recommendations)
Nationalized: 1 January 1949
Headquarter: Mumbai
Governor: Appointed by Central Government
Current Structure: Board of Directors + Governor + 4 Deputy Governors
```

---

### 🔧 FUNCTIONS OF RBI

```
┌─────────────────────────────────────────────────────────┐
│                 RBI FUNCTIONS                           │
├─────────────────────────────────────────────────────────┤
│ 1. MONETARY AUTHORITY                                   │
│    → Formulates and implements monetary policy         │
│    → Controls money supply and credit                  │
├─────────────────────────────────────────────────────────┤
│ 2. ISSUER OF CURRENCY                                   │
│    → Issues all currency notes EXCEPT ₹1 note          │
│    → ₹1 note issued by Ministry of Finance (not RBI)   │
├─────────────────────────────────────────────────────────┤
│ 3. BANKER'S BANK                                        │
│    → All commercial banks maintain accounts with RBI   │
│    → RBI is lender of last resort                      │
├─────────────────────────────────────────────────────────┤
│ 4. BANKER TO GOVERNMENT                                 │
│    → Manages government accounts                       │
│    → Issues government securities                      │
├─────────────────────────────────────────────────────────┤
│ 5. CUSTODIAN OF FOREIGN EXCHANGE                        │
│    → Manages India's foreign exchange reserves         │
│    → Maintains exchange rate stability                 │
├─────────────────────────────────────────────────────────┤
│ 6. REGULATOR OF BANKING SYSTEM                          │
│    → Grants banking licences                           │
│    → Sets prudential norms                             │
└─────────────────────────────────────────────────────────┘

⚠️ BPSC TRAP: "RBI issues ₹1 note"
→ WRONG! ₹1 note is issued by Ministry of Finance.
  It bears signature of Finance Secretary, NOT RBI Governor.
  All OTHER currency notes (₹2 and above) are issued by RBI.
```

---

## 💹 SECTION 3: MONETARY POLICY TOOLS — BPSC GOLDMINE

### What is Monetary Policy?
Policy of the RBI to **control money supply and credit** in the economy to achieve economic goals (price stability, growth, employment).

---

### 🔑 KEY MONETARY POLICY RATES — MEMORIZE ALL!

```
┌──────────────────┬────────────────────────────────────────────────┐
│ Rate/Tool        │ Definition & BPSC Key Fact                     │
├──────────────────┼────────────────────────────────────────────────┤
│ REPO RATE        │ Rate at which RBI LENDS money to commercial     │
│                  │ banks (short term, against securities)         │
│                  │ High Repo → expensive borrowing → less money   │
│                  │ in economy → controls inflation                │
├──────────────────┼────────────────────────────────────────────────┤
│ REVERSE REPO     │ Rate at which RBI BORROWS from commercial banks │
│ RATE             │ (RBI pays this to banks for parking funds)     │
│                  │ Always LOWER than Repo Rate                    │
├──────────────────┼────────────────────────────────────────────────┤
│ CRR              │ Cash Reserve Ratio                             │
│ (Cash Reserve    │ % of deposits banks MUST keep as CASH with RBI │
│  Ratio)          │ High CRR → banks have less money to lend →     │
│                  │ reduces money supply                           │
├──────────────────┼────────────────────────────────────────────────┤
│ SLR              │ Statutory Liquidity Ratio                      │
│ (Statutory       │ % of deposits banks MUST maintain as liquid    │
│  Liquidity Ratio)│ assets (cash, gold, govt securities)           │
│                  │ High SLR → banks can lend less → controls money│
├──────────────────┼────────────────────────────────────────────────┤
│ MSF              │ Marginal Standing Facility                     │
│                  │ Rate at which banks borrow OVERNIGHT from RBI  │
│                  │ Higher than Repo Rate (emergency lending)      │
├──────────────────┼────────────────────────────────────────────────┤
│ BANK RATE        │ Rate at which RBI provides LONG-TERM credit    │
│                  │ to banks (no collateral required)              │
│                  │ Higher than Repo Rate                          │
└──────────────────┴────────────────────────────────────────────────┘
```

---

### 🧠 HOW MONETARY POLICY FIGHTS INFLATION:

```
INFLATION (prices rising too fast) → RBI acts:

RBI raises Repo Rate
    ↓
Borrowing becomes expensive for banks
    ↓
Banks raise interest rates on loans
    ↓
People and businesses borrow less
    ↓
Less spending in economy
    ↓
Demand falls → Prices stop rising → INFLATION CONTROLLED

DEFLATION (prices falling) → RBI REDUCES Repo Rate
(Opposite effect: cheap borrowing → more spending → prices rise)
```

---

### 💵 TYPES OF MONEY — BPSC BASICS

```
M1 = Narrow Money
   = Currency with public + Demand deposits (current + savings accounts)
   = Most liquid

M2 = M1 + Savings deposits with Post Office Savings Banks

M3 = Broad Money (most commonly used)
   = M1 + Time deposits (Fixed Deposits) with banks
   = Used to measure overall money supply

M4 = M3 + All deposits with Post Office Savings Banks

REMEMBER: M1 ⊂ M2 ⊂ M3 ⊂ M4 (each includes the previous)
```

---

## 📈 SECTION 4: TYPES OF ECONOMY & PLANNING

### Mixed Economy:
```
India has a MIXED ECONOMY:
= Both Public sector (government) + Private sector coexist

Features of Indian Economy:
• Developing economy (not developed)
• Agrarian economy (large % in agriculture)
• Labour-intensive
• Dualistic economy (modern + traditional sectors)
• Mixed economy (public + private sectors)

NOT a characteristic of planned economy: "Market determines all prices"
(In planned economy, state determines production; market = free economy)
```

---

### NITI Aayog vs Planning Commission:

```
┌─────────────────────────┬──────────────────────────────────┐
│ PLANNING COMMISSION     │ NITI AAYOG                       │
├─────────────────────────┼──────────────────────────────────┤
│ Established: 1950       │ Established: 1 January 2015      │
│ Abolished: 2014         │ Replaced Planning Commission     │
│ Formulated 5-Year Plans │ No 5-Year Plans                  │
│ Had fund allocation     │ No fund allocation power         │
│ power                   │                                  │
│ Top-down approach       │ Bottom-up approach               │
│ Chairman: PM            │ Chairperson: PM                  │
│ Vice Chairman:          │ CEO: appointed by PM             │
│ full-time position      │                                  │
└─────────────────────────┴──────────────────────────────────┘

NITI Aayog full form: National Institution for Transforming India
```

---

### Five Year Plans — Key Facts:

```
1st Plan (1951–56): Focus on AGRICULTURE (Harrod-Domar model)
2nd Plan (1956–61): Focus on HEAVY INDUSTRY (Mahalanobis model)
3rd Plan (1961–66): Agriculture + Industry (failed due to wars)
4th Plan (1969–74): Growth with stability (Green Revolution impact)
5th Plan (1974–79): Poverty alleviation + self-reliance
6th Plan (1980–85): Infrastructure + poverty removal
7th Plan (1985–90): Food, work, productivity
8th Plan (1992–97): Human resource development (post-LPG reform)
9th Plan (1997–02): Growth with social justice
10th Plan (2002–07): 8% growth target
11th Plan (2007–12): Inclusive growth
12th Plan (2012–17): Faster, sustainable, inclusive growth
Last Five Year Plan: 12th (2012–17)
After 12th Plan: NITI Aayog replaced Planning Commission
```

---

## 📊 SECTION 5: IMPORTANT ECONOMIC TERMS — BPSC GLOSSARY

```
INFLATION: Rise in general price level; fall in purchasing power of money
DEFLATION: Fall in general price level (opposite of inflation)
STAGFLATION: High inflation + high unemployment + low growth (worst scenario)
RECESSION: Negative GDP growth for 2+ consecutive quarters
DEPRESSION: Severe, prolonged recession (e.g., Great Depression 1929)

WPI: Wholesale Price Index (measures wholesale price changes)
CPI: Consumer Price Index (measures retail price changes; used for inflation targeting)
India's inflation target: 4% (±2%) — set by RBI Monetary Policy Committee (MPC)

FDI: Foreign Direct Investment (long-term ownership in foreign company)
FII/FPI: Foreign Institutional/Portfolio Investment (short-term, stocks/bonds)

Balance of Trade: Exports - Imports (goods only)
Balance of Payment (BoP): All economic transactions between India and world

GST (Goods and Services Tax):
→ Implemented: 1 July 2017
→ Replaced: Excise duty, service tax, VAT, and many other taxes
→ CGST: Central GST; SGST: State GST; IGST: Integrated GST (inter-state)
→ 101st Constitutional Amendment Act, 2016
```

---

## ⚠️ BPSC EXAM TRAPS — ECONOMY SECTION

| Common Wrong Answer | Correct Answer |
|---------------------|----------------|
| "RBI issues ₹1 note" | **Ministry of Finance** issues ₹1 note |
| "GNP includes production by foreigners in India" | GNP = production **BY nationals** anywhere |
| "GDP includes Indian production abroad" | GDP = production **within country** only |
| "Repo rate = rate RBI borrows from banks" | Repo = RBI **lends**; Reverse Repo = RBI **borrows** |
| "CRR = government securities" | CRR = **cash** kept with RBI; SLR = liquid assets |
| "NITI Aayog was formed in 2014" | NITI Aayog formed on **1 January 2015** |
| "India's economy is capitalist" | India has **Mixed economy** |
| "NNP = GDP - Depreciation" | NNP = **GNP** - Depreciation |
| "Fiscal deficit = revenue deficit" | They are different! Fiscal = total; Revenue = current ops |
| "GST implemented in 2016" | GST implemented **1 July 2017** |
| "Planning Commission still exists" | Planning Commission **abolished 2014**; replaced by NITI Aayog |

---

## 🏆 TOPPER LEVEL FACTS — TODAY'S GS

1. GDP = **C + I + G + (X–M)** — must memorize this formula
2. **GNP = GDP + NFIA** (Net Factor Income from Abroad)
3. **NNP = GNP – Depreciation**; NNP at factor cost = National Income
4. RBI established **1 April 1935**; nationalized **1 January 1949**
5. **Repo Rate** = RBI lends to banks; **Reverse Repo** = RBI borrows from banks
6. **CRR** = % of deposits kept as cash with RBI; **SLR** = % kept as liquid assets
7. **₹1 note** issued by Ministry of Finance, NOT RBI
8. India inflation target = **4% (±2%)** managed by MPC (Monetary Policy Committee)
9. **NITI Aayog** replaced Planning Commission on 1 January 2015
10. Last Five Year Plan = **12th Plan (2012–17)**
11. **GST** = 101st Constitutional Amendment, implemented **1 July 2017**
12. **M3** = Broad Money = most used measure of money supply

---
---

# 📝 PRACTICE QUESTIONS

## ⚠️ IMPORTANT INSTRUCTION:
### Attempt ALL 50 questions first. Answers are given ONLY AFTER ALL 50 QUESTIONS.
### Cover the answer section completely while solving. Test yourself honestly!

---

# 🖥️ SECTION A: COMPUTER SCIENCE — TCP/IP, IPv4/IPv6, PROTOCOLS
## 25 MCQs | BPSC TRE Style | 5 Options Each

---

**Q1.** The TCP/IP model was originally developed by which organization?

(A) ISO (International Organization for Standardization)  
(B) IEEE  
(C) US Department of Defense (DARPA)  
(D) More than one of the above  
(E) None of the above  

---

**Q2.** How many layers does the TCP/IP model have?

(A) 5  
(B) 7  
(C) 4  
(D) More than one of the above  
(E) None of the above  

---

**Q3.** The "Host-to-Host" layer of the TCP/IP model corresponds to which layer of the OSI model?

(A) Network Layer  
(B) Session Layer  
(C) Transport Layer  
(D) More than one of the above  
(E) None of the above  

---

**Q4.** Which of the following protocols belong to the Application layer of the TCP/IP model?

(A) SMTP  
(B) FTP  
(C) DNS  
(D) More than one of the above  
(E) None of the above  

---

**Q5.** IPv4 addresses are how many bits in size?

(A) 16 bits  
(B) 64 bits  
(C) 32 bits  
(D) More than one of the above  
(E) None of the above  

---

**Q6.** IPv6 addresses are how many bits in size?

(A) 32 bits  
(B) 64 bits  
(C) 128 bits  
(D) More than one of the above  
(E) None of the above  

---

**Q7.** During IPv6 header translation, what happens to the flow label field?

(A) It is discarded  
(B) It is set to zero  
(C) It is considered  
(D) More than one of the above  
(E) None of the above  

---

**Q8.** Which of the following is a private IP address range?

(A) 172.16.0.0 – 172.31.255.255  
(B) 192.168.0.0 – 192.168.255.255  
(C) 10.0.0.0 – 10.255.255.255  
(D) More than one of the above  
(E) None of the above  

---

**Q9.** The subnet mask identifies which portion of an IP address?

(A) The host portion  
(B) The network portion  
(C) The class of the address  
(D) More than one of the above  
(E) None of the above  

---

**Q10.** When a mail server sends an email to another mail server, the sending server acts as:

(A) SMTP Server  
(B) SMTP Host  
(C) SMTP Client  
(D) More than one of the above  
(E) None of the above  

---

**Q11.** The PING utility summarizes which of the following?

(A) Packet loss  
(B) Round-trip delay  
(C) Bandwidth consumed  
(D) More than one of the above  
(E) None of the above  

---

**Q12.** MQTT protocol is primarily used for communication between:

(A) Web browsers and servers  
(B) Mail servers  
(C) IoT (Internet of Things) devices  
(D) More than one of the above  
(E) None of the above  

---

**Q13.** A SOCKET is defined as:

(A) A type of network cable  
(B) The entry point of an inter-process communication  
(C) The endpoint of an inter-process communication flow  
(D) More than one of the above  
(E) None of the above  

---

**Q14.** Which IPv4 address class is used for MULTICAST communication?

(A) Class A  
(B) Class C  
(C) Class D  
(D) More than one of the above  
(E) None of the above  

---

**Q15.** Which transmission medium offers the HIGHEST transmission speed and is best for electrical interference?

(A) Coaxial cable  
(B) UTP (Unshielded Twisted Pair)  
(C) Optical Fiber  
(D) More than one of the above  
(E) None of the above  

---

**Q16.** UTP (Unshielded Twisted Pair) cable is MOST vulnerable to:

(A) Physical cutting  
(B) Water damage  
(C) Electrical interference  
(D) More than one of the above  
(E) None of the above  

---

**Q17.** In asymmetric key cryptography, the PRIVATE key is kept by:

(A) The sender  
(B) The network administrator  
(C) The receiver  
(D) More than one of the above  
(E) None of the above  

---

**Q18.** Packet sniffing attacks can be prevented by using which type of network?

(A) Wireless network  
(B) Hub-based network  
(C) Switched network  
(D) More than one of the above  
(E) None of the above  

---

**Q19.** Which of the following correctly maps OSI layers to the TCP/IP Application layer?

(A) Only OSI Application Layer (Layer 7)  
(B) OSI Layers 6 and 7 (Application and Presentation)  
(C) OSI Layers 5, 6, and 7 (Session, Presentation, and Application)  
(D) More than one of the above  
(E) None of the above  

---

**Q20.** The address 127.0.0.1 in IPv4 is used for:

(A) Default gateway  
(B) Broadcast address  
(C) Loopback (testing your own computer)  
(D) More than one of the above  
(E) None of the above  

---

**Q21.** Which device connects multiple networks together and operates at the Network Layer?

(A) Switch  
(B) Hub  
(C) Router  
(D) More than one of the above  
(E) None of the above  

---

**Q22.** In TDM (Time Division Multiplexing), slots are divided into:

(A) Packets  
(B) Frames  
(C) Segments  
(D) More than one of the above  
(E) None of the above  

---

**Q23.** WWW (World Wide Web) is best defined as:

(A) The internet itself  
(B) A collection of hyperlinked documents on the internet  
(C) The physical cable infrastructure of the internet  
(D) More than one of the above  
(E) None of the above  

---

**Q24.** Which of the following is NOT a topology in computer networks?

(A) Star topology  
(B) Ring topology  
(C) Peer-to-peer  
(D) More than one of the above  
(E) None of the above  

---

**Q25.** The DNS (Domain Name System) is responsible for:

(A) Converting IP addresses to MAC addresses  
(B) Converting domain names to IP addresses  
(C) Encrypting web traffic  
(D) More than one of the above  
(E) None of the above  

---

---

# 🇮🇳 SECTION B: GENERAL STUDIES — INDIAN ECONOMY
## 25 MCQs | BPSC TRE Style | 5 Options Each

---

**Q26.** GDP is defined as the total value of all final goods and services produced:

(A) By nationals of a country anywhere in the world  
(B) Within the geographical boundaries of a country  
(C) Only by the government sector of a country  
(D) More than one of the above  
(E) None of the above  

---

**Q27.** GNP (Gross National Product) is calculated as:

(A) GDP + Depreciation  
(B) GDP + Net Factor Income from Abroad (NFIA)  
(C) GDP - Net Indirect Taxes  
(D) More than one of the above  
(E) None of the above  

---

**Q28.** NNP (Net National Product) is calculated as:

(A) GDP - Depreciation  
(B) GNP + Depreciation  
(C) GNP - Depreciation  
(D) More than one of the above  
(E) None of the above  

---

**Q29.** The Reserve Bank of India was established in which year?

(A) 1947  
(B) 1949  
(C) 1935  
(D) More than one of the above  
(E) None of the above  

---

**Q30.** The ₹1 (One Rupee) note in India is issued by:

(A) Reserve Bank of India  
(B) State Bank of India  
(C) Ministry of Finance, Government of India  
(D) More than one of the above  
(E) None of the above  

---

**Q31.** The Repo Rate is the rate at which:

(A) RBI borrows money from commercial banks  
(B) Commercial banks lend money to customers  
(C) RBI lends money to commercial banks  
(D) More than one of the above  
(E) None of the above  

---

**Q32.** CRR (Cash Reserve Ratio) refers to the percentage of deposits that commercial banks must:

(A) Invest in government securities  
(B) Keep as cash reserves with RBI  
(C) Lend to priority sectors  
(D) More than one of the above  
(E) None of the above  

---

**Q33.** When RBI increases the Repo Rate, what is the expected effect on the economy?

(A) Inflation increases  
(B) Money supply increases  
(C) Borrowing becomes expensive and money supply decreases  
(D) More than one of the above  
(E) None of the above  

---

**Q34.** NITI Aayog was established on:

(A) 1 January 2014  
(B) 1 January 2015  
(C) 15 August 2014  
(D) More than one of the above  
(E) None of the above  

---

**Q35.** The GDP formula using the Expenditure Method is:

(A) GDP = C + I + G + (X + M)  
(B) GDP = C + I + G + (X - M)  
(C) GDP = GNP - NFIA  
(D) More than one of the above  
(E) None of the above  

---

**Q36.** Which of the following is NOT included in National Income calculation?

(A) Wages paid to workers  
(B) Profits earned by businesses  
(C) Transfer payments (pensions, scholarships)  
(D) More than one of the above  
(E) None of the above  

---

**Q37.** India's current monetary policy inflation target is:

(A) 2% (±1%)  
(B) 4% (±2%)  
(C) 6% (±1%)  
(D) More than one of the above  
(E) None of the above  

---

**Q38.** GST (Goods and Services Tax) was implemented in India on:

(A) 1 April 2017  
(B) 1 January 2017  
(C) 1 July 2017  
(D) More than one of the above  
(E) None of the above  

---

**Q39.** The last Five Year Plan in India was:

(A) 11th Five Year Plan (2007–12)  
(B) 12th Five Year Plan (2012–17)  
(C) 10th Five Year Plan (2002–07)  
(D) More than one of the above  
(E) None of the above  

---

**Q40.** Stagflation is characterized by:

(A) High inflation + high economic growth  
(B) Low inflation + high unemployment  
(C) High inflation + high unemployment + low growth  
(D) More than one of the above  
(E) None of the above  

---

**Q41.** Which of the following correctly describes India's economy?

(A) Capitalist economy  
(B) Socialist economy  
(C) Mixed economy  
(D) More than one of the above  
(E) None of the above  

---

**Q42.** M3 (Broad Money) includes:

(A) Only currency with the public  
(B) M1 + Time deposits with banks  
(C) Only demand deposits  
(D) More than one of the above  
(E) None of the above  

---

**Q43.** The SLR (Statutory Liquidity Ratio) requires banks to maintain a portion of their deposits as:

(A) Cash only  
(B) Government bonds only  
(C) Liquid assets (cash, gold, or approved securities)  
(D) More than one of the above  
(E) None of the above  

---

**Q44.** Per Capita Income is calculated as:

(A) GDP ÷ Population  
(B) National Income ÷ Population  
(C) GNP ÷ Population  
(D) More than one of the above  
(E) None of the above  

---

**Q45.** The GDP Deflator is used to:

(A) Calculate the trade deficit  
(B) Convert Nominal GDP to Real GDP (measure overall price changes)  
(C) Measure foreign exchange reserves  
(D) More than one of the above  
(E) None of the above  

---

**Q46.** The Reverse Repo Rate is always:

(A) Higher than the Repo Rate  
(B) Equal to the Repo Rate  
(C) Lower than the Repo Rate  
(D) More than one of the above  
(E) None of the above  

---

**Q47.** The Second Five Year Plan (1956–61) focused primarily on:

(A) Agriculture  
(B) Heavy Industry (Mahalanobis model)  
(C) Human resource development  
(D) More than one of the above  
(E) None of the above  

---

**Q48.** GST was introduced through which Constitutional Amendment?

(A) 100th Amendment  
(B) 101st Amendment  
(C) 102nd Amendment  
(D) More than one of the above  
(E) None of the above  

---

**Q49.** Which of the following correctly identifies the Fiscal Deficit?

(A) Revenue Expenditure - Revenue Receipts  
(B) Total Expenditure - Revenue Receipts only  
(C) Total Expenditure - Total Revenue (excluding borrowings)  
(D) More than one of the above  
(E) None of the above  

---

**Q50.** The Reserve Bank of India was nationalized in which year?

(A) 1935  
(B) 1947  
(C) 1949  
(D) More than one of the above  
(E) None of the above  

---

---

# ✅ ANSWER KEY
## (Scroll here ONLY after attempting all 50 questions!)

---

### 🖥️ CS SECTION — ANSWER KEY WITH EXPLANATIONS

| Q# | Answer | Explanation |
|----|--------|-------------|
| 1 | **(C)** | TCP/IP was developed by **US Department of Defense (DARPA)** in 1970s for ARPANET. ISO developed OSI. |
| 2 | **(C)** | TCP/IP has **4 layers**: Application, Transport, Internet, Network Access. OSI has 7 layers. |
| 3 | **(C)** | TCP/IP "Host-to-Host" = OSI **Transport Layer**. This is the single most tested mapping in BPSC Networks. |
| 4 | **(D)** | SMTP, FTP, and DNS are ALL at the Application layer of TCP/IP. Option D = More than one = correct. |
| 5 | **(C)** | IPv4 = **32 bits**. Format: 4 octets (groups of 8 bits) in dotted decimal. |
| 6 | **(C)** | IPv6 = **128 bits**. This is a direct PYQ. Wrong options include 32, 64, 256 bits. |
| 7 | **(C)** | IPv6 flow label is **considered** (not discarded) during header translation. Direct PYQ from TRE 3.0. |
| 8 | **(D)** | ALL THREE are private IP ranges: 10.x.x.x (Class A), 172.16–31.x.x (Class B), 192.168.x.x (Class C). D = correct. |
| 9 | **(B)** | Subnet mask identifies the **NETWORK PORTION** of an IP address. This is a direct PYQ fact. |
| 10 | **(C)** | When mail server sends to another, sending server = **SMTP Client**. The sender is always the client. |
| 11 | **(D)** | Ping summarizes BOTH packet loss AND round-trip delay. Both A and B are correct → D = More than one. |
| 12 | **(C)** | MQTT = IoT device communication protocol. Lightweight for devices with limited bandwidth. |
| 13 | **(C)** | Socket = **endpoint** of inter-process communication flow. Not "entry point" — endpoint means BOTH sides. |
| 14 | **(C)** | Class **D** (224–239) = reserved for multicast. Class E = experimental/reserved. |
| 15 | **(C)** | **Optical Fiber** = highest transmission speed + best resistance to electrical interference. |
| 16 | **(C)** | UTP = most vulnerable to **electrical interference** because it has no shielding around the wires. |
| 17 | **(C)** | In asymmetric cryptography, private key is kept by the **receiver**. Public key = shared with everyone. |
| 18 | **(C)** | **Switched network** prevents sniffers because switches send data only to intended recipient (unlike hubs). |
| 19 | **(C)** | TCP/IP Application = OSI **Application + Presentation + Session** (layers 7+6+5). All three merge. |
| 20 | **(C)** | 127.0.0.1 = **loopback** address. Used to test network stack of your own computer. |
| 21 | **(C)** | **Router** connects multiple networks together at Network Layer (Layer 3). Switch connects LAN devices. |
| 22 | **(B)** | In TDM, slots are divided into **frames**. Each frame contains one slot from each channel. |
| 23 | **(B)** | WWW = **collection of hyperlinked documents** on the internet. The internet is the infrastructure; WWW is a service. |
| 24 | **(C)** | **Peer-to-peer** is a network TYPE (architecture), NOT a topology. Star, Ring, Bus, Mesh = topologies. |
| 25 | **(B)** | DNS converts **domain names → IP addresses** (e.g., google.com → 142.250.190.46). |

---

### 🇮🇳 GS SECTION — ANSWER KEY WITH EXPLANATIONS

| Q# | Answer | Explanation |
|----|--------|-------------|
| 26 | **(B)** | GDP = production **within the geographical boundaries** of a country. GNP = by nationals anywhere. |
| 27 | **(B)** | **GNP = GDP + NFIA** (Net Factor Income from Abroad). NFIA = income by Indians abroad - income by foreigners in India. |
| 28 | **(C)** | **NNP = GNP - Depreciation**. NOT GDP - Depreciation. Common trap in exam. |
| 29 | **(C)** | RBI was established on **1 April 1935** based on Hilton-Young Commission. Nationalized in 1949. |
| 30 | **(C)** | ₹1 note is issued by **Ministry of Finance** (not RBI). It carries Finance Secretary's signature. All other notes = RBI. |
| 31 | **(C)** | **Repo Rate** = rate at which **RBI lends** money to commercial banks. Reverse Repo = RBI borrows. |
| 32 | **(B)** | **CRR** = percentage banks must keep as **cash reserves with RBI**. SLR = liquid assets (gold, govt securities). |
| 33 | **(C)** | Higher Repo Rate → expensive borrowing → banks lend less → **money supply decreases → inflation controlled**. |
| 34 | **(B)** | NITI Aayog was established on **1 January 2015** (not 2014). Common exam trap — confuse with abolition of Planning Commission (2014). |
| 35 | **(B)** | GDP = **C + I + G + (X - M)**. X = Exports, M = Imports. Net Exports = X-M (not X+M). |
| 36 | **(C)** | **Transfer payments** (pensions, unemployment benefits, scholarships) are NOT included — no new production occurs. |
| 37 | **(B)** | India's inflation target = **4% (±2%)**, i.e., 2% to 6% range. Set by Monetary Policy Committee (MPC). |
| 38 | **(C)** | GST implemented **1 July 2017** in India. One of the biggest tax reforms. Not April 2017. |
| 39 | **(B)** | Last Five Year Plan = **12th Plan (2012–17)**. After that, Planning Commission abolished, NITI Aayog formed. |
| 40 | **(C)** | Stagflation = **high inflation + high unemployment + low/stagnant growth** simultaneously. Worst economic scenario. |
| 41 | **(C)** | India has a **mixed economy** — both public sector and private sector coexist. Not purely capitalist or socialist. |
| 42 | **(B)** | **M3 (Broad Money) = M1 + Time deposits (Fixed Deposits)**. M3 is the most commonly referenced money supply measure. |
| 43 | **(C)** | SLR = banks must maintain **liquid assets** (cash + gold + approved government securities). NOT just cash (that's CRR). |
| 44 | **(B)** | Per Capita Income = **National Income ÷ Population**. National Income = NNP at factor cost. |
| 45 | **(B)** | GDP Deflator = (Nominal GDP ÷ Real GDP) × 100. Used to **convert nominal to real** by removing price level effect. |
| 46 | **(C)** | Reverse Repo Rate is **always LOWER** than Repo Rate. It's the rate RBI pays banks for parking funds with RBI. |
| 47 | **(B)** | 2nd Five Year Plan (1956–61) focused on **Heavy Industry** based on **Mahalanobis model** (Prof. P.C. Mahalanobis). |
| 48 | **(B)** | GST was introduced by the **101st Constitutional Amendment Act, 2016** (implemented 1 July 2017). |
| 49 | **(C)** | **Fiscal Deficit = Total Expenditure - Total Revenue (excluding borrowings)**. Revenue Deficit = revenue exp. - revenue receipts. |
| 50 | **(C)** | RBI was nationalized on **1 January 1949**. Established 1935, nationalized 1949, HQ Mumbai. |

---

---

## 📊 SCORE YOURSELF

### CS Section (25 Questions):
- **23–25 correct → Topper Level ✅**
- **19–22 correct → Good — re-read IPv6 & Protocol section**
- **Below 19 → Re-study TCP/IP mapping + private IP ranges**

### GS Section (25 Questions):
- **23–25 correct → Topper Level ✅**
- **19–22 correct → Revise GDP formulae and RBI rates**
- **Below 19 → Re-read National Income hierarchy and RBI tools**

---

## 🔮 PYQ PATTERN ANALYSIS — WHAT BPSC HAS ASKED

### CS PYQs on TCP/IP & Networks (from TRE 1.0, 2.0, 3.0):
1. TCP/IP "Host-to-Host" layer = **Transport Layer** ← asked in 2+ papers
2. IPv6 = **128 bits** (wrong options: 32, 64, 256 bits) ← asked TRE 2.0
3. IPv6 flow label during header translation = **Considered** ← TRE 3.0
4. Socket = **endpoint** of inter-process communication ← TRE 2.0
5. SMTP client when mail servers communicate = **Sending server** ← TRE 1.0

### GS PYQs on Economy (from BPSC + Bihar STET pattern):
1. RBI established = **1935**, nationalized = **1949** ← every exam
2. ₹1 note issued by = **Ministry of Finance** ← repeated trap
3. Repo Rate = RBI **lends** (Reverse Repo = borrows) ← every exam
4. NITI Aayog formed = **1 January 2015** ← recent exams
5. GDP formula = **C + I + G + (X-M)** ← every economy question set

---

## 🌙 NIGHT REVISION — 5 BULLET POINT SUMMARY

### CS (Write from memory before sleeping):
1. TCP/IP = 4 layers: Application → Transport (Host-to-Host) → Internet → Network Access
2. IPv4 = 32 bits (dotted decimal); IPv6 = 128 bits (hexadecimal, flow label = considered)
3. Private IPs: 10.x.x.x, 172.16-31.x.x, 192.168.x.x; Subnet mask = identifies network portion
4. SMTP: sending server to another = SMTP CLIENT; MQTT = IoT; Ping = packet loss + round-trip delay
5. Optical Fiber = highest speed + best for interference; UTP = most vulnerable; Switch = prevents sniffers

### GS (Write from memory before sleeping):
1. GDP = within country; GNP = GDP + NFIA; NNP = GNP - Depreciation; NI = NNP at factor cost
2. RBI: est. 1935, nationalized 1949; issues all notes except ₹1 (Finance Ministry issues ₹1)
3. Repo Rate = RBI lends to banks; Reverse Repo = RBI borrows; CRR = cash; SLR = liquid assets
4. NITI Aayog replaced Planning Commission on 1 January 2015; Last FYP = 12th (2012-17)
5. GST = 101st Amendment, implemented 1 July 2017; India inflation target = 4% (±2%)

---

## 📅 DAY 45 PREVIEW

**CS Topic:** IP Addressing Deep Dive + Subnetting + Network Topologies  
**GS Topic:** Biology — Human Immune System + Vitamins & Deficiency Diseases

Come back tomorrow and say: **"Day-45"** — your personal mentor is ready! 🎯

---

*Day 44 Complete | Phase 1 Week 7 | Computer Networks Continues*
*Consistent daily effort = Topper Rank. Every concept mastered today = marks secured in TRE 4.0! 💪*
