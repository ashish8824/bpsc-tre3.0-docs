# 📅 BPSC TRE 4.0 — DAY 43
## CS Topic: OSI Model — 7 Layers (Computer Networks Unit Begins)
## GS Topic: Indian Polity — Parliament Structure (Lok Sabha + Rajya Sabha)
### 🎯 Target: 130+/150 | TOP 50 RANK

---

> **Topper Benchmark:** Computer Networks contributes ~10% of the CS paper (~8–10 questions in TRE 4.0).
> OSI Model alone has appeared in EVERY paper. Mastering this day = guaranteed 3–4 marks secured.
> GS Polity (Parliament) is a high-scoring, consistently repeating section — target 4–5 marks here.

---

## ⏰ TODAY'S STUDY SCHEDULE

| Slot | Duration | Activity |
|------|----------|----------|
| Morning | 1.5 hrs | CS: OSI Model — full concept mastery |
| Afternoon | 1 hr | GS: Parliament Structure — Lok Sabha + Rajya Sabha |
| Evening | 1 hr | Solve all 50 MCQs (25 CS + 25 GS) |
| Night | 30 min | Write your own summary — 5 bullet points each |

---

---

# 🖥️ PART A — COMPUTER SCIENCE
# OSI MODEL — 7 LAYERS OF NETWORKING

---

## 🔑 WHY THIS TOPIC MATTERS FOR BPSC TRE 4.0

| Exam | OSI/Network Questions |
|------|----------------------|
| TRE 1.0 | 3–4 questions on OSI/TCP-IP/Protocols |
| TRE 2.0 | 4–5 questions on OSI/IP/Protocols |
| TRE 3.0 | 3–4 questions on OSI layers + data units |
| **TRE 4.0 Expected** | **4–6 questions (Networks = 10% of paper)** |

---

## 🌐 WHAT IS THE OSI MODEL?

**OSI = Open Systems Interconnection** model.

It is a **conceptual framework** (NOT an actual protocol) developed by the **International Organization for Standardization (ISO)** in **1984** to standardize how different computer systems communicate over a network.

Think of it as a **7-floor building** — each floor (layer) has a specific job, and each floor talks only to the floor directly above and below it.

### 🏗️ REAL-WORLD ANALOGY:
Imagine sending a letter internationally:
```
You write the letter           → APPLICATION LAYER
Put in an envelope            → PRESENTATION LAYER
Address the envelope           → SESSION LAYER  
Go to the post office          → TRANSPORT LAYER
Post office selects route      → NETWORK LAYER
Mail sorted in local depot     → DATA LINK LAYER
Physical delivery by postman   → PHYSICAL LAYER
```

---

## 📐 THE 7 LAYERS — COMPLETE ASCII DIAGRAM

```
┌─────────────────────────────────────────────────────────────┐
│                    OSI MODEL — 7 LAYERS                     │
├────────┬──────────────────┬──────────┬──────────────────────┤
│ Layer# │  Layer Name      │  PDU     │   Key Protocols      │
├────────┼──────────────────┼──────────┼──────────────────────┤
│   7    │  APPLICATION     │  Data    │  HTTP, FTP, SMTP,    │
│        │                  │          │  DNS, DHCP, Telnet   │
├────────┼──────────────────┼──────────┼──────────────────────┤
│   6    │  PRESENTATION    │  Data    │  SSL/TLS, JPEG,      │
│        │                  │          │  MPEG, ASCII, GIF    │
├────────┼──────────────────┼──────────┼──────────────────────┤
│   5    │  SESSION         │  Data    │  NetBIOS, RPC,       │
│        │                  │          │  PPTP, SAP           │
├────────┼──────────────────┼──────────┼──────────────────────┤
│   4    │  TRANSPORT       │ Segment  │  TCP, UDP, SCTP      │
├────────┼──────────────────┼──────────┼──────────────────────┤
│   3    │  NETWORK         │  Packet  │  IP, ICMP, OSPF,     │
│        │                  │          │  RIP, BGP            │
├────────┼──────────────────┼──────────┼──────────────────────┤
│   2    │  DATA LINK       │  Frame   │  Ethernet, Wi-Fi,    │
│        │                  │          │  MAC, LLC, PPP       │
├────────┼──────────────────┼──────────┼──────────────────────┤
│   1    │  PHYSICAL        │   Bit    │  Ethernet cable,     │
│        │                  │          │  Fiber, Radio waves  │
└────────┴──────────────────┴──────────┴──────────────────────┘

SENDER                                             RECEIVER
  │                                                    ▲
  ▼                                                    │
[7] Application ──────────────────────────────── Application [7]
[6] Presentation ─────────────────────────────── Presentation [6]
[5] Session ──────────────────────────────────── Session [5]
[4] Transport ────────────────────────────────── Transport [4]
[3] Network ──────────────────────────────────── Network [3]
[2] Data Link ────────────────────────────────── Data Link [2]
[1] Physical ════════[ Physical Medium ]═════════ Physical [1]
         (Cables, Wireless, Fiber, Coaxial)
```

---

## 🧠 MEMORY TRICKS — NEVER FORGET THE 7 LAYERS

### ⬇️ Top to Bottom (Layer 7 → Layer 1):
```
"All People Seem To Need Data Processing"
 A     P       S     T     N     D     P
 Application → Presentation → Session → Transport → Network → Data Link → Physical
```

### ⬆️ Bottom to Top (Layer 1 → Layer 7):
```
"Please Do Not Throw Sausage Pizza Away"
 P       D    N    T      S       P     A
 Physical → Data Link → Network → Transport → Session → Presentation → Application
```

### 🎯 PDU Memory Trick:
```
"All People Should Try New Different Bubbly"
 Application = Data
 Presentation = Data
 Session = Data
 Transport = Segment
 Network = Packet (Navigate Packets)
 Data Link = Frame (Data Links Frames)
 Physical = Bit (Physically tiny Bits)
```

---

## 📋 LAYER-BY-LAYER DETAILED EXPLANATION

### LAYER 7 — APPLICATION LAYER
```
┌─────────────────────────────────────┐
│           APPLICATION               │
│  Closest to the USER                │
│  User interacts with this layer     │
│  PDU: Data                          │
│  Protocols: HTTP, HTTPS, FTP,       │
│             SMTP, DNS, DHCP,        │
│             Telnet, SNMP            │
└─────────────────────────────────────┘
```
- **Function:** Provides network services **directly to end-user applications**
- Web browser uses HTTP → Application Layer
- Email client uses SMTP → Application Layer
- **BPSC Trap:** Application layer is NOT only for applications — it provides interface for user programs to access network

---

### LAYER 6 — PRESENTATION LAYER
```
┌─────────────────────────────────────┐
│           PRESENTATION              │
│  "Translator" of the OSI model      │
│  PDU: Data                          │
│  Functions: Encryption/Decryption,  │
│             Compression,            │
│             Translation/Encoding    │
│  Protocols: SSL, TLS, JPEG, GIF,    │
│             MPEG, ASCII, EBCDIC     │
└─────────────────────────────────────┘
```
- **Function:** Translates data formats, compresses data, encrypts/decrypts
- When you open a JPEG image — Presentation layer handles format
- HTTPS encryption (SSL/TLS) — Presentation layer
- **Key Fact:** Also called **"Syntax Layer"** — handles syntax of data

---

### LAYER 5 — SESSION LAYER
```
┌─────────────────────────────────────┐
│             SESSION                 │
│  "Manager" of connections           │
│  PDU: Data                          │
│  Functions: Establishes, Manages,   │
│             and Terminates sessions │
│  Protocols: NetBIOS, RPC, SAP,      │
│             PPTP, NFS               │
└─────────────────────────────────────┘
```
- **Function:** Establishes, maintains, and terminates communication sessions
- When you log in to a website — Session layer manages login session
- **Synchronization:** Adds checkpoints (synchronization points) in data stream
- **Dialog control:** Half-duplex vs Full-duplex

---

### LAYER 4 — TRANSPORT LAYER ⭐ (Most asked in BPSC)
```
┌─────────────────────────────────────┐
│            TRANSPORT                │
│  "Heart" of OSI model               │
│  PDU: SEGMENT                       │
│  Functions: Segmentation,           │
│             Reassembly,             │
│             Flow control,           │
│             Error control,          │
│             Multiplexing            │
│  Protocols: TCP, UDP, SCTP          │
└─────────────────────────────────────┘
```
- **Function:** End-to-end communication, reliability, flow control
- TCP (Transmission Control Protocol) = **Connection-oriented, Reliable**
- UDP (User Datagram Protocol) = **Connectionless, Unreliable, Fast**
- **Port numbers** are used at this layer
- **BPSC Key Fact:** TCP/IP model's "Host-to-Host" layer = OSI **Transport layer**

#### TCP vs UDP Comparison:
```
┌──────────────────┬──────────────────────┬──────────────────────┐
│   Feature        │        TCP           │        UDP           │
├──────────────────┼──────────────────────┼──────────────────────┤
│ Connection       │ Connection-oriented  │ Connectionless       │
│ Reliability      │ Reliable             │ Unreliable           │
│ Speed            │ Slower               │ Faster               │
│ Error check      │ Yes                  │ Minimal              │
│ Handshake        │ 3-way handshake      │ No handshake         │
│ Use case         │ File transfer,       │ Video streaming,     │
│                  │ Email, Web           │ DNS, Gaming, VoIP    │
│ Data unit        │ Segment              │ Datagram             │
└──────────────────┴──────────────────────┴──────────────────────┘
```

#### TCP Three-Way Handshake:
```
CLIENT                              SERVER
  │                                    │
  │──── SYN (synchronize) ──────────→ │
  │                                    │
  │ ←─── SYN-ACK (sync+acknowledge) ──│
  │                                    │
  │──── ACK (acknowledge) ──────────→ │
  │                                    │
  │════ Connection Established ════════│
```

---

### LAYER 3 — NETWORK LAYER ⭐ (Critical for BPSC)
```
┌─────────────────────────────────────┐
│             NETWORK                 │
│  "Postman" of OSI model             │
│  PDU: PACKET                        │
│  Functions: Logical addressing,     │
│             Routing,                │
│             Forwarding,             │
│             Fragmentation           │
│  Protocols: IP (v4, v6), ICMP,      │
│             OSPF, RIP, BGP, ARP     │
│  Device: ROUTER                     │
└─────────────────────────────────────┘
```
- **Function:** Determines the best path for data from source to destination
- Uses **IP addresses** (logical addressing)
- **ROUTER** operates at Network layer
- **BPSC Key Fact:** Network layer = routing AND forwarding of packets

---

### LAYER 2 — DATA LINK LAYER ⭐ (Most complex — sublayers!)
```
┌─────────────────────────────────────┐
│           DATA LINK                 │
│  "Traffic Police" of networks       │
│  PDU: FRAME                         │
│  Functions: Physical addressing,    │
│             Error detection,        │
│             Flow control,           │
│             Access control          │
│  Protocols: Ethernet, Wi-Fi,        │
│             PPP, HDLC               │
│  Device: SWITCH, BRIDGE             │
└─────────────────────────────────────┘
```

#### Data Link Layer has TWO SUBLAYERS:
```
┌─────────────────────────────────────────────────────┐
│              DATA LINK LAYER                        │
│  ┌─────────────────────────────────────────────┐   │
│  │  LLC — Logical Link Control  (UPPER sublayer)│   │
│  │  • Error detection & correction              │   │
│  │  • Flow control                              │   │
│  │  • Provides interface to Network Layer       │   │
│  ├─────────────────────────────────────────────┤   │
│  │  MAC — Media Access Control  (LOWER sublayer)│   │
│  │  • Physical (MAC) addressing                 │   │
│  │  • Controls access to transmission medium    │   │
│  │  • Functions depend on medium type           │   │
│  └─────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────┘
```

> **🎯 BPSC PYQ TRAP:** 
> - LLC = **Upper** sublayer of Data Link Layer
> - MAC = **Lower** sublayer of Data Link Layer
> - MAC "performs functions depending on medium type" ← exact PYQ wording

---

### LAYER 1 — PHYSICAL LAYER
```
┌─────────────────────────────────────┐
│             PHYSICAL                │
│  "Cable/Wire" layer                 │
│  PDU: BIT (0 and 1)                 │
│  Functions: Bit transmission,       │
│             Signal encoding,        │
│             Cable types,            │
│             Electrical/optical specs│
│  Media: Copper wire, Fiber optic,   │
│         Wireless (radio waves)      │
│  Devices: Hub, Repeater, Modem      │
└─────────────────────────────────────┘
```
- **Function:** Transmits raw bits over a physical medium
- Deals with: Voltage levels, pin layout, cable specifications, modulation
- **Hub** and **Repeater** operate at Physical layer
- **BPSC Key Fact:** Physical layer PDU = **Bits** (smallest unit)

---

## 🔗 NETWORKING DEVICES — WHICH LAYER?

```
┌────────────────────────────────────────────────────┐
│        DEVICE → LAYER MAPPING (PYQ CRITICAL)       │
├──────────────────────┬─────────────────────────────┤
│ Device               │ OSI Layer                   │
├──────────────────────┼─────────────────────────────┤
│ Hub                  │ Layer 1 — Physical          │
│ Repeater             │ Layer 1 — Physical          │
│ Modem                │ Layer 1 — Physical          │
│ Bridge               │ Layer 2 — Data Link         │
│ Switch               │ Layer 2 — Data Link         │
│ Router               │ Layer 3 — Network           │
│ Gateway              │ Layer 4–7 (All layers)      │
│ Firewall             │ Layer 3–7                   │
└──────────────────────┴─────────────────────────────┘
```

---

## 🆚 OSI MODEL vs TCP/IP MODEL — BPSC COMPARISON TABLE

```
┌────────────────────────────────────────────────────────────┐
│          OSI MODEL (7 layers) vs TCP/IP (4 layers)         │
├────────────────┬───────────────┬────────────────────────────┤
│  OSI Layer     │  OSI Layer #  │  TCP/IP Layer              │
├────────────────┼───────────────┼────────────────────────────┤
│  Application   │      7        │                            │
│  Presentation  │      6        │  Application               │
│  Session       │      5        │                            │
├────────────────┼───────────────┼────────────────────────────┤
│  Transport     │      4        │  Transport (Host-to-Host)  │
├────────────────┼───────────────┼────────────────────────────┤
│  Network       │      3        │  Internet                  │
├────────────────┼───────────────┼────────────────────────────┤
│  Data Link     │      2        │                            │
│  Physical      │      1        │  Network Access            │
└────────────────┴───────────────┴────────────────────────────┘

KEY MAPPINGS TO MEMORIZE:
• OSI Application + Presentation + Session = TCP/IP Application
• OSI Transport = TCP/IP Transport (Host-to-Host)
• OSI Network = TCP/IP Internet
• OSI Data Link + Physical = TCP/IP Network Access
```

---

## 📦 PDU (PROTOCOL DATA UNIT) — COMPLETE SUMMARY

```
Layer 7 — Application    →  DATA
Layer 6 — Presentation   →  DATA
Layer 5 — Session        →  DATA
Layer 4 — Transport      →  SEGMENT (TCP) / DATAGRAM (UDP)
Layer 3 — Network        →  PACKET
Layer 2 — Data Link      →  FRAME
Layer 1 — Physical       →  BIT
```

**Memory Hook:** "Data Data Data Segment Packet Frame Bit" → D D D S P F B → **"Doctors Don't Suddenly Pull Friends' Body Bits"**

---

## ⚠️ BPSC EXAM TRAPS — OSI MODEL

| Common Wrong Answer | Correct Answer |
|---------------------|----------------|
| "Physical layer transmits Frames" | Physical layer transmits **Bits** |
| "Router works at Data Link layer" | Router works at **Network layer** |
| "Switch works at Network layer" | Switch works at **Data Link layer** |
| "MAC is the upper sublayer" | MAC is the **lower** sublayer; LLC is upper |
| "TCP/IP has 7 layers" | TCP/IP has **4 layers** |
| "Application layer is only for apps" | Application layer provides services to user applications |
| "Transport layer PDU = Packet" | Transport layer PDU = **Segment** |
| "Presentation layer = Translator only" | Presentation layer also does encryption AND compression |

---

## 🔄 DATA ENCAPSULATION PROCESS

When you send data across a network, each layer **adds its own header** (encapsulation):

```
APPLICATION:    [  DATA                        ]
TRANSPORT:      [ TCP Header |  DATA           ]  → SEGMENT
NETWORK:        [ IP Header | TCP Header | DATA]  → PACKET
DATA LINK:      [MAC Header | IP Header | TCP | DATA | MAC Trailer] → FRAME
PHYSICAL:       [ 0 1 0 1 1 0 0 1 1 ... ]  → BITS
```

On the receiving end, each layer **removes** its header (de-encapsulation) and passes data up.

---

## 🏆 TOPPER LEVEL FACTS — OSI MODEL

1. **OSI = conceptual model** (ISO standard); TCP/IP = practical implementation
2. Physical layer deals with **electrical, mechanical, and functional** specifications
3. Data Link layer uses **MAC address** (hardware address) for communication
4. Network layer uses **IP address** (logical address) for routing
5. Transport layer provides **port-to-port** communication (process-to-process)
6. Session layer = **dialog control + synchronization**
7. Presentation layer = **encryption + compression + translation**
8. Application layer = **network service to user** (NOT just "applications")
9. **Encapsulation** = adding headers going DOWN the layers
10. **De-encapsulation** = removing headers going UP the layers

---
---

# 🇮🇳 PART B — GENERAL STUDIES
# INDIAN POLITY: PARLIAMENT OF INDIA
## Lok Sabha + Rajya Sabha + Bills + Joint Session

---

## 🔑 WHY THIS TOPIC IS HIGH SCORING IN BPSC TRE

Parliament questions appear in EVERY BPSC exam (not just TRE). This topic is:
- **Predictable** — same facts repeat year after year
- **Factual** — no opinion, just memorize numbers and articles
- **High yield** — 2–4 questions per GS section guaranteed

---

## 🏛️ PARLIAMENT OF INDIA — OVERVIEW

```
┌─────────────────────────────────────────────────┐
│          PARLIAMENT OF INDIA                    │
│                                                 │
│    ┌──────────────┐    ┌──────────────────┐    │
│    │  RAJYA SABHA │    │   LOK SABHA      │    │
│    │ (Upper House)│    │  (Lower House)   │    │
│    │ Council of   │    │  House of the    │    │
│    │  States      │    │    People        │    │
│    └──────────────┘    └──────────────────┘    │
│                  +  PRESIDENT                   │
│         (President is part of Parliament)       │
└─────────────────────────────────────────────────┘

Article 79: Constitution of Parliament
Parliament = President + Lok Sabha + Rajya Sabha
```

---

## 🟠 LOK SABHA — THE LOWER HOUSE (HOUSE OF THE PEOPLE)

### Basic Facts:
```
┌─────────────────────────────────────────────────────┐
│                 LOK SABHA — KEY FACTS                │
├─────────────────────────────┬───────────────────────┤
│ Constitutional Authority    │ Article 81             │
│ Maximum Strength            │ 552                    │
│ Elected from States         │ 530 max                │
│ Elected from UTs            │ 20 max                 │
│ President's Nomination      │ 2 (Anglo-Indian)       │
│                             │ [Note: 104th Amendment │
│                             │  2020 ended this]      │
│ Current Strength            │ 543 elected            │
│ Minimum Age (Member)        │ 25 years               │
│ Term                        │ 5 years                │
│ Presided by                 │ SPEAKER                │
│ First Speaker               │ G.V. Mavalankar        │
│ Election of Speaker         │ By members of Lok Sabha│
│ Pro-tem Speaker             │ Most senior member,    │
│                             │ appointed by President │
│ Quorum                      │ 1/10th of total members│
│ Dissolution                 │ By President (Art. 85) │
└─────────────────────────────┴───────────────────────┘
```

### Qualifications to be Lok Sabha Member:
- Must be a **citizen of India**
- Minimum age: **25 years**
- Name on electoral rolls
- Must NOT hold office of profit under government
- Must NOT be of unsound mind / insolvent

### Powers and Functions of Lok Sabha:
```
1. LEGISLATIVE POWER    → Passes laws on Union + Concurrent list
2. FINANCIAL POWER      → Money bills originate ONLY in Lok Sabha
                          Rajya Sabha has NO power over Money Bills
3. EXECUTIVE POWER      → Council of Ministers responsible to Lok Sabha
                          Passes Vote of No-confidence
4. CONSTITUTIONAL POWER → Participates in constitutional amendments
5. ELECTORAL POWER      → Elects President + Vice President
```

### Speaker of Lok Sabha:
- Elected by members of Lok Sabha
- **Does NOT vote except in case of TIE** (casting vote)
- Cannot be removed except by resolution passed by majority of ALL members
- Presides over joint sitting of Parliament

---

## 🔵 RAJYA SABHA — THE UPPER HOUSE (COUNCIL OF STATES)

### Basic Facts:
```
┌─────────────────────────────────────────────────────┐
│               RAJYA SABHA — KEY FACTS                │
├─────────────────────────────┬───────────────────────┤
│ Constitutional Authority    │ Article 80             │
│ Maximum Strength            │ 250                    │
│ Elected by State Legislatures│ 238 max               │
│ Nominated by President      │ 12 (Arts, Science,     │
│                             │  Literature, Social    │
│                             │  Service)              │
│ Current Strength            │ 245                    │
│ Minimum Age (Member)        │ 30 years               │
│ Term of each member         │ 6 years                │
│ Retirement (1/3 retire)     │ Every 2 years          │
│ Presided by                 │ VICE PRESIDENT         │
│                             │ (Ex-officio Chairman)  │
│ Deputy Chairman             │ Elected by Rajya Sabha │
│ Dissolution                 │ CANNOT be dissolved    │
│                             │ (PERMANENT house)      │
│ First Chairman              │ S. Radhakrishnan        │
│ Quorum                      │ 1/10th of total members│
└─────────────────────────────┴───────────────────────┘
```

### Special Powers of Rajya Sabha (BPSC Favourite!):
```
┌─────────────────────────────────────────────────────────────┐
│          RAJYA SABHA SPECIAL POWERS                         │
│                                                             │
│  1. ARTICLE 249: Can authorize Parliament to legislate      │
│     on STATE LIST subject (2/3 majority)                    │
│                                                             │
│  2. ARTICLE 312: Can create new All-India Services          │
│     (IAS, IPS, IFS) by 2/3 majority                        │
│                                                             │
│  3. Cannot be dissolved (PERMANENT HOUSE)                   │
│                                                             │
│  4. NO power over Money Bills                               │
│     (can only suggest amendments within 14 days)           │
└─────────────────────────────────────────────────────────────┘
```

---

## 🆚 LOK SABHA vs RAJYA SABHA — COMPARISON TABLE

```
┌───────────────────────┬──────────────────────┬──────────────────────┐
│ Feature               │ LOK SABHA            │ RAJYA SABHA          │
├───────────────────────┼──────────────────────┼──────────────────────┤
│ Also called           │ House of the People  │ Council of States    │
│ Type                  │ Lower House          │ Upper House          │
│ Max Strength          │ 552                  │ 250                  │
│ Current Strength      │ 543                  │ 245                  │
│ Min Age               │ 25 years             │ 30 years             │
│ Term                  │ 5 years              │ 6 years per member   │
│ Dissolution           │ Can be dissolved     │ CANNOT be dissolved  │
│ Presided by           │ Speaker              │ Vice President       │
│ Money Bills           │ Originates here ONLY │ No power to reject   │
│ No-confidence motion  │ Can be passed here   │ NOT applicable       │
│ Article               │ Article 81           │ Article 80           │
│ Election method       │ Direct (by voters)   │ Indirect (by MLAs)   │
│ Nominations           │ 2 (Anglo-Indian)     │ 12 (by President)    │
└───────────────────────┴──────────────────────┴──────────────────────┘
```

---

## 📋 TYPES OF BILLS IN PARLIAMENT

### 1. ORDINARY BILL (Most Common)
```
Can be introduced in EITHER house → Passes both houses → Presidential assent
If disagreement → JOINT SITTING (Article 108)
```

### 2. MONEY BILL (Article 110) — BPSC FAVOURITE!
```
Definition: Deals with taxation, government expenditure, borrowing
Can be introduced ONLY in LOK SABHA
Rajya Sabha can ONLY suggest amendments (14 days max)
Lok Sabha MAY or MAY NOT accept Rajya Sabha suggestions
Speaker certifies if a bill is a Money Bill
President CANNOT return Money Bill — only give or withhold assent
```

**Important Money Bill Facts:**
- Rajya Sabha has **no power to reject** a Money Bill
- If Rajya Sabha doesn't return in 14 days → deemed PASSED by both houses
- Cannot go to Joint Sitting (Lok Sabha alone decides)

### 3. FINANCIAL BILL
- Related to financial matters BUT not purely a Money Bill
- Needs to pass BOTH houses
- Can be introduced only in Lok Sabha

### 4. CONSTITUTIONAL AMENDMENT BILL (Article 368)
- Can be introduced in **EITHER** house
- Needs **Special Majority**: 2/3 of members present and voting + majority of total membership
- Some provisions also need ratification by half the state legislatures
- **NO Joint Sitting** for Constitutional Amendment Bills

---

## 🤝 JOINT SITTING OF PARLIAMENT (ARTICLE 108)

```
┌─────────────────────────────────────────────────────────┐
│              JOINT SITTING — ARTICLE 108                │
│                                                         │
│  WHEN held:                                             │
│  • When a bill is rejected by one house                 │
│  • When houses disagree on amendments                   │
│  • When no action taken in 6 months                     │
│                                                         │
│  PRESIDED BY: Speaker of Lok Sabha                      │
│                                                         │
│  BILLS NOT applicable for Joint Sitting:                │
│  • Money Bills (Lok Sabha alone decides)                │
│  • Constitutional Amendment Bills (Special Majority)    │
│                                                         │
│  Joint Sittings held so far (India): 3 times           │
│  1961, 1978, 2002                                       │
└─────────────────────────────────────────────────────────┘
```

---

## 👤 THE PRESIDENT AND PARLIAMENT

### Presidential Role in Bills:
```
ORDINARY BILL options for President:
  ├── Give Assent → Bill becomes Law
  ├── Withhold Assent → Bill rejected
  └── Return for Reconsideration → If passed again, MUST give assent

MONEY BILL options for President:
  ├── Give Assent → Law
  └── Withhold Assent → Bill rejected
  (Cannot return Money Bill to Parliament)
```

### President's Address to Parliament:
- **Article 87:** President addresses both houses at start of each session
- First session after general election and first session of each year

---

## 🔑 IMPORTANT ARTICLES — PARLIAMENT (BPSC Must Know)

```
┌─────────┬──────────────────────────────────────────────┐
│ Article │ Provision                                    │
├─────────┼──────────────────────────────────────────────┤
│  79     │ Constitution of Parliament                   │
│  80     │ Composition of Rajya Sabha                   │
│  81     │ Composition of Lok Sabha                     │
│  83     │ Duration of Houses (5 yrs for LS)            │
│  84     │ Qualification for membership                 │
│  85     │ Sessions, Prorogation, Dissolution           │
│  86     │ President's right to address Parliament      │
│  87     │ Special address by President                 │
│  93     │ Speaker and Deputy Speaker of Lok Sabha      │
│  100    │ Voting in Houses, Quorum                     │
│  108    │ Joint sitting of both Houses                 │
│  109    │ Special procedure for Money Bills            │
│  110    │ Definition of Money Bills                    │
│  112    │ Annual Financial Statement (Budget)          │
│  123    │ Presidential Ordinances                      │
│  368    │ Amendment of Constitution                    │
└─────────┴──────────────────────────────────────────────┘
```

---

## 💡 PARLIAMENT — SESSIONS AND TERMS

### Sessions of Parliament:
```
1. BUDGET SESSION    → February to May (Longest session)
   • Union Budget presented in February
   • General Discussion on Budget

2. MONSOON SESSION   → July to August

3. WINTER SESSION    → November to December (Shortest)
```

### Parliamentary Terms to Know:
- **Prorogation:** End of a session (by President) — pending bills lapse EXCEPT those passed by one house
- **Dissolution:** End of the Lok Sabha itself (only Lok Sabha, not Rajya Sabha)
- **Adjournment:** Temporary suspension of sitting for a specific period
- **Adjournment sine die:** Indefinite adjournment
- **Quorum:** Minimum number required to conduct business = **1/10th** of total members

---

## ⚠️ BPSC EXAM TRAPS — PARLIAMENT SECTION

| Common Wrong Answer | Correct Answer |
|---------------------|----------------|
| "Rajya Sabha can be dissolved" | Rajya Sabha is a **PERMANENT** house — cannot be dissolved |
| "Money bill can be introduced in Rajya Sabha" | Money bill originates ONLY in **Lok Sabha** |
| "Speaker votes on all bills" | Speaker votes ONLY in case of a **tie** |
| "Joint sitting is for constitutional amendment" | Joint sitting NOT for Constitutional Amendment Bills |
| "Minimum age for Rajya Sabha = 25" | Minimum age for Rajya Sabha = **30 years** |
| "Rajya Sabha is chaired by Speaker" | Rajya Sabha is chaired by **Vice President** |
| "Rajya Sabha has 12 elected and 238 nominated" | Rajya Sabha: **238 elected, 12 nominated** by President |
| "President can return Money Bill" | President CANNOT return a Money Bill |

---

## 🏆 TOPPER LEVEL FACTS — PARLIAMENT

1. President is an **integral part** of Parliament (not just head of state)
2. **Article 105:** Powers, privileges of members — freedom of speech in Parliament
3. **No-confidence motion** can only be passed in **Lok Sabha** (not Rajya Sabha)
4. Parliamentary Committee work = most actual legislative work happens here
5. **Private Member Bill** = bill introduced by a member who is NOT a minister
6. Collective responsibility of Council of Ministers = to **Lok Sabha** (not Rajya Sabha)
7. **Zero Hour** = Questions without notice, immediately after Question Hour (not constitutional)
8. **Question Hour** = First hour of Parliament session — ministers answer questions
9. **Starred Question** = requires oral answer + supplementary questions allowed
10. **Unstarred Question** = written answer only, no supplementary

---
---

# 📝 PRACTICE QUESTIONS

## ⚠️ IMPORTANT INSTRUCTION:
### Solve ALL 50 questions first. Answers are given ONLY AFTER ALL 50 QUESTIONS.
### Do NOT scroll to answers before attempting. Cover the answers section!

---

# 🖥️ SECTION A: COMPUTER SCIENCE — OSI MODEL
## 25 MCQs | BPSC TRE Style | 5 Options Each

---

**Q1.** The OSI Model was developed by which organization?

(A) IEEE  
(B) IETF  
(C) ISO (International Organization for Standardization)  
(D) More than one of the above  
(E) None of the above  

---

**Q2.** Which of the following correctly lists the OSI layers from top to bottom (Layer 7 to Layer 1)?

(A) Physical, Data Link, Network, Transport, Session, Presentation, Application  
(B) Application, Presentation, Session, Transport, Network, Data Link, Physical  
(C) Application, Session, Presentation, Transport, Network, Data Link, Physical  
(D) More than one of the above  
(E) None of the above  

---

**Q3.** What is the Protocol Data Unit (PDU) at the Transport Layer of the OSI model?

(A) Bit  
(B) Frame  
(C) Packet  
(D) More than one of the above  
(E) None of the above  

---

**Q4.** Which layer of the OSI model is responsible for routing and forwarding of packets?

(A) Data Link Layer  
(B) Transport Layer  
(C) Network Layer  
(D) More than one of the above  
(E) None of the above  

---

**Q5.** A Router operates at which layer of the OSI model?

(A) Layer 1 — Physical  
(B) Layer 2 — Data Link  
(C) Layer 3 — Network  
(D) More than one of the above  
(E) None of the above  

---

**Q6.** The Data Link Layer of the OSI model has two sublayers. Which is the UPPER sublayer?

(A) MAC (Media Access Control)  
(B) LLC (Logical Link Control)  
(C) NLC (Network Link Control)  
(D) More than one of the above  
(E) None of the above  

---

**Q7.** The "Host-to-Host" layer in the TCP/IP model corresponds to which layer of the OSI model?

(A) Network Layer  
(B) Session Layer  
(C) Transport Layer  
(D) More than one of the above  
(E) None of the above  

---

**Q8.** Which of the following is the PDU at the Data Link Layer?

(A) Segment  
(B) Packet  
(C) Frame  
(D) More than one of the above  
(E) None of the above  

---

**Q9.** A Switch operates at which layer of the OSI model?

(A) Physical Layer  
(B) Data Link Layer  
(C) Network Layer  
(D) More than one of the above  
(E) None of the above  

---

**Q10.** Which layer of the OSI model is responsible for encryption, compression, and data translation?

(A) Application Layer  
(B) Session Layer  
(C) Presentation Layer  
(D) More than one of the above  
(E) None of the above  

---

**Q11.** Which of the following statements about TCP is CORRECT?

(A) TCP is connectionless  
(B) TCP is unreliable  
(C) TCP uses three-way handshake to establish connection  
(D) More than one of the above  
(E) None of the above  

---

**Q12.** At which layer does the OSI model add MAC address information?

(A) Network Layer  
(B) Data Link Layer  
(C) Transport Layer  
(D) More than one of the above  
(E) None of the above  

---

**Q13.** Which layer of the OSI model deals with the physical transmission of raw bits over a communication channel?

(A) Data Link Layer  
(B) Physical Layer  
(C) Network Layer  
(D) More than one of the above  
(E) None of the above  

---

**Q14.** The TCP/IP model has how many layers?

(A) 5  
(B) 6  
(C) 7  
(D) More than one of the above  
(E) None of the above  

---

**Q15.** Which of the following protocols operate at the Application Layer of the OSI model?

(A) IP  
(B) TCP  
(C) HTTP  
(D) More than one of the above  
(E) None of the above  

---

**Q16.** Which device operates at Layer 1 (Physical Layer) of the OSI model?

(A) Router  
(B) Switch  
(C) Hub  
(D) More than one of the above  
(E) None of the above  

---

**Q17.** The process of adding headers at each layer while sending data is called:

(A) De-encapsulation  
(B) Multiplexing  
(C) Encapsulation  
(D) More than one of the above  
(E) None of the above  

---

**Q18.** Which layer of the OSI model establishes, manages, and terminates sessions between applications?

(A) Presentation Layer  
(B) Transport Layer  
(C) Session Layer  
(D) More than one of the above  
(E) None of the above  

---

**Q19.** UDP (User Datagram Protocol) is characterized by which of the following?

(A) Connection-oriented  
(B) Reliable data transfer  
(C) Connectionless and faster than TCP  
(D) More than one of the above  
(E) None of the above  

---

**Q20.** The PDU at the Network Layer is called:

(A) Frame  
(B) Segment  
(C) Packet  
(D) More than one of the above  
(E) None of the above  

---

**Q21.** Which OSI layer provides an interface between the OSI network and the user's application program?

(A) Session Layer  
(B) Presentation Layer  
(C) Application Layer  
(D) More than one of the above  
(E) None of the above  

---

**Q22.** In the OSI model, which layers of OSI correspond to the Application layer of TCP/IP?

(A) Only Application Layer (Layer 7)  
(B) Application and Presentation Layers  
(C) Application, Presentation, and Session Layers  
(D) More than one of the above  
(E) None of the above  

---

**Q23.** Which of the following is NOT a protocol at the Network Layer?

(A) IP  
(B) OSPF  
(C) TCP  
(D) More than one of the above  
(E) None of the above  

---

**Q24.** The MAC sublayer of the Data Link layer performs functions that depend on:

(A) The type of application being used  
(B) The type of physical medium being used  
(C) The IP address of the destination  
(D) More than one of the above  
(E) None of the above  

---

**Q25.** Which of the following correctly describes the role of the Transport Layer?

(A) It handles physical transmission of bits  
(B) It provides end-to-end communication between processes on different hosts  
(C) It is responsible for routing packets between networks  
(D) More than one of the above  
(E) None of the above  

---

---

# 🇮🇳 SECTION B: GENERAL STUDIES — PARLIAMENT OF INDIA
## 25 MCQs | BPSC TRE Style | 5 Options Each

---

**Q26.** Which Article of the Indian Constitution defines the composition of Parliament?

(A) Article 75  
(B) Article 79  
(C) Article 81  
(D) More than one of the above  
(E) None of the above  

---

**Q27.** The maximum strength of the Lok Sabha, as provided by the Constitution, is:

(A) 543  
(B) 545  
(C) 552  
(D) More than one of the above  
(E) None of the above  

---

**Q28.** Who presides over the joint sitting of both Houses of Parliament?

(A) Vice President  
(B) President  
(C) Speaker of Lok Sabha  
(D) More than one of the above  
(E) None of the above  

---

**Q29.** Which of the following statements about Rajya Sabha is CORRECT?

(A) Rajya Sabha can be dissolved by the President  
(B) The minimum age to become a Rajya Sabha member is 25 years  
(C) Rajya Sabha is a permanent body that cannot be dissolved  
(D) More than one of the above  
(E) None of the above  

---

**Q30.** A Money Bill under the Indian Constitution can be introduced in:

(A) Rajya Sabha only  
(B) Lok Sabha only  
(C) Either House of Parliament  
(D) More than one of the above  
(E) None of the above  

---

**Q31.** The maximum number of members that can be nominated to Rajya Sabha by the President is:

(A) 2  
(B) 12  
(C) 20  
(D) More than one of the above  
(E) None of the above  

---

**Q32.** Which Article provides for the joint sitting of both Houses of Parliament?

(A) Article 105  
(B) Article 108  
(C) Article 110  
(D) More than one of the above  
(E) None of the above  

---

**Q33.** The minimum age required to become a member of the Lok Sabha is:

(A) 18 years  
(B) 21 years  
(C) 25 years  
(D) More than one of the above  
(E) None of the above  

---

**Q34.** Who is the ex-officio Chairman of the Rajya Sabha?

(A) President of India  
(B) Prime Minister  
(C) Vice President of India  
(D) More than one of the above  
(E) None of the above  

---

**Q35.** Which of the following bills CANNOT be introduced in Rajya Sabha?

(A) Ordinary Bill  
(B) Constitutional Amendment Bill  
(C) Money Bill  
(D) More than one of the above  
(E) None of the above  

---

**Q36.** The quorum to constitute a sitting of either House of Parliament is:

(A) 1/5th of total membership  
(B) 1/10th of total membership  
(C) 1/3rd of total membership  
(D) More than one of the above  
(E) None of the above  

---

**Q37.** For a Constitutional Amendment Bill (Article 368), which type of majority is required?

(A) Simple majority  
(B) Special majority (2/3 of members present and voting + majority of total membership)  
(C) Absolute majority  
(D) More than one of the above  
(E) None of the above  

---

**Q38.** The Speaker of Lok Sabha is elected by:

(A) The President of India  
(B) Members of both Houses of Parliament  
(C) Members of Lok Sabha  
(D) More than one of the above  
(E) None of the above  

---

**Q39.** If Rajya Sabha does not return a Money Bill within 14 days, what happens?

(A) The bill is deemed rejected  
(B) The bill lapses  
(C) The bill is deemed passed by both Houses  
(D) More than one of the above  
(E) None of the above  

---

**Q40.** Under Article 249, Rajya Sabha can pass a resolution authorizing Parliament to legislate on a subject in the State List. This requires:

(A) Simple majority  
(B) 2/3 majority of members present and voting  
(C) Absolute majority  
(D) More than one of the above  
(E) None of the above  

---

**Q41.** Which of the following is a special power of Rajya Sabha that Lok Sabha does NOT possess?

(A) Passing Money Bills  
(B) Passing Vote of No-confidence against the government  
(C) Creating new All-India Services under Article 312  
(D) More than one of the above  
(E) None of the above  

---

**Q42.** The first Speaker of Lok Sabha was:

(A) B.R. Ambedkar  
(B) G.V. Mavalankar  
(C) S. Radhakrishnan  
(D) More than one of the above  
(E) None of the above  

---

**Q43.** The term of members of Rajya Sabha is:

(A) 5 years  
(B) 6 years  
(C) 4 years  
(D) More than one of the above  
(E) None of the above  

---

**Q44.** Which of the following correctly identifies the Article for Money Bills?

(A) Article 108  
(B) Article 112  
(C) Article 110  
(D) More than one of the above  
(E) None of the above  

---

**Q45.** For which of the following bills is Joint Sitting of Parliament NOT applicable?

(A) Ordinary Bills  
(B) Financial Bills  
(C) Money Bills  
(D) More than one of the above  
(E) None of the above  

---

**Q46.** Which session of Parliament is generally the longest session in a year?

(A) Monsoon Session  
(B) Budget Session  
(C) Winter Session  
(D) More than one of the above  
(E) None of the above  

---

**Q47.** Under Article 312, Rajya Sabha can create new All-India Services. This requires a resolution passed by:

(A) Simple majority  
(B) 2/3 majority of members present and voting  
(C) Absolute majority  
(D) More than one of the above  
(E) None of the above  

---

**Q48.** The first session of Parliament after a general election and the first session of each year is addressed by:

(A) Prime Minister  
(B) Speaker of Lok Sabha  
(C) President of India  
(D) More than one of the above  
(E) None of the above  

---

**Q49.** Which of the following is NOT a parliamentary device used in Indian Parliament?

(A) Zero Hour  
(B) Question Hour  
(C) Green Hour  
(D) More than one of the above  
(E) None of the above  

---

**Q50.** In the Lok Sabha, the Speaker exercises a casting vote:

(A) In every voting  
(B) Only when there is a tie  
(C) Only on constitutional amendment bills  
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
| 1 | **(C)** | OSI model = ISO standard. IEEE develops network standards like Ethernet, IETF develops internet protocols like TCP/IP — but OSI itself is ISO. |
| 2 | **(B)** | Correct top-to-bottom order: Application, Presentation, Session, Transport, Network, Data Link, Physical. Mnemonic: "All People Seem To Need Data Processing" |
| 3 | **(E)** | PDU at Transport Layer = **Segment** (TCP) or **Datagram** (UDP). None of the options A, B, C given are "Segment" — be careful, this is a trap. The answer is Segment, which is not listed as A/B/C — so answer is (E) None of the above. |
| 4 | **(C)** | Network Layer (Layer 3) handles routing and forwarding. It determines the best path for packets. |
| 5 | **(C)** | Router = Layer 3 (Network Layer). Remember: Router → Route → Network layer. |
| 6 | **(B)** | LLC = **upper** sublayer of Data Link Layer. MAC = lower sublayer. PYQ trap: they swap these options. LLC = Logical Link Control is upper. |
| 7 | **(C)** | TCP/IP "Host-to-Host" layer = OSI **Transport Layer**. This exact mapping is a direct PYQ fact. |
| 8 | **(C)** | Data Link Layer PDU = **Frame**. Remember: Data Link = Frame (both have physical connection feel). |
| 9 | **(B)** | Switch = Layer 2 (Data Link Layer). Switch uses MAC addresses → MAC is at Data Link. Hub (layer 1) vs Switch (layer 2) — classic BPSC distinction. |
| 10 | **(C)** | Presentation Layer = Encryption + Compression + Translation/Encoding. It is the "translator" layer. |
| 11 | **(C)** | TCP IS connection-oriented AND uses three-way handshake AND is reliable. Option C says "TCP uses three-way handshake" — CORRECT. A and B are false. |
| 12 | **(B)** | MAC address is a hardware/physical address. MAC = Media Access Control = **Data Link Layer**. |
| 13 | **(B)** | Physical Layer handles raw bit transmission over the physical medium. |
| 14 | **(E)** | TCP/IP model has **4 layers** (Application, Transport, Internet, Network Access). Not 5, 6, or 7. Answer is (E) None of the above. |
| 15 | **(C)** | HTTP = Application Layer. IP = Network Layer. TCP = Transport Layer. Only HTTP is at Application Layer among the choices. |
| 16 | **(C)** | Hub = Layer 1 (Physical Layer). Router = Layer 3. Switch = Layer 2. Hub is a dumb device that just broadcasts — Physical layer. |
| 17 | **(C)** | **Encapsulation** = adding headers as data travels DOWN the layers from Application to Physical. De-encapsulation = removing headers going UP. |
| 18 | **(C)** | Session Layer establishes, manages, and terminates sessions. The word "Session" is in the function! |
| 19 | **(C)** | UDP = **Connectionless** and **faster** than TCP. A and B describe TCP (connection-oriented, reliable). |
| 20 | **(C)** | Network Layer PDU = **Packet**. Navigate (Network) Packets — memory trick. |
| 21 | **(C)** | Application Layer provides the interface between the network and user application programs. |
| 22 | **(C)** | OSI Application + Presentation + Session layers all map to TCP/IP Application layer. |
| 23 | **(C)** | TCP is at **Transport Layer** (Layer 4), NOT Network Layer. IP and OSPF are at Network Layer. |
| 24 | **(B)** | MAC sublayer functions depend on the **type of physical medium** (e.g., Ethernet, Wi-Fi, fiber). This is a direct PYQ fact from TRE papers. |
| 25 | **(B)** | Transport Layer = end-to-end communication between processes on different hosts. Layer 1 = bits. Layer 3 = routing. |

---

### 🇮🇳 GS SECTION — ANSWER KEY WITH EXPLANATIONS

| Q# | Answer | Explanation |
|----|--------|-------------|
| 26 | **(B)** | Article 79 = Constitution of Parliament (President + Rajya Sabha + Lok Sabha). Article 81 = Composition of Lok Sabha specifically. |
| 27 | **(C)** | Maximum strength of Lok Sabha = **552** (530 from states + 20 from UTs + 2 nominated). Current strength = 543. |
| 28 | **(C)** | Joint sitting is presided over by the **Speaker of Lok Sabha**. This is a direct PYQ — don't confuse with Vice President (who chairs Rajya Sabha). |
| 29 | **(C)** | Rajya Sabha is a **PERMANENT** house — it CANNOT be dissolved. Only Lok Sabha can be dissolved. This is a classic BPSC trap. |
| 30 | **(B)** | Money Bill = **Lok Sabha ONLY**. This is a fundamental rule. Rajya Sabha has no power to originate or reject money bills. |
| 31 | **(B)** | President nominates **12** members to Rajya Sabha from fields of art, science, literature, social service. |
| 32 | **(B)** | Article **108** = Joint Sitting. Article 110 = Money Bill definition. Article 105 = Privileges of members. |
| 33 | **(C)** | Minimum age for Lok Sabha = **25 years**. For Rajya Sabha = 30 years. Don't mix these up. |
| 34 | **(C)** | Vice President is the **ex-officio** (by virtue of office) Chairman of Rajya Sabha. |
| 35 | **(C)** | Money Bill CANNOT be introduced in Rajya Sabha. Ordinary bills and Constitutional Amendment Bills can be introduced in either house. |
| 36 | **(B)** | Quorum = **1/10th** of total membership. For Lok Sabha: 55 members (1/10 of 543). |
| 37 | **(B)** | Constitutional Amendment requires **Special Majority**: 2/3 of members present and voting PLUS majority of total membership of each house. |
| 38 | **(C)** | Speaker of Lok Sabha is elected by **members of Lok Sabha** only (not both houses, not President). |
| 39 | **(C)** | If Rajya Sabha doesn't return Money Bill within 14 days, it is deemed **passed by both Houses**. The bill does NOT lapse or get rejected. |
| 40 | **(B)** | Article 249 resolution requires **2/3 majority** of Rajya Sabha members present and voting. |
| 41 | **(C)** | Article 312 — creating new All-India Services — is an **exclusive special power of Rajya Sabha**. Lok Sabha cannot do this. |
| 42 | **(B)** | First Speaker of Lok Sabha = **G.V. Mavalankar** (1952–1956). S. Radhakrishnan was first Chairman of Rajya Sabha (and later 2nd President). |
| 43 | **(B)** | Rajya Sabha members serve for **6 years**. 1/3rd retire every 2 years. Rajya Sabha itself is permanent. |
| 44 | **(C)** | Article **110** = Definition and special procedure for Money Bills. Article 112 = Annual Financial Statement (Budget). Article 108 = Joint Sitting. |
| 45 | **(D)** | Joint Sitting is NOT applicable for both: **Money Bills** (Lok Sabha alone) AND **Constitutional Amendment Bills** (special majority required). So C and implied constitutional amendment bills = both. D = More than one. |
| 46 | **(B)** | **Budget Session** (February to May) is the longest session as it covers Budget discussion, Vote on Account, Appropriation Bills etc. |
| 47 | **(B)** | Article 312 (All-India Services) requires **2/3 majority** of members present and voting in Rajya Sabha. |
| 48 | **(C)** | **President** addresses both Houses at the start of the first session after general election and first session of each year (Article 87). |
| 49 | **(C)** | "**Green Hour**" is NOT a parliamentary device. Zero Hour and Question Hour are real devices. Answer is (C) — "None of the above" would also be tricky here — Green Hour doesn't exist. |
| 50 | **(B)** | Speaker exercises a **casting vote ONLY when there is a tie**. In normal votes, Speaker does not vote. |

---

---

## 📊 SCORE YOURSELF

### CS Section (25 Questions):
- **23–25 correct → Topper Level ✅**
- **19–22 correct → Good — revise traps**
- **Below 19 → Re-read OSI layer functions + PDUs**

### GS Section (25 Questions):
- **23–25 correct → Topper Level ✅**
- **19–22 correct → Good — revise article numbers**
- **Below 19 → Re-read Lok Sabha vs Rajya Sabha comparison table**

---

## 🔮 PYQ PATTERN ANALYSIS — WHAT BPSC HAS ASKED

### CS PYQs on Networks (Direct from TRE 1.0, 2.0, 3.0):
1. Which layer of OSI corresponds to TCP/IP Host-to-Host layer? → **Transport Layer**
2. What is the PDU at Physical Layer? → **Bit**
3. Which is the upper sublayer of Data Link layer? → **LLC**
4. MAC sublayer performs functions depending on? → **Medium type**
5. What does Router work at? → **Network Layer (Layer 3)**

### GS PYQs on Parliament:
1. Maximum members of Rajya Sabha nominated by President? → **12**
2. Which article provides for joint sitting? → **Article 108**
3. Which bill can only originate in Lok Sabha? → **Money Bill**
4. Rajya Sabha chairman is? → **Vice President**
5. Minimum age for Rajya Sabha? → **30 years**

---

## 🌙 NIGHT REVISION — 5 BULLET POINT SUMMARY

### CS Summary (Write from memory tonight):
1. OSI has 7 layers; PDUs = Data/Data/Data/Segment/Packet/Frame/Bit (top to bottom)
2. Router = Layer 3; Switch = Layer 2; Hub = Layer 1
3. LLC = upper sublayer; MAC = lower sublayer of Data Link Layer
4. TCP/IP "Host-to-Host" = OSI Transport Layer; TCP/IP has 4 layers
5. Encapsulation = adding headers going down; De-encapsulation = removing headers going up

### GS Summary (Write from memory tonight):
1. Parliament = President + Lok Sabha + Rajya Sabha (Article 79)
2. Lok Sabha: max 552, min age 25, presided by Speaker, can be dissolved
3. Rajya Sabha: max 250, min age 30, presided by VP, PERMANENT (cannot dissolve)
4. Money Bill: only in Lok Sabha, Rajya Sabha returns in 14 days, no joint sitting
5. Article 108 = Joint Sitting; Article 110 = Money Bill; Article 368 = Amendment

---

## 📅 DAY 44 PREVIEW

**CS Topic:** TCP/IP Model & Layer Mapping in Detail + IPv4/IPv6 Addressing Basics
**GS Topic:** Indian Economy — GDP, National Income, Budget Basics

Come back tomorrow and say: **"Day-44"** — your mentor will be ready!

---

*Day 43 Complete | Phase 1 Week 7 | Computer Networks Unit Begins*
*Study hard. Stay consistent. TOP 50 RANK is yours — one day at a time! 🎯*
