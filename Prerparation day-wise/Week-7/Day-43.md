# 📅 BPSC TRE 4.0 — DAY 43 COMPLETE STUDY MODULE
### Computer Networks: OSI Model & Networking Basics + Indian Polity — Parliament
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Computer Networks — OSI Model, Layers, PDUs, Encapsulation
> - Afternoon (1 hr): Polity — Structure of Parliament (Lok Sabha, Rajya Sabha, President)
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Computer Networks — OSI Model & Networking Basics

---

## 🔷 SECTION 1: What is a Computer Network?

### Real-Life Analogy — The Post Office System:

Imagine sending a letter to a friend in another city. You write the letter, put it in an envelope, write the address, hand it to the post office. The post office has rules — how to address, how to sort, which route to take. Your friend receives it and reads it. Neither you nor your friend knows every detail of the delivery mechanism — but it WORKS because everyone follows the SAME RULES.

A Computer Network works exactly like this:
- **Devices** = You and your friend
- **Rules** = Protocols
- **Post Office infrastructure** = Network (cables, switches, routers)

> **A Computer Network is a collection of two or more interconnected devices (computers, phones, printers) that can communicate and share resources.**

### Why do we need Computer Networks?
```
WITHOUT NETWORK:                    WITH NETWORK:
  → Each device works in isolation    → Devices share files, printers, internet
  → No sharing possible               → Communication possible (email, chat)
  → Information not accessible        → Central data accessible everywhere
  → Example: Pen drive to transfer    → Example: Google Drive — access anywhere!
```

---

## 🔷 SECTION 2: Types of Networks (LAN, MAN, WAN)

### The "Distance" Model:

Think of it as THREE concentric circles:
```
                    ┌─────────────────────────────────┐
                    │              WAN                 │
                    │   ┌───────────────────────┐     │
                    │   │          MAN           │     │
                    │   │   ┌───────────────┐   │     │
                    │   │   │      LAN      │   │     │
                    │   │   │  (one building│   │     │
                    │   │   │   / campus)   │   │     │
                    │   │   └───────────────┘   │     │
                    │   │   (one city/metro)     │     │
                    │   └───────────────────────┘     │
                    │   (countries / global)           │
                    └─────────────────────────────────┘
```

### Comparison Table:

```
┌──────────────────┬──────────────────────────┬────────────────────────────┬──────────────────────────┐
│     FEATURE      │          LAN             │           MAN              │          WAN             │
│                  │  (Local Area Network)    │  (Metropolitan Area Network│   (Wide Area Network)   │
├──────────────────┼──────────────────────────┼────────────────────────────┼──────────────────────────┤
│ Full Form        │ Local Area Network       │ Metropolitan Area Network  │ Wide Area Network        │
├──────────────────┼──────────────────────────┼────────────────────────────┼──────────────────────────┤
│ Coverage Area    │ Small — single building  │ Medium — a city or town    │ Large — countries/global │
│                  │ or campus                │                            │                          │
├──────────────────┼──────────────────────────┼────────────────────────────┼──────────────────────────┤
│ Range            │ Up to ~1 km              │ Up to ~50–100 km           │ Unlimited (global)       │
├──────────────────┼──────────────────────────┼────────────────────────────┼──────────────────────────┤
│ Speed            │ Very High                │ High                       │ Lower (more latency)     │
│                  │ (100 Mbps–10 Gbps)       │ (10 Mbps–1 Gbps)          │ (Kbps–Mbps typically)    │
├──────────────────┼──────────────────────────┼────────────────────────────┼──────────────────────────┤
│ Ownership        │ Privately owned          │ Owned by ISP / Govt        │ Owned by telecom         │
│                  │ (office/home)            │ or consortium              │ providers (BSNL, Airtel) │
├──────────────────┼──────────────────────────┼────────────────────────────┼──────────────────────────┤
│ Cost             │ Low                      │ Moderate                   │ High                     │
├──────────────────┼──────────────────────────┼────────────────────────────┼──────────────────────────┤
│ Real Example     │ Computer lab in a school │ Cable TV network in Patna  │ The Internet itself      │
│                  │ Office network (TCS)     │ City-wide Wi-Fi            │ Bank's national network  │
├──────────────────┼──────────────────────────┼────────────────────────────┼──────────────────────────┤
│ Technology Used  │ Ethernet, Wi-Fi          │ Fiber optic, WiMAX         │ Satellite, leased lines  │
└──────────────────┴──────────────────────────┴────────────────────────────┴──────────────────────────┘
```

### 🎯 PYQ FACT: The Internet is the world's largest WAN. LAN is confined to a building/campus.

---

## 🔷 SECTION 3: Basic Components of a Network

```
COMPONENT        │ WHAT IT IS                    │ REAL-LIFE ANALOGY
─────────────────┼───────────────────────────────┼──────────────────────────────────
NODE             │ Any device connected to the   │ Each PERSON in a phone network
                 │ network (computer, phone,      │ (they send/receive calls)
                 │ printer, server, router)       │
─────────────────┼───────────────────────────────┼──────────────────────────────────
LINK             │ The communication channel      │ The PHONE LINE or road between
                 │ connecting nodes               │ two people/cities
                 │ (cable, Wi-Fi, fiber optic)    │
─────────────────┼───────────────────────────────┼──────────────────────────────────
PROTOCOL         │ Set of RULES that govern how  │ Language rules — if you speak in
                 │ data is transmitted            │ Hindi, both sides must know Hindi!
                 │ (TCP/IP, HTTP, FTP, etc.)      │ Protocols = common language
─────────────────┼───────────────────────────────┼──────────────────────────────────
SERVER           │ A node that PROVIDES services  │ A library that serves books to
                 │ to other nodes (web server,    │ students (on request)
                 │ file server, mail server)      │
─────────────────┼───────────────────────────────┼──────────────────────────────────
CLIENT           │ A node that REQUESTS services  │ A student who requests a book
                 │ from a server                  │ from the library
```

### 🎯 PYQ FACT: A protocol is a set of rules for communication. Without protocols, devices cannot understand each other even if physically connected.

---

## 🔷 SECTION 4: OSI Model — The Crown Jewel of Networking

### Why Was OSI Model Created?

Before OSI, every company made its own networking equipment with its OWN rules. An IBM computer couldn't talk to a Hewlett-Packard computer. Chaos!

In **1984**, the **International Organization for Standardization (ISO)** created the **OSI Model** — a universal framework so ALL networking equipment could communicate.

> **OSI = Open Systems Interconnection Model**
> **Developed by: ISO (International Organization for Standardization) in 1984**
> **Purpose: Standardize networking so devices from different manufacturers can communicate.**

### The 7-Layer Stack — The Big Picture:

```
OSI MODEL — TOP TO BOTTOM (Sender sends from top → bottom; Receiver receives bottom → top)

┌────────────────────────────────────────────────────────────────────────────┐
│  Layer 7 │  APPLICATION LAYER     │  Data     │  Where YOU interact        │
├──────────┼────────────────────────┼───────────┼───────────────────────────┤
│  Layer 6 │  PRESENTATION LAYER    │  Data     │  Encryption, Compression   │
├──────────┼────────────────────────┼───────────┼───────────────────────────┤
│  Layer 5 │  SESSION LAYER         │  Data     │  Session management        │
├──────────┼────────────────────────┼───────────┼───────────────────────────┤
│  Layer 4 │  TRANSPORT LAYER       │  Segment  │  End-to-end reliability    │
├──────────┼────────────────────────┼───────────┼───────────────────────────┤
│  Layer 3 │  NETWORK LAYER         │  Packet   │  Routing (IP address)      │
├──────────┼────────────────────────┼───────────┼───────────────────────────┤
│  Layer 2 │  DATA LINK LAYER       │  Frame    │  MAC address, Framing      │
├──────────┼────────────────────────┼───────────┼───────────────────────────┤
│  Layer 1 │  PHYSICAL LAYER        │  Bits     │  Actual signal on wire     │
└──────────┴────────────────────────┴───────────┴───────────────────────────┘
              ↑ Upper Layers (Software)               Lower Layers (Hardware) ↑

SENDER:    Application (7) → ... → Physical (1)   [Top to Bottom = ENCAPSULATION]
RECEIVER:  Physical (1) → ... → Application (7)   [Bottom to Top = DECAPSULATION]
```

### 🧠 MNEMONIC — Remember OSI Layers (Top to Bottom):

```
"All People Seem To Need Data Processing"

A → Application     (Layer 7)
P → Presentation    (Layer 6)
S → Session         (Layer 5)
T → Transport       (Layer 4)
N → Network         (Layer 3)
D → Data Link       (Layer 2)
P → Physical        (Layer 1)
```

### Bottom to Top Mnemonic (as receiver processes):
```
"Please Do Not Throw Sausage Pizza Away"

P → Physical        (Layer 1)
D → Data Link       (Layer 2)
N → Network         (Layer 3)
T → Transport       (Layer 4)
S → Session         (Layer 5)
P → Presentation    (Layer 6)
A → Application     (Layer 7)
```

---

## 🔷 SECTION 5: Functions of Each Layer (Deep Explanation)

### LAYER 7 — APPLICATION LAYER

```
FUNCTION: Provides an interface between the USER/APPLICATION and the network.
          This is the layer the user directly interacts with.
          It provides NETWORK SERVICES to end-user applications.

WHAT IT DOES:
  → Identifies communication partners (who are you talking to?)
  → Determines resource availability
  → Synchronises communication
  → Provides services: email, file transfer, web browsing

PROTOCOLS AT THIS LAYER:
  HTTP  → Web browsing (HyperText Transfer Protocol)
  HTTPS → Secure web browsing
  FTP   → File Transfer Protocol (sending files between computers)
  SMTP  → Simple Mail Transfer Protocol (sending emails)
  POP3  → Post Office Protocol (receiving emails)
  IMAP  → Internet Message Access Protocol (receiving emails)
  DNS   → Domain Name System (translates google.com → IP address)
  Telnet → Remote login to another computer
  SNMP  → Simple Network Management Protocol

DATA UNIT (PDU): DATA

REAL-LIFE ANALOGY:
  You opening Gmail to send an email.
  The APPLICATION LAYER is the Gmail interface you see and use.
  You type your message, press send — this layer handles the "send email" request.

🎯 PYQ FACT: HTTP, FTP, SMTP, DNS — all Application layer protocols!
🎯 PYQ FACT: Application layer is the CLOSEST to the end user.
```

---

### LAYER 6 — PRESENTATION LAYER

```
FUNCTION: Acts as a TRANSLATOR between the application and the network.
          Ensures data sent from one system can be READ by another system.

WHAT IT DOES:
  → TRANSLATION: Converts data formats (e.g., EBCDIC to ASCII)
  → ENCRYPTION / DECRYPTION: Secures data before sending
  → COMPRESSION / DECOMPRESSION: Reduces data size for faster transmission

WHY NEEDED:
  Computer A uses ASCII encoding.
  Computer B uses EBCDIC encoding.
  Without a translator, they'd send gibberish to each other!
  Presentation Layer = UNIVERSAL TRANSLATOR.

FORMATS HANDLED:
  → Image formats: JPEG, PNG, GIF
  → Video formats: MPEG, AVI
  → Text encoding: ASCII, Unicode
  → Encryption: SSL/TLS (HTTPS uses this!)

DATA UNIT (PDU): DATA

REAL-LIFE ANALOGY:
  A HINDI-to-ENGLISH translator at a UN meeting.
  Both parties speak different "languages" (data formats).
  The Presentation Layer translates so BOTH understand each other.

🎯 PYQ FACT: Encryption/Decryption = Presentation Layer!
🎯 PYQ FACT: Data compression = Presentation Layer!
🚨 TRAP: Some students confuse encryption with Session Layer — WRONG!
         ENCRYPTION → PRESENTATION LAYER (not Session!)
```

---

### LAYER 5 — SESSION LAYER

```
FUNCTION: Manages the ESTABLISHMENT, MAINTENANCE, and TERMINATION of sessions
          (communication connections) between applications.

WHAT IS A "SESSION"?
  A session = One complete conversation between two devices.
  Example: From when you LOG IN to a website until you LOG OUT.
           That entire period = ONE SESSION.

WHAT IT DOES:
  → SESSION ESTABLISHMENT: Sets up a connection ("Hello, let's talk")
  → SESSION MAINTENANCE: Keeps the connection alive during communication
  → SESSION SYNCHRONISATION: Adds checkpoints in data transfer
    (If transfer fails at 60%, resume from 60% instead of restarting!)
  → SESSION TERMINATION: Properly closes the connection ("Goodbye!")
  → DIALOG CONTROL: Half-duplex (one speaks at a time) or full-duplex

PROTOCOLS AT THIS LAYER:
  → NetBIOS (Windows file sharing)
  → RPC (Remote Procedure Call)
  → PAP (Password Authentication Protocol)

DATA UNIT (PDU): DATA

REAL-LIFE ANALOGY:
  A PHONE CALL:
  → Dialing = Session Establishment
  → Speaking / Listening = Session Maintenance
  → "Bye, goodbye" = Session Termination
  → Taking turns speaking = Dialog Control

🎯 PYQ FACT: Session Layer manages dialog control and synchronization checkpoints.
🎯 PYQ FACT: Session = logical connection between two devices (not physical!).
```

---

### LAYER 4 — TRANSPORT LAYER

```
FUNCTION: Provides END-TO-END (source to destination) reliable data delivery.
          Breaks data into segments, ensures all arrive correctly, in order.

WHAT IT DOES:
  → SEGMENTATION: Breaks large data into smaller SEGMENTS
  → REASSEMBLY: At receiver, puts segments back in correct order
  → FLOW CONTROL: Prevents sender from overwhelming receiver
    (If receiver is slow, sender slows down too)
  → ERROR CONTROL: Detects and retransmits lost/corrupted segments
  → CONNECTION MANAGEMENT:
      TCP = Connection-oriented (handshake before sending)
      UDP = Connectionless (just send, no confirmation)

KEY PROTOCOLS:
  TCP (Transmission Control Protocol):
  → RELIABLE — confirms every packet was received
  → ORDERED — data arrives in sequence
  → SLOWER (due to acknowledgments)
  → Used for: Web browsing (HTTP), email (SMTP), file transfer (FTP)

  UDP (User Datagram Protocol):
  → UNRELIABLE — no confirmation of delivery
  → FAST (no overhead of acknowledgments)
  → Used for: Video streaming, online gaming, DNS, VoIP
  → "Best effort" delivery

PORT NUMBERS (Transport Layer concept):
  → HTTP  → Port 80
  → HTTPS → Port 443
  → FTP   → Port 21
  → SMTP  → Port 25
  → DNS   → Port 53

DATA UNIT (PDU): SEGMENT

REAL-LIFE ANALOGY:
  Sending a large BOOK by courier:
  → You can't send the whole book in ONE package (too big)
  → You BREAK IT into chapters (segmentation)
  → Each chapter sent in a separate package
  → Courier confirms each package arrived (TCP) OR just sends without confirming (UDP)
  → Receiver REASSEMBLES chapters in correct order

🎯 PYQ FACT: Transport Layer PDU = SEGMENT (not packet, not frame!)
🎯 PYQ FACT: TCP = reliable, connection-oriented | UDP = unreliable, connectionless
🎯 PYQ FACT: Flow control and Error control = Transport Layer responsibilities
🚨 TRAP: "Packet" is Network Layer's PDU. "Segment" is Transport Layer's PDU.
```

---

### LAYER 3 — NETWORK LAYER

```
FUNCTION: Responsible for ROUTING — determining the best path to send data
          from source to destination across multiple networks.

WHAT IT DOES:
  → LOGICAL ADDRESSING: Assigns IP addresses (not physical MAC addresses)
  → ROUTING: Finds the best path from source to destination
    (Router is the key device here!)
  → PACKET FORWARDING: Moves packets from one router to the next
  → FRAGMENTATION: Breaks packets into smaller fragments if needed

KEY CONCEPT — IP ADDRESS:
  → Each device gets a unique IP address (like a postal address)
  → IPv4: 192.168.1.1 (32-bit, ~4 billion addresses)
  → IPv6: 2001:0db8:85a3::... (128-bit, virtually unlimited)

KEY DEVICE: ROUTER
  Router = Network Layer device
  (It reads IP addresses and forwards packets to correct destination)

KEY PROTOCOLS:
  → IP (Internet Protocol) — the core protocol (IPv4, IPv6)
  → ICMP (Internet Control Message Protocol) — error messages (ping uses this!)
  → ARP (Address Resolution Protocol) — maps IP address to MAC address
  → OSPF, RIP, BGP — Routing protocols (how routers share path info)

DATA UNIT (PDU): PACKET

REAL-LIFE ANALOGY:
  GPS NAVIGATION for data:
  → You're in Patna. You want to reach Delhi.
  → GPS (Router) calculates the best route: Patna → Varanasi → Agra → Delhi
  → If one road is blocked, GPS reroutes automatically!
  → Network Layer does exactly this for DATA PACKETS.

🎯 PYQ FACT: Network Layer PDU = PACKET
🎯 PYQ FACT: Router works at Network Layer (Layer 3)
🎯 PYQ FACT: IP address = Network Layer addressing
🚨 TRAP: "Router works at Data Link Layer" → WRONG! Router = Layer 3 (Network)
🚨 TRAP: "Frame" is Data Link PDU. "Packet" is Network Layer PDU.
```

---

### LAYER 2 — DATA LINK LAYER

```
FUNCTION: Provides node-to-node (hop-to-hop) data transfer between
          TWO DIRECTLY CONNECTED devices on the SAME network.
          Ensures error-free transmission over the physical link.

WHAT IT DOES:
  → FRAMING: Packages raw bits into structured FRAMES
    (Adds header + trailer around data for identification)
  → PHYSICAL ADDRESSING: Uses MAC addresses (not IP!)
    MAC = Media Access Control address (hardware address burned into NIC)
  → ERROR DETECTION: Detects errors using CRC (Cyclic Redundancy Check)
  → FLOW CONTROL: Controls data flow between adjacent nodes
  → ACCESS CONTROL: Decides who can use the channel when multiple devices share it

TWO SUB-LAYERS:
  ┌───────────────────────────────────────────────────┐
  │  LLC (Logical Link Control) — upper sub-layer     │
  │  → Error control, flow control                    │
  ├───────────────────────────────────────────────────┤
  │  MAC (Media Access Control) — lower sub-layer     │
  │  → Physical addressing (MAC address)              │
  │  → Channel access control                         │
  └───────────────────────────────────────────────────┘

KEY DEVICE: SWITCH, BRIDGE
  Switch = Data Link Layer device (reads MAC addresses)
  Bridge = Data Link Layer device (connects two LANs)

MAC ADDRESS FORMAT:
  → 48-bit hardware address
  → Written as: 00:1A:2B:3C:4D:5E (hexadecimal, 6 pairs)
  → Assigned by manufacturer — UNIQUE globally
  → Unlike IP, MAC cannot be changed (burned into NIC hardware)

KEY PROTOCOLS:
  → Ethernet (IEEE 802.3) — wired LAN
  → Wi-Fi (IEEE 802.11) — wireless LAN
  → PPP (Point-to-Point Protocol)
  → HDLC (High-level Data Link Control)

DATA UNIT (PDU): FRAME

REAL-LIFE ANALOGY:
  Sending a PARCEL within a CITY:
  → Network Layer (IP) gave you the CITY address (Delhi)
  → Data Link Layer gives the SPECIFIC HOUSE address (House #42, Street 5)
    = MAC address is the door-to-door delivery address
  → The postman (Switch) reads the house number and delivers to the RIGHT DOOR
  → The FRAME is the ENVELOPE with proper labeling

🎯 PYQ FACT: Data Link Layer PDU = FRAME
🎯 PYQ FACT: Switch and Bridge work at Data Link Layer (Layer 2)
🎯 PYQ FACT: MAC address = Data Link Layer addressing
🎯 PYQ FACT: MAC has TWO sub-layers: LLC (upper) and MAC (lower)
🚨 TRAP: "Switch works at Network Layer" → WRONG! Switch = Layer 2 (Data Link)
🚨 TRAP: "MAC address = Network Layer" → WRONG! MAC address = Data Link Layer
```

---

### LAYER 1 — PHYSICAL LAYER

```
FUNCTION: Transmits RAW BITS (0s and 1s) over a physical medium (cable, fiber, air).
          Concerned with HARDWARE specifications — voltage, timing, connectors.

WHAT IT DOES:
  → BIT TRANSMISSION: Converts bits to electrical/optical/radio signals
    (and back from signals to bits at receiver)
  → DEFINES PHYSICAL MEDIUM: What cables, connectors, pins to use
  → DEFINES SIGNAL ENCODING: How 0s and 1s are represented as signals
  → DEFINES DATA RATE: How many bits per second (bps)
  → DEFINES TOPOLOGY: Physical arrangement (bus, star, ring, mesh)
  → SYNCHRONISATION: Bit synchronization between sender/receiver

TYPES OF TRANSMISSION MEDIA (Physical Layer concerns):
  WIRED:
  → Twisted Pair Cable (Cat5, Cat6) — Ethernet LAN
  → Coaxial Cable — older cable TV networks
  → Fiber Optic Cable — fastest, uses light signals

  WIRELESS:
  → Radio waves (Wi-Fi, cellular)
  → Microwave (satellite communication)
  → Infrared (TV remotes, short range)

KEY DEVICES at Physical Layer:
  → Hub (repeats signals to all ports)
  → Repeater (regenerates signals over long distances)
  → Modem (Modulates/Demodulates digital ↔ analog signals)
  → Cables and connectors

DATA UNIT (PDU): BITS (0s and 1s)

REAL-LIFE ANALOGY:
  The ACTUAL ROAD on which vehicles travel:
  → Network Layer designed the ROUTE (GPS)
  → Data Link Layer addressed the PARCEL (house number)
  → Physical Layer is the ACTUAL ROAD (the physical infrastructure)
  → Whether it's a highway (fiber optic) or dirt road (coaxial),
    that's the Physical Layer's concern!

🎯 PYQ FACT: Physical Layer PDU = BITS (NOT frames, NOT packets!)
🎯 PYQ FACT: Hub and Repeater work at Physical Layer (Layer 1)
🎯 PYQ FACT: Physical Layer deals with SIGNALS (electrical, optical, radio)
🚨 TRAP: "Physical Layer uses frames" → WRONG! Physical = BITS only
🚨 TRAP: "Hub works at Data Link Layer" → WRONG! Hub = Physical Layer (Layer 1)
```

---

## 🔷 SECTION 6: Data Units (PDU) — Master Table

**PDU = Protocol Data Unit** — the name of data at each layer

```
┌──────────┬──────────────────────┬──────────────────────┬──────────────────────────────────────────┐
│  LAYER   │    LAYER NAME        │   DATA UNIT (PDU)    │         KEY IDENTIFYING FEATURE          │
├──────────┼──────────────────────┼──────────────────────┼──────────────────────────────────────────┤
│  Layer 7 │  Application         │      DATA            │  What the USER sees                      │
├──────────┼──────────────────────┼──────────────────────┼──────────────────────────────────────────┤
│  Layer 6 │  Presentation        │      DATA            │  Encrypted/Compressed data               │
├──────────┼──────────────────────┼──────────────────────┼──────────────────────────────────────────┤
│  Layer 5 │  Session             │      DATA            │  Session-managed data                    │
├──────────┼──────────────────────┼──────────────────────┼──────────────────────────────────────────┤
│  Layer 4 │  Transport           │    SEGMENT           │  Broken into segments; TCP/UDP header    │
├──────────┼──────────────────────┼──────────────────────┼──────────────────────────────────────────┤
│  Layer 3 │  Network             │    PACKET            │  IP header added; routing info           │
├──────────┼──────────────────────┼──────────────────────┼──────────────────────────────────────────┤
│  Layer 2 │  Data Link           │    FRAME             │  MAC header + trailer; CRC error check   │
├──────────┼──────────────────────┼──────────────────────┼──────────────────────────────────────────┤
│  Layer 1 │  Physical            │    BITS              │  Raw 0s and 1s as signals                │
└──────────┴──────────────────────┴──────────────────────┴──────────────────────────────────────────┘

🧠 MEMORY TRICK for PDUs (Layer 4 downward):
"Sergeant Peters Fought Bravely"
  S → Segment  (Transport Layer 4)
  P → Packet   (Network Layer 3)
  F → Frame    (Data Link Layer 2)
  B → Bits     (Physical Layer 1)
```

---

## 🔷 SECTION 7: Devices at Each Layer

```
┌──────────┬──────────────────────┬──────────────────────────────────────────────┐
│  LAYER   │    LAYER NAME        │   DEVICES / TECHNOLOGIES                    │
├──────────┼──────────────────────┼──────────────────────────────────────────────┤
│  Layer 7 │  Application         │  Gateway (Application gateway), Firewall     │
├──────────┼──────────────────────┼──────────────────────────────────────────────┤
│  Layer 6 │  Presentation        │  Software (SSL/TLS encryption), Gateways     │
├──────────┼──────────────────────┼──────────────────────────────────────────────┤
│  Layer 5 │  Session             │  Software (NetBIOS), API                     │
├──────────┼──────────────────────┼──────────────────────────────────────────────┤
│  Layer 4 │  Transport           │  Firewall (packet filtering), Load Balancer  │
├──────────┼──────────────────────┼──────────────────────────────────────────────┤
│  Layer 3 │  Network             │  ROUTER, Layer-3 Switch                      │
├──────────┼──────────────────────┼──────────────────────────────────────────────┤
│  Layer 2 │  Data Link           │  SWITCH, BRIDGE, NIC (Network Interface Card)│
├──────────┼──────────────────────┼──────────────────────────────────────────────┤
│  Layer 1 │  Physical            │  HUB, REPEATER, MODEM, Cables, Connectors    │
└──────────┴──────────────────────┴──────────────────────────────────────────────┘

🎯 DEVICE QUICK REFERENCE (Most-tested in PYQ):
  Hub        → Layer 1 (Physical)
  Switch     → Layer 2 (Data Link)
  Router     → Layer 3 (Network)
  Bridge     → Layer 2 (Data Link)
  Repeater   → Layer 1 (Physical)
  Modem      → Layer 1 (Physical)
  Gateway    → Layer 7 (Application) [connects different network architectures]
```

---

## 🔷 SECTION 8: Encapsulation — Data Flow from Sender to Receiver

### What is Encapsulation?

Think of sending a LETTER:
- You write the **letter** (data)
- Put it in an **envelope** (adds session/presentation formatting)
- Write the **recipient's address** (Transport adds port numbers)
- Add a **routing label** (Network adds IP address)
- Wrap in a **package with tracking** (Data Link adds MAC address + frame)
- Put it on the **conveyor belt** (Physical converts to signals/bits)

Each layer ADDS ITS OWN HEADER (and sometimes trailer). This is called **ENCAPSULATION**.

```
ENCAPSULATION (Sender — Top to Bottom):

APPLICATION DATA:
   ┌────────────────────────────────────────────┐
   │                  DATA                       │  ← User data (your email text)
   └────────────────────────────────────────────┘

TRANSPORT LAYER adds SEGMENT header:
   ┌──────────┬─────────────────────────────────┐
   │ TCP/UDP  │              DATA               │  ← Source/Dest Port, Sequence #
   │ HEADER   │                                 │
   └──────────┴─────────────────────────────────┘
              = SEGMENT

NETWORK LAYER adds PACKET header:
   ┌──────────┬──────────┬─────────────────────┐
   │  IP      │ TCP/UDP  │         DATA        │  ← Source/Dest IP address
   │ HEADER   │ HEADER   │                     │
   └──────────┴──────────┴─────────────────────┘
              = PACKET

DATA LINK LAYER adds FRAME header + trailer:
   ┌──────────┬──────────┬──────────┬──────────┬───────────┐
   │  MAC     │  IP      │ TCP/UDP  │  DATA    │  TRAILER  │  ← MAC address, CRC
   │ HEADER   │ HEADER   │ HEADER   │          │  (CRC)    │
   └──────────┴──────────┴──────────┴──────────┴───────────┘
              = FRAME

PHYSICAL LAYER converts to BITS:
   01001010 11001010 00110101 01010110 ...
              = BITS sent over wire/air

─────────────────────────────────────────────────────────────────────────────

DECAPSULATION (Receiver — Bottom to Top):

Physical → Bits received → converted back to Frame
Data Link → Removes MAC header/trailer → extracts Packet
Network  → Removes IP header → extracts Segment
Transport→ Removes TCP header → extracts Data
Application → Reads the DATA (sees your email!)

KEY INSIGHT:
  Encapsulation = ADDING headers (sender side, top → bottom)
  Decapsulation = REMOVING headers (receiver side, bottom → top)
```

### 🎯 PYQ FACTS:
```
✅ Encapsulation = adding headers as data moves DOWN the OSI stack
✅ Decapsulation = removing headers as data moves UP the OSI stack
✅ Each layer communicates with its PEER LAYER on the other device
   (Transport layer talks to Transport layer; Network talks to Network)
✅ Only Physical Layer has ACTUAL physical communication — all others are LOGICAL
```

---

## 🔷 SECTION 9: OSI Model — Layer vs Real-Life Protocols Mapping

```
┌──────────┬──────────────────────┬─────────────────────────────────────────────────────────────────┐
│  LAYER   │    LAYER NAME        │   REAL-WORLD PROTOCOLS / EXAMPLES                              │
├──────────┼──────────────────────┼─────────────────────────────────────────────────────────────────┤
│  Layer 7 │  Application         │  HTTP, HTTPS, FTP, SMTP, POP3, IMAP, DNS, Telnet, SNMP         │
├──────────┼──────────────────────┼─────────────────────────────────────────────────────────────────┤
│  Layer 6 │  Presentation        │  SSL/TLS (encryption), JPEG, MPEG, GIF, ASCII, Unicode         │
├──────────┼──────────────────────┼─────────────────────────────────────────────────────────────────┤
│  Layer 5 │  Session             │  NetBIOS, RPC, PAP, NFS, SQL session management                │
├──────────┼──────────────────────┼─────────────────────────────────────────────────────────────────┤
│  Layer 4 │  Transport           │  TCP (reliable), UDP (fast), Port numbers (80, 443, 21, 25)    │
├──────────┼──────────────────────┼─────────────────────────────────────────────────────────────────┤
│  Layer 3 │  Network             │  IP (IPv4, IPv6), ICMP (ping), ARP, OSPF, RIP, BGP            │
├──────────┼──────────────────────┼─────────────────────────────────────────────────────────────────┤
│  Layer 2 │  Data Link           │  Ethernet (IEEE 802.3), Wi-Fi (IEEE 802.11), PPP, HDLC         │
├──────────┼──────────────────────┼─────────────────────────────────────────────────────────────────┤
│  Layer 1 │  Physical            │  Ethernet cables, Fiber optic, Coaxial, Radio waves, USB        │
└──────────┴──────────────────────┴─────────────────────────────────────────────────────────────────┘
```

---

## 🔷 SECTION 10: Complete OSI Layer Summary — Master Reference

```
┌──────────┬───────────────────┬───────────┬─────────────────────┬──────────────────────┬───────────────────────┐
│  LAYER # │    LAYER NAME     │    PDU    │   KEY FUNCTION      │   KEY PROTOCOL/TECH  │   KEY DEVICE          │
├──────────┼───────────────────┼───────────┼─────────────────────┼──────────────────────┼───────────────────────┤
│    7     │  Application      │   Data    │  User interface,    │  HTTP, FTP, SMTP,    │  Gateway, Firewall    │
│          │                   │           │  network services   │  DNS, Telnet         │                       │
├──────────┼───────────────────┼───────────┼─────────────────────┼──────────────────────┼───────────────────────┤
│    6     │  Presentation     │   Data    │  Translation,       │  SSL/TLS, JPEG,      │  (Software-based)     │
│          │                   │           │  Encryption,        │  MPEG, ASCII         │                       │
│          │                   │           │  Compression        │                      │                       │
├──────────┼───────────────────┼───────────┼─────────────────────┼──────────────────────┼───────────────────────┤
│    5     │  Session          │   Data    │  Session setup,     │  NetBIOS, RPC        │  (Software-based)     │
│          │                   │           │  maintenance,       │                      │                       │
│          │                   │           │  termination        │                      │                       │
├──────────┼───────────────────┼───────────┼─────────────────────┼──────────────────────┼───────────────────────┤
│    4     │  Transport        │  Segment  │  End-to-end         │  TCP, UDP            │  Firewall,            │
│          │                   │           │  reliability,       │                      │  Load Balancer        │
│          │                   │           │  Flow/Error control │                      │                       │
├──────────┼───────────────────┼───────────┼─────────────────────┼──────────────────────┼───────────────────────┤
│    3     │  Network          │  Packet   │  Routing, Logical   │  IP, ICMP, ARP       │  ROUTER               │
│          │                   │           │  addressing (IP)    │  OSPF, RIP           │                       │
├──────────┼───────────────────┼───────────┼─────────────────────┼──────────────────────┼───────────────────────┤
│    2     │  Data Link        │  Frame    │  Framing, Physical  │  Ethernet, Wi-Fi     │  SWITCH, BRIDGE       │
│          │                   │           │  addressing (MAC),  │  PPP, HDLC           │                       │
│          │                   │           │  Error detection    │                      │                       │
├──────────┼───────────────────┼───────────┼─────────────────────┼──────────────────────┼───────────────────────┤
│    1     │  Physical         │   Bits    │  Bit transmission,  │  Cables, Fiber       │  HUB, REPEATER        │
│          │                   │           │  Signal conversion  │  Radio, USB          │  MODEM                │
└──────────┴───────────────────┴───────────┴─────────────────────┴──────────────────────┴───────────────────────┘
```

---

## 🔷 SECTION 11: Common PYQ Traps — OSI Model

```
🚨 TRAP 1: "OSI has 5 layers" or "OSI has 4 layers" → FALSE!
   OSI = EXACTLY 7 LAYERS. Always 7.

🚨 TRAP 2: "Physical Layer PDU = Frame" → FALSE!
   Physical Layer = BITS only.
   Frame = Data LINK Layer (Layer 2).

🚨 TRAP 3: "Router works at Data Link Layer" → FALSE!
   Router = Layer 3 (Network Layer).
   Switch = Layer 2 (Data Link Layer).

🚨 TRAP 4: "Hub works at Data Link Layer" → FALSE!
   Hub = Layer 1 (Physical Layer). Hub is dumb — no address reading.
   Switch = Layer 2 — Switch is smart, reads MAC addresses.

🚨 TRAP 5: "TCP is at the Network Layer" → FALSE!
   TCP = Transport Layer (Layer 4).
   IP = Network Layer (Layer 3).
   Remember: TCP/IP → Transport/Network (different layers!)

🚨 TRAP 6: "Encryption happens at Network Layer" → FALSE!
   Encryption = Presentation Layer (Layer 6).

🚨 TRAP 7: "Packet is the PDU at Transport Layer" → FALSE!
   Transport = SEGMENT.
   Network = PACKET.

🚨 TRAP 8: "Data Link Layer uses IP addresses" → FALSE!
   Data Link Layer = MAC addresses.
   Network Layer = IP addresses.

🚨 TRAP 9: "Session Layer creates the physical connection" → FALSE!
   Session Layer = LOGICAL connection (dialog management).
   Physical Layer = actual physical transmission.

🚨 TRAP 10: "FTP is a Transport Layer protocol" → FALSE!
   FTP = Application Layer (Layer 7).
   Transport = TCP/UDP only.

🚨 TRAP 11: "ISO developed TCP/IP" → FALSE!
   OSI Model developed by ISO.
   TCP/IP developed by DARPA (US Department of Defense).

🚨 TRAP 12: "OSI Model is ACTUALLY used in the internet today" → FALSE!
   OSI is a REFERENCE MODEL (theoretical framework).
   The Internet actually uses TCP/IP model (4 layers).
   But OSI is studied because it explains networking concepts clearly.
```

---

# PART 2: GENERAL STUDIES
## 🏛️ Indian Polity — Structure and Functions of Parliament

---

## 🔷 SECTION 1: Overview — What is Parliament?

### Real-Life Analogy — A Village Panchayat on a National Scale:

In a village, the Gram Panchayat makes decisions FOR the village. Members are elected by villagers. They pass rules (laws), control money, and hold the sarpanch (executive) accountable.

India's Parliament does the same, but at the NATIONAL level:
- Elected by ALL citizens
- Makes laws for the entire country
- Controls national finances
- Holds the government accountable

> **Parliament = The Supreme Legislative Body of India. It represents the people and makes laws for the nation.**

### Constitutional Provision:
```
ARTICLE 79 of the Indian Constitution:
  "There shall be a Parliament for the Union which shall consist of:
   (a) The President of India
   (b) The Council of States (Rajya Sabha)
   (c) The House of the People (Lok Sabha)"

FORMULA:
  PARLIAMENT = PRESIDENT + RAJYA SABHA + LOK SABHA

❗ IMPORTANT: The PRESIDENT is PART of Parliament (but NOT a member of either House!)
   The President summons, prorogues, and addresses Parliament.
```

---

## 🔷 SECTION 2: LOK SABHA — House of the People

### Basic Facts:
```
OFFICIAL NAME:    House of the People (Lok Sabha)
TYPE:             Lower House (First Chamber / Popular Chamber)
NATURE:           Temporary House — dissolves every 5 years (or earlier)
REPRESENTS:       Directly elected by the people of India
ARTICLES:         Articles 81, 83, 84, 85 mainly
```

### Composition:
```
MAXIMUM STRENGTH:   552 members total
  → 530 members from States (elected from constituencies)
  → 20 members from Union Territories
  → 2 members nominated by President (Anglo-Indian community)*
    *Note: Anglo-Indian nomination ABOLISHED by 104th Constitutional Amendment Act, 2019
    
CURRENT EFFECTIVE MAXIMUM: 550 elected members

PRESENT STRENGTH: 543 seats (currently functioning)

QUALIFYING AGE: Minimum 25 years to become a Lok Sabha member
```

### Term and Dissolution:
```
NORMAL TERM: 5 years from the date of its FIRST SITTING after a general election
EXCEPTION 1: President can dissolve Lok Sabha BEFORE 5 years
             (on advice of Council of Ministers — when government loses majority)
EXCEPTION 2: During National Emergency (Article 352) — Lok Sabha's term can be
             EXTENDED by Parliament by 1 year at a time

CURRENT LOK SABHA: 18th Lok Sabha (elected 2024)
SPEAKER: Om Birla (as of 2024)
DEPUTY SPEAKER: (Position may be filled)
```

### Key Powers of Lok Sabha:
```
1. FINANCIAL POWERS (Most powerful — superior to Rajya Sabha!):
   → Money Bills ORIGINATE ONLY in Lok Sabha (NEVER in Rajya Sabha)
   → Rajya Sabha can only suggest amendments — cannot reject a Money Bill
   → Rajya Sabha must return Money Bill within 14 days
   → If not returned within 14 days → DEEMED PASSED by both Houses

2. CONFIDENCE IN GOVERNMENT:
   → Council of Ministers (Cabinet) is COLLECTIVELY responsible to Lok Sabha
   → If Lok Sabha passes a vote of NO CONFIDENCE → Government MUST resign
   → Rajya Sabha CANNOT pass a no-confidence motion

3. LEGISLATION:
   → Participates equally in passing Ordinary Bills
   → In case of deadlock → Joint Sitting (combined meeting) — Lok Sabha usually wins
     (Lok Sabha has more members than Rajya Sabha)

4. JOINT SESSION:
   → President summons joint sitting of both Houses
   → Only for Ordinary Bills (NOT for Money Bills or Constitutional Amendment Bills)
   → Speaker of Lok Sabha presides over Joint Session
```

### 🎯 PYQ FACTS:
```
✅ Lok Sabha = Lower House = Temporary (5 years)
✅ Maximum strength = 552 (practically 543)
✅ Minimum age = 25 years
✅ Money Bills ONLY originate in Lok Sabha
✅ Government (Cabinet) responsible to Lok Sabha (not Rajya Sabha)
✅ Lok Sabha Speaker presides over Joint Session
✅ Lok Sabha can be dissolved by President; Rajya Sabha CANNOT be dissolved
```

---

## 🔷 SECTION 3: RAJYA SABHA — Council of States

### Basic Facts:
```
OFFICIAL NAME:    Council of States (Rajya Sabha)
TYPE:             Upper House (Second Chamber / Permanent House)
NATURE:           PERMANENT — never dissolved as a whole
REPRESENTS:       States and Union Territories
ARTICLES:         Articles 80, 83, 84
```

### Composition:
```
MAXIMUM STRENGTH:   250 members total
  → 238 members from States + Union Territories (elected by State legislatures)
  → 12 members NOMINATED by President
    (from distinguished persons in literature, science, art, social service)

PRESENT STRENGTH: 245 members

QUALIFYING AGE: Minimum 30 years to become a Rajya Sabha member
(🚨 TRAP: Rajya Sabha = 30 years; Lok Sabha = 25 years — frequently confused!)
```

### Retirement Mechanism (Why it's "Permanent"):
```
TERM OF EACH MEMBER: 6 years
RETIREMENT: 1/3rd of members retire every 2 YEARS
            (and fresh elections held for those seats)

RESULT: Rajya Sabha NEVER fully dissolves!
  → Some members always remain (continuity!)
  → Called PERMANENT HOUSE because it cannot be dissolved

ANALOGY: Like a relay race — some runners are always on the track,
         new ones join, old ones leave — but the race never stops!
```

### Special (Exclusive) Powers of Rajya Sabha:
```
POWERS ONLY RAJYA SABHA CAN EXERCISE (not Lok Sabha):

1. ARTICLE 249 — Empowering Parliament on State Subjects:
   → Normally Parliament cannot make laws on State List subjects
   → If Rajya Sabha passes a resolution by 2/3 majority →
     Parliament can make laws on State List subject for 1 year

2. ARTICLE 312 — Creation of All-India Services:
   → All-India Services (IAS, IPS, IFS) created only if Rajya Sabha passes
     resolution by 2/3 majority
   → Example: If a new All-India Service needs to be created → Rajya Sabha alone decides

3. REPRESENTS STATES:
   → Rajya Sabha gives voice to states in central legislation
   → Protects states from over-centralization by Union

WHAT RAJYA SABHA CANNOT DO (Lok Sabha's exclusive domain):
  → Cannot introduce Money Bills
  → Cannot pass vote of no confidence against government
  → In Joint Session, Rajya Sabha's smaller numbers are outvoted
```

### Comparison — Lok Sabha vs Rajya Sabha:

```
┌──────────────────────────┬──────────────────────────────┬──────────────────────────────┐
│         FEATURE          │         LOK SABHA            │         RAJYA SABHA          │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Official Name            │ House of the People          │ Council of States            │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Type                     │ Lower House                  │ Upper House                  │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Nature                   │ Temporary (5 year term)      │ Permanent (never dissolved)  │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Maximum Strength         │ 552 (nominally)              │ 250                          │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Present Strength         │ 543                          │ 245                          │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Min. Age of Member       │ 25 years                     │ 30 years                     │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Term of Members          │ 5 years (or till dissolution)│ 6 years                      │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Election Method          │ Direct election by voters    │ Indirect election by State   │
│                          │                              │ legislative assemblies       │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Nominated Members        │ 2 (Anglo-Indian) [abolished] │ 12 (President nominates)     │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Presiding Officer        │ SPEAKER                      │ CHAIRMAN                     │
│                          │ (elected from members)       │ (Vice President is Chairman) │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Money Bills              │ Originates ONLY here         │ Cannot originate Money Bills │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ No-Confidence Motion     │ CAN pass no-confidence       │ CANNOT pass no-confidence    │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Joint Session            │ Speaker presides             │ Participates (outnumbered)   │
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Special Powers           │ Financial control            │ Art. 249 (State List laws),  │
│                          │ Government accountability    │ Art. 312 (All-India Services)│
├──────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│ Representation           │ Population (people)          │ States of India              │
└──────────────────────────┴──────────────────────────────┴──────────────────────────────┘
```

### 🎯 PYQ FACTS:
```
✅ Rajya Sabha = Permanent House (never dissolved as a whole)
✅ Rajya Sabha = 1/3rd members retire every 2 years
✅ Vice President of India = Ex-officio Chairman of Rajya Sabha
✅ Rajya Sabha member's term = 6 years
✅ Minimum age for Rajya Sabha = 30 years (NOT 25!)
✅ Rajya Sabha special power = Article 249 (State List), Article 312 (All-India Services)
```

---

## 🔷 SECTION 4: THE PRESIDENT — Role in Parliament

```
CONSTITUTIONAL PROVISION: Article 79
Parliament = President + Rajya Sabha + Lok Sabha

PRESIDENT'S ROLE IN PARLIAMENT:

1. SUMMONS Parliament (calls it to meet)
2. PROROGUES Parliament (ends a session)
3. DISSOLVES Lok Sabha (can dissolve on advice of PM/Council of Ministers)
4. ADDRESSES Parliament:
   → At the commencement of the first session after each general election
   → At the commencement of the first session each year (both Houses together)
5. ASSENT TO BILLS: No bill becomes law without President's assent
6. NOMINATES 12 members to Rajya Sabha

IMPORTANT: President is NOT a MEMBER of either House
           But CONSTITUTIONALLY, President is part of Parliament

🚨 TRAP: "President is a member of Rajya Sabha" → FALSE!
         President is PART OF Parliament but NOT a MEMBER of any House.
         President cannot attend sessions, cannot vote.
```

---

## 🔷 SECTION 5: Functions of Parliament

### Three Core Functions:

```
1. LEGISLATIVE FUNCTION (Making Laws):
   → Parliament is the supreme law-making body at the national level
   → Can make laws on UNION LIST (97 subjects): Defense, Foreign Affairs, Banking
   → Can make laws on CONCURRENT LIST (52 subjects): Education, Criminal Law
   → Cannot make laws on STATE LIST (66 subjects) — except under special circumstances
   
   HOW A BILL BECOMES LAW:
   Bill Introduced in House → Passed by that House → Passed by other House →
   President's Assent → Becomes ACT (Law)

2. FINANCIAL FUNCTION (Control over money):
   → Government CANNOT spend public money without Parliament's approval
   → BUDGET presented in Lok Sabha (Finance Bill = type of Money Bill)
   → Consolidated Fund of India — Parliament controls withdrawals
   → CAG (Comptroller and Auditor General) reports to Parliament

3. EXECUTIVE CONTROL (Keeping government accountable):
   → Question Hour (first hour of each session) — MPs question ministers
   → Zero Hour — informal time for urgent matters
   → Calling Attention Motion — draw minister's attention to urgent matters
   → Censure Motion / No-Confidence Motion — ultimate accountability tool
   → Parliamentary Committees examine government work in detail

🎯 PYQ FACT: The MOST IMPORTANT function of Parliament = Law making
🎯 PYQ FACT: Question Hour = First hour of each parliamentary sitting
🎯 PYQ FACT: Zero Hour = Starts at 12 noon (hence "Zero Hour")
```

---

## 🔷 SECTION 6: Important Parliament Facts for PYQ

```
SESSIONS OF PARLIAMENT (3 in a year):
  → Budget Session: Feb–May (LONGEST session; Budget presented)
  → Monsoon Session: July–August
  → Winter Session: November–December (shortest)

QUORUM:
  → Minimum members required for proceedings
  → Lok Sabha: 1/10th of total membership = ~55 members
  → Rajya Sabha: 1/10th of total membership = ~25 members

JOINT SESSION (ARTICLE 108):
  → Convened by President
  → Presided by SPEAKER of Lok Sabha
  → Called when ordinary bill stuck in deadlock
  → CANNOT be held for: Money Bills, Constitution Amendment Bills

MONEY BILL (ARTICLE 110):
  → Only in Lok Sabha
  → Speaker certifies a bill as a Money Bill
  → Rajya Sabha cannot amend/reject — only suggest, must return in 14 days
  → If not returned in 14 days → deemed passed by BOTH houses

CONSTITUTIONAL AMENDMENT (ARTICLE 368):
  → Special majority: 2/3 majority of members present and voting
    PLUS more than 50% of total membership of each House
  → Some amendments also need ratification by half of State Legislatures
  → President MUST give assent (no pocket veto for amendment bills)

PRIVILEGED POSITIONS:
  → Speaker of Lok Sabha: Om Birla (18th Lok Sabha, 2024)
  → Chairman of Rajya Sabha = Vice President of India = Jagdeep Dhankhar
  → Deputy Chairman of Rajya Sabha = Harivansh Narayan Singh
```

### 🚨 PYQ Traps — Parliament:

```
🚨 TRAP 1: "Rajya Sabha can originate Money Bills" → FALSE!
   Money Bills originate ONLY in Lok Sabha.

🚨 TRAP 2: "Rajya Sabha can be dissolved" → FALSE!
   Rajya Sabha is PERMANENT — never dissolved.
   Only LOK SABHA can be dissolved.

🚨 TRAP 3: "President is a member of Lok Sabha" → FALSE!
   President is part of Parliament but NOT a member of any House.

🚨 TRAP 4: "Minimum age for Rajya Sabha = 25 years" → FALSE!
   Rajya Sabha = 30 years; Lok Sabha = 25 years.

🚨 TRAP 5: "Lok Sabha has more nominated members than Rajya Sabha" → FALSE!
   Rajya Sabha has 12 nominated members.
   Lok Sabha's 2 nominated Anglo-Indian seats are now abolished.

🚨 TRAP 6: "Speaker presides over Rajya Sabha" → FALSE!
   Rajya Sabha Chairman = Vice President of India.
   Speaker presides only over Lok Sabha.

🚨 TRAP 7: "Joint Session presided by President" → FALSE!
   Joint Session presided by SPEAKER OF LOK SABHA.

🚨 TRAP 8: "Parliament can make laws on State List freely" → FALSE!
   Parliament can legislate on State List ONLY under Article 249 
   (Rajya Sabha 2/3 resolution), Article 250 (National Emergency),
   or Article 252 (consent of 2+ states).

🚨 TRAP 9: "Rajya Sabha has power to pass no-confidence motion" → FALSE!
   No-confidence motion ONLY in LOK SABHA.

🚨 TRAP 10: "Budget is presented in Rajya Sabha" → FALSE!
   Budget (Finance Bill = Money Bill) → presented in LOK SABHA only.
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: OSI Model, Layers, Functions, Data Units, Network Types, Devices

---

**Q1.** The OSI (Open Systems Interconnection) model was developed by:
(A) IEEE (Institute of Electrical and Electronics Engineers)
(B) ISO (International Organization for Standardization)
(C) IETF (Internet Engineering Task Force)
(D) More than one of the above
(E) None of the above

---

**Q2.** How many layers does the OSI model have?
(A) 4
(B) 5
(C) 7
(D) More than one of the above
(E) None of the above

---

**Q3.** Which of the following correctly lists the OSI layers from Layer 7 (top) to Layer 1 (bottom)?
(A) Physical, Data Link, Network, Transport, Session, Presentation, Application
(B) Application, Presentation, Session, Transport, Network, Data Link, Physical
(C) Application, Session, Presentation, Network, Transport, Data Link, Physical
(D) More than one of the above
(E) None of the above

---

**Q4.** The Protocol Data Unit (PDU) at the Transport Layer is called a:
(A) Packet
(B) Frame
(C) Segment
(D) More than one of the above
(E) None of the above

---

**Q5.** The PDU at the Network Layer is called a:
(A) Segment
(B) Frame
(C) Packet
(D) More than one of the above
(E) None of the above

---

**Q6.** The PDU at the Data Link Layer is called a:
(A) Packet
(B) Frame
(C) Segment
(D) More than one of the above
(E) None of the above

---

**Q7.** The Physical Layer is responsible for transmitting:
(A) Packets
(B) Frames
(C) Bits (raw 0s and 1s)
(D) More than one of the above
(E) None of the above

---

**Q8.** Encryption and compression of data is handled by which OSI layer?
(A) Application Layer (Layer 7)
(B) Session Layer (Layer 5)
(C) Presentation Layer (Layer 6)
(D) More than one of the above
(E) None of the above

---

**Q9.** Which layer is responsible for ROUTING data packets from source to destination?
(A) Data Link Layer
(B) Transport Layer
(C) Network Layer
(D) More than one of the above
(E) None of the above

---

**Q10.** A ROUTER primarily operates at which OSI layer?
(A) Physical Layer (Layer 1)
(B) Data Link Layer (Layer 2)
(C) Network Layer (Layer 3)
(D) More than one of the above
(E) None of the above

---

**Q11.** A SWITCH primarily operates at which OSI layer?
(A) Physical Layer (Layer 1)
(B) Data Link Layer (Layer 2)
(C) Network Layer (Layer 3)
(D) More than one of the above
(E) None of the above

---

**Q12.** A HUB operates at which OSI layer?
(A) Physical Layer (Layer 1)
(B) Data Link Layer (Layer 2)
(C) Network Layer (Layer 3)
(D) More than one of the above
(E) None of the above

---

**Q13.** Which of the following protocols belong to the APPLICATION LAYER of the OSI model?
(A) TCP and UDP
(B) IP and ICMP
(C) HTTP, FTP, SMTP, DNS
(D) More than one of the above
(E) None of the above

---

**Q14.** The Session Layer (Layer 5) is primarily responsible for:
(A) Converting data formats and encrypting data
(B) Establishing, maintaining, and terminating sessions between applications
(C) Routing packets across different networks
(D) More than one of the above
(E) None of the above

---

**Q15.** TCP (Transmission Control Protocol) operates at which OSI layer?
(A) Network Layer (Layer 3)
(B) Transport Layer (Layer 4)
(C) Session Layer (Layer 5)
(D) More than one of the above
(E) None of the above

---

**Q16.** MAC (Media Access Control) addresses are used at which OSI layer?
(A) Network Layer — because IP addresses are used here
(B) Physical Layer — because it handles actual transmission
(C) Data Link Layer — physical addressing between directly connected devices
(D) More than one of the above
(E) None of the above

---

**Q17.** The process of adding headers to data as it moves DOWN from Application to Physical layer is called:
(A) Decapsulation
(B) Multiplexing
(C) Encapsulation
(D) More than one of the above
(E) None of the above

---

**Q18.** Which type of network covers a SINGLE BUILDING or campus?
(A) WAN (Wide Area Network)
(B) MAN (Metropolitan Area Network)
(C) LAN (Local Area Network)
(D) More than one of the above
(E) None of the above

---

**Q19.** The Internet is an example of which type of network?
(A) LAN
(B) MAN
(C) WAN
(D) More than one of the above
(E) None of the above

---

**Q20.** Which of the following correctly describes TCP vs UDP?
(A) TCP is fast and connectionless; UDP is reliable and connection-oriented
(B) TCP is reliable and connection-oriented; UDP is fast and connectionless
(C) TCP and UDP both provide reliable, ordered delivery
(D) More than one of the above
(E) None of the above

---

**Q21.** The ANSI-SPARC three-level architecture and the OSI 7-layer model are both examples of:
(A) Physical network configurations
(B) LAYERED ABSTRACTION — separating concerns at different levels
(C) Programming language specifications
(D) More than one of the above
(E) None of the above

---

**Q22.** Which of the following are correctly matched (OSI Layer → PDU)?
I.   Transport Layer → Segment
II.  Network Layer → Frame
III. Data Link Layer → Frame
IV.  Physical Layer → Bits

(A) I, III, and IV only
(B) I, II, and III only
(C) All of I, II, III, IV
(D) More than one of the above
(E) None of the above

---

**Q23.** IP address belongs to which OSI layer?
(A) Data Link Layer
(B) Transport Layer
(C) Network Layer
(D) More than one of the above
(E) None of the above

---

**Q24.** A Repeater is a Physical Layer device. Its PRIMARY function is to:
(A) Read MAC addresses and forward frames to the correct port
(B) Regenerate and amplify signals to extend network distance
(C) Route packets based on IP addresses
(D) More than one of the above
(E) None of the above

---

**Q25.** Which statement about the OSI model is CORRECT?
(A) OSI model is the actual model used by the Internet today
(B) OSI has 4 layers; TCP/IP has 7 layers
(C) OSI is a conceptual/reference model; the Internet actually uses TCP/IP (4 layers)
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: Indian Parliament — Lok Sabha, Rajya Sabha, President, Powers, Functions

---

**Q26.** According to Article 79 of the Indian Constitution, Parliament consists of:
(A) Lok Sabha and Rajya Sabha only
(B) President, Rajya Sabha, and Lok Sabha
(C) Prime Minister, Lok Sabha, and Rajya Sabha
(D) More than one of the above
(E) None of the above

---

**Q27.** Lok Sabha is known as:
(A) Upper House / Permanent House
(B) Lower House / House of the People
(C) House of States / Council of States
(D) More than one of the above
(E) None of the above

---

**Q28.** The MAXIMUM strength of Lok Sabha (as originally provided) is:
(A) 545 members
(B) 543 members
(C) 552 members
(D) More than one of the above
(E) None of the above

---

**Q29.** The minimum age required to become a MEMBER OF RAJYA SABHA is:
(A) 21 years
(B) 25 years
(C) 30 years
(D) More than one of the above
(E) None of the above

---

**Q30.** Rajya Sabha is called the "Permanent House" because:
(A) Its members serve for life and never retire
(B) It is never dissolved as a whole; 1/3rd members retire every 2 years
(C) It was the first legislative house created in India
(D) More than one of the above
(E) None of the above

---

**Q31.** Who is the EX-OFFICIO CHAIRMAN of the Rajya Sabha?
(A) Speaker of Lok Sabha
(B) President of India
(C) Vice President of India
(D) More than one of the above
(E) None of the above

---

**Q32.** A Money Bill can be introduced ONLY in:
(A) Rajya Sabha
(B) Either House of Parliament
(C) Lok Sabha
(D) More than one of the above
(E) None of the above

---

**Q33.** After a Money Bill is passed by Lok Sabha and sent to Rajya Sabha, Rajya Sabha MUST return it within:
(A) 7 days
(B) 14 days
(C) 30 days
(D) More than one of the above
(E) None of the above

---

**Q34.** The Council of Ministers is COLLECTIVELY RESPONSIBLE to:
(A) Rajya Sabha
(B) The President of India
(C) Lok Sabha
(D) More than one of the above
(E) None of the above

---

**Q35.** A JOINT SESSION of both Houses of Parliament is presided over by:
(A) President of India
(B) Chairman of Rajya Sabha (Vice President)
(C) Speaker of Lok Sabha
(D) More than one of the above
(E) None of the above

---

**Q36.** Which ARTICLE empowers Rajya Sabha, by 2/3 majority resolution, to allow Parliament to legislate on State List subjects?
(A) Article 248
(B) Article 249
(C) Article 312
(D) More than one of the above
(E) None of the above

---

**Q37.** How many members does the PRESIDENT NOMINATE to the Rajya Sabha?
(A) 2 members
(B) 10 members
(C) 12 members
(D) More than one of the above
(E) None of the above

---

**Q38.** Which of the following statements is CORRECT about Joint Session of Parliament?
(A) Joint Session can be called for both Money Bills and Ordinary Bills
(B) Speaker of Rajya Sabha presides over Joint Session
(C) Joint Session is convened by the President; Speaker of Lok Sabha presides; applicable only to Ordinary Bills
(D) More than one of the above
(E) None of the above

---

**Q39.** The term of a Rajya Sabha member is:
(A) 5 years
(B) 6 years
(C) Same as Lok Sabha members — till dissolution
(D) More than one of the above
(E) None of the above

---

**Q40.** The Budget (Annual Financial Statement) is presented in:
(A) Rajya Sabha — as it's the Upper House
(B) Both Houses simultaneously in a joint session
(C) Lok Sabha — as the Budget is a Money Bill
(D) More than one of the above
(E) None of the above

---

**Q41.** A vote of NO-CONFIDENCE against the government can ONLY be passed in:
(A) Rajya Sabha — as it's the Upper House
(B) A Joint Session of both Houses
(C) Lok Sabha
(D) More than one of the above
(E) None of the above

---

**Q42.** Under Article 312 of the Constitution, which House has the SPECIAL POWER to authorize creation of new All-India Services?
(A) Lok Sabha, by simple majority
(B) Rajya Sabha, by 2/3rd majority of members present and voting
(C) Both Houses in joint session
(D) More than one of the above
(E) None of the above

---

**Q43.** Which of the following is the CORRECT role of the President with respect to Parliament?
(A) President is a permanent member of Lok Sabha
(B) President is part of Parliament but not a member of either House; summons, prorogues, dissolves Lok Sabha
(C) President votes only in cases of tie in Rajya Sabha
(D) More than one of the above
(E) None of the above

---

**Q44.** The MINIMUM number of members required to be present (quorum) for conducting business in Lok Sabha is:
(A) 50 members
(B) 1/10th of total membership
(C) 1/4th of total membership
(D) More than one of the above
(E) None of the above

---

**Q45.** Consider the following pairs — which are CORRECTLY matched?
I.   Rajya Sabha Chairman → Vice President of India
II.  Lok Sabha Speaker → presides over Joint Sessions
III. President → nominates 12 members to Rajya Sabha
IV.  Rajya Sabha → can originate Money Bills

(A) I, II, and III only
(B) I, II, III, and IV all correct
(C) I and III only
(D) More than one of the above
(E) None of the above

---

**Q46.** Under Article 108, a Joint Session of Parliament CANNOT be convened for:
(A) Ordinary Bills that have been rejected or delayed
(B) Money Bills and Constitutional Amendment Bills
(C) Bills relating to banking regulations
(D) More than one of the above
(E) None of the above

---

**Q47.** The MAXIMUM strength of Rajya Sabha is:
(A) 238 members
(B) 245 members
(C) 250 members
(D) More than one of the above
(E) None of the above

---

**Q48.** "Question Hour" in Parliament refers to:
(A) The last hour of each parliamentary session
(B) The first hour of each sitting where MPs question ministers
(C) A special session called once a week for questions
(D) More than one of the above
(E) None of the above

---

**Q49.** Which of the following statements about the 104th Constitutional Amendment Act (2019) is CORRECT?
(A) It increased the strength of Rajya Sabha to 250
(B) It abolished the provision for nomination of Anglo-Indian members to Lok Sabha and State Assemblies
(C) It extended the term of Lok Sabha from 5 to 6 years
(D) More than one of the above
(E) None of the above

---

**Q50.** Consider these statements about Indian Parliament:
I. Parliament can make laws on all 3 Lists (Union, State, Concurrent) without restriction.
II. Rajya Sabha represents the states of India.
III. Lok Sabha has greater powers over financial matters than Rajya Sabha.
IV. A Constitutional Amendment requires the same simple majority as ordinary bills.
Which statements are CORRECT?

(A) I and IV only
(B) II and III only
(C) I, II, and III only
(D) More than one of the above
(E) None of the above

---

# ✅ ANSWER KEY

## ⚠️ ATTEMPT ALL 50 QUESTIONS BEFORE CHECKING ANSWERS

---

### CS Answers (Q1–Q25):

| Q  | Ans | Key Reason |
|----|-----|-----------|
| 1  | (B) | OSI developed by ISO (International Organization for Standardization) in 1984 |
| 2  | (C) | OSI = exactly 7 layers — always |
| 3  | (B) | Top to Bottom: Application, Presentation, Session, Transport, Network, Data Link, Physical |
| 4  | (C) | Transport Layer PDU = Segment (not packet!) |
| 5  | (C) | Network Layer PDU = Packet |
| 6  | (B) | Data Link Layer PDU = Frame |
| 7  | (C) | Physical Layer = Bits (raw 0s and 1s) — never frames or packets |
| 8  | (C) | Encryption and Compression = Presentation Layer (Layer 6) |
| 9  | (C) | Routing = Network Layer (Layer 3) |
| 10 | (C) | Router = Network Layer (Layer 3) |
| 11 | (B) | Switch = Data Link Layer (Layer 2) — reads MAC addresses |
| 12 | (A) | Hub = Physical Layer (Layer 1) — dumb device, no address reading |
| 13 | (C) | HTTP, FTP, SMTP, DNS = Application Layer; TCP/UDP = Transport; IP = Network |
| 14 | (B) | Session Layer = session establishment, maintenance, termination |
| 15 | (B) | TCP = Transport Layer (Layer 4) |
| 16 | (C) | MAC address = Data Link Layer (Layer 2) |
| 17 | (C) | Adding headers going DOWN = Encapsulation |
| 18 | (C) | LAN = single building or campus |
| 19 | (C) | Internet = WAN (largest WAN in the world) |
| 20 | (B) | TCP = reliable, connection-oriented; UDP = fast, connectionless |
| 21 | (B) | Both are examples of layered abstraction separating concerns |
| 22 | (A) | I correct (Transport=Segment), II WRONG (Network=Packet not Frame), III correct (Data Link=Frame), IV correct (Physical=Bits) |
| 23 | (C) | IP address = Network Layer (Layer 3) |
| 24 | (B) | Repeater = regenerates/amplifies signals over long distance |
| 25 | (C) | OSI = reference/conceptual model; Internet uses TCP/IP (4 layers) |

---

### GS Answers (Q26–Q50):

| Q  | Ans | Key Reason |
|----|-----|-----------|
| 26 | (B) | Article 79: Parliament = President + Rajya Sabha + Lok Sabha |
| 27 | (B) | Lok Sabha = Lower House / House of the People |
| 28 | (C) | Maximum = 552 (530 States + 20 UTs + 2 nominated — now nominally 550 after 104th amendment) |
| 29 | (C) | Rajya Sabha minimum age = 30 years (Lok Sabha = 25 years) |
| 30 | (B) | Permanent = never dissolved; 1/3rd retire every 2 years |
| 31 | (C) | Vice President of India = Ex-officio Chairman of Rajya Sabha |
| 32 | (C) | Money Bills originate ONLY in Lok Sabha (Article 110) |
| 33 | (B) | Rajya Sabha must return Money Bill within 14 days |
| 34 | (C) | Council of Ministers collectively responsible to Lok Sabha |
| 35 | (C) | Speaker of Lok Sabha presides over Joint Session (Article 108) |
| 36 | (B) | Article 249 = Rajya Sabha 2/3 majority → Parliament can legislate on State List |
| 37 | (C) | President nominates 12 members to Rajya Sabha |
| 38 | (C) | Joint Session: by President; Speaker presides; only for Ordinary Bills (not Money/Amendment Bills) |
| 39 | (B) | Rajya Sabha member term = 6 years |
| 40 | (C) | Budget = Finance Bill = Money Bill → only Lok Sabha |
| 41 | (C) | No-confidence motion ONLY in Lok Sabha |
| 42 | (B) | Article 312: Rajya Sabha by 2/3 majority creates new All-India Services |
| 43 | (B) | President = part of Parliament, not a member; summons/prorogues/dissolves |
| 44 | (B) | Quorum = 1/10th of total membership (both Houses) |
| 45 | (A) | I, II, III correct; IV wrong (Rajya Sabha CANNOT originate Money Bills) |
| 46 | (B) | Joint Session CANNOT be for Money Bills or Constitutional Amendment Bills |
| 47 | (C) | Maximum strength of Rajya Sabha = 250 |
| 48 | (B) | Question Hour = first hour of each sitting; MPs question ministers |
| 49 | (B) | 104th Amendment (2019) abolished Anglo-Indian nomination to Lok Sabha and State Assemblies |
| 50 | (B) | II (Rajya Sabha represents states) and III (Lok Sabha stronger in finance) are correct; I wrong (Parliament cannot freely legislate on State List); IV wrong (Amendment needs special majority) |

---

# 🔁 DAY 43 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Computer Networks & OSI Model

### OSI Layers — Top to Bottom (MNEMONIC):
```
"All People Seem To Need Data Processing"

Layer 7: APPLICATION   → Data     → HTTP, FTP, SMTP, DNS
Layer 6: PRESENTATION  → Data     → SSL/TLS, JPEG, Encryption
Layer 5: SESSION       → Data     → Session setup/teardown, NetBIOS
Layer 4: TRANSPORT     → Segment  → TCP (reliable), UDP (fast)
Layer 3: NETWORK       → Packet   → IP, ICMP, Routing
Layer 2: DATA LINK     → Frame    → MAC address, Ethernet, Switch
Layer 1: PHYSICAL      → Bits     → Cables, Hub, Repeater
```

### PDU Quick Reference:
```
"Sergeant Peters Fought Bravely" (Layer 4 → 1)
  S = Segment  (Transport Layer 4)
  P = Packet   (Network Layer 3)
  F = Frame    (Data Link Layer 2)
  B = Bits     (Physical Layer 1)

Layers 7, 6, 5 = all called "DATA"
```

### Device → Layer (Most-tested):
```
Hub / Repeater / Modem   →  Layer 1 (Physical)
Switch / Bridge / NIC    →  Layer 2 (Data Link)
Router                   →  Layer 3 (Network)
Gateway                  →  Layer 7 (Application)
```

### Network Types:
```
LAN = Local (building/campus) — fast, cheap, private
MAN = Metropolitan (city) — medium
WAN = Wide (country/global) — Internet is WAN
```

### PYQ Trap List — OSI:
```
✅ OSI = EXACTLY 7 layers (not 4, not 5)
✅ Physical Layer = BITS (never frames)
✅ Data Link Layer = FRAME (not packet)
✅ Network Layer = PACKET (not segment)
✅ Transport Layer = SEGMENT (not packet)
✅ Router = Layer 3 (Network) — NOT Layer 2
✅ Switch = Layer 2 (Data Link) — NOT Layer 3
✅ Hub = Layer 1 (Physical) — NOT Layer 2
✅ Encryption = Presentation Layer (NOT Session)
✅ TCP/UDP = Transport Layer (NOT Network)
✅ IP address = Network Layer; MAC address = Data Link Layer
✅ OSI = reference model; Internet uses TCP/IP (4 layers)
✅ Encapsulation = adding headers (top → bottom, sender)
✅ Decapsulation = removing headers (bottom → top, receiver)
```

---

## ⚡ RAPID FIRE — Indian Parliament

### Parliament Formula:
```
PARLIAMENT = PRESIDENT + RAJYA SABHA + LOK SABHA (Article 79)
(President is PART of Parliament but NOT a member of any House)
```

### Lok Sabha vs Rajya Sabha Quick Comparison:
```
FEATURE           │ LOK SABHA              │ RAJYA SABHA
──────────────────┼────────────────────────┼────────────────────────
Type              │ Lower House            │ Upper House
Nature            │ Temporary (5 yrs)      │ PERMANENT (never dissolved)
Max Strength      │ 552                    │ 250
Min Age           │ 25 years               │ 30 years
Member Term       │ 5 years                │ 6 years
Election          │ Direct (voters)        │ Indirect (State legislatures)
Nominated Members │ 2 (Anglo-Indian — now  │ 12 (by President)
                  │ abolished, 104th Amdt) │
Presiding Officer │ SPEAKER                │ CHAIRMAN (= Vice President)
Money Bills       │ ORIGINATES here ONLY   │ Cannot originate
No-Confidence     │ CAN pass it            │ CANNOT pass it
Joint Session     │ Speaker presides       │ (participates)
Special Powers    │ Financial control      │ Art. 249 (State List)
                  │ Govt accountability    │ Art. 312 (All-India Services)
```

### Key Numbers — Parliament:
```
Lok Sabha:   Max 552 | Present 543 | Min age 25 | Term 5 years
Rajya Sabha: Max 250 | Present 245 | Min age 30 | Term 6 years
Quorum:      1/10th of total membership (both houses)
Money Bill:  14 days for Rajya Sabha to return
President nominates: 12 to Rajya Sabha
1/3rd Rajya Sabha members retire every: 2 years
```

### PYQ Trap List — Parliament:
```
✅ Rajya Sabha CANNOT be dissolved (Permanent House)
✅ Rajya Sabha = 30 years min age (NOT 25)
✅ Rajya Sabha CANNOT introduce Money Bills
✅ Rajya Sabha CANNOT pass no-confidence motion
✅ Joint Session: presided by SPEAKER of Lok Sabha (not VP, not President)
✅ Joint Session CANNOT be for Money Bills or Constitutional Amendments
✅ Vice President = Chairman of Rajya Sabha (ex-officio)
✅ President = part of Parliament but NOT a member of either House
✅ Article 249 = Rajya Sabha empowers Parliament on State List
✅ Article 312 = Rajya Sabha creates new All-India Services
✅ Budget = Money Bill = only in Lok Sabha
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **OSI = 7 Layers** (top→bottom: Application, Presentation, Session, Transport, Network, Data Link, Physical); PDUs = Data/Data/Data/Segment/Packet/Frame/Bits; mnemonic: "All People Seem To Need Data Processing."
2. **Device-Layer mapping**: Hub=L1 (Physical), Switch=L2 (Data Link), Router=L3 (Network); MAC address=L2; IP address=L3; Encryption=L6 (Presentation); TCP/UDP=L4 (Transport).
3. **Encapsulation**: Sender adds headers going DOWN (Application→Physical); Receiver removes headers going UP (Physical→Application); Only Physical Layer has actual physical communication.
4. **Parliament Formula (Art. 79)**: Parliament = President + Rajya Sabha + Lok Sabha; President is PART of Parliament but NOT a member; Rajya Sabha is PERMANENT (never dissolved); 1/3rd retire every 2 years.
5. **Lok Sabha vs Rajya Sabha traps**: Money Bills ONLY in Lok Sabha; No-confidence ONLY in Lok Sabha; Rajya Sabha min age = 30 (not 25); Joint Session = Speaker of Lok Sabha presides; Rajya Sabha special power = Art. 249 (State List) + Art. 312 (All-India Services).

---

## 📅 DAY 44 PREVIEW — What's Coming Next:
**CS**: Computer Networks — TCP/IP Model (4 layers), Comparison with OSI, Key Protocols (TCP, UDP, IP, HTTP, FTP, SMTP, DNS), Port Numbers
**GS**: Indian Polity — Fundamental Rights (Articles 12–35): Right to Equality, Right to Freedom, Right Against Exploitation, Cultural & Educational Rights, Right to Constitutional Remedies (Article 32)

---

*🚀 Day 43 of 170 — You're 25% through the journey. OSI Model is one of the MOST REPEATED topics in CS — every layer, every PDU, every device must be locked in. You've got this!*
