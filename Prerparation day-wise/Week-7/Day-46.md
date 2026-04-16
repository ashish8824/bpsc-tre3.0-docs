# 📅 BPSC TRE 4.0 — DAY 46
## CS Topic: Network Protocols — TCP, UDP, SMTP, HTTP, MQTT & More
## GS Topic: Government Schemes — Central & State Flagship Programmes
### 🎯 Target: 130+/150 | TOP 50 RANK

---

> **Topper Benchmark:** Network Protocols appear in EVERY BPSC TRE paper — typically 3–5 questions.
> TCP vs UDP comparison, SMTP server/client distinction, and MQTT (IoT) are HIGH-FREQUENCY traps.
> Government Schemes is a GUARANTEED GS section — BPSC TRE 4.0 expects awareness of PM schemes, Bihar schemes, and their objectives. Never skip this!

---

## ⏰ TODAY'S STUDY SCHEDULE

| Slot | Duration | Activity |
|------|----------|----------|
| Morning | 1.5 hrs | CS: All major protocols — concept + ASCII diagrams |
| Afternoon | 1 hr | GS: Central + Bihar Govt. Schemes — purpose + keywords |
| Evening | 1 hr | Solve all 50 MCQs (25 CS + 25 GS) |
| Night | 30 min | Write 5 bullet summary for each part |

---

---

# 🖥️ PART A — COMPUTER SCIENCE
# NETWORK PROTOCOLS — TCP, UDP, SMTP, HTTP, MQTT & MORE

---

## 🔑 WHY THIS TOPIC MATTERS FOR BPSC TRE 4.0

| Exam | Protocol Questions |
|------|-------------------|
| TRE 1.0 | 3 questions — TCP/UDP/SMTP |
| TRE 2.0 | 4 questions — HTTP/HTTPS/DNS/SMTP client |
| TRE 3.0 | 5 questions — TCP handshake, MQTT, Ping, Socket |
| **TRE 4.0 Expected** | **4–6 questions — VERY high probability** |

---

## 📡 WHAT IS A PROTOCOL?

A **protocol** is a set of rules that governs how data is **transmitted and received** over a network.

**Simple Analogy:**
Think of two people speaking on a phone. Both must:
- Use the same language (encoding)
- Take turns speaking (flow control)
- Confirm they heard correctly (acknowledgement)
- Handle dropped calls (error recovery)

This "agreement" is exactly what a network protocol is!

---

## 🔵 1. TCP — TRANSMISSION CONTROL PROTOCOL

### Definition:
TCP is a **connection-oriented**, **reliable** transport layer protocol that guarantees data delivery in the correct order.

### Key Characteristics:
```
┌─────────────────────────────────────────────────────────────┐
│                   TCP — KEY FEATURES                        │
├──────────────────────────┬──────────────────────────────────┤
│ Feature                  │ Detail                           │
├──────────────────────────┼──────────────────────────────────┤
│ Type                     │ Connection-Oriented              │
│ Reliability              │ Guaranteed (ACK mechanism)       │
│ Ordering                 │ Yes — data arrives in order      │
│ Error Checking           │ Yes — checksums                  │
│ Speed                    │ Slower than UDP                  │
│ Data Unit                │ Segment                          │
│ OSI Layer                │ Transport Layer (Layer 4)        │
│ Connection Setup         │ Three-Way Handshake              │
│ Data Stream              │ Single stream (byte stream)      │
│ Applications             │ HTTP, HTTPS, FTP, SMTP, Telnet   │
└──────────────────────────┴──────────────────────────────────┘
```

### ✅ THREE-WAY HANDSHAKE (VERY IMPORTANT FOR BPSC!)

```
     CLIENT                              SERVER
       │                                   │
       │──── SYN (Synchronize) ───────────>│  Step 1: Client asks to connect
       │                                   │
       │<─── SYN-ACK (Sync + Acknowledge)──│  Step 2: Server agrees + confirms
       │                                   │
       │──── ACK (Acknowledge) ───────────>│  Step 3: Client confirms
       │                                   │
       │═══════════ CONNECTION ESTABLISHED ═════════════
       │          (Data transfer begins)   │
```

**Memory Trick:** "**S**end **S**ome **A**cknowledgement" → SYN → SYN-ACK → ACK

### ✅ FOUR-WAY TERMINATION (Connection Closing):
```
CLIENT ──── FIN ────> SERVER   (I want to close)
CLIENT <─── ACK ──── SERVER   (OK, noted)
CLIENT <─── FIN ──── SERVER   (I'm done too)
CLIENT ──── ACK ───> SERVER   (Connection closed)
```

---

## 🟡 2. UDP — USER DATAGRAM PROTOCOL

### Definition:
UDP is a **connectionless**, **unreliable** transport layer protocol. It sends data without establishing a connection and without guaranteeing delivery.

### Key Characteristics:
```
┌─────────────────────────────────────────────────────────────┐
│                   UDP — KEY FEATURES                        │
├──────────────────────────┬──────────────────────────────────┤
│ Feature                  │ Detail                           │
├──────────────────────────┼──────────────────────────────────┤
│ Type                     │ Connectionless                   │
│ Reliability              │ NOT guaranteed (no ACK)          │
│ Ordering                 │ No — packets may arrive out of   │
│                          │ order or be lost                 │
│ Error Checking           │ Minimal (checksum only)          │
│ Speed                    │ FASTER than TCP                  │
│ Data Unit                │ Datagram                         │
│ OSI Layer                │ Transport Layer (Layer 4)        │
│ Connection Setup         │ None (fire and forget)           │
│ Applications             │ DNS, DHCP, Video streaming,      │
│                          │ VoIP, online gaming, TFTP        │
└──────────────────────────┴──────────────────────────────────┘
```

### ✅ TCP vs UDP — THE MASTER COMPARISON TABLE

```
┌────────────────────┬─────────────────────────┬────────────────────────┐
│ Feature            │ TCP                     │ UDP                    │
├────────────────────┼─────────────────────────┼────────────────────────┤
│ Connection         │ Connection-oriented      │ Connectionless         │
│ Reliability        │ Reliable                │ Unreliable             │
│ Speed              │ Slower                  │ Faster                 │
│ Ordering           │ Guaranteed order         │ No order guarantee     │
│ Handshake          │ 3-way handshake          │ No handshake           │
│ Header size        │ 20 bytes                │ 8 bytes (SMALLER)      │
│ Flow control       │ Yes                     │ No                     │
│ Congestion control │ Yes                     │ No                     │
│ Use case           │ Data integrity needed    │ Speed needed           │
│ Examples           │ HTTP, FTP, SMTP, Telnet  │ DNS, VoIP, Video, DHCP │
└────────────────────┴─────────────────────────┴────────────────────────┘
```

**🚨 EXAM TRAP:** DNS uses UDP (not TCP) for regular queries. TCP is used by DNS only for zone transfers.

**Memory Trick:** UDP = "**U** Don't Panic" — it just sends data without worrying about delivery.

---

## 🟠 3. SMTP — SIMPLE MAIL TRANSFER PROTOCOL

### Definition:
SMTP is the protocol used for **sending** email messages between servers.

```
┌─────────────────────────────────────────────────────────────────┐
│                    EMAIL FLOW DIAGRAM                           │
│                                                                 │
│  Sender's              SMTP            SMTP           Receiver  │
│  Mail Client ─────────> Server A ─────> Server B ──────> Client│
│  (You)         SMTP     (Gmail etc)     (Yahoo etc)    (POP3/  │
│               CLIENT      acts as         acts as       IMAP)  │
│                           SMTP SERVER   SMTP CLIENT            │
│                           (for you)     (for Server B)         │
└─────────────────────────────────────────────────────────────────┘
```

### 🚨 CRITICAL BPSC TRAP — SMTP CLIENT vs SMTP SERVER:

> **When a mail server SENDS email to ANOTHER mail server → it acts as SMTP CLIENT**
> **When a mail server RECEIVES email from another server → it acts as SMTP SERVER**

This is a VERY common PYQ question. The server sending the email IS the client in this context!

### Key SMTP Facts:
```
┌──────────────────────────────────────────────────┐
│ SMTP Port          │  25 (standard), 587 (TLS)   │
│ Protocol Type      │  Application Layer           │
│ Direction          │  Only SENDING of emails      │
│ Receiving email    │  POP3 (port 110) or          │
│                    │  IMAP (port 143)             │
│ Secure SMTP        │  SMTPS (port 465)            │
│ Used by            │  Gmail, Yahoo, Outlook, etc. │
└──────────────────────────────────────────────────┘
```

**Memory:** SMTP = "**S**ending **M**ail **T**o **P**eople"

---

## 🟢 4. HTTP & HTTPS

### HTTP — HyperText Transfer Protocol:
- Used for **web browsing** — transferring web pages
- **Application layer** protocol
- **Port 80**
- **Stateless** — each request is independent (no memory of past requests)
- Based on **request-response** model

### HTTPS — HTTP Secure:
- HTTP + **SSL/TLS encryption**
- **Port 443**
- Data is **encrypted** in transit
- Uses **digital certificates** for server authentication
- Mandatory for banking, e-commerce websites

```
┌──────────────────────────────────────────────────┐
│           HTTP vs HTTPS COMPARISON               │
├──────────────────────┬───────────┬───────────────┤
│ Feature              │ HTTP      │ HTTPS          │
├──────────────────────┼───────────┼───────────────┤
│ Security             │ Insecure  │ Secure         │
│ Port                 │ 80        │ 443            │
│ Encryption           │ No        │ Yes (SSL/TLS)  │
│ Certificate needed   │ No        │ Yes            │
│ Speed                │ Faster    │ Slightly slower│
│ Data in transit      │ Plain text│ Encrypted      │
└──────────────────────┴───────────┴───────────────┘
```

### HTTP Methods (PYQ Frequent!):
```
GET    → Retrieve data (most common)
POST   → Submit data (forms, login)
PUT    → Update existing data
DELETE → Delete data
HEAD   → Get headers only (no body)
```

**🚨 EXAM TRAP:** GET requests are visible in the URL. POST requests are NOT visible in the URL — they are in the request body.

---

## 🔵 5. FTP — FILE TRANSFER PROTOCOL

- Used to **transfer files** between client and server
- **Port 20** (data transfer) and **Port 21** (control/commands)
- Uses **TWO connections** — control connection + data connection (this is special and frequently asked!)
- Active FTP vs Passive FTP
- FTPS = FTP + SSL (secure version)
- SFTP = SSH File Transfer Protocol (different from FTPS!)

**🚨 EXAM TRAP:** FTP uses TWO ports — 20 and 21. This is unique among common protocols.

---

## 🟣 6. DNS — DOMAIN NAME SYSTEM

- Translates **domain names** (www.google.com) to **IP addresses** (142.250.77.14)
- Called the "**phonebook of the Internet**"
- **Port 53**
- Uses **UDP** for regular queries (fast)
- Uses **TCP** only for zone transfers (large data)
- **Hierarchical** system: Root → TLD (.com, .in) → Domain → Subdomain

```
                DNS RESOLUTION PROCESS
                
User types: www.bpsc.bih.nic.in
       │
       ▼
Local Cache? ──YES──> Done!
       │NO
       ▼
DNS Resolver (ISP)
       │
       ▼
Root Name Server  (knows .in location)
       │
       ▼
TLD Name Server   (knows .nic.in location)
       │
       ▼
Authoritative DNS (gives actual IP)
       │
       ▼
IP returned to browser → Connect!
```

---

## 🔴 7. DHCP — DYNAMIC HOST CONFIGURATION PROTOCOL

- **Automatically assigns IP addresses** to devices on a network
- **Port 67** (server), **Port 68** (client)
- Uses **UDP**
- Process: **DORA** = Discover → Offer → Request → Acknowledge

```
     DEVICE                           DHCP SERVER
       │                                   │
       │──── DISCOVER (I need an IP!) ────>│
       │                                   │
       │<─── OFFER (Use 192.168.1.5) ──────│
       │                                   │
       │──── REQUEST (I'll take it!) ─────>│
       │                                   │
       │<─── ACK (IP is yours!) ───────────│
```

**Memory:** **DORA** the Explorer finds an IP address!

---

## 🟤 8. MQTT — MESSAGE QUEUING TELEMETRY TRANSPORT

### ✅ THIS IS A HIGH-FREQUENCY BPSC TRE 4.0 TOPIC!

- **IoT (Internet of Things) communication protocol**
- Designed for **low-bandwidth, high-latency** networks
- Uses **Publish-Subscribe** model (NOT client-server like HTTP)
- Very **lightweight** — minimal bandwidth usage
- Uses **TCP** as transport (port 1883, or 8883 for MQTTS)
- Invented by IBM's **Andy Stanford-Clark** and Arlen Nipper

```
┌─────────────────────────────────────────────────────────────┐
│              MQTT PUBLISH-SUBSCRIBE MODEL                    │
│                                                             │
│   Sensor ──PUBLISH──> MQTT BROKER <──SUBSCRIBE── App       │
│   (Temperature)      (Message Hub)               (Phone)   │
│                                                             │
│   Device publishes to a TOPIC.                              │
│   Subscriber receives from that TOPIC via BROKER.           │
└─────────────────────────────────────────────────────────────┘
```

### MQTT Quality of Service (QoS) Levels:
```
QoS 0: At most once  (fire and forget — may lose message)
QoS 1: At least once (guaranteed but may duplicate)
QoS 2: Exactly once  (guaranteed, no duplicates)
```

### Real-world Applications:
- Smart home sensors (temperature, motion)
- Hospital patient monitoring
- Smart agriculture (soil sensors)
- Industrial IoT (factory machines)

---

## 🟠 9. TELNET vs SSH

```
┌────────────────────┬──────────────┬──────────────────────┐
│ Feature            │ Telnet       │ SSH                  │
├────────────────────┼──────────────┼──────────────────────┤
│ Security           │ INSECURE     │ SECURE (encrypted)   │
│ Port               │ 23           │ 22                   │
│ Data transmission  │ Plain text   │ Encrypted            │
│ Use                │ Remote login │ Secure remote login  │
│ Status             │ Obsolete     │ Modern standard      │
└────────────────────┴──────────────┴──────────────────────┘
```

---

## 📌 10. PING — What It Actually Does

**Ping** is a network **diagnostic tool** that uses **ICMP (Internet Control Message Protocol)**.

### What Ping Reports:
```
ping google.com

Pinging google.com [142.250.77.14] with 32 bytes of data:
Reply from 142.250.77.14: bytes=32 time=12ms TTL=117
Reply from 142.250.77.14: bytes=32 time=11ms TTL=117
...

Ping statistics for 142.250.77.14:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss)
Approximate round trip times:
    Minimum = 11ms, Maximum = 14ms, Average = 12ms
```

### Ping Summarizes:
1. **Packet loss** — how many packets were lost
2. **Round-trip delay (latency)** — how long the trip took

### 🚨 EXAM TRAP:
- Ping is NOT "Packet Internet Groper" — this is a **WRONG option** regularly placed in BPSC TRE papers
- Ping uses **ICMP**, not TCP or UDP
- Ping can be blocked by **firewalls**

---

## 🔵 11. SOCKET — THE ENDPOINT

**Socket** = Software endpoint of inter-process communication (IPC) over a network.

A socket identifies a specific process on a specific machine using:
```
Socket = IP Address + Port Number

Example:
  Server IP: 192.168.1.100
  Port: 80 (HTTP)
  Socket: 192.168.1.100:80
```

Think of it as: **IP Address = House Address | Port = Room Number | Socket = Full Door Address**

---

## 📊 MASTER PROTOCOL PORT NUMBER TABLE (Memorize This!)

```
┌──────────┬────────┬────────────────────────────────────────┐
│ Protocol │  Port  │ Purpose                                │
├──────────┼────────┼────────────────────────────────────────┤
│ FTP      │ 20, 21 │ File Transfer (20=data, 21=control)    │
│ SSH      │ 22     │ Secure Remote Login                    │
│ Telnet   │ 23     │ Remote Login (insecure)                │
│ SMTP     │ 25     │ Sending Email                          │
│ DNS      │ 53     │ Domain Name Resolution                 │
│ DHCP     │ 67/68  │ IP Address Assignment                  │
│ HTTP     │ 80     │ Web Browsing                           │
│ POP3     │ 110    │ Receiving Email (downloads)            │
│ IMAP     │ 143    │ Receiving Email (syncs)                │
│ HTTPS    │ 443    │ Secure Web Browsing                    │
│ SMTPS    │ 465    │ Secure SMTP                            │
│ MQTT     │ 1883   │ IoT Protocol                           │
│ MQTTS    │ 8883   │ Secure MQTT                            │
└──────────┴────────┴────────────────────────────────────────┘
```

---

## 🚨 BPSC TOPPER TRAP CARD — CS PROTOCOLS

| Wrong Option (Commonly Set) | Correct Answer |
|----------------------------|----------------|
| Ping = "Packet Internet Groper" | ❌ WRONG — Ping has no such expansion |
| MQTT uses UDP | ❌ WRONG — MQTT uses TCP |
| SMTP server sends email to another server | ❌ TRAP — It acts as SMTP CLIENT |
| HTTP is stateful | ❌ WRONG — HTTP is stateless |
| FTP uses only one port | ❌ WRONG — FTP uses TWO ports (20 and 21) |
| DNS always uses TCP | ❌ WRONG — DNS uses UDP for queries |
| UDP is reliable | ❌ WRONG — UDP is unreliable (connectionless) |
| HTTPS uses port 80 | ❌ WRONG — HTTPS uses port 443 |

---

## 🧠 QUICK REVISION DIAGRAM — ALL PROTOCOLS AT A GLANCE

```
APPLICATION LAYER PROTOCOLS:
┌─────────┬──────┬──────────┬───────────────────────────┐
│Protocol │ Port │ Transport│ Purpose                   │
├─────────┼──────┼──────────┼───────────────────────────┤
│ HTTP    │  80  │ TCP      │ Web browsing              │
│ HTTPS   │ 443  │ TCP      │ Secure web                │
│ FTP     │20/21 │ TCP      │ File transfer             │
│ SMTP    │  25  │ TCP      │ Send email                │
│ POP3    │ 110  │ TCP      │ Receive email (download)  │
│ IMAP    │ 143  │ TCP      │ Receive email (sync)      │
│ DNS     │  53  │ UDP/TCP  │ Name resolution           │
│ DHCP    │67/68 │ UDP      │ IP assignment             │
│ SSH     │  22  │ TCP      │ Secure remote login       │
│ Telnet  │  23  │ TCP      │ Remote login (old)        │
│ MQTT    │1883  │ TCP      │ IoT messaging             │
└─────────┴──────┴──────────┴───────────────────────────┘

TRANSPORT LAYER PROTOCOLS:
┌─────────────────┬───────────────────────────────────────┐
│ TCP             │ Reliable, connection-oriented          │
│ UDP             │ Unreliable, connectionless, fast       │
└─────────────────┴───────────────────────────────────────┘

NETWORK LAYER PROTOCOLS:
┌─────────────────┬───────────────────────────────────────┐
│ IP (IPv4/IPv6)  │ Addressing and routing                │
│ ICMP            │ Error reporting (used by Ping)        │
│ ARP             │ IP → MAC address resolution           │
│ RARP            │ MAC → IP address resolution           │
└─────────────────┴───────────────────────────────────────┘
```

---

## ✅ BPSC CS CONCEPT SUMMARY — DAY 46

| # | Key Fact | Never Forget |
|---|----------|-------------|
| 1 | TCP = Connection-oriented + Reliable | 3-way handshake: SYN→SYN-ACK→ACK |
| 2 | UDP = Connectionless + Unreliable | Faster, used by DNS/DHCP/Video |
| 3 | SMTP server sending to another = SMTP CLIENT | Classic PYQ trap |
| 4 | HTTP = stateless, Port 80 | HTTPS = Port 443 |
| 5 | Ping uses ICMP | Reports packet loss + round-trip delay |
| 6 | FTP uses two ports | Port 20 (data) + Port 21 (control) |
| 7 | DNS uses UDP for queries | TCP only for zone transfers |
| 8 | MQTT = IoT protocol | Publish-Subscribe model |
| 9 | Socket = IP + Port | Endpoint of IPC |
| 10 | DHCP process = DORA | Discover-Offer-Request-Acknowledge |

---

---

# 📚 PART B — GENERAL STUDIES (GS)
# GOVERNMENT SCHEMES — CENTRAL & BIHAR STATE PROGRAMMES

---

## 🔑 WHY THIS TOPIC MATTERS FOR BPSC TRE 4.0

Government schemes appear in EVERY Bihar exam's GS/Current Affairs section. TRE 4.0 expects awareness of:
- **Central government flagship schemes** (PM-level schemes)
- **Bihar state-specific schemes**
- **Target beneficiaries, launch year, objectives**
- **Ministries responsible**

Typically **4–6 questions** in GS come from schemes and current affairs.

---

## 🏛️ SECTION 1: MAJOR CENTRAL GOVERNMENT SCHEMES

---

### 1. PM-KISAN (Pradhan Mantri Kisan Samman Nidhi)

```
┌─────────────────────────────────────────────────────────────┐
│ Scheme            │ PM-KISAN                               │
│ Launched          │ December 2018 (operative from Feb 2019)│
│ Ministry          │ Agriculture & Farmers Welfare          │
│ Benefit           │ ₹6,000/year in 3 installments of ₹2000│
│ Target            │ Small & marginal farmers               │
│ Mode              │ Direct Benefit Transfer (DBT)          │
│ Funding           │ 100% Central Government                │
└─────────────────────────────────────────────────────────────┘
```

**Key Facts for Exam:**
- ₹6,000 per year = ₹2,000 every 4 months (3 installments)
- Direct transfer to bank account (DBT)
- No state contribution — fully central funded

---

### 2. PM Awas Yojana — PMAY

```
┌─────────────────────────────────────────────────────────────┐
│ Scheme            │ PM Awas Yojana                         │
│ Launched          │ June 2015                              │
│ Ministry          │ Housing & Urban Affairs (Urban)        │
│                   │ Rural Development (Gramin/Rural)       │
│ Objective         │ Housing for All by 2022 (extended)     │
│ Two Components    │ PMAY-Urban & PMAY-Gramin (Rural)       │
│ Beneficiary       │ Economically Weaker Section (EWS),     │
│                   │ Low Income Group (LIG)                 │
└─────────────────────────────────────────────────────────────┘
```

**Memory:** PMAY = "Pucca Makan Apna Yojana" (your own pucca house)

---

### 3. Ayushman Bharat — PM-JAY

```
┌─────────────────────────────────────────────────────────────┐
│ Full Name         │ Pradhan Mantri Jan Arogya Yojana       │
│ Launched          │ September 2018 (PM Modi)               │
│ Ministry          │ Health & Family Welfare                │
│ Coverage          │ ₹5 lakh health cover per family/year   │
│ Target            │ Bottom 40% families (poor, vulnerable) │
│ Nickname          │ World's largest health scheme          │
│ Basis             │ SECC 2011 data                         │
│ Beneficiaries     │ ~50 crore people                       │
└─────────────────────────────────────────────────────────────┘
```

**🚨 EXAM TRAP:** Coverage is ₹5 lakh per FAMILY per year, NOT per person.

---

### 4. Ujjwala Yojana — PMUY

```
┌─────────────────────────────────────────────────────────────┐
│ Full Name         │ PM Ujjwala Yojana                      │
│ Launched          │ May 2016 (Ballia, UP)                  │
│ Ministry          │ Petroleum & Natural Gas                │
│ Objective         │ Free LPG connections to BPL households │
│ Target            │ Women from BPL households              │
│ Benefit           │ Free LPG connection + cylinder         │
│ Phase 2           │ Ujjwala 2.0 (2021)                    │
└─────────────────────────────────────────────────────────────┘
```

**Memory:** Ujjwala = "Illumination" → Light up BPL kitchens with clean fuel

---

### 5. MNREGA — Mahatma Gandhi National Rural Employment Guarantee Act

```
┌─────────────────────────────────────────────────────────────┐
│ Full Form         │ Mahatma Gandhi NREGA                   │
│ Launched          │ 2005 (Act), February 2006 (implemented)│
│ Ministry          │ Rural Development                      │
│ Guarantee         │ 100 days of wage employment per year   │
│ Target            │ Rural households (unskilled work)      │
│ Benefit           │ Wage employment guarantee              │
│ Wage payment      │ Within 15 days (else compensation)     │
└─────────────────────────────────────────────────────────────┘
```

**Key Facts:**
- Originally called NREGA, renamed to MGNREGA in 2009
- **Right to work** — if work not given within 15 days → unemployment allowance
- Applies only to **rural** areas (NOT urban)

---

### 6. Digital India Programme

```
┌─────────────────────────────────────────────────────────────┐
│ Launched          │ July 2015                              │
│ Ministry          │ Electronics & IT (MeitY)               │
│ Vision            │ Transform India into digitally         │
│                   │ empowered society and knowledge economy│
│ 3 Key Vision Areas│ 1. Digital Infrastructure as utility  │
│                   │ 2. Governance & services on demand     │
│                   │ 3. Digital Empowerment of citizens     │
│ Components        │ BharatNet, e-Governance, DigiLocker,  │
│                   │ Aadhaar, UPI, UMANG                    │
└─────────────────────────────────────────────────────────────┘
```

---

### 7. Swachh Bharat Mission — SBM

```
┌─────────────────────────────────────────────────────────────┐
│ Launched          │ October 2, 2014 (Gandhi Jayanti)       │
│ Ministry          │ Jal Shakti (Rural), Housing (Urban)    │
│ Objective         │ Open Defecation Free (ODF) India       │
│ Target            │ Build toilets, clean cities & villages │
│ Phase 2           │ SBM 2.0 launched 2020-21               │
└─────────────────────────────────────────────────────────────┘
```

**🚨 EXAM TRAP:** Launched on October 2 (Gandhi's birthday) — symbolically significant.

---

### 8. Beti Bachao Beti Padhao — BBBP

```
┌─────────────────────────────────────────────────────────────┐
│ Launched          │ January 22, 2015 (Panipat, Haryana)    │
│ Ministry          │ Women & Child Development +            │
│                   │ Health + Education (3 Ministries)      │
│ Objective         │ Address declining Child Sex Ratio (CSR)│
│                   │ and girls' education                   │
│ Focus Districts   │ 100 low CSR districts initially        │
└─────────────────────────────────────────────────────────────┘
```

**Key Fact:** Beti Bachao Beti Padhao involves **THREE ministries** — this is a PYQ trap.

---

### 9. Pradhan Mantri Mudra Yojana — PMMY

```
┌─────────────────────────────────────────────────────────────┐
│ Launched          │ April 2015                             │
│ Ministry          │ Finance                                │
│ Objective         │ Loans to micro/small enterprises       │
│ 3 Categories      │ Shishu: up to ₹50,000                 │
│                   │ Kishore: ₹50,001 to ₹5 lakh           │
│                   │ Tarun: ₹5 lakh to ₹10 lakh            │
│ Target            │ Non-corporate, non-farm small/micro    │
└─────────────────────────────────────────────────────────────┘
```

**Memory:** **S**mall → **K**iddo → **T**een = Shishu → Kishore → Tarun (increasing loan size)

---

### 10. Stand Up India

```
┌─────────────────────────────────────────────────────────────┐
│ Launched          │ April 5, 2016                          │
│ Ministry          │ Finance / SIDBI                        │
│ Objective         │ Loans to SC/ST and Women entrepreneurs │
│ Loan Amount       │ ₹10 lakh to ₹1 crore                  │
│ At least          │ One SC/ST and one woman borrower per   │
│                   │ bank branch                            │
└─────────────────────────────────────────────────────────────┘
```

**🚨 EXAM TRAP:** Stand Up India ≠ Start Up India
- **Stand Up India** = for SC/ST and Women (social inclusion)
- **Start Up India** = for entrepreneurs (innovation & start-ups)

---

### 11. Start Up India

```
┌─────────────────────────────────────────────────────────────┐
│ Launched          │ January 16, 2016                       │
│ Ministry          │ Commerce & Industry (DPIIT)            │
│ Objective         │ Promote entrepreneurship, innovation   │
│ Benefits          │ Tax exemptions (3 years), fast-track   │
│                   │ patent, easy compliance                │
└─────────────────────────────────────────────────────────────┘
```

---

### 12. National Education Policy — NEP 2020

```
┌─────────────────────────────────────────────────────────────┐
│ Policy Name       │ National Education Policy (NEP) 2020   │
│ Approved          │ July 2020                              │
│ Ministry          │ Education (formerly HRD)               │
│ Structure         │ 5+3+3+4 replacing 10+2                │
│                   │ (Foundational+Preparatory+Middle+Sec.) │
│ Key Features      │ Multidisciplinary, mother tongue medium│
│                   │ Board exams twice a year, holistic     │
│ Previous Policy   │ NPE 1986                               │
└─────────────────────────────────────────────────────────────┘
```

**🚨 EXAM TRAP:** NEP 2020 introduces **5+3+3+4 structure**, not the old 10+2. Also renamed HRD Ministry to **Ministry of Education**.

---

## 🏛️ SECTION 2: BIHAR-SPECIFIC SCHEMES

---

### 1. Bihar Student Credit Card Scheme — BSCCS

```
┌─────────────────────────────────────────────────────────────┐
│ Launched          │ October 2, 2016 (Chief Minister Nitish) │
│ Benefit           │ Loan up to ₹4 lakh for higher education│
│ Interest Rate     │ Simple interest @ 4% (1% for women,    │
│                   │ divyangjans)                            │
│ Target            │ Students who passed Class 12           │
│ Guarantee         │ State Government is guarantor          │
└─────────────────────────────────────────────────────────────┘
```

---

### 2. Mukhyamantri Kanya Utthan Yojana — MKUY

```
┌─────────────────────────────────────────────────────────────┐
│ Launched          │ 2019, Bihar Government                 │
│ Benefit           │ ₹54,100 total for girls (birth to      │
│                   │ graduation in instalments)             │
│ Target            │ Girl child empowerment and education   │
│ Objective         │ Reduce child marriage, increase female │
│                   │ literacy, improve sex ratio            │
└─────────────────────────────────────────────────────────────┘
```

---

### 3. Mukhyamantri Gram Parivahan Yojana

```
┌─────────────────────────────────────────────────────────────┐
│ Launched          │ Bihar Government                       │
│ Benefit           │ Subsidy on vehicle purchase for SC/ST/ │
│                   │ EBC families in rural areas            │
│ Objective         │ Rural connectivity and livelihood      │
└─────────────────────────────────────────────────────────────┘
```

---

### 4. Har Ghar Nal Ka Jal — Jal Jeevan Mission

```
┌─────────────────────────────────────────────────────────────┐
│ Central Scheme    │ Jal Jeevan Mission (JJM) — 2019        │
│ Bihar Component   │ Har Ghar Nal Ka Jal                    │
│ Ministry          │ Jal Shakti                             │
│ Target            │ Tap water to every rural household     │
│ Target Year       │ 2024                                   │
└─────────────────────────────────────────────────────────────┘
```

---

### 5. Bihar Har Ghar Bijli Yojana (BHGBY)

- **Objective:** Electricity to every household in Bihar
- State scheme to complement Central **Saubhagya Yojana**
- Target: 100% household electrification in Bihar

---

## 📊 QUICK REFERENCE — CENTRAL SCHEMES MASTER TABLE

```
┌────┬─────────────────────────┬──────────┬────────────────────────────┐
│ #  │ Scheme                  │ Launched │ Key Feature                │
├────┼─────────────────────────┼──────────┼────────────────────────────┤
│ 1  │ PM-KISAN                │ 2018     │ ₹6,000/yr to farmers       │
│ 2  │ PM Awas Yojana          │ 2015     │ Housing for all            │
│ 3  │ Ayushman Bharat (PMJAY) │ 2018     │ ₹5 lakh health cover       │
│ 4  │ Ujjwala Yojana          │ 2016     │ Free LPG to BPL women      │
│ 5  │ MNREGA                  │ 2006     │ 100 days rural employment  │
│ 6  │ Digital India           │ 2015     │ Digital empowerment        │
│ 7  │ Swachh Bharat           │ 2014     │ ODF — clean India          │
│ 8  │ Beti Bachao Beti Padhao │ 2015     │ Girl child — 3 ministries  │
│ 9  │ PM Mudra Yojana         │ 2015     │ Shishu/Kishore/Tarun loans │
│ 10 │ Stand Up India          │ 2016     │ SC/ST + women entrepreneurs│
│ 11 │ Start Up India          │ 2016     │ Innovation & startups      │
│ 12 │ NEP 2020                │ 2020     │ 5+3+3+4 structure          │
│ 13 │ Jal Jeevan Mission      │ 2019     │ Tap water to all rural HH  │
│ 14 │ Saubhagya Yojana        │ 2017     │ Household electrification  │
│ 15 │ PM Garib Kalyan Yojana  │ 2020     │ Free ration during COVID   │
└────┴─────────────────────────┴──────────┴────────────────────────────┘
```

---

## 🚨 BPSC TOPPER TRAP CARD — GS SCHEMES

| Trap | Correct Answer |
|------|----------------|
| PM-KISAN gives ₹2000/year | ❌ WRONG — ₹6000/year in 3 installments of ₹2000 |
| Ayushman Bharat = ₹5 lakh per person | ❌ WRONG — ₹5 lakh per FAMILY |
| BBBP involves 1 ministry | ❌ WRONG — involves 3 ministries |
| NEP 2020 continues 10+2 structure | ❌ WRONG — introduces 5+3+3+4 |
| Stand Up India = Start Up India | ❌ WRONG — completely different schemes |
| MNREGA applies to urban areas too | ❌ WRONG — rural areas only |
| MGNREGA guarantees 150 days of work | ❌ WRONG — 100 days per year |
| Ujjwala Yojana launched in 2018 | ❌ WRONG — launched May 2016 |

---

## ✅ GS CONCEPT SUMMARY — DAY 46

| # | Scheme | Critical Fact |
|---|--------|--------------|
| 1 | PM-KISAN | ₹6,000/year in 3 installments |
| 2 | Ayushman Bharat | ₹5 lakh per family (50 crore beneficiaries) |
| 3 | Ujjwala | Free LPG to BPL women (launched 2016) |
| 4 | MNREGA | 100 days rural employment guarantee |
| 5 | Beti Bachao | 3 ministries, launched Jan 2015, Panipat |
| 6 | MUDRA | Shishu → Kishore → Tarun (increasing loans) |
| 7 | Stand Up India | SC/ST + women; ₹10L–₹1Cr |
| 8 | Start Up India | Innovation; launched Jan 16, 2016 |
| 9 | NEP 2020 | 5+3+3+4 structure (replaces 10+2) |
| 10 | BSCCS (Bihar) | ₹4 lakh education loan (Oct 2, 2016) |

---

---

# 📝 PRACTICE QUESTIONS

> ⚠️ **INSTRUCTION:** Attempt ALL 50 questions FIRST. Answers are provided at the END of the file.
> Do NOT scroll down. Cover the answer section with paper or your hand.
> BPSC Five-Option Format: (A), (B), (C), (D) More than one of the above, (E) None of the above

---

## 🖥️ CS PRACTICE QUESTIONS (Q1–Q25)
### Topic: Network Protocols — TCP, UDP, SMTP, HTTP, MQTT, DNS, FTP

---

**Q1.** TCP (Transmission Control Protocol) is best described as:

(A) A connectionless and unreliable protocol  
(B) A protocol that uses only one port number  
(C) A connection-oriented and reliable protocol that uses three-way handshake  
(D) More than one of the above  
(E) None of the above  

---

**Q2.** Which of the following correctly describes the three-way handshake in TCP?

(A) SYN → ACK → SYN-ACK  
(B) ACK → SYN → SYN-ACK  
(C) SYN → SYN-ACK → ACK  
(D) More than one of the above  
(E) None of the above  

---

**Q3.** Which of the following protocols is CONNECTIONLESS?

(A) TCP  
(B) FTP  
(C) SMTP  
(D) More than one of the above  
(E) None of the above — UDP is connectionless  

---

**Q4.** UDP (User Datagram Protocol) is preferred over TCP when:

(A) Data integrity is more important than speed  
(B) Speed and low latency is more important than reliability  
(C) File transfer needs to be 100% accurate  
(D) More than one of the above  
(E) None of the above  

---

**Q5.** When a mail server sends an email to another mail server, the sending server acts as:

(A) SMTP Server  
(B) IMAP Client  
(C) SMTP Client  
(D) More than one of the above  
(E) None of the above  

---

**Q6.** SMTP is used for which of the following purposes?

(A) Downloading email from server to client  
(B) Sending email from client to server or between servers  
(C) Browsing the internet  
(D) More than one of the above  
(E) None of the above  

---

**Q7.** The default port number for SMTP is:

(A) 110  
(B) 143  
(C) 80  
(D) More than one of the above  
(E) None of the above — it is 25  

---

**Q8.** Which of the following correctly describes HTTP?

(A) HTTP is a stateful protocol with memory of past requests  
(B) HTTP uses port 443 by default  
(C) HTTP is a stateless application layer protocol using port 80  
(D) More than one of the above  
(E) None of the above  

---

**Q9.** What is the primary difference between HTTP and HTTPS?

(A) HTTPS uses a different programming language  
(B) HTTPS adds SSL/TLS encryption to HTTP on port 443  
(C) HTTPS is slower than HTTP because it downloads more data  
(D) More than one of the above  
(E) None of the above  

---

**Q10.** FTP (File Transfer Protocol) uses which port numbers?

(A) Port 21 only  
(B) Port 80 and 443  
(C) Port 20 for data transfer and Port 21 for control commands  
(D) More than one of the above  
(E) None of the above  

---

**Q11.** MQTT protocol is specifically designed for:

(A) Email transmission between servers  
(B) Browsing World Wide Web  
(C) Communication in IoT (Internet of Things) devices  
(D) More than one of the above  
(E) None of the above  

---

**Q12.** MQTT follows which communication model?

(A) Client-Server model like HTTP  
(B) Peer-to-Peer model  
(C) Publish-Subscribe model  
(D) More than one of the above  
(E) None of the above  

---

**Q13.** Which of the following statements about the Ping utility is CORRECT?

(A) Ping stands for "Packet Internet Groper"  
(B) Ping uses TCP protocol  
(C) Ping uses ICMP and summarizes packet loss and round-trip delay  
(D) More than one of the above  
(E) None of the above  

---

**Q14.** DNS (Domain Name System) primarily uses which transport protocol for standard queries?

(A) TCP  
(B) UDP  
(C) SMTP  
(D) More than one of the above  
(E) None of the above  

---

**Q15.** The DHCP process follows which sequence?

(A) DORA — Discover, Offer, Request, Acknowledge  
(B) DORA — Data, Open, Relay, Acknowledge  
(C) SYN-ACK — Synchronize and Acknowledge  
(D) More than one of the above  
(E) None of the above  

---

**Q16.** A "Socket" in networking is best defined as:

(A) A physical port on the computer's motherboard  
(B) A software endpoint of inter-process communication, identified by IP + Port  
(C) A type of network cable connector  
(D) More than one of the above  
(E) None of the above  

---

**Q17.** Which protocol is used to RECEIVE emails with synchronization across devices?

(A) SMTP  
(B) POP3  
(C) IMAP  
(D) More than one of the above  
(E) None of the above  

---

**Q18.** SSH (Secure Shell) uses which port number?

(A) 23  
(B) 21  
(C) 22  
(D) More than one of the above  
(E) None of the above  

---

**Q19.** Which of the following protocols are used at the APPLICATION LAYER of the OSI model?

(A) TCP and UDP  
(B) IP and ICMP  
(C) HTTP, FTP, SMTP, and DNS  
(D) More than one of the above  
(E) None of the above  

---

**Q20.** The header size of a TCP segment is ______ bytes, while a UDP datagram header is ______ bytes.

(A) 8 bytes TCP, 20 bytes UDP  
(B) 20 bytes TCP, 8 bytes UDP  
(C) 16 bytes TCP, 8 bytes UDP  
(D) More than one of the above  
(E) None of the above  

---

**Q21.** Which of the following is a use case where UDP is PREFERRED over TCP?

(A) Online banking transactions  
(B) File download from a server  
(C) Video streaming and VoIP calls  
(D) More than one of the above  
(E) None of the above  

---

**Q22.** In the context of Telnet vs SSH, which statement is CORRECT?

(A) Telnet transmits data in encrypted form; SSH does not  
(B) Telnet uses port 22; SSH uses port 23  
(C) Telnet is insecure (plain text, port 23); SSH is secure (encrypted, port 22)  
(D) More than one of the above  
(E) None of the above  

---

**Q23.** MQTT's port number for standard (non-secure) connections is:

(A) 8883  
(B) 25  
(C) 1883  
(D) More than one of the above  
(E) None of the above  

---

**Q24.** Which of the following correctly identifies protocols by their data unit name?

(A) TCP uses "Datagram"; UDP uses "Segment"  
(B) TCP uses "Segment"; UDP uses "Datagram"  
(C) Both TCP and UDP use "Packet"  
(D) More than one of the above  
(E) None of the above  

---

**Q25.** Consider the following statements:
1. HTTP is a stateless protocol.
2. FTP uses two ports — 20 and 21.
3. SMTP client is a mail server that SENDS email to another mail server.
4. MQTT uses UDP for IoT communication.

Which of the above statements are CORRECT?

(A) Only 1 and 2  
(B) Only 1, 2, and 3  
(C) Only 1, 3, and 4  
(D) More than one of the above (1, 2, and 3 are correct)  
(E) None of the above  

---

---

## 📚 GS PRACTICE QUESTIONS (Q26–Q50)
### Topic: Government Schemes — Central & Bihar State

---

**Q26.** Under PM-KISAN (Pradhan Mantri Kisan Samman Nidhi), eligible farmers receive:

(A) ₹2,000 per year in one installment  
(B) ₹12,000 per year in 6 installments  
(C) ₹6,000 per year in 3 installments of ₹2,000 each  
(D) More than one of the above  
(E) None of the above  

---

**Q27.** PM-KISAN scheme was launched in:

(A) 2014  
(B) 2016  
(C) 2018 (operative from February 2019)  
(D) More than one of the above  
(E) None of the above  

---

**Q28.** Ayushman Bharat — Pradhan Mantri Jan Arogya Yojana provides health cover of:

(A) ₹1 lakh per person per year  
(B) ₹5 lakh per family per year  
(C) ₹5 lakh per person per year  
(D) More than one of the above  
(E) None of the above  

---

**Q29.** Under which scheme are free LPG connections provided to BPL women households?

(A) PM Awas Yojana  
(B) Pradhan Mantri Ujjwala Yojana  
(C) Beti Bachao Beti Padhao  
(D) More than one of the above  
(E) None of the above  

---

**Q30.** The MNREGA scheme guarantees how many days of wage employment per year?

(A) 200 days  
(B) 150 days  
(C) 100 days  
(D) More than one of the above  
(E) None of the above  

---

**Q31.** In which year was the Mahatma Gandhi National Rural Employment Guarantee Act (MGNREGA) implemented?

(A) 2002  
(B) 2004  
(C) 2006  
(D) More than one of the above  
(E) None of the above  

---

**Q32.** Swachh Bharat Mission was launched on:

(A) November 14, 2014 (Children's Day)  
(B) October 2, 2014 (Gandhi Jayanti)  
(C) January 26, 2014 (Republic Day)  
(D) More than one of the above  
(E) None of the above  

---

**Q33.** The primary objective of Swachh Bharat Mission is:

(A) Providing clean drinking water to all households  
(B) Building roads in rural areas  
(C) Making India Open Defecation Free (ODF) and solid waste management  
(D) More than one of the above  
(E) None of the above  

---

**Q34.** Beti Bachao Beti Padhao scheme was launched in:

(A) Panipat, Haryana on January 22, 2015  
(B) New Delhi on August 15, 2014  
(C) Patna, Bihar on October 2, 2015  
(D) More than one of the above  
(E) None of the above  

---

**Q35.** Beti Bachao Beti Padhao scheme involves how many central ministries?

(A) One ministry — Women & Child Development  
(B) Two ministries — Women & Child Development + Health  
(C) Three ministries — Women & Child Development + Health + Education  
(D) More than one of the above  
(E) None of the above  

---

**Q36.** Under PM Mudra Yojana, the loan category "Kishore" provides loans of:

(A) Up to ₹50,000  
(B) ₹50,001 to ₹5 lakh  
(C) ₹5 lakh to ₹10 lakh  
(D) More than one of the above  
(E) None of the above  

---

**Q37.** "Stand Up India" scheme is designed to provide loans to:

(A) Start-up companies and technology innovators  
(B) SC/ST borrowers and women entrepreneurs  
(C) Agricultural farmers for irrigation  
(D) More than one of the above  
(E) None of the above  

---

**Q38.** Which of the following CORRECTLY differentiates Stand Up India from Start Up India?

(A) Both schemes serve the same purpose — they are identical  
(B) Stand Up India = SC/ST and Women (social inclusion); Start Up India = Innovation and entrepreneurship  
(C) Stand Up India focuses on agriculture; Start Up India focuses on manufacturing  
(D) More than one of the above  
(E) None of the above  

---

**Q39.** National Education Policy (NEP) 2020 introduced which school structure?

(A) Continued the old 10+2 system  
(B) 4+4+4 structure  
(C) 5+3+3+4 structure replacing the 10+2 system  
(D) More than one of the above  
(E) None of the above  

---

**Q40.** NEP 2020 was approved in which year and replaced which earlier policy?

(A) 2019, replaced NPE 1992  
(B) 2020, replaced NPE 1986  
(C) 2021, replaced NPE 2000  
(D) More than one of the above  
(E) None of the above  

---

**Q41.** Digital India Programme was launched in:

(A) 2013  
(B) 2015  
(C) 2017  
(D) More than one of the above  
(E) None of the above  

---

**Q42.** Bihar Student Credit Card Scheme (BSCCS) was launched on:

(A) January 26, 2016 — Republic Day  
(B) October 2, 2016 — Gandhi Jayanti  
(C) August 15, 2016 — Independence Day  
(D) More than one of the above  
(E) None of the above  

---

**Q43.** Under the Bihar Student Credit Card Scheme, the maximum loan amount for higher education is:

(A) ₹2 lakh  
(B) ₹4 lakh  
(C) ₹10 lakh  
(D) More than one of the above  
(E) None of the above  

---

**Q44.** Mukhyamantri Kanya Utthan Yojana in Bihar is aimed at:

(A) Providing jobs to unemployed men in rural Bihar  
(B) Financial support to girl children from birth to graduation to empower girls  
(C) Construction of schools in rural Bihar  
(D) More than one of the above  
(E) None of the above  

---

**Q45.** Jal Jeevan Mission was launched in which year and targets:

(A) 2015, targets clean rivers in India  
(B) 2019, targets tap water connection to every rural household  
(C) 2018, targets flood control in Bihar  
(D) More than one of the above  
(E) None of the above  

---

**Q46.** PM Awas Yojana (Urban) was launched in:

(A) 2014  
(B) 2015  
(C) 2016  
(D) More than one of the above  
(E) None of the above  

---

**Q47.** Which of the following is a flagship scheme for household electrification in India?

(A) Jal Jeevan Mission  
(B) Saubhagya Yojana (Pradhan Mantri Sahaj Bijli Har Ghar Yojana)  
(C) Ujjwala Yojana  
(D) More than one of the above  
(E) None of the above  

---

**Q48.** MNREGA primarily provides employment in:

(A) Urban areas only  
(B) Both urban and rural areas  
(C) Rural areas only  
(D) More than one of the above  
(E) None of the above  

---

**Q49.** Consider the following matches of scheme and launch year:
1. PM-KISAN — 2018 ✓
2. Swachh Bharat Mission — 2014 ✓
3. Ujjwala Yojana — 2016 ✓
4. Beti Bachao Beti Padhao — 2016 ✗ (correct: 2015)

Which of the above are CORRECTLY matched?

(A) Only 1 and 2  
(B) Only 1, 2, and 3  
(C) Only 2 and 3  
(D) More than one of the above  
(E) None of the above  

---

**Q50.** Which scheme provides subsidized loans to micro and small enterprises under three categories — Shishu, Kishore, and Tarun?

(A) Stand Up India  
(B) Startup India  
(C) Pradhan Mantri Mudra Yojana (PMMY)  
(D) More than one of the above  
(E) None of the above  

---

---

# 🔑 ANSWER KEY

> ✅ Attempt all 50 questions BEFORE checking answers!

---

## CS ANSWERS (Q1–Q25)

| Q | Ans | Explanation |
|---|-----|-------------|
| Q1 | **(C)** | TCP = connection-oriented + reliable + 3-way handshake |
| Q2 | **(C)** | Correct sequence: SYN → SYN-ACK → ACK |
| Q3 | **(E)** | TCP/FTP/SMTP are all connection-oriented — UDP is connectionless |
| Q4 | **(B)** | UDP preferred when speed matters more (video, VoIP) |
| Q5 | **(C)** | SMTP CLIENT — a server sending email to another server is the CLIENT |
| Q6 | **(B)** | SMTP only sends email; POP3/IMAP receive email |
| Q7 | **(E)** | Port 25 is SMTP's default — none of A, B, C |
| Q8 | **(C)** | HTTP is stateless, Application layer, port 80 |
| Q9 | **(B)** | HTTPS = HTTP + SSL/TLS encryption on port 443 |
| Q10 | **(C)** | FTP: Port 20 (data) + Port 21 (control) — unique among protocols |
| Q11 | **(C)** | MQTT = IoT protocol — for devices like sensors |
| Q12 | **(C)** | MQTT = Publish-Subscribe model via MQTT Broker |
| Q13 | **(C)** | Ping uses ICMP, reports packet loss + round-trip delay |
| Q14 | **(B)** | DNS uses UDP for standard queries; TCP for zone transfers only |
| Q15 | **(A)** | DHCP DORA = Discover → Offer → Request → Acknowledge |
| Q16 | **(B)** | Socket = IP Address + Port Number = endpoint of IPC |
| Q17 | **(C)** | IMAP = syncs email across devices; POP3 downloads and deletes |
| Q18 | **(C)** | SSH = port 22; Telnet = port 23 |
| Q19 | **(C)** | HTTP, FTP, SMTP, DNS are ALL Application layer protocols |
| Q20 | **(B)** | TCP header = 20 bytes; UDP header = 8 bytes (smaller) |
| Q21 | **(C)** | Video streaming and VoIP = latency-sensitive → UDP preferred |
| Q22 | **(C)** | Telnet = insecure, port 23; SSH = secure, port 22 |
| Q23 | **(C)** | MQTT standard port = 1883; MQTTS (secure) = 8883 |
| Q24 | **(B)** | TCP → Segment; UDP → Datagram |
| Q25 | **(D)** | Statements 1, 2, 3 are correct; Statement 4 is WRONG (MQTT uses TCP not UDP) → "More than one" (1, 2, 3) |

---

## GS ANSWERS (Q26–Q50)

| Q | Ans | Explanation |
|---|-----|-------------|
| Q26 | **(C)** | PM-KISAN = ₹6,000/year in 3 equal installments of ₹2,000 |
| Q27 | **(C)** | Launched December 2018; operative from Feb 2019 |
| Q28 | **(B)** | Ayushman Bharat = ₹5 lakh per FAMILY (not per person) |
| Q29 | **(B)** | Pradhan Mantri Ujjwala Yojana — free LPG to BPL women |
| Q30 | **(C)** | MNREGA guarantees 100 days per year (not 150 or 200) |
| Q31 | **(C)** | MGNREGA implemented in February 2006 |
| Q32 | **(B)** | October 2, 2014 — Gandhi Jayanti (symbolically important) |
| Q33 | **(C)** | Swachh Bharat = ODF India + solid waste management |
| Q34 | **(A)** | Panipat, Haryana on January 22, 2015 |
| Q35 | **(C)** | BBBP involves THREE ministries: WCD + Health + Education |
| Q36 | **(B)** | Kishore = ₹50,001 to ₹5 lakh (middle category) |
| Q37 | **(B)** | Stand Up India = SC/ST borrowers + women entrepreneurs |
| Q38 | **(B)** | Stand Up India (social inclusion) ≠ Start Up India (innovation) |
| Q39 | **(C)** | NEP 2020 = 5+3+3+4 structure (replaces old 10+2) |
| Q40 | **(B)** | Approved July 2020; replaced NPE 1986 |
| Q41 | **(B)** | Digital India = July 2015 |
| Q42 | **(B)** | BSCCS launched October 2, 2016 (Gandhi Jayanti in Bihar) |
| Q43 | **(B)** | BSCCS max loan = ₹4 lakh for higher education |
| Q44 | **(B)** | MKUY = financial support to girls from birth to graduation |
| Q45 | **(B)** | JJM = 2019; tap water to every rural household |
| Q46 | **(B)** | PM Awas Yojana (Urban) launched June 2015 |
| Q47 | **(B)** | Saubhagya Yojana = household electrification scheme (2017) |
| Q48 | **(C)** | MNREGA applies to RURAL areas ONLY |
| Q49 | **(B)** | Items 1, 2, 3 are correctly matched; Item 4 is wrong (BBBP = 2015) |
| Q50 | **(C)** | PM Mudra Yojana = Shishu / Kishore / Tarun categories |

---

---

# 📌 DAILY NIGHT REVISION — 5-BULLET SUMMARY

Write these from memory before sleeping:

## CS — Protocol Key Facts:
1. TCP = connection-oriented, reliable; 3-way handshake (SYN→SYN-ACK→ACK)
2. UDP = connectionless, unreliable, faster; used by DNS/DHCP/Video/VoIP
3. SMTP server sending to another server = SMTP CLIENT (exam trap!)
4. HTTP = stateless, port 80; HTTPS = encrypted SSL/TLS, port 443
5. MQTT = IoT protocol, Publish-Subscribe, TCP, port 1883; Ping = ICMP (not TCP)

## GS — Schemes Key Facts:
1. PM-KISAN = ₹6,000/year (3 × ₹2,000 installments), full central funding
2. Ayushman Bharat = ₹5 lakh per FAMILY (not per person), launched 2018
3. MNREGA = 100 days rural employment guarantee; urban areas NOT included
4. BBBP = 3 ministries; launched Jan 22, 2015, Panipat; Stand Up ≠ Start Up
5. NEP 2020 = 5+3+3+4 structure (replaced old 10+2); Bihar BSCCS = ₹4 lakh loan

---

## ⚡ TOPPER'S SELF-ASSESSMENT CHECKLIST

After completing Day 46, verify:

- [ ] Can you explain TCP three-way handshake without notes?
- [ ] Do you know when a mail server becomes SMTP CLIENT?
- [ ] Can you list 5 differences between TCP and UDP?
- [ ] Do you know all 5 correct port numbers: FTP/SSH/SMTP/HTTP/HTTPS?
- [ ] Do you know MQTT = IoT = Publish-Subscribe?
- [ ] Can you state what Ping actually measures?
- [ ] Do you know PM-KISAN amount correctly (₹6000, not ₹2000)?
- [ ] Can you distinguish Stand Up India from Start Up India?
- [ ] Do you remember BBBP involves 3 ministries?
- [ ] Can you state the NEP 2020 structure (5+3+3+4)?

**Score yourself:** 9–10 ✅ = Ready for next day | 6–8 = Quick re-read needed | <6 = Re-study today

---

*Day 46 Complete | Next: Day 47 — Network Topologies & Devices + Bihar GK (Famous Personalities)*
*Running Total: Phase 1 (Day 1–60) | Networks Week (Day 43–49)*
