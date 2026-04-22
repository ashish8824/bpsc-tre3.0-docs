# 📅 BPSC TRE 4.0 — DAY 49 COMPLETE STUDY MODULE
### FULL COMPUTER NETWORKS REVISION (Days 43–48) + Geography — India & Bihar
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Full Networks Revision — OSI, TCP/IP, IP, Protocols, Topologies, Security
> - Afternoon (1 hr): Geography — India Physical Features, Climate, Monsoon + Bihar Geography
> - Evening (1 hr): Solve all 55 MCQs (30 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points + mark weak areas

---

# PART 1: COMPUTER SCIENCE
## 🔁 FULL COMPUTER NETWORKS — ONE-PAGE POWER REVISION

---

## 🔷 BLOCK 1: OSI MODEL — 7 Layers

```
┌──────────────────────────────────────────────────────────────────────────────┐
│         OSI MODEL — TOP TO BOTTOM (Sender: 7→1 ; Receiver: 1→7)             │
├──────┬──────────────────────┬───────────┬────────────────────┬───────────────┤
│  #   │    LAYER NAME        │   PDU     │   KEY FUNCTION     │  KEY PROTOCOL │
├──────┼──────────────────────┼───────────┼────────────────────┼───────────────┤
│  7   │  Application         │   Data    │ User interface,    │ HTTP, FTP,    │
│      │                      │           │ network services   │ SMTP, DNS     │
├──────┼──────────────────────┼───────────┼────────────────────┼───────────────┤
│  6   │  Presentation        │   Data    │ Encryption,        │ SSL/TLS,      │
│      │                      │           │ Compression,       │ JPEG, MPEG    │
│      │                      │           │ Translation        │               │
├──────┼──────────────────────┼───────────┼────────────────────┼───────────────┤
│  5   │  Session             │   Data    │ Session setup,     │ NetBIOS, RPC  │
│      │                      │           │ maintenance,       │               │
│      │                      │           │ termination        │               │
├──────┼──────────────────────┼───────────┼────────────────────┼───────────────┤
│  4   │  Transport           │  SEGMENT  │ End-to-end         │ TCP, UDP      │
│      │                      │           │ reliability,       │               │
│      │                      │           │ flow control       │               │
├──────┼──────────────────────┼───────────┼────────────────────┼───────────────┤
│  3   │  Network             │  PACKET   │ Routing, IP        │ IP, ICMP,     │
│      │                      │           │ addressing         │ ARP, OSPF     │
├──────┼──────────────────────┼───────────┼────────────────────┼───────────────┤
│  2   │  Data Link           │  FRAME    │ MAC addressing,    │ Ethernet,     │
│      │                      │           │ framing, error     │ Wi-Fi (802.11)│
│      │                      │           │ detection          │               │
├──────┼──────────────────────┼───────────┼────────────────────┼───────────────┤
│  1   │  Physical            │  BITS     │ Signal/bit         │ Cables, Hub,  │
│      │                      │           │ transmission       │ Repeater      │
└──────┴──────────────────────┴───────────┴────────────────────┴───────────────┘

MNEMONIC (Top→Bottom): "All People Seem To Need Data Processing"
MNEMONIC (Bottom→Top): "Please Do Not Throw Sausage Pizza Away"
PDU TRICK (L4→L1):    "Sergeant Peters Fought Bravely"
                        S=Segment, P=Packet, F=Frame, B=Bits

OSI DEVICE MAPPING:
  Layer 1 → Hub, Repeater, Modem, Cables
  Layer 2 → Switch, Bridge, NIC
  Layer 3 → Router
  Layer 7 → Gateway (connects different protocol networks)
```

### OSI — Top 10 PYQ Traps:
```
✅ OSI = EXACTLY 7 layers (never 4 or 5)
✅ Physical Layer = BITS (never frames or packets)
✅ Data Link Layer = FRAME (never packet)
✅ Network Layer = PACKET (never segment)
✅ Transport Layer = SEGMENT (never packet)
✅ Router = Layer 3 (never Layer 2!)
✅ Switch = Layer 2 (never Layer 3!)
✅ Hub = Layer 1 (broadcasts ALL ports — not intelligent)
✅ Encryption = Presentation Layer (Layer 6)
✅ Gateway = Application Layer (Layer 7) — connects DIFFERENT protocols
```

---

## 🔷 BLOCK 2: TCP/IP MODEL — 4 Layers

```
┌─────────────────────────────────────────────────────────────────────────────┐
│     TCP/IP MODEL                  OSI MAPPING          KEY PROTOCOLS        │
├──────────────────────────────────────────────────────────────────────────────┤
│                           ┌──── OSI Layer 7 ────┐                           │
│  4. APPLICATION LAYER ←───┤    OSI Layer 6      ├──── HTTP, FTP, SMTP, DNS │
│                           └──── OSI Layer 5 ────┘                           │
├──────────────────────────────────────────────────────────────────────────────┤
│  3. TRANSPORT LAYER    ←───── OSI Layer 4 ──────────── TCP, UDP             │
│     (Host-to-Host)                                                           │
├──────────────────────────────────────────────────────────────────────────────┤
│  2. INTERNET LAYER     ←───── OSI Layer 3 ──────────── IP, ICMP, ARP       │
│     (Network Layer)                                                          │
├──────────────────────────────────────────────────────────────────────────────┤
│                           ┌──── OSI Layer 2 ────┐                           │
│  1. NETWORK ACCESS     ←───┤    OSI Layer 1      ├──── Ethernet, Wi-Fi,MAC  │
│                           └─────────────────────┘                           │
└─────────────────────────────────────────────────────────────────────────────┘

MNEMONIC: "A Tall Indian Ninja" (Application, Transport, Internet, Network Access)

KEY DIFFERENCES:
  OSI = 7 layers (theoretical reference model)
  TCP/IP = 4 layers (ACTUALLY used on the Internet)
  OSI developer = ISO (1984)
  TCP/IP developer = DARPA (1974, Vinton Cerf & Robert Kahn)
  TCP/IP has NO separate Presentation, Session, or Physical layers
```

---

## 🔷 BLOCK 3: OSI vs TCP/IP — MASTER COMPARISON TABLE

```
┌──────────────────────────┬────────────────────────────┬──────────────────────────────┐
│         FEATURE          │          OSI               │          TCP/IP              │
├──────────────────────────┼────────────────────────────┼──────────────────────────────┤
│ Number of layers         │ 7                          │ 4                            │
├──────────────────────────┼────────────────────────────┼──────────────────────────────┤
│ Developed by             │ ISO (1984)                 │ DARPA (1974)                 │
├──────────────────────────┼────────────────────────────┼──────────────────────────────┤
│ Nature                   │ Theoretical (reference)    │ Practical (Internet uses it) │
├──────────────────────────┼────────────────────────────┼──────────────────────────────┤
│ Separate Session Layer?  │ YES (Layer 5)              │ NO (merged into Application) │
├──────────────────────────┼────────────────────────────┼──────────────────────────────┤
│ Separate Physical Layer? │ YES (Layer 1)              │ NO (merged into Net Access)  │
├──────────────────────────┼────────────────────────────┼──────────────────────────────┤
│ Transport Layer name     │ Transport Layer            │ Transport/Host-to-Host Layer │
├──────────────────────────┼────────────────────────────┼──────────────────────────────┤
│ Network Layer name       │ Network Layer              │ Internet Layer               │
├──────────────────────────┼────────────────────────────┼──────────────────────────────┤
│ Founders of Internet     │ N/A                        │ Vinton Cerf + Robert Kahn    │
└──────────────────────────┴────────────────────────────┴──────────────────────────────┘
```

---

## 🔷 BLOCK 4: TCP vs UDP — MASTER COMPARISON

```
┌────────────────────────┬──────────────────────────────┬────────────────────────────┐
│       FEATURE          │            TCP               │            UDP             │
├────────────────────────┼──────────────────────────────┼────────────────────────────┤
│ Connection type        │ Connection-ORIENTED          │ Connection-LESS            │
│                        │ (3-way handshake)            │ (no setup)                 │
├────────────────────────┼──────────────────────────────┼────────────────────────────┤
│ Reliability            │ RELIABLE (ACK + retransmit)  │ UNRELIABLE (no ACK)        │
├────────────────────────┼──────────────────────────────┼────────────────────────────┤
│ Speed                  │ SLOWER                       │ FASTER                     │
├────────────────────────┼──────────────────────────────┼────────────────────────────┤
│ PDU                    │ Segment                      │ Datagram                   │
├────────────────────────┼──────────────────────────────┼────────────────────────────┤
│ Flow control           │ YES (sliding window)         │ NO                         │
├────────────────────────┼──────────────────────────────┼────────────────────────────┤
│ Header size            │ 20+ bytes                    │ 8 bytes (minimal)          │
├────────────────────────┼──────────────────────────────┼────────────────────────────┤
│ Use cases              │ Web, Email, FTP, SSH,        │ Streaming, Gaming, DNS,    │
│                        │ Online banking               │ VoIP, IoT                  │
├────────────────────────┼──────────────────────────────┼────────────────────────────┤
│ 3-way handshake        │ SYN → SYN-ACK → ACK          │ None                       │
└────────────────────────┴──────────────────────────────┴────────────────────────────┘

MEMORY: TCP = "Takes Care Perfectly" | UDP = "Ultra Direct & Primitive"
```

---

## 🔷 BLOCK 5: IPv4 vs IPv6 — MASTER COMPARISON

```
┌────────────────────────┬──────────────────────────────┬────────────────────────────┐
│       FEATURE          │            IPv4              │            IPv6            │
├────────────────────────┼──────────────────────────────┼────────────────────────────┤
│ Address size           │ 32 BITS                      │ 128 BITS                   │
├────────────────────────┼──────────────────────────────┼────────────────────────────┤
│ Total addresses        │ ~4.3 billion (2^32)          │ ~340 undecillion (2^128)   │
├────────────────────────┼──────────────────────────────┼────────────────────────────┤
│ Notation               │ Dotted DECIMAL (192.168.1.1) │ HEX with colons (2001::1)  │
├────────────────────────┼──────────────────────────────┼────────────────────────────┤
│ NAT required?          │ YES                          │ NO (every device unique)   │
├────────────────────────┼──────────────────────────────┼────────────────────────────┤
│ Security               │ Optional (IPSec add-on)      │ BUILT-IN (IPSec mandatory) │
├────────────────────────┼──────────────────────────────┼────────────────────────────┤
│ Loopback address       │ 127.0.0.1                    │ ::1                        │
├────────────────────────┼──────────────────────────────┼────────────────────────────┤
│ Broadcast              │ YES (255.255.255.255)         │ NO (uses multicast)        │
├────────────────────────┼──────────────────────────────┼────────────────────────────┤
│ Auto-config            │ Needs DHCP                   │ SLAAC (self-configures)    │
└────────────────────────┴──────────────────────────────┴────────────────────────────┘

IPv4 CLASSES:
  Class A: 1–126    | 255.0.0.0    (/8)  | ~16.7M hosts
  Class B: 128–191  | 255.255.0.0  (/16) | ~65K hosts
  Class C: 192–223  | 255.255.255.0(/24) | 254 hosts
  Class D: 224–239  | Multicast only
  Class E: 240–255  | Experimental/Reserved

PRIVATE RANGES: 10.x.x.x | 172.16-31.x.x | 192.168.x.x
LOOPBACK: 127.0.0.1 | BROADCAST: 255.255.255.255

CIDR SHORTCUTS:
  /8  = 255.0.0.0        (Class A mask)
  /16 = 255.255.0.0      (Class B mask)
  /24 = 255.255.255.0    (Class C mask, 254 hosts)
  /25 = 255.255.255.128  (126 hosts)
  /26 = 255.255.255.192  (62 hosts)

USABLE HOSTS FORMULA: 2^(host bits) − 2
```

---

## 🔷 BLOCK 6: KEY PROTOCOLS — RAPID REFERENCE

```
┌───────────────┬──────────┬──────────────────────────┬─────────────────────────────┐
│   PROTOCOL    │   PORT   │         PURPOSE          │          NOTES              │
├───────────────┼──────────┼──────────────────────────┼─────────────────────────────┤
│ HTTP          │   80     │ Web browsing             │ Stateless; request-response │
│ HTTPS         │   443    │ Secure web               │ HTTP + SSL/TLS encryption   │
│ FTP           │  20/21   │ File transfer            │ Port 21=control; 20=data    │
│ SMTP          │   25     │ SEND email               │ ⚠️ SENDING only!            │
│ POP3          │   110    │ RECEIVE email (download) │ Deletes from server         │
│ IMAP          │   143    │ READ email (stays)       │ Stays on server             │
│ DNS           │   53     │ Domain → IP address      │ Uses UDP primarily          │
│ DHCP          │  67/68   │ Auto-assign IP           │ Server=67; Client=68        │
│ SSH           │   22     │ Secure remote access     │ Secure version of Telnet    │
│ Telnet        │   23     │ Remote access (insecure) │ Plain text (avoid!)         │
│ SNMP          │   161    │ Network mgmt             │ Monitors devices            │
│ MQTT          │  1883    │ IoT messaging            │ Publish-Subscribe; Port 1883│
└───────────────┴──────────┴──────────────────────────┴─────────────────────────────┘

PING = ICMP protocol (NOT TCP or UDP!) = Measures RTT + Packet Loss
PING full form = Packet Internet Groper (NOT Generator!)
SMTP TRAP = SMTP CLIENT = the SENDING mail server (server-to-server)
```

---

## 🔷 BLOCK 7: NETWORK TOPOLOGIES — RAPID REFERENCE

```
┌───────────┬──────────────────────────────┬──────────────────────┬────────────────┐
│ TOPOLOGY  │      KEY FEATURE             │    FAILURE POINT     │ RELIABILITY    │
├───────────┼──────────────────────────────┼──────────────────────┼────────────────┤
│ BUS       │ Single backbone cable        │ One cable break =    │ LOWEST         │
│           │ + terminators at both ends   │ whole network down   │                │
├───────────┼──────────────────────────────┼──────────────────────┼────────────────┤
│ STAR      │ All to central hub/switch    │ Central device fails │ Medium         │
│           │ MOST POPULAR for LAN         │ = whole network down │                │
├───────────┼──────────────────────────────┼──────────────────────┼────────────────┤
│ RING      │ Circular; token passing      │ One break =          │ Medium-Low     │
│           │ No collisions                │ whole network down   │                │
├───────────┼──────────────────────────────┼──────────────────────┼────────────────┤
│ MESH      │ Every device to every other  │ No single failure    │ HIGHEST        │
│           │ n(n-1)/2 links; most costly  │ point (multiple paths│                │
├───────────┼──────────────────────────────┼──────────────────────┼────────────────┤
│ TREE      │ Hierarchical (Star + Bus)    │ Root failure =       │ Medium-High    │
│           │                              │ whole network down   │                │
├───────────┼──────────────────────────────┼──────────────────────┼────────────────┤
│ HYBRID    │ Mix of 2+ topologies         │ Depends on design    │ Flexible       │
└───────────┴──────────────────────────────┴──────────────────────┴────────────────┘

⚠️ PYQ TRAP: Peer-to-Peer = NETWORK MODEL (not a topology!)
⚠️ PYQ TRAP: Bus uses CSMA/CD for collision control
⚠️ PYQ TRAP: Ring uses TOKEN PASSING (no collisions in Ring!)
⚠️ PYQ TRAP: Mesh formula = n(n-1)/2 links (most expensive)
```

---

## 🔷 BLOCK 8: NETWORKING DEVICES — LAYER MAPPING

```
┌──────────────────────┬────────────────────────┬────────────────────────────────┐
│       DEVICE         │       OSI LAYER        │         KEY FUNCTION           │
├──────────────────────┼────────────────────────┼────────────────────────────────┤
│ Repeater             │ Layer 1 — Physical      │ Regenerates/amplifies signal   │
│ Hub                  │ Layer 1 — Physical      │ Broadcasts to ALL ports        │
│ Modem                │ Layer 1 — Physical      │ Digital ↔ Analog conversion    │
├──────────────────────┼────────────────────────┼────────────────────────────────┤
│ NIC                  │ Layer 2 — Data Link     │ Device's network interface     │
│ Bridge               │ Layer 2 — Data Link     │ Connects two LAN segments      │
│ Switch               │ Layer 2 — Data Link     │ MAC table → unicast to correct │
├──────────────────────┼────────────────────────┼────────────────────────────────┤
│ Router               │ Layer 3 — Network       │ IP table → routes between nets │
├──────────────────────┼────────────────────────┼────────────────────────────────┤
│ Gateway              │ Layer 7 — Application   │ Connects DIFFERENT protocol    │
│                      │ (all layers)           │ networks (protocol translator) │
└──────────────────────┴────────────────────────┴────────────────────────────────┘

KEY DISTINCTIONS:
  Switch uses MAC address → Switch connects devices on SAME network (LAN)
  Router uses IP address → Router connects DIFFERENT networks
  Hub broadcasts to ALL → Switch unicasts to CORRECT device
  Gateway ≠ Router (Gateway = different protocols; Router = same protocol)
```

---

## 🔷 BLOCK 9: TRANSMISSION MEDIA — RAPID REFERENCE

```
┌──────────────────┬──────────────┬─────────────────┬───────────────────────────┐
│     MEDIUM       │    SPEED     │   INTERFERENCE  │   MAIN USE                │
├──────────────────┼──────────────┼─────────────────┼───────────────────────────┤
│ UTP              │ Moderate     │ HIGH (vulnerable)│ Office LAN (most common)  │
│ STP              │ Moderate     │ Low (shielded)   │ Industrial LAN            │
│ Coaxial          │ Moderate     │ Medium           │ Cable TV / Cable internet │
│ OPTICAL FIBER    │ HIGHEST⚠️   │ ZERO (immune!)   │ Backbone, FTTH, BharatNet │
├──────────────────┼──────────────┼─────────────────┼───────────────────────────┤
│ Radio Waves      │ Varies       │ High (spectrum)  │ Wi-Fi, Mobile, FM radio   │
│ Microwaves       │ High         │ Medium (LoS)     │ Satellite, relay towers   │
│ Infrared         │ Low-Medium   │ Low              │ Remote controls (TV/AC)   │
└──────────────────┴──────────────┴─────────────────┴───────────────────────────┘

⚠️ KEY FACTS:
  Fiber = FASTEST + IMMUNE to EMI (uses light, not electricity)
  UTP = CHEAPEST but MOST vulnerable to EMI
  Microwaves = LINE-OF-SIGHT (blocked by obstacles)
  Infrared = SHORT RANGE + cannot penetrate walls
  BharatNet = uses OPTICAL FIBER for rural broadband
```

---

## 🔷 BLOCK 10: NETWORK SECURITY & CRYPTOGRAPHY — RAPID REFERENCE

```
CIA TRIAD: Confidentiality + Integrity + Availability

SNIFFING:
  → Most effective on HUB networks (hub broadcasts to all)
  → SWITCH-based networks PREVENT/REDUCE sniffing
  → Wireshark = legitimate packet analyser tool

MALWARE QUICK REFERENCE:
  Virus     = attaches to HOST FILES; spreads when files shared
  Worm      = spreads INDEPENDENTLY through network (no host file needed)
  Trojan    = disguised as legitimate software (appears safe)
  Ransomware= ENCRYPTS files + demands ransom for decryption key
  Spyware   = secretly monitors user activity

CRYPTOGRAPHY:
  ┌─────────────────────────────────────────────────────────────────┐
  │  SYMMETRIC          │  ASYMMETRIC (Public Key)                  │
  │  Same key (one key) │  Two keys (public + private)              │
  │  FASTER             │  SLOWER                                   │
  │  Key sharing = PROBLEM│ Key sharing = SOLVED                    │
  │  AES, DES, 3DES     │  RSA, ECC, DSA                           │
  └─────────────────────────────────────────────────────────────────┘
  
⚠️ PRIVATE KEY = NEVER shared = kept SECRET by RECEIVER/OWNER
⚠️ PUBLIC KEY = shared FREELY with everyone
⚠️ Digital Signature = created with PRIVATE key; verified with PUBLIC key
⚠️ HTTPS = HYBRID (asymmetric for key exchange + symmetric AES for data)
⚠️ AES = symmetric; RSA = asymmetric (common exam confusion!)

WWW vs INTERNET:
  Internet = global network infrastructure (hardware)
  WWW = service running ON the internet (websites, browsers)
  WWW inventor = Tim Berners-Lee (1989, CERN)
  Internet developed by DARPA
```

---

## 🔷 MASTER PYQ TRAP LIST — ALL NETWORKS

```
#   STATEMENT                                          TRUTH
──────────────────────────────────────────────────────────────────
1.  "OSI has 4/5 layers"                        → FALSE! OSI = 7 layers
2.  "Physical Layer = Frames"                   → FALSE! Physical = BITS
3.  "Transport Layer = Packets"                 → FALSE! Transport = SEGMENTS
4.  "Router = Layer 2 device"                   → FALSE! Router = Layer 3
5.  "Switch = Layer 3 device"                   → FALSE! Switch = Layer 2
6.  "Hub reads MAC addresses"                   → FALSE! Hub broadcasts ALL
7.  "TCP/IP has 7 layers"                       → FALSE! TCP/IP = 4 layers
8.  "IPv4 = 128 bits"                           → FALSE! IPv4 = 32 bits
9.  "IPv6 = 32 bits"                            → FALSE! IPv6 = 128 bits
10. "192.168.x.x = public IP"                   → FALSE! It's PRIVATE range
11. "/24 = 255.255.0.0"                         → FALSE! /24 = 255.255.255.0
12. "SMTP = receiving emails"                   → FALSE! SMTP = SENDING only
13. "Ping uses UDP"                             → FALSE! Ping uses ICMP
14. "Ping full form = Packet Internet Generator"→ FALSE! = Groper
15. "P2P is a network topology"                 → FALSE! P2P = network model
16. "Bus topology = no single failure point"    → FALSE! One break = total failure
17. "Fiber affected by EMI"                     → FALSE! Fiber = IMMUNE to EMI
18. "Private key shared publicly"               → FALSE! Private key = SECRET
19. "AES = asymmetric algorithm"               → FALSE! AES = symmetric
20. "RSA = symmetric algorithm"                → FALSE! RSA = asymmetric
21. "Symmetric is slower than asymmetric"      → FALSE! Symmetric is FASTER
22. "WWW = Internet"                           → FALSE! WWW is a service ON internet
23. "MQTT = web browsing protocol"             → FALSE! MQTT = IoT (IoT devices)
24. "Ring topology uses CSMA/CD"               → FALSE! Ring uses TOKEN PASSING
25. "TCP is faster than UDP"                   → FALSE! UDP is faster
```

---

# PART 2: GENERAL STUDIES
## 🗺️ Geography — India Physical Features + Bihar Geography

---

## 🔷 SECTION 1: India — Physical Geography Overview

### Location and Extent:
```
INDIA'S GEOGRAPHICAL POSITION:
  → Located in South Asia (Northern Hemisphere)
  → Latitudinal extent: 8°4'N to 37°6'N
  → Longitudinal extent: 68°7'E to 97°25'E
  → Standard Meridian: 82°30'E (passes through Mirzapur, UP)
    → Standard Time (IST) = GMT + 5:30 hours

AREA AND DIMENSIONS:
  → Total area: 3.287 million sq km (7th largest in world)
  → North-South extent: ~3,214 km
  → East-West extent: ~2,933 km
  → Coastline length: ~7,516 km (including islands)
  → Land borders: ~15,200 km

INDIA'S BORDERS:
  → North: China, Nepal, Bhutan
  → Northwest: Pakistan, Afghanistan
  → East: Bangladesh, Myanmar
  → South: Sri Lanka (across Palk Strait)
  → Southwest: Maldives (in Indian Ocean)

SOUTHERNMOST POINT: Indira Point (Andaman & Nicobar Islands) at ~6°45'N
NORTHERNMOST POINT: Siachen Glacier area (~37°6'N)
EASTERNMOST POINT: Kibithu, Arunachal Pradesh
WESTERNMOST POINT: Sir Creek area, Gujarat

🎯 PYQ FACT: Standard meridian = 82°30'E (Mirzapur, Allahabad, UP)
🎯 PYQ FACT: IST = GMT + 5 hours 30 minutes
🎯 PYQ FACT: India shares land border with 6 countries: Pakistan, Afghanistan, China, Nepal, Bhutan, Bangladesh, Myanmar (7 countries including Myanmar)
```

---

## 🔷 SECTION 2: Physical Divisions of India

```
INDIA'S FIVE MAJOR PHYSICAL DIVISIONS:

1. THE HIMALAYAS (Northern Mountains)
2. THE INDO-GANGETIC PLAINS (Northern Plains)
3. THE PENINSULAR PLATEAU (Deccan Plateau)
4. THE COASTAL PLAINS (East and West coasts)
5. THE ISLANDS (Andaman & Nicobar + Lakshadweep)
```

### 1. THE HIMALAYAS:
```
FORMATION: Formed by collision of Indo-Australian and Eurasian plates
           = FOLD MOUNTAINS (youngest mountains in India)
           
THREE PARALLEL RANGES:
  → Himadri (Greater Himalayas): Highest, avg >6,000m
    Contains: Mt. Everest (8,849m — world's highest, Nepal/China border)
    K2 (8,611m — in Pakistan, 2nd highest in world)
    Kanchenjunga (8,586m — highest peak in INDIA, Sikkim)
  → Himachal (Lesser Himalayas): 3,700-4,500m range
    Contains: Shimla, Mussoorie, Nainital hill stations
    Pirpanjal Range, Dhauladhar Range
  → Shivaliks (Sub-Himalayas / Outer Himalayas): Lowest, 900-1,200m
    Foothills — Doon Valley (Dehradun) between Shivaliks and Himachal

IMPORTANT PASSES:
  → Karakoram Pass: Jammu & Kashmir (route to China/Central Asia)
  → Zoji La: J&K (connects Srinagar to Leh)
  → Rohtang Pass: Himachal Pradesh (connects Manali to Lahaul-Spiti)
  → Nathu La: Sikkim (trade route to China — reopened 2006!)
  → Bomdi La: Arunachal Pradesh (India-China border)

🎯 PYQ FACT: Kanchenjunga = highest peak IN INDIA (not Everest — Everest is in Nepal!)
🎯 PYQ FACT: Himalayas = FOLD mountains (youngest)
🎯 PYQ FACT: Nathu La pass = Sikkim (India-China trade route)
```

### 2. NORTHERN PLAINS (Indo-Gangetic Plains):
```
FORMATION: Deposited by Indus, Ganga, and Brahmaputra river systems
           = ALLUVIAL PLAINS (most fertile agricultural land!)

EXTENT: From Punjab (west) to Assam (east) — ~2,400 km long

THREE DIVISIONS:
  → Punjab Plains: Western part; Indus river system; now mostly in Pakistan
  → Ganga Plains: Central; most densely populated; includes Bihar!
  → Brahmaputra Plains: Eastern; Assam

SOIL: Alluvial (Khadar = new fertile; Bhangar = old less fertile)
RIVERS: Indus, Ganga, Yamuna, Brahmaputra and their tributaries

WHY MOST POPULATED?
  → Flat land (easy farming and transport)
  → Fertile alluvial soil
  → Perennial rivers (year-round water)
  → Good climate for agriculture

BIHAR LOCATION: Bihar lies entirely in the GANGA PLAINS
                Ganga River divides Bihar into North and South Bihar

🎯 PYQ FACT: Northern Plains = most fertile agricultural region of India
🎯 PYQ FACT: Bihar = located in Indo-Gangetic Plains (Ganga Plains)
🎯 PYQ FACT: ALLUVIAL SOIL = most fertile soil type in Northern Plains
```

### 3. PENINSULAR PLATEAU (Deccan Plateau):
```
FORMATION: Oldest geological formation in India (part of Gondwana landmass)
           = Made of HARD IGNEOUS and METAMORPHIC rocks
           
EXTENT: Entire southern/central India; triangular shape

KEY FEATURES:
  → Deccan Plateau: Main plateau (Maharashtra, Andhra Pradesh, Telangana, Karnataka)
  → Malwa Plateau: Madhya Pradesh and Rajasthan
  → Chotanagpur Plateau: Jharkhand (mineral-rich!)
  → Vindhya Range: Separates North India from Peninsular India
  → Satpura Range: Parallel to Vindhyas (south)
  → Western Ghats: Western edge of Deccan (continuous, causes orographic rainfall)
  → Eastern Ghats: Discontinuous along eastern coast

RIVERS FROM DECCAN:
  → Westward flowing (into Arabian Sea): Narmada, Tapi/Tapti
  → Eastward flowing (into Bay of Bengal): Mahanadi, Godavari, Krishna, Kaveri

CHOTANAGPUR PLATEAU (Bihar/Jharkhand connection):
  → Was part of Bihar before Jharkhand's formation in 2000
  → Rich in minerals: Coal, Iron ore, Copper, Mica, Uranium
  → Called "Ruhr of India" (like Germany's Ruhr industrial region)

🎯 PYQ FACT: Chotanagpur Plateau = mineral-rich; "Ruhr of India"
🎯 PYQ FACT: Deccan Plateau = oldest landform in India
🎯 PYQ FACT: Narmada and Tapi flow WESTWARD (unique among Peninsular rivers)
```

---

## 🔷 SECTION 3: India — Climate and Monsoon

### Types of Climate:
```
INDIA'S CLIMATE = Tropical Monsoon Climate (mainly)

FOUR SEASONS:
  1. Winter (Dec–Feb): Cold and dry; NE winds
     → North India: Cold with fog; Snowfall in Himalayas
     → South India: Mild winter (never very cold)
     
  2. Hot Weather / Summer (Mar–May): Hot and dry
     → North India: Very hot (45°C+ in Rajasthan!)
     → Loo = hot, dry, dusty western wind in Indo-Gangetic plains
     → Mango showers in Kerala/Karnataka (pre-monsoon showers)
     
  3. Southwest Monsoon (Jun–Sept): Main rainy season
     → The most important season — provides ~80% of India's rainfall!
     
  4. Retreating Monsoon / Northeast Monsoon (Oct–Nov):
     → Southwest monsoon retreats from north to south
     → Tamil Nadu gets most rain NOW (from NE monsoon off Bay of Bengal)
     → Cyclones common in Bay of Bengal during this period
```

### The Monsoon — India's Lifeline:
```
SOUTHWEST MONSOON (June–September):

ORIGIN: Differential heating of land and sea
  → Summer: Indian subcontinent heats up rapidly
  → Arabian Sea and Bay of Bengal remain cooler
  → Hot air over land rises → creates LOW PRESSURE area over India
  → Moist ocean air rushes in to fill the low pressure
  → This moist wind = MONSOON!

TWO BRANCHES:
  1. ARABIAN SEA BRANCH:
     → Strikes Kerala coast first (around June 1 — "Monsoon onset")
     → Moves north along Western Ghats (heavy rain on west coast)
     → Then moves into Gujarat, Maharashtra, Madhya Pradesh
     → One part enters Punjab, Rajasthan (weaker here)
     
  2. BAY OF BENGAL BRANCH:
     → Enters northeast India (Assam, Meghalaya) first
     → Mawsynram and Cherrapunji (Meghalaya) = WETTEST places on Earth!
       (>11,000 mm annual rainfall!)
     → Moves up the Ganga plains west
     → Joins Arabian Sea branch over northwest India

MONSOON ONSET:
  → Kerala: Around June 1 (earliest in India — also called "Monsoon Burst")
  → Bihar: Around June 10-15
  → Delhi: Around June 29
  → Rajasthan: July (last to get monsoon)

MONSOON WITHDRAWAL:
  → Withdraws from Rajasthan first (September)
  → Withdraws from Tamil Nadu last (November/December)

MAWSYNRAM vs CHERRAPUNJI:
  → Mawsynram = HIGHEST average annual rainfall in the world!
  → Cherrapunji = holds records for highest rainfall in specific months
  → Both in Meghalaya (East Khasi Hills)
  
ZERO RAINFALL AREA:
  → Jaisalmer, Rajasthan = driest place in India (Desert)
  → Leh/Ladakh = very low rainfall (rain shadow of Himalayas)

🎯 PYQ FACT: Southwest Monsoon = India's main rainy season (June-Sept)
🎯 PYQ FACT: Monsoon onset = Kerala first (around June 1)
🎯 PYQ FACT: Mawsynram = highest annual rainfall in world (Meghalaya)
🎯 PYQ FACT: Tamil Nadu gets rain in October-November (NE monsoon)
🎯 PYQ FACT: Rajasthan = driest region; Leh-Ladakh = cold desert
```

---

## 🔷 SECTION 4: Bihar Geography — Key Facts

### Location and Basic Facts:
```
BIHAR — GEOGRAPHICAL PROFILE:
  → Location: East India; 24°20'N to 27°31'N, 83°19'E to 88°17'E
  → Area: 94,163 sq km (13th largest state in India)
  → Population: ~12.4 crore (2011 census) — 3rd most populous state!
  → Population share: ~8.6% of India's total population
  → Population density: ~1,106 per sq km (highest among large states!)
  → Borders: UP (west), Jharkhand (south), West Bengal (east), Nepal (north)
  → Districts: 38 districts
  → Capital: Patna (ancient name: Pataliputra)
  → Highest point: Someshwar Hill, West Champaran (~880m)

DIVISIONS OF BIHAR:
  → Ganga River divides Bihar into:
    NORTH BIHAR: Mithila, Bhojpur (west), Saran, Koshi, Tirhut regions
    SOUTH BIHAR: Patna, Magadh, Munger, Bhagalpur regions

🎯 PYQ FACT: Bihar = 3rd most populous state; ~8.6% of India's population
🎯 PYQ FACT: Bihar has 38 districts
🎯 PYQ FACT: Bihar borders Nepal to the north (important!)
🎯 PYQ FACT: Bihar = Jharkhand carved out from it in November 2000
```

### Bihar's Major Rivers:
```
RIVERS FLOWING THROUGH BIHAR:

MAIN RIVER:
  GANGA:
  → Enters Bihar at Chausa (Buxar district)
  → Divides Bihar into North and South
  → Exits at Rajmahal (Jharkhand border)
  → KEY CITIES ON GANGA: Patna, Hajipur (on Gandak confluence), Bhagalpur

NORTH BIHAR RIVERS (from Nepal/Himalayas):
  GANDAK (Narayani):
  → Originates in Nepal
  → Enters Bihar at Valmikinagar (West Champaran)
  → Meets Ganga at Hajipur (Vaishali district)
  
  KOSI (Sorrow of Bihar):
  → Originates in Nepal Himalayas
  → Known as "Bihar's Sorrow" — causes floods every year!
  → Frequent course-changes cause widespread devastation
  → Meets Ganga near Kursela (Katihar district)
  → Kosi river system: Supaul, Saharsa, Madhepura, Khagaria
  
  BAGMATI:
  → Originates in Nepal (near Kathmandu)
  → Enters Bihar, meets Ganga in Khagaria district
  
  KAMLA-BALAN:
  → Originates in Nepal
  → Causes floods in Madhubani and Darbhanga districts
  
  BURHI GANDAK:
  → Originates in Someshwar Hills (West Champaran)
  → Meets Ganga near Monghyr/Munger

SOUTH BIHAR RIVERS:
  SONE:
  → Originates in Shahdol, Madhya Pradesh (near Amarkantak)
  → Major tributary of Ganga
  → MAJOR IRRIGATION source for South Bihar
  → Enters Ganga at Arrah/Patna area
  → Indrapuri Dam, Sone Barrage (irrigation projects)
  
  PUNPUN:
  → Meets Ganga near Fatuha, Patna district
  
  FALGU:
  → Tributary of Punpun
  → Flows through Gaya (sacred river — Pind daan rituals here!)
  → Often called "reverse river" (water flows underground in dry season)

🎯 PYQ FACT: Kosi = "Bihar's Sorrow" (floods); enters Ganga near Kursela
🎯 PYQ FACT: Gandak meets Ganga at HAJIPUR (Vaishali)
🎯 PYQ FACT: Sone = major south Bihar irrigation river (from MP)
🎯 PYQ FACT: Falgu river = flows through Gaya (sacred for Hindu rituals)
🎯 PYQ FACT: Ganga enters Bihar at Chausa (Buxar district)
```

---

## 🔷 SECTION 5: Bihar — Districts, Divisions and Key Facts

```
BIHAR'S 9 ADMINISTRATIVE DIVISIONS:
  1. Patna Division: Patna, Nalanda, Bhojpur, Buxar, Rohtas, Kaimur
  2. Magadh Division: Gaya, Arwal, Jehanabad, Aurangabad, Nawada
  3. Munger Division: Munger, Lakhisarai, Sheikhpura, Jamui, Khagaria
  4. Bhagalpur Division: Bhagalpur, Banka
  5. Purnia Division: Purnia, Katihar, Araria, Kishanganj
  6. Kosi Division: Saharsa, Supaul, Madhepura
  7. Darbhanga Division: Darbhanga, Madhubani, Samastipur
  8. Muzaffarpur Division: Muzaffarpur, Sitamarhi, Sheohar, Vaishali
  9. Saran/Chapra Division: Saran, Siwan, Gopalganj
  10. Champaran Division: West Champaran, East Champaran
  (Actually 9 divisions as East & West Champaran are one)
  
LARGEST DISTRICT BY AREA: West Champaran
SMALLEST DISTRICT BY AREA: Sheohar
MOST POPULOUS DISTRICT: Patna
LARGEST CITY: Patna (state capital)
SECOND CITY: Gaya
```

### Bihar — Population Facts:
```
BIHAR POPULATION (2011 Census):
  Total: 10.41 crore (now estimated ~13-14 crore in 2024)
  Male: 5.41 crore | Female: 5.00 crore
  Population Density: 1,106 per sq km (highest for large states)
  Sex Ratio: 918 females per 1,000 males
  Literacy Rate: 63.82% (below national average of 74.04%)
  Male Literacy: 73.39% | Female Literacy: 53.33%
  
URBAN-RURAL SPLIT:
  → ~88-89% rural population (highly agrarian)
  → Only ~11-12% urban

SCHEDULED CASTE (SC) POPULATION: ~16% of Bihar's population
SCHEDULED TRIBE (ST) POPULATION: ~1.3% of Bihar's population

🎯 PYQ FACT: Bihar = 3rd most populous state (after UP and Maharashtra)
🎯 PYQ FACT: Bihar = highest population density among large states
🎯 PYQ FACT: Bihar literacy rate (~64%) = below national average (~74%)
```

---

## 🔷 SECTION 6: Geography PYQ Traps

```
🚨 TRAP 1: "Everest is the highest peak in India" → FALSE!
   Everest = highest in the world but in NEPAL (not India).
   Highest in INDIA = Kanchenjunga (Sikkim, 8,586m).

🚨 TRAP 2: "Standard time of India = GMT + 5 hours exactly" → FALSE!
   IST = GMT + 5 hours 30 MINUTES (half-hour offset!).

🚨 TRAP 3: "Mawsynram is in Assam" → FALSE!
   Mawsynram = Meghalaya (East Khasi Hills district).

🚨 TRAP 4: "Tamil Nadu gets most rain from Southwest Monsoon" → FALSE!
   Tamil Nadu = receives most rain from NORTHEAST Monsoon (Oct-Nov).

🚨 TRAP 5: "Himalayas are the oldest mountains in India" → FALSE!
   Himalayas = YOUNGEST fold mountains.
   OLDEST landform = Deccan Plateau (Gondwana landmass).

🚨 TRAP 6: "Narmada flows into Bay of Bengal" → FALSE!
   Narmada flows WESTWARD into Arabian Sea (unique among peninsular rivers).

🚨 TRAP 7: "Bihar is the largest state in India by population" → FALSE!
   Bihar = 3rd largest by population (after UP and Maharashtra).
   Largest by area = Rajasthan.

🚨 TRAP 8: "Kosi river is called the sorrow of India" → PARTIALLY WRONG!
   Kosi = "Sorrow of BIHAR" (not India).
   "Sorrow of Bengal" = Damodar River (historically).

🚨 TRAP 9: "Ganga enters Bihar from the north" → FALSE!
   Ganga enters Bihar from the WEST (at Chausa, Buxar district).
   Nepal rivers (Kosi, Gandak) enter Bihar from the NORTH.

🚨 TRAP 10: "Bihar's smallest district is Patna" → FALSE!
   Smallest district = Sheohar.
   Largest district = West Champaran.
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 30 MCQs (FULL NETWORKS REVISION TEST)
### Mixed Topics: OSI, TCP/IP, IP Addressing, Protocols, Topologies, Devices, Security

---

**Q1.** The OSI model has how many layers, and which is the CORRECT top-to-bottom order?
(A) 4 layers: Application, Transport, Internet, Network Access
(B) 7 layers: Application, Presentation, Session, Transport, Network, Data Link, Physical
(C) 7 layers: Physical, Data Link, Network, Transport, Session, Presentation, Application
(D) More than one of the above
(E) None of the above

---

**Q2.** "All People Seem To Need Data Processing" is a mnemonic for which layer ordering?
(A) TCP/IP model layers (bottom to top)
(B) OSI model layers (top to bottom: Application → Physical)
(C) OSI model layers (bottom to top: Physical → Application)
(D) More than one of the above
(E) None of the above

---

**Q3.** Which OSI layer is responsible for ENCRYPTION and COMPRESSION?
(A) Session Layer (Layer 5)
(B) Transport Layer (Layer 4)
(C) Presentation Layer (Layer 6)
(D) More than one of the above
(E) None of the above

---

**Q4.** The TCP/IP model's "Internet Layer" corresponds to which OSI layer?
(A) OSI Transport Layer (Layer 4)
(B) OSI Network Layer (Layer 3)
(C) OSI Data Link Layer (Layer 2)
(D) More than one of the above
(E) None of the above

---

**Q5.** TCP/IP Application Layer combines which THREE OSI layers?
(A) Physical + Data Link + Network (bottom three)
(B) Transport + Network + Data Link (middle three)
(C) Application + Presentation + Session (top three, layers 7+6+5)
(D) More than one of the above
(E) None of the above

---

**Q6.** An IPv4 address "172.25.30.5" belongs to which class?
(A) Class A (first octet 1–126)
(B) Class B (first octet 128–191)
(C) Class C (first octet 192–223)
(D) More than one of the above
(E) None of the above

---

**Q7.** What is the number of USABLE HOST addresses in a /26 subnet?
(A) 64
(B) 62
(C) 30
(D) More than one of the above
(E) None of the above

---

**Q8.** The subnet mask /24 in dotted decimal notation is:
(A) 255.255.0.0
(B) 255.0.0.0
(C) 255.255.255.0
(D) More than one of the above
(E) None of the above

---

**Q9.** Which THREE are private IPv4 address ranges?
(A) 10.x.x.x ; 172.16–31.x.x ; 192.168.x.x
(B) 10.x.x.x ; 172.x.x.x (all of 172) ; 192.168.x.x
(C) 10.x.x.x ; 127.x.x.x ; 192.168.x.x
(D) More than one of the above
(E) None of the above

---

**Q10.** IPv6 addresses use which notation format?
(A) Four dotted decimal octets (e.g., 192.168.1.1)
(B) Eight hexadecimal groups separated by colons (e.g., 2001:db8::1)
(C) Binary notation with slashes
(D) More than one of the above
(E) None of the above

---

**Q11.** TCP uses which mechanism to establish a connection before data transfer?
(A) Two-way handshake (SYN + ACK)
(B) Three-way handshake (SYN → SYN-ACK → ACK)
(C) Four-way handshake (SYN → ACK → SYN → ACK)
(D) More than one of the above
(E) None of the above

---

**Q12.** Which protocol would be BEST suited for a real-time online multiplayer game?
(A) TCP — because reliability is critical for gaming
(B) FTP — because game files need to be downloaded
(C) UDP — because low latency/speed is more important than guaranteed delivery
(D) More than one of the above
(E) None of the above

---

**Q13.** When Gmail's server sends an email to Yahoo's server, Gmail's server is acting as:
(A) An SMTP Server (receiving the email)
(B) A POP3 Client (downloading the email)
(C) An SMTP Client (initiating the SMTP connection to deliver mail)
(D) More than one of the above
(E) None of the above

---

**Q14.** The full form of "Ping" is:
(A) Packet Internet Generator
(B) Protocol Internet Groper
(C) Packet Internet Groper
(D) More than one of the above
(E) None of the above

---

**Q15.** Which protocol does the Ping command use?
(A) TCP (Transmission Control Protocol)
(B) UDP (User Datagram Protocol)
(C) ICMP (Internet Control Message Protocol)
(D) More than one of the above
(E) None of the above

---

**Q16.** MQTT protocol (Port 1883) is designed specifically for:
(A) Web browsing on low-bandwidth connections
(B) Sending emails between enterprise mail servers
(C) IoT devices — lightweight, low-bandwidth, publish-subscribe communication
(D) More than one of the above
(E) None of the above

---

**Q17.** A network where ALL devices connect to a central switch, and any individual device failure does NOT affect the rest of the network, is:
(A) Ring Topology
(B) Bus Topology
(C) Star Topology
(D) More than one of the above
(E) None of the above

---

**Q18.** For a FULL MESH network of 6 devices, how many physical links are required?
(A) 12
(B) 15
(C) 10
(D) More than one of the above
(E) None of the above

---

**Q19.** "Peer-to-Peer" (P2P) in networking is correctly classified as:
(A) A network topology (like Bus or Star)
(B) A network architecture/model (not a topology)
(C) A type of network security protocol
(D) More than one of the above
(E) None of the above

---

**Q20.** A HUB and a SWITCH are both connected to multiple devices in a LAN. The KEY difference is:
(A) Hub reads IP addresses; Switch reads MAC addresses
(B) Hub broadcasts to ALL ports; Switch reads MAC address table and sends ONLY to correct port
(C) Hub is faster than Switch because it has no processing overhead
(D) More than one of the above
(E) None of the above

---

**Q21.** Which device connects networks that use COMPLETELY DIFFERENT protocols?
(A) Router (routes IP packets between networks)
(B) Switch (connects devices within same LAN)
(C) Gateway (translates between different protocol architectures)
(D) More than one of the above
(E) None of the above

---

**Q22.** Optical Fiber cable is IMMUNE to electromagnetic interference because:
(A) It is buried underground away from interference sources
(B) It is surrounded by a strong metal shield
(C) It transmits LIGHT signals, not electrical signals (light is not affected by EMI)
(D) More than one of the above
(E) None of the above

---

**Q23.** Packet sniffing attacks are most effective on which type of network?
(A) Switch-based networks (switch sends only to intended recipient)
(B) Fiber optic networks (light is easy to capture)
(C) Hub-based networks (hub broadcasts all traffic to all ports)
(D) More than one of the above
(E) None of the above

---

**Q24.** In ASYMMETRIC cryptography, if Alice wants to RECEIVE encrypted messages, she should:
(A) Keep both her public and private keys completely secret
(B) Share her PUBLIC key openly; keep her PRIVATE key secret
(C) Share her PRIVATE key with trusted senders; keep public key secret
(D) More than one of the above
(E) None of the above

---

**Q25.** AES (Advanced Encryption Standard) is an example of:
(A) Asymmetric encryption (two-key system)
(B) Hashing (one-way function, not encryption)
(C) Symmetric encryption (same key for encrypt and decrypt)
(D) More than one of the above
(E) None of the above

---

**Q26.** HTTPS uses which COMBINATION for secure communication?
(A) Only RSA asymmetric encryption throughout
(B) Only AES symmetric encryption throughout
(C) Hybrid: RSA/asymmetric to exchange session key + AES/symmetric for data
(D) More than one of the above
(E) None of the above

---

**Q27.** A WORM differs from a VIRUS in that:
(A) Viruses spread independently; worms attach to files
(B) Worms spread independently through networks; viruses attach to host files
(C) Both worm and virus are identical in behavior
(D) More than one of the above
(E) None of the above

---

**Q28.** The World Wide Web (WWW) was invented by Tim Berners-Lee. Which statement about WWW is CORRECT?
(A) WWW and the Internet are the same thing
(B) WWW is the global network of cables, routers, and servers
(C) WWW is a service (hyperlinked documents/websites) that runs ON the Internet infrastructure
(D) More than one of the above
(E) None of the above

---

**Q29.** Consider these Protocol-Port pairs. Which are CORRECTLY matched?
I.   HTTP → Port 80
II.  HTTPS → Port 443
III. SMTP → Port 110
IV.  DNS → Port 53
V.   FTP (control) → Port 21

(A) I, II, IV, and V only
(B) All five are correct
(C) I and II only
(D) More than one of the above
(E) None of the above

---

**Q30.** Consider these OSI layer-PDU-Device mappings. Identify ALL CORRECT ones:
I.   Transport Layer → Segment → Firewall/Load Balancer
II.  Network Layer → Packet → Router
III. Data Link Layer → Frame → Switch
IV.  Physical Layer → Bits → Hub (Layer 1)

(A) II, III, and IV only
(B) I, II, III, and IV — all correct
(C) I and II only
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: India Physical Geography, Climate, Monsoon, Bihar Geography

---

**Q31.** India's Standard Meridian (82°30'E) passes through which city?
(A) Patna, Bihar
(B) Mirzapur (Prayagraj area), Uttar Pradesh
(C) Bhopal, Madhya Pradesh
(D) More than one of the above
(E) None of the above

---

**Q32.** Indian Standard Time (IST) differs from Greenwich Mean Time (GMT) by:
(A) +5 hours exactly
(B) +5 hours 30 minutes
(C) +6 hours 30 minutes
(D) More than one of the above
(E) None of the above

---

**Q33.** The HIGHEST peak entirely within India is:
(A) Mount Everest (Nepal/China border)
(B) K2 (Pakistan/China border)
(C) Kanchenjunga (Sikkim)
(D) More than one of the above
(E) None of the above

---

**Q34.** Himalayas are classified as which type of mountains?
(A) Block mountains (formed by faulting)
(B) Volcanic mountains (formed by volcanic activity)
(C) Fold mountains (youngest mountains formed by plate collision)
(D) More than one of the above
(E) None of the above

---

**Q35.** Mawsynram — one of the wettest places on Earth — is located in:
(A) Assam
(B) Arunachal Pradesh
(C) Meghalaya
(D) More than one of the above
(E) None of the above

---

**Q36.** Tamil Nadu receives MOST of its annual rainfall from which source?
(A) Southwest Monsoon (June–September)
(B) Northeast Monsoon (October–November)
(C) Western Disturbances in winter
(D) More than one of the above
(E) None of the above

---

**Q37.** Which river is called "Bihar's Sorrow"?
(A) Sone River
(B) Gandak River
(C) Kosi River
(D) More than one of the above
(E) None of the above

---

**Q38.** The Ganga River enters Bihar at:
(A) Hajipur (Vaishali district)
(B) Chausa (Buxar district)
(C) Patna (Patna district)
(D) More than one of the above
(E) None of the above

---

**Q39.** Gandak River meets the Ganga at:
(A) Patna
(B) Hajipur (Vaishali)
(C) Bhagalpur
(D) More than one of the above
(E) None of the above

---

**Q40.** Bihar's approximate share of India's population (2011 Census) is:
(A) 5.8%
(B) 8.6%
(C) 12.4%
(D) More than one of the above
(E) None of the above

---

**Q41.** Which is the LARGEST district of Bihar by geographical area?
(A) Patna
(B) Rohtas
(C) West Champaran
(D) More than one of the above
(E) None of the above

---

**Q42.** The Chotanagpur Plateau (now in Jharkhand, carved from Bihar in 2000) is called the "Ruhr of India" because:
(A) It has rich agricultural land and water resources
(B) It is rich in minerals — coal, iron ore, copper, mica, uranium
(C) It has the highest concentration of IT companies in India
(D) More than one of the above
(E) None of the above

---

**Q43.** Which Indian river is unique in that it flows WESTWARD into the Arabian Sea (unlike most peninsular rivers)?
(A) Godavari
(B) Mahanadi
(C) Narmada (and Tapi)
(D) More than one of the above
(E) None of the above

---

**Q44.** The Southwest Monsoon first arrives in India around June 1 at:
(A) Mumbai, Maharashtra
(B) Chennai, Tamil Nadu
(C) Kerala (Thiruvananthapuram area)
(D) More than one of the above
(E) None of the above

---

**Q45.** The "Loo" is a hot, dry, dusty wind that blows in India during:
(A) Winter season (December–February)
(B) Monsoon season (June–September)
(C) Summer season (March–May) — mainly in Indo-Gangetic plains
(D) More than one of the above
(E) None of the above

---

**Q46.** Bihar's total number of districts is:
(A) 28
(B) 36
(C) 38
(D) More than one of the above
(E) None of the above

---

**Q47.** Which state was carved out of Bihar in November 2000?
(A) Uttarakhand
(B) Chhattisgarh
(C) Jharkhand
(D) More than one of the above
(E) None of the above

---

**Q48.** The Falgu River that flows through Gaya (a sacred Hindu pilgrimage city) is a tributary of which river?
(A) Sone River
(B) Kosi River
(C) Punpun River
(D) More than one of the above
(E) None of the above

---

**Q49.** Bihar's literacy rate (as per 2011 Census) compared to India's national average is:
(A) Higher than the national average
(B) Equal to the national average (both ~74%)
(C) Lower than the national average (Bihar ~64%; India ~74%)
(D) More than one of the above
(E) None of the above

---

**Q50.** The Someshwar Hills in West Champaran district represent Bihar's:
(A) Lowest elevation point
(B) Highest geographical point (~880m above sea level)
(C) Largest river junction
(D) More than one of the above
(E) None of the above

---

**Q51.** Nathu La pass, which serves as an India-China trade route, is located in:
(A) Himachal Pradesh
(B) Uttarakhand
(C) Sikkim
(D) More than one of the above
(E) None of the above

---

**Q52.** The Eastern Ghats differ from Western Ghats in that:
(A) Eastern Ghats are CONTINUOUS; Western Ghats are discontinuous
(B) Eastern Ghats are DISCONTINUOUS; Western Ghats are continuous
(C) Both Eastern and Western Ghats are equally discontinuous
(D) More than one of the above
(E) None of the above

---

**Q53.** Which of the following statements about Indian geography is CORRECT?
(A) Kanchenjunga is the highest peak in the world
(B) Standard Meridian 82°30'E passes through Patna, Bihar
(C) Mawsynram in Meghalaya is one of the wettest places on Earth
(D) More than one of the above
(E) None of the above

---

**Q54.** The Bay of Bengal branch of Southwest Monsoon enters India first through:
(A) West Bengal and Odisha
(B) Northeast India (Assam, Meghalaya, Arunachal Pradesh area)
(C) Andhra Pradesh and Tamil Nadu coast
(D) More than one of the above
(E) None of the above

---

**Q55.** Consider these Bihar geography statements:
I.  Bihar is bordered by Nepal to the north.
II. Kosi River is called "Bihar's Sorrow" for causing floods.
III. Ganga enters Bihar at Chausa, Buxar.
IV. West Champaran is the largest district in Bihar by area.

Which statements are CORRECT?
(A) I and II only
(B) I, II, and III only
(C) I, II, III, and IV — all correct
(D) More than one of the above
(E) None of the above

---

# ✅ ANSWER KEY

## ⚠️ ATTEMPT ALL 55 QUESTIONS BEFORE CHECKING ANSWERS

---

### CS Answers (Q1–Q30):

| Q  | Ans | Key Reason |
|----|-----|-----------|
| 1  | (B) | OSI = 7 layers top→bottom: Application...Physical |
| 2  | (B) | Mnemonic = OSI top-to-bottom (A=Application...P=Physical) |
| 3  | (C) | Encryption/Compression = Presentation Layer (Layer 6) |
| 4  | (B) | TCP/IP Internet Layer = OSI Network Layer (Layer 3) |
| 5  | (C) | TCP/IP Application = OSI App(7) + Presentation(6) + Session(5) |
| 6  | (B) | 172 falls in 128–191 range = Class B |
| 7  | (B) | /26 = 6 host bits → 2^6 - 2 = 62 usable hosts |
| 8  | (C) | /24 = 24 bits of 1s = 255.255.255.0 |
| 9  | (A) | Three private ranges: 10.x.x.x; 172.16-31.x.x; 192.168.x.x |
| 10 | (B) | IPv6 = 8 groups of hex, colon-separated |
| 11 | (B) | TCP = 3-way handshake: SYN→SYN-ACK→ACK |
| 12 | (C) | Online gaming = UDP (low latency > guaranteed delivery) |
| 13 | (C) | Gmail server initiating delivery to Yahoo = SMTP CLIENT |
| 14 | (C) | Ping = Packet Internet GROPER (not Generator) |
| 15 | (C) | Ping uses ICMP (not TCP or UDP) |
| 16 | (C) | MQTT = IoT protocol (lightweight, publish-subscribe) |
| 17 | (C) | Star topology: individual device failure = doesn't affect others |
| 18 | (B) | Full mesh: n(n-1)/2 = 6×5/2 = 15 links |
| 19 | (B) | P2P = network model/architecture (NOT a topology!) |
| 20 | (B) | Hub = broadcasts all; Switch = MAC table → correct port only |
| 21 | (C) | Gateway = connects different PROTOCOL networks |
| 22 | (C) | Fiber uses LIGHT (not electricity) → immune to EMI |
| 23 | (C) | Hub-based = sniffing easy (hub broadcasts everything to all) |
| 24 | (B) | Share PUBLIC key openly; keep PRIVATE key secret |
| 25 | (C) | AES = symmetric encryption (same key encrypt+decrypt) |
| 26 | (C) | HTTPS = hybrid: RSA key exchange + AES data encryption |
| 27 | (B) | Worm spreads independently; Virus attaches to host files |
| 28 | (C) | WWW = service ON the Internet (not the Internet itself) |
| 29 | (A) | I(HTTP=80)✓ II(HTTPS=443)✓ III WRONG(SMTP=25,not 110) IV(DNS=53)✓ V(FTP ctrl=21)✓ |
| 30 | (B) | All four correct: I(Transport=Seg+Firewall), II(Network=Pkt+Router), III(DataLink=Frame+Switch), IV(Physical=Bits+Hub) |

---

### GS Answers (Q31–Q55):

| Q  | Ans | Key Reason |
|----|-----|-----------|
| 31 | (B) | Standard Meridian 82°30'E passes through Mirzapur, Uttar Pradesh |
| 32 | (B) | IST = GMT + 5 hours 30 minutes |
| 33 | (C) | Kanchenjunga = highest peak IN India (Sikkim) |
| 34 | (C) | Himalayas = Fold mountains (youngest, formed by plate collision) |
| 35 | (C) | Mawsynram = Meghalaya (East Khasi Hills) |
| 36 | (B) | Tamil Nadu = Northeast Monsoon (Oct-Nov) |
| 37 | (C) | Kosi = "Bihar's Sorrow" |
| 38 | (B) | Ganga enters Bihar at Chausa, Buxar district |
| 39 | (B) | Gandak meets Ganga at Hajipur (Vaishali district) |
| 40 | (B) | Bihar = ~8.6% of India's population (2011 Census) |
| 41 | (C) | Largest district by area = West Champaran |
| 42 | (B) | Chotanagpur = rich in minerals (coal, iron, copper etc.) = "Ruhr of India" |
| 43 | (C) | Narmada (and Tapi) flow WESTWARD into Arabian Sea (unique!) |
| 44 | (C) | SW Monsoon arrives Kerala first (around June 1) |
| 45 | (C) | Loo = hot dry wind in Indo-Gangetic plains during SUMMER (Mar-May) |
| 46 | (C) | Bihar = 38 districts |
| 47 | (C) | Jharkhand carved from Bihar in November 2000 |
| 48 | (C) | Falgu = tributary of Punpun River (which joins Ganga near Fatuha, Patna) |
| 49 | (C) | Bihar literacy ~64%; India national ~74% — Bihar is BELOW national average |
| 50 | (B) | Someshwar Hills, West Champaran = Bihar's highest point (~880m) |
| 51 | (C) | Nathu La pass = Sikkim (India-China trade route) |
| 52 | (B) | Eastern Ghats = discontinuous; Western Ghats = continuous |
| 53 | (C) | Only C is correct: Mawsynram in Meghalaya = one of wettest; A wrong (Everest=world's highest, not Kanchenjunga); B wrong (82°30'E passes through Mirzapur, NOT Patna) |
| 54 | (B) | Bay of Bengal branch enters India through Northeast (Assam, Meghalaya, Arunachal) |
| 55 | (C) | All four are correct: I(Bihar borders Nepal north) II(Kosi=sorrow) III(Ganga enters Chausa/Buxar) IV(W.Champaran=largest district) |

---

# 🔁 DAY 49 — THE ULTIMATE ONE-PAGE REVISION

## ⚡ COMPLETE NETWORKS SUMMARY — 60 SECONDS DRILL

```
OSI LAYERS (7): App→Present→Session→Transport→Network→DataLink→Physical
PDUs:           Data / Data / Data / SEGMENT / PACKET / FRAME / BITS
DEVICES:        — / — / — / Firewall / ROUTER / SWITCH / HUB
MNEMONIC:       "All People Seem To Need Data Processing"

TCP/IP LAYERS (4): Application (=OSI 7+6+5) / Transport / Internet (=OSI 3) / NetAccess (=OSI 2+1)
MNEMONIC:          "A Tall Indian Ninja"

TCP: Reliable, connection-oriented, 3-way handshake (SYN→SYN-ACK→ACK), SLOWER
UDP: Unreliable, connectionless, FASTER, 8-byte header, datagram

IPv4: 32 bits, dotted decimal | IPv6: 128 bits, hex+colons, ::1 loopback
Class A (/8): 1-126 | Class B (/16): 128-191 | Class C (/24): 192-223
Private: 10.x.x.x | 172.16-31.x.x | 192.168.x.x | Loopback: 127.0.0.1

PROTOCOLS: HTTP=80, HTTPS=443, FTP=21, SMTP=25, POP3=110, IMAP=143, DNS=53, SSH=22, MQTT=1883
SMTP = SEND only | Ping = ICMP = Packet Internet Groper = RTT + Packet Loss

TOPOLOGIES: Bus(1 cable), Star(central=MOST POPULAR), Ring(token), Mesh(n(n-1)/2=MOST RELIABLE)
P2P ≠ topology (it's a network model)

DEVICES: Hub=L1(broadcast all) | Switch=L2(MAC table) | Router=L3(IP table) | Gateway=L7(protocol)

MEDIA: Fiber=FASTEST+IMMUNE to EMI | UTP=cheapest+EMI vulnerable | Coax=Cable TV
Microwaves=LINE-OF-SIGHT | Infrared=SHORT RANGE (remote controls)

SECURITY: Switch prevents sniffing | AES=symmetric | RSA=asymmetric
Private key=NEVER shared (receiver keeps it) | HTTPS=hybrid (RSA key + AES data)
Ransomware=encrypts+ransom | Worm=spreads independently | Virus=attaches to files
```

## ⚡ GEOGRAPHY SUMMARY — 60 SECONDS DRILL

```
INDIA: Standard meridian=82°30'E (Mirzapur,UP) | IST=GMT+5:30
       Kanchenjunga=highest in INDIA (not Everest—that's in Nepal!)
       Mawsynram, Meghalaya = wettest place on Earth
       SW Monsoon: arrives Kerala~June 1; Tamil Nadu gets NE monsoon (Oct-Nov)
       Narmada/Tapi flow WESTWARD (unique among peninsular rivers)
       Chotanagpur Plateau = "Ruhr of India" (mineral-rich; now Jharkhand)
       Himalayas = YOUNGEST fold mountains | Deccan = OLDEST landform

BIHAR: 38 districts | 3rd most populous (~8.6% of India) | borders Nepal (north)
       Ganga enters Bihar at Chausa (Buxar) | divides into North and South
       Kosi = "Bihar's Sorrow" (floods) | Gandak meets Ganga at Hajipur
       Largest district = West Champaran | Smallest = Sheohar
       Jharkhand carved from Bihar = November 2000
       Literacy ~64% (BELOW national ~74%)
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY:
1. **OSI=7(PDU: Seg/Pkt/Frame/Bits); TCP/IP=4; Devices: Hub=L1, Switch=L2(MAC), Router=L3(IP), Gateway=L7; TCP=reliable+slow; UDP=fast+unreliable; IPv4=32bits; IPv6=128bits.**
2. **Protocols: HTTP=80, HTTPS=443, SMTP=25(SEND), DNS=53; SMTP client=sending server; Ping=ICMP=RTT+loss; MQTT=IoT(Port 1883); P2P=model not topology.**
3. **Security: Fiber=fastest+EMI immune; Sniffing=Hub networks; Switch reduces sniffing; AES=symmetric(fast); RSA=asymmetric(slow); Private key=NEVER shared; HTTPS=RSA+AES hybrid.**
4. **India geography: 82°30'E=Mirzapur(IST=GMT+5:30); Kanchenjunga=highest IN India; Mawsynram=wettest; Himalayas=youngest fold; Narmada flows WEST; SW Monsoon=Kerala June 1.**
5. **Bihar: 38 districts, 3rd most populous, borders Nepal; Ganga enters at Buxar/Chausa; Kosi=Bihar's Sorrow; Gandak meets Ganga at Hajipur; Jharkhand carved Nov 2000; Literacy=~64%<national.**

---

## 📅 DAY 50 PREVIEW — What's Coming Next:
**CS**: DBMS — SQL Basics: DDL, DML, DCL Commands; SELECT queries, WHERE, ORDER BY, GROUP BY, HAVING; Joins (Inner, Left, Right, Full); Aggregate functions (COUNT, SUM, AVG, MAX, MIN)
**GS**: Indian Polity — Fundamental Rights (Articles 12–35): Right to Equality (Art 14-18), Right to Freedom (Art 19-22), Right Against Exploitation (Art 23-24), Right to Constitutional Remedies + Writs (Art 32)

---

*🚀 Day 49 of 170 — You've completed the entire Computer Networks chapter (Days 43-49)! Today's 30-question revision test is your benchmark — if you score 25+/30, you're ready. Any questions you missed = those are your weak areas to revise tonight. Geography is bonus marks — the Bihar-specific facts (Kosi=sorrow, Gandak=Hajipur, 38 districts) appear EVERY year in BPSC. You're approaching the halfway mark of the Networks-DBMS section. Outstanding consistency!*
