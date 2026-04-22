# 📅 BPSC TRE 4.0 — DAY 44 COMPLETE STUDY MODULE
### Computer Networks: TCP/IP Model, OSI Mapping & Key Protocols + Economics — GDP Basics
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): TCP/IP Model — 4 Layers, OSI Mapping, Key Protocols, Encapsulation
> - Afternoon (1 hr): Economics — GDP: Nominal vs Real, Methods of Calculation, GDP vs GNP
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 TCP/IP Model — The Real-World Networking Framework

---

## 🔷 SECTION 1: Why Do We Need TCP/IP Model?

### The Problem with OSI:

Yesterday we studied the OSI Model — a beautiful 7-layer theoretical framework. But here's the truth that BPSC examiners sometimes test:

> **The OSI Model was NEVER actually implemented in the real Internet.**
> **The Internet runs on the TCP/IP Model — a 4-layer practical model.**

### Real-Life Analogy — Blueprint vs Actual Building:

```
OSI Model  = ARCHITECT'S BLUEPRINT
             Detailed, theoretical, precise — 7 layers
             Never actually built as-is
             But explains EVERY concept clearly!

TCP/IP Model = ACTUAL BUILDING CONSTRUCTED
               Simpler, practical — 4 layers
               What the Internet ACTUALLY uses every day
               DARPA built it for the US military (ARPANET)

BOTH are important:
  → OSI: Study it to UNDERSTAND networking (conceptual)
  → TCP/IP: Study it to understand how Internet ACTUALLY works (practical)
```

### History:
```
TCP/IP HISTORY:
  1969 → ARPANET (first version of Internet) created by US DoD (DARPA)
  1974 → Vinton Cerf & Robert Kahn designed TCP/IP protocol suite
         (Called "Fathers of the Internet")
  1983 → ARPANET officially adopted TCP/IP
  Today → ALL internet communication uses TCP/IP

OSI HISTORY:
  1984 → ISO developed OSI Model as a theoretical standard
  But by then, TCP/IP was already dominant!
  Result: OSI remained a REFERENCE MODEL, TCP/IP became the REAL standard

🎯 PYQ FACT: Vinton Cerf and Robert Kahn = Fathers of the Internet (TCP/IP designers)
🎯 PYQ FACT: TCP/IP was developed by DARPA (US Department of Defense)
🎯 PYQ FACT: OSI developed by ISO; TCP/IP developed by DARPA
```

---

## 🔷 SECTION 2: TCP/IP Model — 4 Layers Overview

### The Architecture:

```
TCP/IP MODEL — 4 LAYERS (Top to Bottom)

┌──────────────────────────────────────────────────────────────────────┐
│  Layer 4 │  APPLICATION LAYER      │  User-facing protocols          │
│          │                         │  HTTP, FTP, SMTP, DNS, Telnet   │
├──────────┼─────────────────────────┼─────────────────────────────────┤
│  Layer 3 │  TRANSPORT LAYER        │  End-to-end communication       │
│          │  (Host-to-Host Layer)   │  TCP, UDP                       │
├──────────┼─────────────────────────┼─────────────────────────────────┤
│  Layer 2 │  INTERNET LAYER         │  Routing and logical addressing │
│          │  (Network Layer)        │  IP, ICMP, ARP                  │
├──────────┼─────────────────────────┼─────────────────────────────────┤
│  Layer 1 │  NETWORK ACCESS LAYER   │  Physical transmission + framing│
│          │  (Link Layer /          │  Ethernet, Wi-Fi, MAC address   │
│          │   Host-to-Network)      │                                  │
└──────────┴─────────────────────────┴─────────────────────────────────┘

KEY POINT: TCP/IP = 4 layers (NOT 7 like OSI!)
```

### 🧠 MNEMONIC — TCP/IP Layers (Top to Bottom):
```
"A Tall Indian Ninja"

A → Application Layer     (Layer 4 — top)
T → Transport Layer       (Layer 3)
I → Internet Layer        (Layer 2)
N → Network Access Layer  (Layer 1 — bottom)
```

---

## 🔷 SECTION 3: Functions of Each TCP/IP Layer (Deep Explanation)

### LAYER 4 — APPLICATION LAYER (TCP/IP)

```
CORRESPONDS TO: OSI Layers 7 + 6 + 5
                (Application + Presentation + Session combined!)

FUNCTION: Provides all user-facing services and handles data formatting,
          session management, and application protocols.
          
          In TCP/IP, there is NO separate Presentation or Session layer —
          all their responsibilities are absorbed into the Application Layer!

WHAT IT DOES:
  → Provides network services directly to user applications
  → Handles data representation (encoding, encryption) — from OSI Presentation
  → Manages sessions — from OSI Session layer
  → Everything the user "sees" in networking happens here

KEY PROTOCOLS:
  HTTP  (Port 80)  → HyperText Transfer Protocol: Web browsing
  HTTPS (Port 443) → Secure HTTP: Encrypted web browsing
  FTP   (Port 21)  → File Transfer Protocol: Uploading/downloading files
  SMTP  (Port 25)  → Simple Mail Transfer Protocol: SENDING emails
  POP3  (Port 110) → Post Office Protocol 3: RECEIVING emails (downloads to device)
  IMAP  (Port 143) → Internet Message Access Protocol: Reading emails (stays on server)
  DNS   (Port 53)  → Domain Name System: Translates google.com → 172.217.163.46
  Telnet(Port 23)  → Remote terminal access (unsecured)
  SSH   (Port 22)  → Secure Shell: Remote terminal access (SECURED version of Telnet)
  SNMP  (Port 161) → Simple Network Management Protocol: Managing network devices
  DHCP  (Port 67/68)→ Dynamic Host Configuration Protocol: Assigns IP addresses

DATA UNIT: DATA (or MESSAGE)

REAL-LIFE ANALOGY:
  When you open a browser and type "www.google.com":
  → Your browser (Application Layer) sends an HTTP request
  → DNS (Application Layer) translates "www.google.com" to an IP address
  → HTTP retrieves the webpage
  Everything visible to you = Application Layer at work!

🎯 PYQ FACT: TCP/IP Application layer = OSI's Application + Presentation + Session (3 layers combined!)
🚨 TRAP: "SMTP is used to RECEIVE emails" → FALSE! SMTP = SENDING. POP3/IMAP = receiving.
🚨 TRAP: "DNS works at Transport Layer" → FALSE! DNS = Application Layer (Port 53).
```

---

### LAYER 3 — TRANSPORT LAYER (TCP/IP)

```
CORRESPONDS TO: OSI Layer 4 (Transport) — same name, same function!

ALTERNATIVE NAME: "Host-to-Host Layer"
                   (because it provides end-to-end communication between two HOSTS)

FUNCTION: Provides reliable (or fast) end-to-end data delivery
          between the source host and destination host.

KEY PROTOCOLS — TCP and UDP (most important!):

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TCP — TRANSMISSION CONTROL PROTOCOL
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
NATURE:  Connection-ORIENTED (establishes connection before sending)
RELIABLE: YES — guarantees delivery; lost packets are RETRANSMITTED
ORDERED:  YES — data arrives in sequence (segments numbered)
SPEED:    SLOWER (overhead of acknowledgments, connection setup)
USE WHEN: Data accuracy matters more than speed

HOW TCP ESTABLISHES CONNECTION — THE 3-WAY HANDSHAKE:
  
  Step 1: Client sends SYN (Synchronize) to Server
          → "Hello, I want to connect!"
  Step 2: Server sends SYN-ACK (Synchronize-Acknowledge) to Client
          → "OK, I hear you. I'm ready!"
  Step 3: Client sends ACK (Acknowledge) to Server
          → "Great! Let's start sending data!"
  
  ┌────────┐  SYN →          ┌────────┐
  │ CLIENT │  ← SYN-ACK      │ SERVER │
  │        │  ACK →          │        │
  └────────┘                 └────────┘
  After this 3-way handshake → data transfer begins

REAL EXAMPLES OF TCP USE:
  → Web browsing (HTTP/HTTPS) — you need the full webpage correctly
  → Email sending (SMTP) — you need every word delivered
  → File transfer (FTP) — you need the complete file without corruption
  → Online banking — every transaction must arrive perfectly

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
UDP — USER DATAGRAM PROTOCOL
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
NATURE:  Connection-LESS (just sends, no setup required)
RELIABLE: NO — no guarantee of delivery; no retransmission
ORDERED:  NO — packets may arrive out of order
SPEED:    FASTER (no overhead, no waiting for ACK)
USE WHEN: Speed matters more than perfect accuracy

REAL EXAMPLES OF UDP USE:
  → Video streaming (YouTube, Netflix) — slight glitch OK, buffering unacceptable
  → Online gaming — delay is worse than occasional dropped data
  → VoIP calls (WhatsApp calls, Zoom) — real-time, speed critical
  → DNS lookups — simple request/response, speed needed
  → Live broadcasts — real-time streaming

TCP vs UDP COMPARISON TABLE:
┌──────────────────────────┬────────────────────────────┬──────────────────────────────┐
│       FEATURE            │          TCP               │           UDP                │
├──────────────────────────┼────────────────────────────┼──────────────────────────────┤
│ Connection               │ Connection-Oriented        │ Connectionless               │
│                          │ (3-way handshake)          │ (no setup)                   │
├──────────────────────────┼────────────────────────────┼──────────────────────────────┤
│ Reliability              │ RELIABLE (ACK, retransmit) │ UNRELIABLE (no ACK)          │
├──────────────────────────┼────────────────────────────┼──────────────────────────────┤
│ Ordering                 │ Ordered delivery           │ No ordering guarantee        │
├──────────────────────────┼────────────────────────────┼──────────────────────────────┤
│ Speed                    │ SLOWER (overhead)          │ FASTER (no overhead)         │
├──────────────────────────┼────────────────────────────┼──────────────────────────────┤
│ Error checking           │ Yes (retransmits)          │ Basic (no retransmit)        │
├──────────────────────────┼────────────────────────────┼──────────────────────────────┤
│ Flow control             │ Yes                        │ No                           │
├──────────────────────────┼────────────────────────────┼──────────────────────────────┤
│ Use case                 │ Web, Email, File Transfer  │ Video, Gaming, DNS, VoIP     │
├──────────────────────────┼────────────────────────────┼──────────────────────────────┤
│ Analogy                  │ REGISTERED MAIL            │ POSTCARD (just drop & forget)│
│                          │ (tracked, confirmed)       │                              │
└──────────────────────────┴────────────────────────────┴──────────────────────────────┘

DATA UNIT: SEGMENT (same as OSI Transport Layer)

🎯 PYQ FACT: Transport Layer in TCP/IP = "Host-to-Host Layer"
🎯 PYQ FACT: TCP = reliable + connection-oriented; UDP = fast + connectionless
🎯 PYQ FACT: TCP uses 3-way handshake (SYN, SYN-ACK, ACK)
🚨 TRAP: "UDP is more reliable than TCP" → COMPLETELY FALSE!
🚨 TRAP: "TCP is used for video streaming" → FALSE! Video uses UDP.
```

---

### LAYER 2 — INTERNET LAYER (TCP/IP)

```
CORRESPONDS TO: OSI Layer 3 (Network Layer) — same function, different name!

ALTERNATIVE NAME: "Network Layer" (sometimes called this in TCP/IP context too)

FUNCTION: Handles LOGICAL ADDRESSING (IP addresses) and ROUTING of packets
          across multiple networks from source to destination.

WHAT IT DOES:
  → Assigns and uses IP addresses to identify devices
  → Determines the BEST PATH (route) for packets to travel
  → Fragments large packets if needed
  → Handles packet forwarding across routers

KEY PROTOCOLS:
  IP (Internet Protocol):
  → The BACKBONE of the Internet!
  → IPv4: 32-bit address (e.g., 192.168.1.1) — ~4.3 billion addresses
  → IPv6: 128-bit address (e.g., 2001:db8::1) — virtually unlimited
  → IP is CONNECTIONLESS and UNRELIABLE at this layer
    (Reliability is handled by TCP at Transport layer above!)

  ICMP (Internet Control Message Protocol):
  → Used for error reporting and diagnostics
  → "PING" command uses ICMP! (checks if a host is reachable)
  → Sends error messages like "Host Unreachable", "Time Exceeded"
  
  ARP (Address Resolution Protocol):
  → Resolves IP address → MAC address
  → "I have IP 192.168.1.5 — what is its MAC address?"
  → Needed because Data Link Layer uses MAC addresses, not IP!
  
  RARP (Reverse ARP):
  → Resolves MAC address → IP address
  → Opposite of ARP
  
  IGMP (Internet Group Management Protocol):
  → Manages multicast group memberships
  → Used in video conferencing, live streaming to groups

  ROUTING PROTOCOLS (how routers share path information):
  → RIP (Routing Information Protocol) — simple, small networks
  → OSPF (Open Shortest Path First) — large enterprise networks
  → BGP (Border Gateway Protocol) — Internet backbone routing

DATA UNIT: PACKET (same as OSI Network Layer)
KEY DEVICE: ROUTER

REAL-LIFE ANALOGY:
  The POST OFFICE SORTING SYSTEM:
  → You write a letter with a city/state address (IP address)
  → The post office (Router) reads the address
  → Decides: "Send to Delhi hub first, then route to specific area"
  → Multiple hops from sorting centre to sorting centre until delivered

🎯 PYQ FACT: Internet Layer (TCP/IP) = Network Layer (OSI) — same function
🎯 PYQ FACT: PING uses ICMP (not TCP, not UDP!)
🎯 PYQ FACT: ARP = IP address → MAC address (at Internet/Network layer boundary)
🚨 TRAP: "ARP is at Transport Layer" → FALSE! ARP = Internet/Network Layer
🚨 TRAP: "ICMP is a Transport Layer protocol" → FALSE! ICMP = Internet Layer
```

---

### LAYER 1 — NETWORK ACCESS LAYER (TCP/IP)

```
CORRESPONDS TO: OSI Layers 2 + 1 (Data Link + Physical combined!)

ALTERNATIVE NAMES:
  → "Link Layer"
  → "Host-to-Network Layer"
  → "Network Interface Layer"

FUNCTION: Handles PHYSICAL TRANSMISSION of data over the actual network medium.
          Combines responsibilities of both Data Link and Physical layers!

WHAT IT DOES:
  → FRAMING: Packages data into frames for transmission
  → PHYSICAL ADDRESSING: Uses MAC addresses for local delivery
  → ERROR DETECTION: CRC checks on frames
  → BIT TRANSMISSION: Converts frames to electrical/optical/radio signals
  → MEDIA ACCESS CONTROL: Controls access to shared medium

WHY COMBINED IN TCP/IP?
  TCP/IP designers merged Data Link and Physical into ONE layer because:
  → Both deal with the SAME local network segment
  → Both are hardware/medium dependent
  → They cannot be truly separated in practice
  
  Think: You can't send a Frame (Data Link) without bits (Physical) —
         they are inherently linked!

KEY TECHNOLOGIES / PROTOCOLS:
  Wired:   Ethernet (IEEE 802.3), Token Ring
  Wireless: Wi-Fi (IEEE 802.11), Bluetooth
  WAN:     PPP (Point-to-Point Protocol), Frame Relay, ATM

KEY CONCEPTS:
  → MAC Address: 48-bit hardware address (e.g., 00:1A:2B:3C:4D:5E)
  → NIC (Network Interface Card): hardware that connects device to network
  → Ethernet Frame structure: [Preamble | Dest MAC | Src MAC | Data | CRC]

DATA UNIT: FRAMES (Data Link) and BITS (Physical) — both at this layer
KEY DEVICES: Switch, Hub, NIC, Cables, Modem

REAL-LIFE ANALOGY:
  The LAST-MILE DELIVERY:
  → The parcel has been routed to your CITY (Internet Layer)
  → Now the delivery boy (Network Access Layer) takes it
  → He knows your exact DOOR address (MAC address)
  → He physically DRIVES to your door and hands it over (Physical transmission)

🎯 PYQ FACT: Network Access Layer = Data Link + Physical (2 OSI layers combined)
🎯 PYQ FACT: MAC address is used at Network Access Layer
🎯 PYQ FACT: Ethernet and Wi-Fi operate at Network Access Layer
🚨 TRAP: "TCP/IP has a separate Physical Layer" → FALSE! Physical is MERGED into Network Access
```

---

## 🔷 SECTION 4: OSI vs TCP/IP Mapping — THE Critical Comparison

This is the **most heavily tested topic** when OSI and TCP/IP both appear in the same exam question!

```
OSI MODEL (7 Layers)          TCP/IP MODEL (4 Layers)
━━━━━━━━━━━━━━━━━━━          ━━━━━━━━━━━━━━━━━━━━━━
┌─────────────────────┐       ┌──────────────────────────┐
│  7. Application     │───┐   │                          │
├─────────────────────┤   ├──▶│  4. Application Layer    │
│  6. Presentation    │───┤   │  (HTTP, FTP, SMTP, DNS)  │
├─────────────────────┤   │   │                          │
│  5. Session         │───┘   └──────────────────────────┘
├─────────────────────┤        ┌──────────────────────────┐
│  4. Transport       │───────▶│  3. Transport Layer      │
│  (TCP/UDP)          │        │  (TCP, UDP)              │
├─────────────────────┤        └──────────────────────────┘
│  3. Network         │        ┌──────────────────────────┐
│  (IP, Routing)      │───────▶│  2. Internet Layer       │
├─────────────────────┤        │  (IP, ICMP, ARP)         │
├─────────────────────┤        └──────────────────────────┘
│  2. Data Link       │───┐    ┌──────────────────────────┐
├─────────────────────┤   ├───▶│  1. Network Access Layer │
│  1. Physical        │───┘    │  (Ethernet, Wi-Fi, MAC)  │
└─────────────────────┘        └──────────────────────────┘

MAPPING FORMULA (memorise this!):
  OSI 7+6+5  →  TCP/IP Application
  OSI 4      →  TCP/IP Transport      (1:1 mapping)
  OSI 3      →  TCP/IP Internet       (1:1 mapping)
  OSI 2+1    →  TCP/IP Network Access
```

### OSI vs TCP/IP Full Comparison Table:

```
┌──────────────────────────┬──────────────────────────────┬────────────────────────────────┐
│         FEATURE          │          OSI MODEL           │         TCP/IP MODEL           │
├──────────────────────────┼──────────────────────────────┼────────────────────────────────┤
│ Full Name                │ Open Systems Interconnection │ Transmission Control Protocol/ │
│                          │ Model                        │ Internet Protocol              │
├──────────────────────────┼──────────────────────────────┼────────────────────────────────┤
│ Developed by             │ ISO (Int'l Org for           │ DARPA (US Dept of Defense)     │
│                          │ Standardization)             │                                │
├──────────────────────────┼──────────────────────────────┼────────────────────────────────┤
│ Year                     │ 1984                         │ 1974 (Cerf & Kahn)             │
├──────────────────────────┼──────────────────────────────┼────────────────────────────────┤
│ Number of Layers         │ 7 Layers                     │ 4 Layers                       │
├──────────────────────────┼──────────────────────────────┼────────────────────────────────┤
│ Nature                   │ Theoretical / Reference      │ Practical / Actually used      │
│                          │ model (conceptual)           │ in the real Internet           │
├──────────────────────────┼──────────────────────────────┼────────────────────────────────┤
│ Protocol Dependency      │ Protocol-INDEPENDENT         │ Protocol-DEPENDENT             │
│                          │ (generic framework)          │ (built around TCP and IP)      │
├──────────────────────────┼──────────────────────────────┼────────────────────────────────┤
│ Session Layer            │ Separate Session Layer       │ NO separate Session Layer      │
│                          │ (Layer 5)                    │ (merged into Application)      │
├──────────────────────────┼──────────────────────────────┼────────────────────────────────┤
│ Presentation Layer       │ Separate Presentation Layer  │ NO separate Presentation Layer │
│                          │ (Layer 6)                    │ (merged into Application)      │
├──────────────────────────┼──────────────────────────────┼────────────────────────────────┤
│ Physical Layer           │ Separate Physical Layer      │ NO separate Physical Layer     │
│                          │ (Layer 1)                    │ (merged into Network Access)   │
├──────────────────────────┼──────────────────────────────┼────────────────────────────────┤
│ Reliability              │ Reliability services defined │ Reliability at Transport layer │
│                          │ at multiple layers           │ only (TCP provides it)         │
├──────────────────────────┼──────────────────────────────┼────────────────────────────────┤
│ Real-world Use           │ NOT actually used in         │ ACTUALLY used in the Internet  │
│                          │ the Internet                 │                                │
├──────────────────────────┼──────────────────────────────┼────────────────────────────────┤
│ Purpose                  │ Educational framework,       │ Practical communication        │
│                          │ troubleshooting guide        │ across the Internet            │
└──────────────────────────┴──────────────────────────────┴────────────────────────────────┘
```

---

## 🔷 SECTION 5: Important Protocols — Detailed Reference

### PORT NUMBERS (Transport Layer entry points):

```
PORT = a logical "door number" on a device
       Each protocol uses a specific port so the OS knows
       which application should receive the data

┌─────────────────────┬────────┬─────────────────────────────────────────────┐
│     PROTOCOL        │  PORT  │              PURPOSE                        │
├─────────────────────┼────────┼─────────────────────────────────────────────┤
│ FTP (Data)          │   20   │ File transfer — actual data                 │
│ FTP (Control)       │   21   │ File transfer — commands/control            │
│ SSH                 │   22   │ Secure remote access (secure Telnet)        │
│ Telnet              │   23   │ Remote terminal access (UNSECURED)          │
│ SMTP                │   25   │ Email SENDING                               │
│ DNS                 │   53   │ Domain Name to IP resolution                │
│ DHCP (Server)       │   67   │ Dynamic IP address assignment               │
│ DHCP (Client)       │   68   │ Client side of DHCP                        │
│ HTTP                │   80   │ Web browsing (unencrypted)                  │
│ POP3                │  110   │ Email RECEIVING (downloads to device)       │
│ IMAP                │  143   │ Email READING (stays on server)             │
│ HTTPS               │  443   │ Secure web browsing (HTTP + SSL/TLS)        │
│ SNMP                │  161   │ Network device management                   │
└─────────────────────┴────────┴─────────────────────────────────────────────┘

🧠 MEMORY TRICKS for port numbers:
  FTP = 20/21 (Twenty/Twenty-one — like age)
  SSH = 22 (two 2s — secure squared!)
  SMTP = 25 (S=19th letter; M=13th; 19+... just remember 25!)
  DNS = 53 (Domain = 6 letters; Name = 4 letters; Server = ... remember 53!)
  HTTP = 80 (like "HyperText = 80 km/hr speed limit!")
  HTTPS = 443 (4-4-3... "For For Three-ply security!")

TOP 5 MOST-TESTED PORTS IN PYQ:
  HTTP  = 80
  HTTPS = 443
  FTP   = 21
  SMTP  = 25
  DNS   = 53
```

### Key Protocol Explanations:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
HTTP — HyperText Transfer Protocol
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
LAYER: Application
PORT:  80 (HTTP) / 443 (HTTPS)
USE:   Web communication between browser and web server
HOW:   Client (browser) sends HTTP REQUEST → Server sends HTTP RESPONSE
       REQUEST: "GET /index.html HTTP/1.1"
       RESPONSE: HTML page content
OVER:  TCP (reliable) — ensures full webpage delivered
HTTPS: HTTP + SSL/TLS encryption = SECURE web browsing

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
FTP — File Transfer Protocol
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
LAYER: Application
PORTS: 21 (control), 20 (data)
USE:   Transferring files between client and server
TWO CHANNELS:
  → Control channel (Port 21): Commands (login, list files, navigate)
  → Data channel (Port 20): Actual file transfer
OVER:  TCP (reliable) — files must arrive completely and correctly
NOTE:  FTP sends passwords in PLAIN TEXT — hence SFTP/FTPS exist for security

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SMTP — Simple Mail Transfer Protocol
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
LAYER: Application
PORT:  25 (and 587 for submission, 465 for SMTPS)
USE:   SENDING emails from client to mail server, and between mail servers
DIRECTION: OUTGOING only (Push protocol)
OVER:  TCP
ANALOGY: SMTP = Post Office that COLLECTS and SENDS your letters

🚨 PYQ TRAP: SMTP is used to SEND emails.
             To RECEIVE/READ emails → use POP3 or IMAP!
             
EMAIL PROTOCOL SUMMARY:
  SMTP → SEND email (outgoing mail)
  POP3 → RECEIVE email, DOWNLOAD to device (deletes from server by default)
  IMAP → RECEIVE email, READ on server (stays on server, sync across devices)
  
  ANALOGY:
  SMTP = You posting a letter at the post office
  POP3 = Postman delivers letter to your house; takes it away from post office
  IMAP = You read the letter at the post office; it stays there

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DNS — Domain Name System
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
LAYER: Application
PORT:  53
USE:   Translates human-readable domain names to IP addresses
       "google.com" → 172.217.163.46
WHY:   Humans remember names; computers use IP numbers
HOW:   Browser asks DNS server: "What is the IP of google.com?"
       DNS replies: "172.217.163.46"
       Browser then connects to that IP.
OVER:  UDP (usually, for speed) — simple request/response
       TCP (for zone transfers — large data between DNS servers)
ANALOGY: DNS = PHONE BOOK of the Internet
         Name → Number just like Domain → IP

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DHCP — Dynamic Host Configuration Protocol
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
LAYER: Application
PORT:  67 (server), 68 (client)
USE:   Automatically assigns IP addresses to devices on a network
WHY:   Without DHCP, every device's IP must be configured MANUALLY!
       With DHCP, router automatically gives each device a unique IP.
HOW:   Device joins network → sends DHCP Discover broadcast
       DHCP Server replies with an IP address offer
       Device accepts → gets IP, subnet mask, gateway, DNS server
ANALOGY: DHCP = Hotel reception that assigns room numbers (IPs) to guests
         Each new guest (device) gets a room (IP) automatically
```

---

## 🔷 SECTION 6: Data Encapsulation — Data Flow in TCP/IP

```
COMPLETE DATA FLOW — Sending an Email via Gmail:

Step 1: You type your email and press "SEND" (APPLICATION LAYER)
  → Gmail uses SMTP to create an email message
  → Data: [FROM | TO | SUBJECT | BODY] = the EMAIL DATA

Step 2: TRANSPORT LAYER adds TCP segment header
  → Breaks email into segments
  → Adds SOURCE PORT (random high port) and DEST PORT (25 for SMTP)
  → Adds sequence numbers for ordering
  → Result: [TCP HEADER | EMAIL DATA] = SEGMENT

Step 3: INTERNET LAYER adds IP packet header
  → Adds YOUR IP address (source) and GMAIL SERVER IP (destination)
  → Result: [IP HEADER | TCP HEADER | EMAIL DATA] = PACKET

Step 4: NETWORK ACCESS LAYER creates Frame
  → Adds MAC address of your router (next hop)
  → Adds frame trailer (CRC for error detection)
  → Result: [MAC HEADER | IP HEADER | TCP HEADER | EMAIL DATA | CRC] = FRAME

Step 5: PHYSICAL TRANSMISSION
  → Frame converted to electrical/optical/radio BITS
  → Bits travel over cable/Wi-Fi to router

At each ROUTER (Internet Layer only):
  → Router strips and re-adds MAC header (Network Access Layer headers change at each hop!)
  → IP header stays the same throughout (source and dest IP don't change)
  → This repeats until packets reach Gmail's server

At GMAIL SERVER — Reverse (Decapsulation):
  → Physical receives BITS → reconstructs FRAME
  → Network Access strips Frame header → extracts PACKET
  → Internet strips IP header → extracts SEGMENT
  → Transport strips TCP header → reassembles EMAIL DATA
  → Application Layer (SMTP) reads the email and delivers it!

KEY INSIGHT:
  → IP header (source/dest IP) stays SAME at every hop
  → MAC header changes at every router hop (local address changes)
  → This is why we need BOTH IP and MAC addresses!
```

---

## 🔷 SECTION 7: TCP/IP Layer Names — Alternative Names (Exam Trap!)

```
VARIOUS NAMES FOR TCP/IP LAYERS (All are correct — exams use different names!):

┌──────────────┬───────────────────────────────────────────────────────────────────────┐
│  TCP/IP LAYER│                    ALTERNATIVE NAMES                                  │
├──────────────┼───────────────────────────────────────────────────────────────────────┤
│ Layer 4      │ Application Layer = Process Layer                                     │
├──────────────┼───────────────────────────────────────────────────────────────────────┤
│ Layer 3      │ Transport Layer = Host-to-Host Layer = End-to-End Layer               │
├──────────────┼───────────────────────────────────────────────────────────────────────┤
│ Layer 2      │ Internet Layer = Network Layer = Internetwork Layer                   │
├──────────────┼───────────────────────────────────────────────────────────────────────┤
│ Layer 1      │ Network Access Layer = Link Layer = Host-to-Network Layer             │
│              │ = Network Interface Layer = Data Link Layer (informal)                │
└──────────────┴───────────────────────────────────────────────────────────────────────┘

🚨 PYQ TRAP: "Host-to-Host Layer" = Transport Layer in TCP/IP (NOT Network Layer!)
🚨 PYQ TRAP: "Internet Layer" = same as "Network Layer" in OSI mapping
🚨 PYQ TRAP: "Link Layer" = Network Access Layer (bottom layer of TCP/IP)
```

---

## 🔷 SECTION 8: Common PYQ Traps — TCP/IP Model

```
🚨 TRAP 1: "TCP/IP model has 7 layers like OSI" → FALSE!
   TCP/IP = 4 layers. OSI = 7 layers.

🚨 TRAP 2: "SMTP is used to RECEIVE emails" → FALSE!
   SMTP = SENDING emails.
   Receiving = POP3 (Port 110) or IMAP (Port 143).

🚨 TRAP 3: "TCP is faster than UDP" → FALSE!
   UDP is FASTER (no overhead).
   TCP is RELIABLE but SLOWER.

🚨 TRAP 4: "DNS uses TCP" → PARTIALLY FALSE!
   DNS primarily uses UDP (Port 53) for speed.
   Uses TCP only for large transfers (zone transfers).

🚨 TRAP 5: "ARP is at Transport Layer" → FALSE!
   ARP = Internet Layer (TCP/IP) = Network Layer boundary (OSI).

🚨 TRAP 6: "TCP/IP Application layer = ONLY OSI Application layer" → FALSE!
   TCP/IP Application = OSI Application (7) + Presentation (6) + Session (5) combined!

🚨 TRAP 7: "TCP/IP has a separate Physical Layer" → FALSE!
   Physical is MERGED with Data Link → Network Access Layer.

🚨 TRAP 8: "OSI model is actually used in the Internet" → FALSE!
   Internet uses TCP/IP. OSI is a REFERENCE MODEL.

🚨 TRAP 9: "HTTP port = 443" → FALSE!
   HTTP = 80. HTTPS = 443.

🚨 TRAP 10: "ICMP is used for file transfer" → FALSE!
   ICMP = error messages and diagnostics (PING).
   File transfer = FTP (Port 21).

🚨 TRAP 11: "Host-to-Host layer = Internet Layer" → FALSE!
   Host-to-Host = TRANSPORT Layer.
   Internet Layer = handles routing (= OSI Network Layer).

🚨 TRAP 12: "FTP uses only one port" → FALSE!
   FTP uses TWO ports: Port 21 (control) and Port 20 (data).
```

---

# PART 2: GENERAL STUDIES
## 📊 Economics — GDP Basics, National Income & Key Concepts

---

## 🔷 SECTION 1: What is GDP?

### Real-Life Analogy — The Report Card of a Country:

Just as a student's report card shows total marks scored across all subjects in a year, **GDP shows the total economic output (production) of a country in one year.**

> **GDP = Gross Domestic Product**
> **The total monetary value of ALL final goods and services produced WITHIN a country's geographical boundaries in a given period (usually one year).**

### Breaking Down the Definition:
```
"GROSS"     → Total without deducting depreciation
              (opposite of "Net" — Net = Gross MINUS depreciation)

"DOMESTIC"  → Within the geographical BOUNDARIES of a country
              (regardless of who produces it — Indian or foreigner!)
              If a US company (e.g., Apple) makes phones in India → counted in India's GDP!

"PRODUCT"   → The final value of goods and services produced

"FINAL"     → Only FINAL goods counted (not intermediate goods!)
              Raw cotton → Thread → Cloth → Shirt
              Only the SHIRT (final product) is counted in GDP.
              Why? To avoid DOUBLE COUNTING!

"VALUE"     → Measured in monetary terms (₹ rupees in India)

"GIVEN PERIOD" → Usually ONE YEAR (India: April 1 to March 31 = Fiscal Year)
```

### What is Included and Excluded:
```
INCLUDED IN GDP:                          NOT INCLUDED IN GDP:
✅ Goods sold in markets                 ❌ Intermediate goods (to avoid double counting)
✅ Services (banking, IT, healthcare)    ❌ Unpaid household work (cooking at home)
✅ Government services                   ❌ Illegal/black market activities
✅ Investment in new factories           ❌ Transfer payments (pension, scholarships)
✅ Exports (goods made here, sold abroad)❌ Second-hand goods resale (already counted)
                                         ❌ Financial transactions (stock market trading)
```

### 🎯 PYQ FACT:
```
✅ GDP measures production WITHIN geographical boundaries
✅ "Domestic" = within borders (not nationality!)
✅ Final goods only — to avoid double counting
✅ India's fiscal year = April 1 to March 31
✅ India's GDP = measured by Ministry of Statistics and Programme Implementation (MoSPI)
✅ Central Statistics Office (CSO) releases GDP data (now part of NSO)
```

---

## 🔷 SECTION 2: Nominal GDP vs Real GDP

### The Problem With Nominal GDP:

Imagine India's GDP was ₹100 lakh crore in 2020 and ₹120 lakh crore in 2021.
**Did the economy actually GROW 20%?** NOT NECESSARILY!

If prices also rose by 20%, then people produced the SAME goods — but everything costs more!

```
EXAMPLE:
  Year 2020: 100 kg rice × ₹50/kg = ₹5,000 (GDP contribution)
  Year 2021: 100 kg rice × ₹60/kg = ₹6,000 (GDP contribution)
  
  Did rice PRODUCTION grow? NO! Same 100 kg produced.
  Did GDP INCREASE? YES — but only because prices rose!
  
  This inflation-inflated GDP = NOMINAL GDP
  GDP adjusted for inflation = REAL GDP
```

### Definitions:

```
┌──────────────────────────────────────────────────────────────────────────────┐
│                    NOMINAL GDP vs REAL GDP                                    │
├──────────────────────────┬───────────────────────────────────────────────────┤
│      NOMINAL GDP         │                 REAL GDP                          │
├──────────────────────────┼───────────────────────────────────────────────────┤
│ GDP calculated at        │ GDP calculated at CONSTANT PRICES                 │
│ CURRENT PRICES           │ (prices of a BASE YEAR)                           │
├──────────────────────────┼───────────────────────────────────────────────────┤
│ NOT adjusted for         │ ADJUSTED for inflation                            │
│ inflation                │                                                   │
├──────────────────────────┼───────────────────────────────────────────────────┤
│ Also called:             │ Also called:                                      │
│ "GDP at Current Prices"  │ "GDP at Constant Prices"                          │
│ "Money GDP"              │ "Inflation-Adjusted GDP"                          │
├──────────────────────────┼───────────────────────────────────────────────────┤
│ Shows price + quantity   │ Shows ONLY quantity changes                       │
│ changes together         │ (true economic growth)                            │
├──────────────────────────┼───────────────────────────────────────────────────┤
│ Formula:                 │ Formula:                                          │
│ Current Year Qty ×       │ Current Year Qty × BASE YEAR Price                │
│ Current Year Price       │                                                   │
├──────────────────────────┼───────────────────────────────────────────────────┤
│ OVERSTATES growth if     │ TRUE measure of economic growth                   │
│ inflation is high        │                                                   │
├──────────────────────────┼───────────────────────────────────────────────────┤
│ USED FOR:                │ USED FOR:                                         │
│ International comparison │ Measuring real growth, economic policy            │
│ of market size           │ decisions, comparing across years                 │
└──────────────────────────┴───────────────────────────────────────────────────┘

FORMULA RELATIONSHIP:
  Real GDP = Nominal GDP / GDP Deflator × 100
  OR
  Real GDP ≈ Nominal GDP adjusted for inflation
  
  GDP Deflator = (Nominal GDP / Real GDP) × 100
  (measures overall price level change)
```

### India's Base Year:
```
CURRENT BASE YEAR FOR INDIA'S GDP = 2011-12
(changed from 2004-05 to 2011-12 in 2015)

This means: India's Real GDP is calculated using 2011-12 prices as reference.

🎯 PYQ FACT: India's base year = 2011-12 (frequently asked!)
🎯 PYQ FACT: GDP at constant prices = Real GDP = true economic growth measure
```

---

## 🔷 SECTION 3: Methods of Calculating GDP

GDP can be calculated three ways — all three should give the SAME answer!
(If the economy is properly measured — in theory they are equal)

```
GDP = EXPENDITURE METHOD = INCOME METHOD = PRODUCTION METHOD

Think of it like three blind men describing an elephant — same elephant, different perspectives!
```

### METHOD 1: EXPENDITURE METHOD (Most commonly used)

```
LOGIC: GDP = Total spending in the economy
       Every rupee spent on a final good = someone's income = something produced

FORMULA: GDP = C + I + G + (X - M)

C = CONSUMPTION (Private/Household spending)
    → What households spend on goods and services
    → Food, clothing, appliances, haircuts, education fees
    → LARGEST component of GDP in most countries (60-70%)!

I = INVESTMENT (Gross Private Domestic Investment)
    → Business investment in capital goods (machines, buildings, equipment)
    → Construction of new houses
    → Changes in inventories
    → NOT stock market investment! (Financial investment ≠ Economic investment)

G = GOVERNMENT EXPENDITURE (Govt spending on goods & services)
    → Government spending on roads, schools, hospitals, defense
    → Does NOT include TRANSFER PAYMENTS like pensions, subsidies
    → (Transfer payments don't produce new goods)

X = EXPORTS (Goods/services produced here, sold abroad)
    → Counts goods produced domestically → adds to GDP

M = IMPORTS (Goods/services produced abroad, consumed here)
    → Counted in C, I, G above but NOT produced domestically
    → Must be SUBTRACTED from GDP

(X - M) = NET EXPORTS = TRADE BALANCE
    → If exports > imports → positive (trade surplus)
    → If imports > exports → negative (trade deficit, common for India)

COMPLETE FORMULA:
  GDP = C + I + G + (X - M)
  
  MEMORY TRICK:
  "Big CIGarette Gone eXport Minus"
  C = Consumption
  I = Investment
  G = Government Expenditure
  X - M = Net Exports (Exports minus Imports)
```

### METHOD 2: INCOME METHOD (Factor Income Method)

```
LOGIC: Every rupee spent is someone's income!
       GDP = Sum of all incomes earned in producing goods and services

COMPONENTS:
  GDP = Wages + Rent + Interest + Profit + Mixed Income

  WAGES/SALARIES:  Income earned by LABOUR (workers)
  RENT:            Income earned by LAND owners
  INTEREST:        Income earned by CAPITAL providers
  PROFIT:          Income earned by ENTREPRENEURS
  MIXED INCOME:    Income of self-employed (farmers, shopkeepers — hard to separate)

MEMORY TRICK — "WRIP + M" or "WRIPM":
  W = Wages (Labour)
  R = Rent (Land)
  I = Interest (Capital)
  P = Profit (Enterprise)
  M = Mixed Income (Self-employed)
  
  Or remember FACTORS OF PRODUCTION:
  Land → Rent
  Labour → Wages
  Capital → Interest
  Enterprise → Profit
```

### METHOD 3: OUTPUT / PRODUCTION METHOD (Value-Added Method)

```
LOGIC: GDP = Sum of VALUE ADDED at each stage of production

VALUE ADDED = Value of output MINUS value of inputs (intermediate goods)

EXAMPLE — Making a Shirt:
  Stage 1: Cotton farmer sells cotton for ₹100
           Value Added = ₹100 (no inputs bought)
  Stage 2: Thread maker buys cotton ₹100, sells thread for ₹200
           Value Added = ₹200 - ₹100 = ₹100
  Stage 3: Cloth maker buys thread ₹200, sells cloth for ₹350
           Value Added = ₹350 - ₹200 = ₹150
  Stage 4: Shirt maker buys cloth ₹350, sells shirt for ₹500
           Value Added = ₹500 - ₹350 = ₹150

  TOTAL VALUE ADDED = ₹100 + ₹100 + ₹150 + ₹150 = ₹500
  FINAL SHIRT PRICE = ₹500 ✅ (Both methods give same answer!)

WHY VALUE ADDED? To AVOID DOUBLE COUNTING!
  If we added: ₹100 + ₹200 + ₹350 + ₹500 = ₹1,150 → WRONG (counting cotton multiple times!)
  Value added method eliminates this problem.

SECTORS IN INDIA (Production method):
  → Primary sector: Agriculture, Mining, Fishing
  → Secondary sector: Manufacturing, Construction
  → Tertiary sector: Services (IT, banking, retail, transport)
```

---

## 🔷 SECTION 4: GDP and Related Concepts — GNP, NDP, GNI

### The Relationship Web:

```
START WITH: GDP (Gross Domestic Product)
            = Total production WITHIN borders (residents + non-residents)

TO GET GNP: ADD income earned by Indian citizens ABROAD
            SUBTRACT income earned by FOREIGNERS in India

GNP = GDP + Factor Income earned ABROAD by residents
          - Factor Income earned IN INDIA by non-residents

OR:
GNP = GDP + Net Factor Income from Abroad (NFIA)

REMEMBER:
  DOMESTIC → within geographical territory (regardless of nationality)
  NATIONAL → by citizens/residents (regardless of location)
  
  GDP → DOMESTIC boundary
  GNP → NATIONAL (by Indians wherever they are)
```

### National Income Aggregates — Summary:

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    NATIONAL INCOME AGGREGATES                                    │
├────────────────┬───────────────────────────────────────────────────────────────┤
│   INDICATOR    │                       FORMULA                                  │
├────────────────┼───────────────────────────────────────────────────────────────┤
│ GDP            │ Total production WITHIN borders                                │
│ (Gross         │ = C + I + G + (X-M)  [Expenditure method]                     │
│  Domestic      │                                                                │
│  Product)      │                                                                │
├────────────────┼───────────────────────────────────────────────────────────────┤
│ GNP            │ GDP + Net Factor Income from Abroad (NFIA)                     │
│ (Gross         │ = GDP + (Income earned by Indians abroad                       │
│  National      │         - Income earned by foreigners in India)                │
│  Product)      │                                                                │
├────────────────┼───────────────────────────────────────────────────────────────┤
│ NDP            │ GDP - Depreciation (Capital Consumption Allowance)             │
│ (Net Domestic  │ Depreciation = wear and tear of capital assets                 │
│  Product)      │ "NET" = after accounting for depreciation                      │
├────────────────┼───────────────────────────────────────────────────────────────┤
│ NNP            │ GNP - Depreciation                                             │
│ (Net National  │ = NDP + NFIA                                                   │
│  Product)      │ Also = NATIONAL INCOME (at factor cost)                        │
├────────────────┼───────────────────────────────────────────────────────────────┤
│ National       │ NNP at Factor Cost                                             │
│ Income (NI)    │ = NNP - Indirect Taxes + Subsidies                             │
├────────────────┼───────────────────────────────────────────────────────────────┤
│ Per Capita     │ National Income ÷ Total Population                             │
│ Income         │ Average income per person                                      │
│                │ Used to compare LIVING STANDARDS across countries              │
└────────────────┴───────────────────────────────────────────────────────────────┘

KEY RELATIONSHIPS:
  GROSS vs NET:
    Gross = includes depreciation
    Net   = Gross MINUS depreciation
    
  DOMESTIC vs NATIONAL:
    Domestic = within territory (all producers)
    National = by residents (regardless of location)
    
  GDP → GNP: add NFIA
  Gross → Net: subtract Depreciation
  
  SIMPLE LADDER (from largest to smallest typically):
  GDP → GNP (add NFIA) → NDP (subtract depreciation) → NNP → NI
```

### India-Specific GDP Facts:

```
INDIA GDP FACTS (important for Bihar exam context):
  → India's GDP (2023-24): approximately ₹295+ lakh crore (Nominal)
  → India = 5th largest economy in world (by nominal GDP)
  → India = 3rd largest economy by PPP (Purchasing Power Parity)
  → India's GDP growth rate target: ~6-7% annually
  → LARGEST sector in India's GDP: Services (~55% of GDP)
  → Agriculture's share: ~18-20% of GDP (but employs ~45% of workforce!)
  → India's fiscal year: April 1 to March 31
  → GDP data released by: NSO (National Statistical Office) / MoSPI
  
  BASE YEAR FOR REAL GDP IN INDIA: 2011-12
  (Changed from 2004-05 to 2011-12 in January 2015)

BIHAR SPECIFIC:
  → Bihar's GSDP (Gross State Domestic Product) has grown rapidly
  → Bihar = one of the FASTEST-growing states in India by GSDP growth rate
  → Despite fast growth, Bihar has one of the LOWEST per capita incomes in India
    (High population + smaller economy = low per capita)
  → Agriculture is proportionally MORE important in Bihar's GSDP than national average
  
🎯 PYQ FACT: Services sector = LARGEST contributor to India's GDP (~55%)
🎯 PYQ FACT: Agriculture contributes ~18% to GDP but ~45% employment (disguised unemployment!)
🎯 PYQ FACT: India's base year = 2011-12
```

---

## 🔷 SECTION 5: GDP vs GNP — When They Differ (India context)

```
WHEN IS GNP > GDP?
  When Indian residents earn MORE ABROAD than foreigners earn in India.
  Example: Indian IT professionals in USA send remittances home → adds to GNP
  Indian banks invest abroad → interest income adds to GNP
  
WHEN IS GDP > GNP?
  When foreigners earn MORE in India than Indians earn abroad.
  Example: American company (Apple) makes phones in India → their profit goes to USA
           → This profit is in India's GDP but NOT in India's GNP
  
IN INDIA'S CASE:
  India receives large REMITTANCES from Indians abroad (NRIs)
  BUT India also pays large amounts to foreign companies operating here
  INDIA: GDP ≈ GNP (the difference is relatively small)
  
  In CONTRAST:
  USA: GDP < GNP (Americans earn a LOT abroad — multinationals)
  Germany: GDP > GNP (many foreign workers in Germany send money home)
```

---

## 🔷 SECTION 6: GDP and Standard of Living — Limitations

```
GDP IS A GOOD MEASURE BUT HAS LIMITATIONS:

WHAT GDP CAPTURES:
  → Overall economic output
  → Economic growth rate
  → Country's productive capacity

WHAT GDP MISSES:
  ❌ Income DISTRIBUTION (who gets the money — top 1% or all?)
  ❌ Environmental degradation (pollution not subtracted!)
  ❌ Quality of life (happiness, health, leisure)
  ❌ Non-market activities (housework, volunteering)
  ❌ Shadow economy / black economy

BETTER MEASURES:
  → HDI (Human Development Index): GDP + Education + Health (UNDP)
  → GNH (Gross National Happiness): Bhutan's alternative measure
  → Green GDP: GDP adjusted for environmental costs

🎯 PYQ FACT: HDI = Human Development Index = UNDP measure
             Three components: GDP per capita + Education (schooling years) + Health (life expectancy)
🎯 PYQ FACT: HDI was created by Mahbub ul Haq (Pakistani economist) and Amartya Sen (Indian)
```

---

## 🔷 SECTION 7: PYQ Traps — Economics GDP

```
🚨 TRAP 1: "GNP = GDP always" → FALSE!
   GNP = GDP + Net Factor Income from Abroad. They can differ.

🚨 TRAP 2: "Real GDP uses current year prices" → FALSE!
   Real GDP uses BASE YEAR prices (constant prices).
   Nominal GDP uses current prices.

🚨 TRAP 3: "GDP includes all goods produced" → FALSE!
   GDP includes only FINAL goods (not intermediate, to avoid double counting).

🚨 TRAP 4: "Transfer payments (pensions) are included in G (Government Expenditure)" → FALSE!
   Transfer payments NOT included in GDP calculation.
   G = only government spending on actual goods and services.

🚨 TRAP 5: "Net GDP = GDP + Depreciation" → FALSE!
   NDP = GDP MINUS depreciation. "Net" = after removing wear and tear.

🚨 TRAP 6: "Agriculture is the largest sector of India's GDP" → FALSE!
   SERVICES sector is largest (~55%). Agriculture ~18%.

🚨 TRAP 7: "Per capita income = GDP / Population" → APPROXIMATELY TRUE but:
   Per Capita income properly = National Income / Population
   (or sometimes GDP / Population for rough comparison)

🚨 TRAP 8: "India's base year = 2004-05" → FALSE! (OLD answer)
   Current base year = 2011-12 (changed in 2015).

🚨 TRAP 9: "Stock market investment = GDP investment (I)" → FALSE!
   GDP 'Investment (I)' = real investment in capital goods (factories, equipment)
   Stock market = financial investment (not counted as GDP investment directly)

🚨 TRAP 10: "Second-hand goods sale adds to current GDP" → FALSE!
   Second-hand goods were counted when FIRST produced. Resale = not new production.
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: TCP/IP Model, OSI Mapping, Protocols, Port Numbers, TCP vs UDP

---

**Q1.** The TCP/IP model was developed by:
(A) ISO (International Organization for Standardization)
(B) IEEE (Institute of Electrical and Electronics Engineers)
(C) DARPA (Defense Advanced Research Projects Agency, US)
(D) More than one of the above
(E) None of the above

---

**Q2.** How many layers does the TCP/IP model have?
(A) 3
(B) 5
(C) 4
(D) More than one of the above
(E) None of the above

---

**Q3.** Which of the following correctly lists TCP/IP layers from top (Layer 4) to bottom (Layer 1)?
(A) Application, Internet, Transport, Network Access
(B) Application, Transport, Internet, Network Access
(C) Application, Transport, Network, Physical
(D) More than one of the above
(E) None of the above

---

**Q4.** The TCP/IP Application Layer corresponds to which OSI layers?
(A) Only OSI Layer 7 (Application)
(B) OSI Layers 7, 6, and 5 (Application + Presentation + Session)
(C) OSI Layers 7 and 6 only
(D) More than one of the above
(E) None of the above

---

**Q5.** The TCP/IP Network Access Layer corresponds to which OSI layers?
(A) OSI Layer 1 (Physical) only
(B) OSI Layer 2 (Data Link) only
(C) OSI Layers 2 and 1 (Data Link + Physical combined)
(D) More than one of the above
(E) None of the above

---

**Q6.** The TCP/IP Internet Layer is equivalent to which OSI layer?
(A) OSI Transport Layer (Layer 4)
(B) OSI Network Layer (Layer 3)
(C) OSI Data Link Layer (Layer 2)
(D) More than one of the above
(E) None of the above

---

**Q7.** The "Host-to-Host Layer" is an alternative name for which TCP/IP layer?
(A) Application Layer
(B) Internet Layer
(C) Transport Layer
(D) More than one of the above
(E) None of the above

---

**Q8.** TCP (Transmission Control Protocol) is best described as:
(A) Fast, connectionless, and unreliable
(B) Reliable, connection-oriented, uses 3-way handshake
(C) Used primarily for video streaming and online gaming
(D) More than one of the above
(E) None of the above

---

**Q9.** The TCP 3-way handshake involves which sequence of messages?
(A) SYN → ACK → SYN-ACK
(B) ACK → SYN → SYN-ACK
(C) SYN → SYN-ACK → ACK
(D) More than one of the above
(E) None of the above

---

**Q10.** UDP (User Datagram Protocol) is used INSTEAD of TCP when:
(A) Data accuracy is more important than speed (email, banking)
(B) Speed is more important than guaranteed delivery (streaming, gaming)
(C) Files need to be transferred without any errors
(D) More than one of the above
(E) None of the above

---

**Q11.** SMTP (Simple Mail Transfer Protocol) is used for:
(A) Receiving emails from the mail server to the client
(B) Sending emails from client to server and between mail servers
(C) Encrypting email content
(D) More than one of the above
(E) None of the above

---

**Q12.** What is the PORT number for HTTP (unencrypted web browsing)?
(A) 443
(B) 21
(C) 80
(D) More than one of the above
(E) None of the above

---

**Q13.** DNS (Domain Name System) primarily uses which protocol and port?
(A) TCP, Port 80
(B) UDP, Port 53
(C) TCP, Port 25
(D) More than one of the above
(E) None of the above

---

**Q14.** Which protocol is used when you TYPE "ping google.com" in your terminal?
(A) TCP (Transmission Control Protocol)
(B) FTP (File Transfer Protocol)
(C) ICMP (Internet Control Message Protocol)
(D) More than one of the above
(E) None of the above

---

**Q15.** FTP uses TWO port numbers. These are:
(A) Port 20 (data) and Port 21 (control)
(B) Port 25 (data) and Port 80 (control)
(C) Port 21 (data) and Port 22 (control)
(D) More than one of the above
(E) None of the above

---

**Q16.** ARP (Address Resolution Protocol) is used to:
(A) Translate domain names to IP addresses
(B) Assign dynamic IP addresses to devices on a network
(C) Resolve IP addresses to MAC addresses
(D) More than one of the above
(E) None of the above

---

**Q17.** DHCP (Dynamic Host Configuration Protocol) is responsible for:
(A) Translating domain names to IP addresses
(B) Automatically assigning IP addresses to devices on a network
(C) Managing email delivery
(D) More than one of the above
(E) None of the above

---

**Q18.** In the TCP/IP model, when data moves from Application Layer DOWN to Network Access Layer, the process of adding headers is called:
(A) Decapsulation
(B) Fragmentation
(C) Encapsulation
(D) More than one of the above
(E) None of the above

---

**Q19.** Which statement CORRECTLY describes the main difference between OSI and TCP/IP models?
(A) OSI has 4 layers; TCP/IP has 7 layers
(B) OSI is the theoretical/reference model; TCP/IP is the practical model used in the Internet
(C) Both OSI and TCP/IP are equally used in the real Internet
(D) More than one of the above
(E) None of the above

---

**Q20.** POP3 (Post Office Protocol version 3) is used for:
(A) Sending emails to the recipient's server
(B) Receiving/downloading emails from server to client device
(C) Encrypting emails during transmission
(D) More than one of the above
(E) None of the above

---

**Q21.** Which of the following is an APPLICATION LAYER protocol in the TCP/IP model?
(A) IP (Internet Protocol)
(B) TCP (Transmission Control Protocol)
(C) FTP (File Transfer Protocol)
(D) More than one of the above
(E) None of the above

---

**Q22.** Which of the following correctly pairs protocol with its primary use?
I.   SMTP → Sending email (Port 25)
II.  HTTP → Web browsing (Port 80)
III. FTP  → File transfer (Port 21)
IV.  DNS  → IP to domain name conversion

(A) I, II, and III only
(B) All four are correct
(C) I, II, III correct; IV is WRONG (DNS = domain to IP, not IP to domain)
(D) More than one of the above
(E) None of the above

---

**Q23.** The TCP/IP model and OSI model have a "1:1 mapping" (one layer maps to exactly one layer) for which two layers?
(A) Application and Internet layers
(B) Transport (TCP/IP) ↔ Transport (OSI); Internet (TCP/IP) ↔ Network (OSI)
(C) Network Access (TCP/IP) ↔ Physical (OSI)
(D) More than one of the above
(E) None of the above

---

**Q24.** Vinton Cerf and Robert Kahn are known as:
(A) Inventors of the OSI model
(B) Founders of ISO (International Organization for Standardization)
(C) Fathers of the Internet — designers of the TCP/IP protocol suite
(D) More than one of the above
(E) None of the above

---

**Q25.** Consider these statements:
I.   TCP/IP Internet Layer uses IP addresses for routing.
II.  TCP/IP Network Access Layer combines Data Link and Physical layers.
III. TCP/IP has a separate Session Layer.
IV.  UDP provides faster but less reliable communication than TCP.

Which statements are CORRECT?
(A) I, II, and IV only
(B) I and IV only
(C) All four are correct
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: GDP, GNP, National Income, Methods of Calculation, India Economics

---

**Q26.** GDP stands for:
(A) Growth Domestic Product
(B) Gross Domestic Product
(C) Gross Domestic Production Index
(D) More than one of the above
(E) None of the above

---

**Q27.** The "D" in GDP stands for "DOMESTIC" which means GDP measures:
(A) Output by domestic companies only (not foreign companies in India)
(B) Output produced WITHIN the geographical boundaries of a country regardless of who produces it
(C) Output only in domestic currency (INR for India)
(D) More than one of the above
(E) None of the above

---

**Q28.** The PRIMARY reason only FINAL goods are counted in GDP (not intermediate goods) is:
(A) Intermediate goods are too difficult to measure
(B) To avoid DOUBLE COUNTING the same production at multiple stages
(C) Intermediate goods don't have monetary value
(D) More than one of the above
(E) None of the above

---

**Q29.** NOMINAL GDP differs from REAL GDP in that:
(A) Nominal GDP is always smaller than Real GDP
(B) Nominal GDP uses CURRENT prices; Real GDP uses BASE YEAR (constant) prices
(C) Nominal GDP measures only manufacturing output; Real GDP measures all sectors
(D) More than one of the above
(E) None of the above

---

**Q30.** India's current BASE YEAR for calculating Real GDP is:
(A) 2004-05
(B) 2011-12
(C) 2014-15
(D) More than one of the above
(E) None of the above

---

**Q31.** The EXPENDITURE METHOD formula for GDP is:
(A) GDP = W + R + I + P (Wages + Rent + Interest + Profit)
(B) GDP = C + I + G + (X - M)
(C) GDP = Value Added at Stage 1 + Stage 2 + Stage 3...
(D) More than one of the above
(E) None of the above

---

**Q32.** In the GDP formula C + I + G + (X - M), what does "G" represent?
(A) All government spending including transfer payments (pensions, subsidies)
(B) Government expenditure on goods and services ONLY (excluding transfer payments)
(C) Gross national income
(D) More than one of the above
(E) None of the above

---

**Q33.** If a country's Exports = ₹500 crore and Imports = ₹700 crore, then (X-M) is:
(A) +₹200 crore (trade surplus — adds to GDP)
(B) -₹200 crore (trade deficit — reduces GDP contribution)
(C) ₹1,200 crore
(D) More than one of the above
(E) None of the above

---

**Q34.** GNP (Gross National Product) differs from GDP because:
(A) GNP = GDP - Depreciation
(B) GNP = GDP + Net Factor Income from Abroad (NFIA)
(C) GNP measures only agricultural output
(D) More than one of the above
(E) None of the above

---

**Q35.** "Net Domestic Product (NDP)" is calculated as:
(A) GDP + Depreciation
(B) GDP - Depreciation (Capital consumption allowance)
(C) GNP + Net Factor Income from Abroad
(D) More than one of the above
(E) None of the above

---

**Q36.** Per Capita Income is calculated as:
(A) GDP × Total Population
(B) National Income ÷ Total Population
(C) Total exports ÷ Population
(D) More than one of the above
(E) None of the above

---

**Q37.** The Income Method of calculating GDP sums up:
(A) Consumption + Investment + Government Spending + Net Exports
(B) Value added at each stage of production
(C) Wages + Rent + Interest + Profit + Mixed Income
(D) More than one of the above
(E) None of the above

---

**Q38.** Which sector contributes the LARGEST share to India's GDP?
(A) Agriculture and Allied Activities
(B) Industry (Manufacturing + Construction)
(C) Services (IT, Banking, Retail, Transport, etc.)
(D) More than one of the above
(E) None of the above

---

**Q39.** "GDP Deflator" is used to:
(A) Measure trade deficit
(B) Convert Nominal GDP to Real GDP by accounting for price changes
(C) Measure GDP growth in agriculture only
(D) More than one of the above
(E) None of the above

---

**Q40.** Which of the following is NOT included in calculating GDP?
(A) Value of cars manufactured and sold in India
(B) Services provided by Indian banks to customers
(C) Pension payments made by government to retired employees (transfer payments)
(D) More than one of the above
(E) None of the above

---

**Q41.** HDI (Human Development Index) is published by:
(A) World Bank
(B) IMF (International Monetary Fund)
(C) UNDP (United Nations Development Programme)
(D) More than one of the above
(E) None of the above

---

**Q42.** The Human Development Index (HDI) measures development based on:
(A) GDP alone
(B) GDP per capita + Education (mean and expected years of schooling) + Health (life expectancy)
(C) GDP + Defense expenditure + Trade balance
(D) More than one of the above
(E) None of the above

---

**Q43.** Consider: A US company (Apple Inc.) manufactures iPhones at a factory in India. This production will be counted in:
(A) Only USA's GDP (since Apple is an American company)
(B) Only India's GNP (since it happens in India)
(C) India's GDP (production within India's borders); NOT India's GNP
(D) More than one of the above
(E) None of the above

---

**Q44.** India's fiscal year runs from:
(A) January 1 to December 31
(B) April 1 to March 31
(C) July 1 to June 30
(D) More than one of the above
(E) None of the above

---

**Q45.** Which of the following statements about GDP is CORRECT?
(A) GDP measures happiness and quality of life accurately
(B) GDP accurately captures all economic activity including informal/black market
(C) GDP has limitations — it doesn't capture income inequality or environmental costs
(D) More than one of the above
(E) None of the above

---

**Q46.** If GDP = ₹200 crore and NFIA (Net Factor Income from Abroad) = +₹10 crore, then GNP =
(A) ₹190 crore
(B) ₹210 crore
(C) ₹200 crore
(D) More than one of the above
(E) None of the above

---

**Q47.** The "Value-Added Method" of GDP calculation is also called:
(A) Income Method
(B) Expenditure Method
(C) Production / Output Method
(D) More than one of the above
(E) None of the above

---

**Q48.** Agriculture contributes about ___% to India's GDP but employs about ___% of India's workforce:
(A) 18-20% GDP; 45-50% workforce
(B) 50% GDP; 18% workforce
(C) 30% GDP; 30% workforce
(D) More than one of the above
(E) None of the above

---

**Q49.** Which of the following is a CORRECT statement about GDP and GNP for India?
(A) India's GNP is always significantly less than its GDP
(B) India's GDP and GNP are approximately equal, as NFIA is relatively small
(C) India's GNP has been consistently higher than GDP because of massive foreign investment in India
(D) More than one of the above
(E) None of the above

---

**Q50.** Consider these statements about National Income accounting:
I.  Three methods of GDP calculation (Expenditure, Income, Production) should give the same result.
II. Real GDP is a better measure of economic GROWTH than Nominal GDP.
III. Transfer payments like pensions DO contribute to GDP calculation under Government Expenditure.
IV. The GDP Deflator measures the average price level change in an economy.

Which statements are CORRECT?
(A) I, II, and III only
(B) I, II, and IV only
(C) All four are correct
(D) More than one of the above
(E) None of the above

---

# ✅ ANSWER KEY

## ⚠️ ATTEMPT ALL 50 QUESTIONS BEFORE CHECKING ANSWERS

---

### CS Answers (Q1–Q25):

| Q  | Ans | Key Reason |
|----|-----|-----------|
| 1  | (C) | TCP/IP developed by DARPA (US DoD); OSI by ISO |
| 2  | (C) | TCP/IP = exactly 4 layers |
| 3  | (B) | Top to bottom: Application, Transport, Internet, Network Access |
| 4  | (B) | TCP/IP Application = OSI Application (7) + Presentation (6) + Session (5) |
| 5  | (C) | Network Access = Data Link (OSI L2) + Physical (OSI L1) combined |
| 6  | (B) | TCP/IP Internet Layer = OSI Network Layer (Layer 3) — same function |
| 7  | (C) | Host-to-Host Layer = Transport Layer (end-to-end between two hosts) |
| 8  | (B) | TCP = reliable, connection-oriented, 3-way handshake |
| 9  | (C) | 3-way handshake: SYN → SYN-ACK → ACK (in that order) |
| 10 | (B) | UDP used when speed > reliability (streaming, gaming) |
| 11 | (B) | SMTP = SENDING emails only; receiving = POP3/IMAP |
| 12 | (C) | HTTP = Port 80; HTTPS = Port 443 |
| 13 | (B) | DNS = UDP, Port 53 (primarily) |
| 14 | (C) | PING uses ICMP (Internet Control Message Protocol) |
| 15 | (A) | FTP: Port 20 (data transfer) and Port 21 (control/commands) |
| 16 | (C) | ARP = resolves IP address → MAC address |
| 17 | (B) | DHCP = automatically assigns IP addresses to devices |
| 18 | (C) | Adding headers going down = Encapsulation |
| 19 | (B) | OSI = theoretical reference model; TCP/IP = practical Internet model |
| 20 | (B) | POP3 = downloads/receives emails from server to device |
| 21 | (C) | FTP = Application Layer; IP = Internet Layer; TCP = Transport Layer |
| 22 | (C) | I, II, III correct; IV wrong: DNS converts DOMAIN → IP (not IP → domain; that's Reverse DNS) |
| 23 | (B) | 1:1 mapping: TCP/IP Transport ↔ OSI Transport; TCP/IP Internet ↔ OSI Network |
| 24 | (C) | Vinton Cerf & Robert Kahn = Fathers of the Internet / TCP/IP designers |
| 25 | (A) | I correct (IP at Internet Layer), II correct (Network Access=L2+L1), III WRONG (no separate Session), IV correct (UDP = faster but unreliable) |

---

### GS Answers (Q26–Q50):

| Q  | Ans | Key Reason |
|----|-----|-----------|
| 26 | (B) | GDP = Gross Domestic Product |
| 27 | (B) | Domestic = within geographical territory regardless of producer's nationality |
| 28 | (B) | Only final goods counted to AVOID DOUBLE COUNTING intermediate inputs |
| 29 | (B) | Nominal = current prices; Real = constant/base year prices |
| 30 | (B) | India's base year = 2011-12 (changed from 2004-05 in 2015) |
| 31 | (B) | Expenditure method: GDP = C + I + G + (X-M) |
| 32 | (B) | G = government spending on goods/services ONLY — excludes transfer payments |
| 33 | (B) | X-M = 500-700 = -200 crore (trade deficit reduces GDP) |
| 34 | (B) | GNP = GDP + Net Factor Income from Abroad (NFIA) |
| 35 | (B) | NDP = GDP - Depreciation ("Net" = after depreciation deduction) |
| 36 | (B) | Per Capita Income = National Income ÷ Total Population |
| 37 | (C) | Income method = Wages + Rent + Interest + Profit + Mixed Income |
| 38 | (C) | Services sector = largest share (~55%) of India's GDP |
| 39 | (B) | GDP Deflator converts Nominal → Real GDP (measures overall price changes) |
| 40 | (C) | Transfer payments (pensions) NOT included in GDP (no new production) |
| 41 | (C) | HDI published by UNDP (United Nations Development Programme) |
| 42 | (B) | HDI = GDP per capita + Education (schooling years) + Health (life expectancy) |
| 43 | (C) | Apple factory in India → India's GDP (within borders); NOT India's GNP (Apple's profit goes to USA) |
| 44 | (B) | India fiscal year = April 1 to March 31 |
| 45 | (C) | GDP has real limitations: doesn't capture inequality, environment, informal economy |
| 46 | (B) | GNP = GDP + NFIA = 200 + 10 = ₹210 crore |
| 47 | (C) | Value-Added Method = Production / Output Method |
| 48 | (A) | Agriculture ~18-20% of GDP but ~45-50% of workforce (disguised unemployment!) |
| 49 | (B) | India's GDP ≈ GNP (NFIA is relatively small; remittances in roughly balance foreign profits out) |
| 50 | (B) | I correct (3 methods = same result), II correct (Real GDP = true growth), III WRONG (transfer payments NOT in GDP), IV correct (GDP Deflator = price level measure) |

---

# 🔁 DAY 44 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — TCP/IP Model

### TCP/IP 4 Layers — Mnemonic:
```
"A Tall Indian Ninja" (Top to Bottom)
  A → Application Layer    (= OSI Layers 7+6+5)
  T → Transport Layer      (= OSI Layer 4)  ["Host-to-Host Layer"]
  I → Internet Layer       (= OSI Layer 3)  ["Network Layer"]
  N → Network Access Layer (= OSI Layers 2+1)
```

### OSI ↔ TCP/IP Mapping:
```
OSI LAYER              TCP/IP LAYER
7 Application  ──┐
6 Presentation ──┼──→  Application Layer
5 Session      ──┘
4 Transport    ─────→  Transport Layer   (Host-to-Host)
3 Network      ─────→  Internet Layer
2 Data Link    ──┐
1 Physical     ──┴──→  Network Access Layer
```

### TCP vs UDP Quick Reference:
```
TCP: Reliable | Connection-oriented | 3-way handshake | Ordered | Slower
     Used for: HTTP, HTTPS, FTP, SMTP, email, banking
     
UDP: Unreliable | Connectionless | No handshake | Unordered | FASTER
     Used for: Video streaming, gaming, DNS, VoIP, live broadcast

ANALOGY: TCP = Registered mail | UDP = Postcard (drop & forget)
```

### Critical Port Numbers (Must Know):
```
HTTP  = 80    | HTTPS = 443  | FTP   = 21/20
SMTP  = 25    | POP3  = 110  | IMAP  = 143
DNS   = 53    | SSH   = 22   | Telnet= 23
DHCP  = 67/68 | SNMP  = 161
```

### Email Protocol Shortcuts:
```
SMTP  → SEND email (outgoing) — Port 25
POP3  → Receive + DOWNLOAD email to device — Port 110
IMAP  → Receive + READ on server (stays there) — Port 143
```

### PYQ Trap Quick List — TCP/IP:
```
✅ TCP/IP = 4 layers (not 7!)
✅ SMTP = SENDING emails (NOT receiving)
✅ UDP = FASTER (not TCP); TCP = RELIABLE
✅ TCP/IP Internet Layer = OSI Network Layer
✅ Host-to-Host = Transport Layer
✅ Network Access = Data Link + Physical combined
✅ TCP/IP has NO separate Presentation or Session layers
✅ OSI = reference model; Internet uses TCP/IP
✅ DNS uses UDP (Port 53); PING uses ICMP
✅ FTP = TWO ports: 20 (data) + 21 (control)
✅ Vinton Cerf + Robert Kahn = Fathers of Internet
```

---

## ⚡ RAPID FIRE — GDP Economics

### GDP Formula:
```
EXPENDITURE METHOD: GDP = C + I + G + (X - M)
  C = Consumption (households) — LARGEST component
  I = Investment (business capital goods)
  G = Government spending (goods/services ONLY — NO transfer payments)
  X = Exports (goods made here, sold abroad)
  M = Imports (subtract — made abroad)

INCOME METHOD: GDP = W + R + I + P + Mixed Income
  W=Wages, R=Rent, I=Interest, P=Profit

PRODUCTION METHOD: Sum of VALUE ADDED at each production stage
```

### Nominal vs Real GDP:
```
NOMINAL GDP = Current Year Quantity × CURRENT Prices  (inflated by price rise)
REAL GDP    = Current Year Quantity × BASE YEAR Prices (true growth)

India's Base Year = 2011-12

Real GDP = BETTER measure of actual economic growth
```

### National Income Aggregates:
```
GDP → +NFIA → GNP → -Depreciation → NNP → -Indirect Taxes + Subsidies → NI
"Good Navigators Go North Never Inland" (GDP→GNP→NDP→NNP→NI)

GDP  = Within borders
GNP  = GDP + NFIA (by residents anywhere)
NDP  = GDP - Depreciation
NNP  = GNP - Depreciation
NI   = NNP at factor cost
```

### India-Specific Key Facts:
```
Largest GDP sector:  SERVICES (~55%)
Agriculture GDP:     ~18-20% (but ~45% employment!)
Base Year:           2011-12
Fiscal Year:         April 1 to March 31
India global rank:   5th by Nominal GDP; 3rd by PPP
HDI published by:    UNDP | HDI founders: Mahbub ul Haq + Amartya Sen
```

### PYQ Trap List — Economics:
```
✅ GDP = within borders (not by nationality)
✅ Only FINAL goods in GDP (to avoid double counting)
✅ Real GDP = constant prices = true growth
✅ India base year = 2011-12 (NOT 2004-05!)
✅ G in GDP formula = government spending (NOT transfer payments)
✅ NDP = GDP MINUS depreciation (not plus!)
✅ Services = largest sector in India GDP (~55%)
✅ Agriculture = ~18% GDP but ~45-50% employment
✅ Transfer payments (pensions) NOT in GDP
✅ GNP = GDP + NFIA (Net Factor Income from Abroad)
✅ HDI = UNDP; 3 components: Income + Education + Health
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **TCP/IP = 4 layers** (Application→Transport→Internet→Network Access); OSI 3 upper layers merge into Application; OSI 2 lower layers merge into Network Access; Internet Layer = OSI Network Layer; Host-to-Host = Transport Layer.
2. **TCP vs UDP**: TCP = reliable, connection-oriented, 3-way handshake (SYN→SYN-ACK→ACK), slower; UDP = fast, connectionless, no ACK; TCP for HTTP/FTP/SMTP; UDP for streaming/gaming/DNS.
3. **Email protocols**: SMTP (Port 25) = SEND only; POP3 (Port 110) = download to device; IMAP (Port 143) = read on server; DNS = Port 53 (UDP); HTTP = Port 80; HTTPS = Port 443.
4. **GDP formula**: GDP = C + I + G + (X-M); Real GDP uses BASE YEAR prices (India = 2011-12); Nominal uses current prices; GNP = GDP + NFIA; NDP = GDP - Depreciation.
5. **India Economics traps**: Services = largest GDP sector (~55%); Agriculture ~18% GDP but ~45% employment; Transfer payments NOT in GDP's "G"; India's base year = 2011-12 (not 2004-05); HDI = UNDP = Income + Education + Health.

---

## 📅 DAY 45 PREVIEW — What's Coming Next:
**CS**: Computer Networks — Network Topologies (Bus, Star, Ring, Mesh, Tree, Hybrid), Network Devices (Hub, Switch, Router, Bridge, Gateway, Repeater, Modem), Transmission Media (Twisted Pair, Coaxial, Fiber Optic, Wireless)
**GS**: Indian Economy — Inflation: Types (Demand-pull, Cost-push), Measurement (CPI, WPI), RBI's role, Monetary Policy basics

---

*🚀 Day 44 of 170 — 26% through the journey. TCP/IP + GDP are two of the highest-value topics in your exam. Nail the mappings and the formulas today and you're set for the Networks section. Keep pushing!*
