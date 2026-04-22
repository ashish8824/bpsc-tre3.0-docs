# 📅 BPSC TRE 4.0 — DAY 46 COMPLETE STUDY MODULE
### Computer Networks: Network Protocols (TCP, UDP, HTTP, SMTP, Ping, MQTT, Socket) + Current Affairs — Government Schemes
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Network Protocols — TCP, UDP, HTTP/HTTPS, SMTP, Ping, MQTT, Socket
> - Afternoon (1 hr): Current Affairs — Important Government Schemes (Digital India, Ayushman Bharat, etc.)
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Network Protocols — TCP, UDP, HTTP, SMTP, Ping, MQTT, Socket

---

## 🔷 SECTION 1: What is a Protocol?

### Real-Life Analogy — The Rules of a Conversation:

When two people meet in India, there's an unspoken protocol:
- You greet first ("Namaste")
- The other person greets back
- You state your purpose
- Discussion happens
- You say goodbye and leave

If one person starts speaking in Japanese while the other only knows Hindi — **communication FAILS** even though both are physically present. They need a **common language + rules**.

Computer networks face the EXACT same problem. Thousands of devices from Apple, Samsung, Dell, made in different countries — they need **agreed-upon rules** to communicate.

> **A Network Protocol is a set of rules and conventions that govern how data is transmitted and received between devices on a network. It defines the format, timing, sequencing, and error-checking of messages.**

### Why Are Protocols Needed?
```
WITHOUT PROTOCOLS:                    WITH PROTOCOLS:
  Device A sends:  01001101...          Device A: "I want to send you data"
  Device B gets:   ????????              Device B: "OK, I'm ready"
  Interpretation:  IMPOSSIBLE!          Device A: Sends data in agreed format
  (Different formats, speeds,           Device B: Receives, decodes correctly
   error handling = complete chaos)     Device B: "Received successfully!"

PROTOCOLS DEFINE:
  → Format of messages (headers, data fields)
  → Timing (when to send, how fast)
  → Sequencing (what order packets arrive)
  → Error handling (what to do if packet lost)
  → Connection management (how to start/end communication)
  → Security (encryption, authentication)

ANALOGY: Protocols = TRAFFIC RULES on the internet highway
  → Without traffic rules: chaos, accidents, gridlock
  → With traffic rules: everyone knows which side to drive, when to stop/go
```

---

## 🔷 SECTION 2: TCP — Transmission Control Protocol

### Overview:
```
TCP = Transmission Control Protocol
OSI LAYER:  Transport Layer (Layer 4)
TCP/IP LAYER: Transport Layer (Host-to-Host Layer)
TYPE:       Connection-ORIENTED
RELIABILITY: RELIABLE (guarantees delivery)
ANALOGY:    REGISTERED POST / COURIER WITH TRACKING
            "Your package is guaranteed to arrive, and you'll get confirmation!"
```

### TCP's Key Features — Deep Explanation:

#### Feature 1: Connection-Oriented
```
WHAT IT MEANS: TCP establishes a CONNECTION before data transfer begins.
               Two devices formally "agree" to communicate first.

PROCESS:
  Step 1: Establish Connection (3-way handshake) → See below
  Step 2: Transfer Data
  Step 3: Terminate Connection (4-way handshake)
  
WHY: Like calling someone on the phone — you first dial, they pick up,
     THEN you start talking. Connection established FIRST!
     
CONTRAST WITH UDP: Like dropping a letter in a mailbox — no setup,
                   no confirmation, just send and hope!
```

#### Feature 2: The Three-Way Handshake (SYN, SYN-ACK, ACK)
```
THE TCP THREE-WAY HANDSHAKE:
(This is the connection ESTABLISHMENT process)

CLIENT (Your browser)           SERVER (Google's server)
      │                                │
      │────── SYN ────────────────────▶│
      │  "Hello! I want to connect.    │
      │   My sequence number is 100"   │
      │                                │
      │◀───── SYN-ACK ─────────────────│
      │  "OK! I got your SYN(100).     │
      │   My sequence number is 300.   │
      │   I acknowledge your 100"      │
      │                                │
      │────── ACK ────────────────────▶│
      │  "Got it! I acknowledge your   │
      │   300. Let's start talking!"   │
      │                                │
      ▼  [Connection established!]     ▼
      │  [Data transfer begins]        │

SYN     = SYNchronize (initiate connection, share sequence number)
SYN-ACK = SYNchronize-ACKnowledge (server agrees + shares its seq number)
ACK     = ACKnowledge (client confirms server's sequence number)

WHY THREE STEPS?
  → 1 message would work for establishing connection from ONE side
  → But TCP needs BOTH sides to agree and sync sequence numbers
  → Minimum messages needed for bidirectional synchronisation = 3

AFTER HANDSHAKE: Data flows! Each packet is acknowledged (ACK).
                If no ACK received → RETRANSMIT the packet!

CONNECTION TERMINATION (4-way handshake):
  CLIENT → FIN → SERVER  (I'm done sending)
  SERVER → ACK → CLIENT  (OK, I received your FIN)
  SERVER → FIN → CLIENT  (I'm also done sending)
  CLIENT → ACK → SERVER  (OK, connection closed)

🎯 PYQ FACT: TCP handshake = SYN → SYN-ACK → ACK (exactly 3 steps)
🎯 PYQ FACT: TCP uses sequence numbers for ordering packets
```

#### Feature 3: Reliable Delivery
```
HOW TCP ENSURES RELIABILITY:
  
  1. ACKNOWLEDGMENT (ACK):
     Receiver sends ACK for every segment received.
     Sender knows segment arrived safely.
     
  2. RETRANSMISSION:
     If sender doesn't receive ACK within timeout period →
     It RETRANSMITS the lost/corrupted packet!
     "If you don't confirm, I'll send it again!"
     
  3. SEQUENCE NUMBERS:
     Every byte of data gets a sequence number.
     Receiver reassembles packets in CORRECT ORDER
     even if they arrive out of order!
     
  4. CHECKSUM:
     Each segment has a checksum for error detection.
     If checksum fails → packet DISCARDED and retransmitted.

ANALOGY: Like a teacher checking attendance:
  Teacher calls each student's name → student says "Present!"
  If no response → teacher calls again!
  TCP = Teacher; ACK = "Present!"
```

#### Feature 4: Flow Control
```
FLOW CONTROL — Prevents Fast Sender from Overwhelming Slow Receiver

PROBLEM:
  Server (fast network): Can send 1 Gbps
  Your mobile (slow network): Can only process 10 Mbps
  WITHOUT flow control: Server floods mobile → data LOST!

TCP SOLUTION: SLIDING WINDOW PROTOCOL
  Receiver tells sender: "I can accept X bytes at a time (my WINDOW SIZE)"
  Sender only sends X bytes before waiting for ACK
  As receiver processes data, it opens the window wider
  
ANALOGY:
  Water tap (sender) + bucket (receiver)
  Flow control = adjusting the tap to match bucket filling speed
  Open tap too fast → bucket overflows (data lost)!

🎯 PYQ FACT: Flow control in TCP = sliding window protocol
```

#### Feature 5: Congestion Control
```
CONGESTION CONTROL — Prevents Network Overload

PROBLEM: Multiple devices sending data simultaneously → network congestion
         (Like rush-hour traffic — everyone slows down!)

TCP SOLUTION: Slow Start algorithm
  → Begin with small window size
  → Gradually increase (exponentially at first, then linearly)
  → If packet loss detected → reduce window size drastically
  → Gradually increase again

This ensures TCP is "network-friendly" — backs off when network is congested.

🎯 PYQ FACT: TCP has BOTH flow control AND congestion control
```

### TCP Use Cases:
```
TCP USED FOR (when accuracy matters more than speed):
  → Web browsing (HTTP/HTTPS) — you need complete webpage
  → Email (SMTP, IMAP, POP3) — every word must arrive
  → File Transfer (FTP) — complete file without corruption
  → Secure Shell (SSH) — commands must arrive exactly
  → Online banking — transactions must be perfect
  → Database operations — no partial records allowed
```

---

## 🔷 SECTION 3: UDP — User Datagram Protocol

### Overview:
```
UDP = User Datagram Protocol
OSI LAYER:  Transport Layer (Layer 4)
TYPE:       Connection-LESS
RELIABILITY: UNRELIABLE (no guarantee)
ANALOGY:    POSTCARD — drop in mailbox, no tracking, no confirmation!
            Fast, cheap, but no guarantee it arrives!
```

### UDP's Key Features:
```
1. CONNECTIONLESS:
   → NO handshake before sending
   → Just fire data and forget!
   → No setup overhead → FASTER!

2. UNRELIABLE (by design — not a bug!):
   → No ACK (acknowledgment)
   → No retransmission if packet lost
   → No ordering guarantee (packets may arrive out of sequence)
   → Application must handle errors if needed

3. STATELESS:
   → Each datagram treated INDEPENDENTLY
   → No memory of previous packets
   → Simple, minimal processing

4. LOW OVERHEAD:
   → UDP header = only 8 bytes
   → TCP header = 20+ bytes
   → UDP = lighter, faster, less processing

5. NO FLOW CONTROL / CONGESTION CONTROL:
   → Sender sends at whatever speed it wants
   → No throttling back based on receiver capacity
   → Great for real-time applications where speed > accuracy

UDP DATAGRAM HEADER STRUCTURE (just 8 bytes!):
  ┌──────────────┬──────────────┐
  │  Source Port │  Dest Port   │  (2 bytes each)
  ├──────────────┼──────────────┤
  │   Length     │  Checksum    │  (2 bytes each)
  └──────────────┴──────────────┘
  That's it! Only 4 fields.
  TCP header has 10+ fields — much more complex.
```

### When to Use UDP (and Why):
```
UDP IS BETTER THAN TCP WHEN:

1. REAL-TIME COMMUNICATION:
   Video calls (Zoom, WhatsApp Video):
   → A slightly choppy call is better than a frozen, delayed call!
   → If a packet is lost → don't retransmit old audio (it's already outdated)
   → Just continue with new audio packets!

2. LIVE STREAMING (YouTube Live, Twitch):
   → Slight glitch OK; buffering/delay unacceptable
   → TCP retransmissions would PAUSE the stream to re-request lost packets
   → UDP → just skips lost data and keeps the stream flowing

3. ONLINE GAMING:
   → Position of player 0.1 seconds ago is USELESS information
   → Better to have current (slightly inaccurate) position than old (accurate) position
   → UDP's speed >> TCP's reliability for gaming

4. DNS LOOKUPS:
   → Simple request: "What is the IP of google.com?"
   → Simple response: "172.217.163.46"
   → If DNS packet lost → just ask again (client retries)
   → No need for TCP's heavy connection overhead for one-shot queries

5. IoT SENSORS:
   → Temperature sensor sending readings every second
   → If one reading lost → doesn't matter; next reading coming in 1 second!
   → UDP's lightweight nature perfect for small, frequent sensor data

🎯 PYQ FACT: UDP used for: streaming, gaming, VoIP, DNS, IoT, TFTP
🎯 PYQ FACT: UDP header = 8 bytes; TCP header = 20+ bytes
```

---

## 🔷 SECTION 4: TCP vs UDP — Master Comparison

```
┌──────────────────────────────┬───────────────────────────────┬───────────────────────────────┐
│          FEATURE             │             TCP               │             UDP               │
├──────────────────────────────┼───────────────────────────────┼───────────────────────────────┤
│ Full Name                    │ Transmission Control Protocol │ User Datagram Protocol        │
├──────────────────────────────┼───────────────────────────────┼───────────────────────────────┤
│ Connection Type              │ Connection-ORIENTED           │ Connection-LESS               │
│                              │ (establishes connection first)│ (just sends, no setup)        │
├──────────────────────────────┼───────────────────────────────┼───────────────────────────────┤
│ Reliability                  │ RELIABLE                      │ UNRELIABLE                    │
│                              │ (guaranteed delivery)         │ (best-effort delivery)        │
├──────────────────────────────┼───────────────────────────────┼───────────────────────────────┤
│ Acknowledgment               │ YES — ACK for every segment   │ NO — no acknowledgment        │
├──────────────────────────────┼───────────────────────────────┼───────────────────────────────┤
│ Retransmission               │ YES — resends lost packets    │ NO — lost packets stay lost   │
├──────────────────────────────┼───────────────────────────────┼───────────────────────────────┤
│ Ordering                     │ YES — guaranteed in-order     │ NO — may arrive out of order  │
│                              │ delivery                      │                               │
├──────────────────────────────┼───────────────────────────────┼───────────────────────────────┤
│ Speed                        │ SLOWER (overhead of ACKs,     │ FASTER (no overhead,          │
│                              │ retransmission, handshake)    │ no connection setup)          │
├──────────────────────────────┼───────────────────────────────┼───────────────────────────────┤
│ Header Size                  │ 20+ bytes (complex)           │ 8 bytes (minimal)             │
├──────────────────────────────┼───────────────────────────────┼───────────────────────────────┤
│ Flow Control                 │ YES (sliding window)          │ NO                            │
├──────────────────────────────┼───────────────────────────────┼───────────────────────────────┤
│ Congestion Control           │ YES (slow start algorithm)    │ NO                            │
├──────────────────────────────┼───────────────────────────────┼───────────────────────────────┤
│ Error Checking               │ YES (checksum + retransmit)   │ Basic checksum only           │
│                              │                               │ (no retransmission)           │
├──────────────────────────────┼───────────────────────────────┼───────────────────────────────┤
│ Protocol Data Unit           │ SEGMENT                       │ DATAGRAM                      │
├──────────────────────────────┼───────────────────────────────┼───────────────────────────────┤
│ Best For                     │ Accuracy over speed           │ Speed over accuracy           │
├──────────────────────────────┼───────────────────────────────┼───────────────────────────────┤
│ USE CASES                    │ HTTP/HTTPS (web browsing)     │ Video streaming (YouTube)     │
│                              │ FTP (file transfer)           │ Online gaming                 │
│                              │ SMTP/POP3/IMAP (email)        │ VoIP (Zoom, WhatsApp calls)   │
│                              │ SSH (remote access)           │ DNS lookups                   │
│                              │ Online banking                │ IoT sensor data               │
│                              │ Database queries              │ TFTP, SNMP                    │
├──────────────────────────────┼───────────────────────────────┼───────────────────────────────┤
│ Analogy                      │ REGISTERED MAIL               │ POSTCARD                      │
│                              │ (tracked, confirmed, reliable)│ (no tracking, no confirm)     │
└──────────────────────────────┴───────────────────────────────┴───────────────────────────────┘

🧠 MEMORY TRICK:
  TCP = "Takes Care Perfectly" (reliable, ordered, everything confirmed)
  UDP = "Ultra Direct & Primitive" (fast, no frills, connectionless)
```

---

## 🔷 SECTION 5: HTTP and HTTPS

### HTTP — HyperText Transfer Protocol:
```
HTTP = HyperText Transfer Protocol
PORT:  80
LAYER: Application Layer (both OSI Layer 7 and TCP/IP Application)
OVER:  TCP (reliable transport underneath)
USE:   Communication between WEB BROWSERS and WEB SERVERS

THE REQUEST-RESPONSE MODEL:

CLIENT (Browser)                    SERVER (Web Server)
      │                                     │
      │──── HTTP REQUEST ──────────────────▶│
      │  GET /index.html HTTP/1.1           │
      │  Host: www.example.com             │
      │  Accept: text/html                 │
      │                                     │
      │◀─── HTTP RESPONSE ─────────────────│
      │  HTTP/1.1 200 OK                   │
      │  Content-Type: text/html           │
      │  [HTML page content...]            │
      │                                     │
      ▼  [Browser renders webpage]          ▼

HTTP METHODS (verbs):
  GET    → Retrieve data (read a webpage)
  POST   → Send data to server (submit a form, login)
  PUT    → Update existing resource
  DELETE → Delete a resource
  HEAD   → Get headers only (no body)

HTTP STATUS CODES:
  2xx → SUCCESS  : 200 OK, 201 Created
  3xx → REDIRECT : 301 Moved Permanently, 302 Found
  4xx → CLIENT ERROR: 404 Not Found, 403 Forbidden, 400 Bad Request
  5xx → SERVER ERROR: 500 Internal Server Error, 503 Service Unavailable

STATELESS PROTOCOL:
  HTTP is STATELESS — each request is INDEPENDENT.
  The server has NO memory of previous requests!
  
  Problem: How does a shopping cart remember what you added?
  Solution: COOKIES (small data stored on browser) and SESSIONS
            These make HTTP "appear" stateful even though it isn't.

🎯 PYQ FACT: HTTP = stateless protocol (no memory between requests)
🎯 PYQ FACT: HTTP uses TCP on Port 80
🎯 PYQ FACT: 404 = Not Found (most famous HTTP error code!)
```

### HTTPS — HTTP Secure:
```
HTTPS = HTTP + SSL/TLS (Secure Sockets Layer / Transport Layer Security)
PORT:  443
DIFFERENCE FROM HTTP: ALL data is ENCRYPTED

HOW HTTPS WORKS:
  1. Browser connects to server over TCP
  2. SSL/TLS HANDSHAKE:
     → Server sends its DIGITAL CERTIFICATE (proves it's really the server)
     → Browser verifies certificate (issued by trusted CA — Certificate Authority)
     → Session encryption keys are exchanged
     → Encrypted channel established!
  3. HTTP requests/responses now travel ENCRYPTED
  
VISUAL INDICATOR: 
  🔒 Padlock icon in browser address bar = HTTPS active
  "https://" in URL = encrypted connection

WHY HTTPS MATTERS:
  → Prevents EAVESDROPPING (no one can read your data in transit)
  → Prevents TAMPERING (data can't be modified mid-transit)
  → AUTHENTICATION (confirms you're talking to real website, not fake)
  → Protects: passwords, credit card numbers, personal data

SSL vs TLS:
  SSL = Secure Sockets Layer (older, now deprecated)
  TLS = Transport Layer Security (newer, more secure version of SSL)
  Today: We say "SSL" colloquially but technically use TLS!

🎯 PYQ FACT: HTTPS = HTTP + SSL/TLS encryption on Port 443
🎯 PYQ FACT: HTTP = Port 80 (unencrypted); HTTPS = Port 443 (encrypted)
🎯 PYQ FACT: SSL operates at Presentation Layer (OSI Layer 6)
🚨 TRAP: "HTTPS uses a different transport protocol than HTTP" → FALSE!
         Both use TCP. HTTPS just adds SSL/TLS encryption layer.
```

---

## 🔷 SECTION 6: SMTP — Simple Mail Transfer Protocol

### What SMTP Does:
```
SMTP = Simple Mail Transfer Protocol
PORT:  25 (standard), 587 (submission), 465 (SMTPS — encrypted)
LAYER: Application Layer
USE:   SENDING emails (outgoing only!)
OVER:  TCP (reliable)

🚨 THE MOST COMMON SMTP PYQ TRAP:
   SMTP is for SENDING emails ONLY.
   To RECEIVE/READ emails → POP3 (Port 110) or IMAP (Port 143)!
```

### How Email Works — End to End:
```
THE COMPLETE EMAIL JOURNEY:
(From sender to receiver — multiple SMTP "hops")

YOU (Prag)                    SMTP Server          Recipient's
Gmail Account                  Gmail's Server       Mail Server
     │                              │                   │
     │──── SMTP (Port 587) ────────▶│                   │
     │  "Send this email to         │                   │
     │   friend@yahoo.com"          │                   │
     │                              │──── SMTP ────────▶│
     │                              │  Gmail delivers    │
     │                              │  to Yahoo's server│
     │                              │                   │
                                                Your friend's
                                                Mail Client
                                                         │
                                              POP3/IMAP ─┤
                                                         │
                                              Friend reads email!

STEP 1: Your Gmail app → Gmail's SMTP server (Port 587, using STARTTLS)
STEP 2: Gmail SMTP server → Recipient's mail server (Port 25, server-to-server)
STEP 3: Recipient's mail server stores email in their mailbox
STEP 4: Recipient's mail client → retrieves email via POP3 or IMAP
```

### SMTP Client vs SMTP Server — The Critical PYQ Concept:
```
🚨 PYQ CRITICAL CONCEPT: SMTP CLIENT vs SMTP SERVER

SMTP CLIENT (the sender role):
  → The device/application that INITIATES the SMTP connection
  → SENDS the email to an SMTP server
  → Examples:
     → Your Gmail app when you press "Send"
     → Gmail's server when it forwards to Yahoo's server
     → ANY server that initiates a connection to deliver mail
     → The "Mail Transfer Agent" acting as a client
  
SMTP SERVER (the receiver role):
  → The device that RECEIVES and processes the SMTP connection
  → Accepts incoming email for delivery
  → Examples:
     → Gmail's server receiving your email from your app
     → Yahoo's server receiving email from Gmail's server

KEY INSIGHT: The SAME MACHINE can be BOTH client and server!
  Gmail's server = SMTP SERVER when receiving your email
  Gmail's server = SMTP CLIENT when forwarding to Yahoo!

🎯 PYQ TRAP ANSWER: "SMTP client = the sending mail server"
   In server-to-server communication, the SENDING server acts as SMTP CLIENT.
   This is the most frequently tested SMTP fact!

EMAIL PROTOCOL SUMMARY:
  SMTP (Port 25/587)  → SEND email (push protocol)
  POP3 (Port 110)     → Download and delete from server (pull protocol)
  IMAP (Port 143)     → Read email on server, stays there, sync devices (pull protocol)

ANALOGY:
  SMTP = POST OFFICE collecting your outgoing letters
  POP3 = Postman delivering letters to your house (then removes from post office)
  IMAP = Reading your post box at the post office (letters stay there)
```

---

## 🔷 SECTION 7: Ping — Network Diagnostic Tool

### What is Ping?
```
PING = Packet Internet Groper
       (Some sources debate this expansion, but this is the standard accepted full form)

⚠️ PYQ TRAP: Some question options say "Ping = Packet Internet Generator" → WRONG!
             Standard = "Packet Internet Groper"
             Some modern sources say "ping" is just the onomatopoeic name (sound of sonar)
             but for exam purposes: Packet Internet Groper is the accepted expansion.

PROTOCOL USED: ICMP (Internet Control Message Protocol)
               NOT TCP, NOT UDP — it uses ICMP!
OSI LAYER:     Network Layer (Layer 3) — because ICMP is at Network Layer
PORT:          NO PORT NUMBER — ICMP doesn't use ports!

PURPOSE: Diagnostic tool to check if a REMOTE HOST is REACHABLE
         and to measure ROUND-TRIP TIME (latency)
```

### How Ping Works:
```
PING PROCESS:

YOUR COMPUTER                         TARGET HOST
     │                                     │
     │──── ICMP ECHO REQUEST ─────────────▶│
     │  "Are you there? Timestamp: T1"     │
     │                                     │
     │◀─── ICMP ECHO REPLY ───────────────│
     │  "Yes, I'm here! Timestamp: T2"    │
     │                                     │
     
ROUND-TRIP TIME (RTT) = T2 - T1
This is the time for packet to go TO the host and come BACK.

COMMAND: ping google.com
  (Windows) or ping -c 4 google.com (Linux/Mac, sends 4 packets)

SAMPLE OUTPUT:
  PING google.com (142.250.182.46): 56 data bytes
  64 bytes from 142.250.182.46: icmp_seq=1 ttl=117 time=12.4 ms
  64 bytes from 142.250.182.46: icmp_seq=2 ttl=117 time=11.8 ms
  64 bytes from 142.250.182.46: icmp_seq=3 ttl=117 time=13.1 ms
  64 bytes from 142.250.182.46: icmp_seq=4 ttl=117 time=12.0 ms
  
  --- google.com ping statistics ---
  4 packets transmitted, 4 received, 0% packet loss
  round-trip min/avg/max = 11.8/12.3/13.1 ms
```

### What Ping Measures:
```
PING MEASURES:
  1. REACHABILITY: Is the host alive and responding?
     → If no replies → host is down, unreachable, or blocking ICMP
     
  2. ROUND-TRIP TIME (RTT) / LATENCY:
     → Time in milliseconds (ms) for packet to go and return
     → Lower = better!
     → Gaming: <30ms = excellent, 30-60ms = good, >100ms = noticeable lag
     → Video call: <100ms barely noticeable; >300ms = annoying delay
     
  3. PACKET LOSS:
     → What % of sent ICMP packets did NOT receive a reply?
     → 0% packet loss = perfect connection
     → >5% packet loss = connection issues
     → 100% packet loss = host unreachable / completely down
     
  4. TTL (Time To Live):
     → Number of router hops a packet can travel before being discarded
     → Each router DECREMENTS TTL by 1
     → When TTL = 0 → packet dropped (prevents infinite routing loops)
     → From TTL value you can roughly identify the OS of the target!
       TTL starting at 128 → likely Windows
       TTL starting at 64  → likely Linux/Mac

PING IS USED FOR:
  → Testing internet connectivity ("Is my internet working?")
  → Diagnosing network problems (latency, packet loss)
  → Verifying a server is online
  → Measuring network performance (ISP quality check)
  → Network troubleshooting by admins

🎯 PYQ FACT: Ping uses ICMP protocol (NOT TCP, NOT UDP)
🎯 PYQ FACT: Ping measures RTT (Round-Trip Time) and Packet Loss
🎯 PYQ FACT: Ping full form = Packet Internet Groper
🎯 PYQ FACT: ICMP operates at Network Layer (Layer 3)
🚨 TRAP: "Ping uses UDP" → FALSE! Ping uses ICMP.
🚨 TRAP: "Ping full form = Packet Internet Generator" → FALSE! = Groper.
```

---

## 🔷 SECTION 8: MQTT — Message Queuing Telemetry Transport

### What is MQTT?
```
MQTT = Message Queuing Telemetry Transport
TYPE: Lightweight publish-subscribe messaging protocol
PORT: 1883 (unencrypted), 8883 (encrypted with SSL/TLS)
LAYER: Application Layer
CREATED BY: Andy Stanford-Clark (IBM) and Arlen Nipper — 1999
STANDARDISED BY: OASIS (Organization for the Advancement of Structured Information Standards)
OVER: TCP (uses TCP as transport)
USE:  IoT (Internet of Things), machine-to-machine (M2M) communication
```

### Why MQTT for IoT?
```
IoT DEVICE CONSTRAINTS:
  → Very low processing power (microcontrollers, not full computers)
  → Very limited memory (kilobytes, not gigabytes)
  → Slow, unreliable network connections (GSM, LoRa, Zigbee)
  → Battery-powered (must minimise data transmission)
  → Millions of devices sending small, frequent messages

MQTT IS PERFECT BECAUSE:
  → MINIMAL OVERHEAD: Smallest header (2 bytes minimum vs HTTP's 200+ bytes!)
  → LIGHTWEIGHT: Tiny bandwidth usage — ideal for low-power devices
  → PUBLISH-SUBSCRIBE MODEL: Decoupled communication — devices don't
    need to know about each other!
  → ASYNCHRONOUS: Devices don't wait for responses
  → SUPPORTS UNRELIABLE NETWORKS: Has built-in QoS levels!
```

### MQTT Architecture — Publish-Subscribe Model:
```
MQTT PUBLISH-SUBSCRIBE MODEL:

PUBLISHERS         MQTT BROKER          SUBSCRIBERS
(Sensors/Devices)  (Central Server)     (Apps/Devices)

Temperature ──── PUBLISH ──────────────▶ [BROKER]
Sensor           "temperature/room1"     │   │
"28°C"           "28°C"                 │   │
                                         │   └──── App Dashboard
                                         │          "Temperature Alert!"
                                         │
Motion ────── PUBLISH ──────────────────▶│
Sensor        "motion/door1"             └──── Security System
"Motion!"     "Motion detected"               "ALARM!"

HOW IT WORKS:
  1. PUBLISHERS: IoT devices that SEND data (sensors, actuators)
     → They PUBLISH messages to a TOPIC (like a channel name)
     → Example topic: "home/livingroom/temperature"
     
  2. BROKER: The central message router (like a Post Office)
     → Receives all published messages
     → Routes them to the right subscribers
     → Popular brokers: Eclipse Mosquitto, HiveMQ, AWS IoT Core
     
  3. SUBSCRIBERS: Apps/devices that RECEIVE data
     → They SUBSCRIBE to topics they're interested in
     → Example: Dashboard subscribes to "home/+/temperature" (all rooms!)
     
KEY FEATURE: Publishers and Subscribers DON'T KNOW about each other!
  → The temperature sensor doesn't know WHO is reading its data
  → The dashboard doesn't know WHICH specific sensors it gets data from
  → The BROKER handles all routing
  → This DECOUPLING makes IoT systems scalable and flexible!
```

### MQTT QoS Levels:
```
QoS = Quality of Service

MQTT has 3 QoS levels for different reliability needs:

QoS 0: "At Most Once" (Fire and Forget)
  → Like UDP — no acknowledgment, message may be lost
  → Fastest, lowest overhead
  → Use: Sensor data where occasional loss is OK (temperature every second)

QoS 1: "At Least Once"
  → Message delivered at least once (may be duplicates if retry triggered)
  → Receiver sends ACK; if no ACK → sender retransmits
  → Use: Important events where loss unacceptable but duplicates OK

QoS 2: "Exactly Once"
  → Message delivered EXACTLY ONCE — no loss, no duplicates
  → Uses 4-step handshake
  → Slowest, most overhead
  → Use: Financial transactions, critical commands (open/close valve)

🎯 PYQ FACT: MQTT = lightweight protocol for IoT (Internet of Things)
🎯 PYQ FACT: MQTT uses publish-subscribe model (not request-response like HTTP)
🎯 PYQ FACT: MQTT port = 1883 (unencrypted) and 8883 (encrypted)
🎯 PYQ FACT: MQTT = designed by IBM for oil pipeline monitoring (original use!)
```

### MQTT vs HTTP:
```
┌───────────────────┬──────────────────────────┬──────────────────────────┐
│     FEATURE       │          MQTT            │          HTTP            │
├───────────────────┼──────────────────────────┼──────────────────────────┤
│ Model             │ Publish-Subscribe        │ Request-Response         │
├───────────────────┼──────────────────────────┼──────────────────────────┤
│ Overhead          │ Very LOW (2 byte header) │ HIGH (200+ byte headers) │
├───────────────────┼──────────────────────────┼──────────────────────────┤
│ Use Case          │ IoT, M2M                 │ Web browsing             │
├───────────────────┼──────────────────────────┼──────────────────────────┤
│ Connection        │ Persistent (stays open)  │ Usually stateless/close  │
├───────────────────┼──────────────────────────┼──────────────────────────┤
│ Best For          │ Small, frequent messages │ Request-response cycles  │
└───────────────────┴──────────────────────────┴──────────────────────────┘
```

---

## 🔷 SECTION 9: Socket — The Endpoint of Communication

### What is a Socket?
```
SOCKET = An endpoint for sending and receiving data across a network.
         The combination of an IP address + Port Number.

> A socket is like a TELEPHONE HANDSET:
  → The PHONE NUMBER (IP address) tells you which building to call
  → The EXTENSION NUMBER (Port) tells you which person in the building
  → Together (IP:Port) = SOCKET = the exact endpoint

FORMAL DEFINITION:
  Socket = {IP Address : Port Number}
  
EXAMPLE:
  Server socket: 192.168.1.100 : 80  (web server on port 80)
  Client socket: 10.0.0.5 : 54321   (browser using random port 54321)
  
  These two sockets form a SOCKET PAIR = one complete connection!
```

### Socket in Client-Server Communication:
```
CLIENT-SERVER SOCKET COMMUNICATION:

SERVER SIDE:                    CLIENT SIDE:
  1. Create socket                1. Create socket
  2. BIND to IP:Port              2. CONNECT to server's IP:Port
     (192.168.1.100:80)              (192.168.1.100:80)
  3. LISTEN for connections       3. (TCP 3-way handshake happens)
  4. ACCEPT incoming connection   4. SEND request data
  5. RECEIVE data                 5. RECEIVE response
  6. SEND response                6. CLOSE socket
  7. CLOSE socket

VISUAL:

CLIENT (Browser)                 SERVER (Web Server)
  ┌──────────────┐                ┌──────────────────┐
  │ Socket:      │                │ Socket:          │
  │ 10.0.0.5:    │                │ 192.168.1.100:80 │
  │   54321      │                │ (listening for   │
  └──────┬───────┘                │  connections)    │
         │  TCP Connection        └────────┬─────────┘
         └────────────────────────────────┘
                 Data Exchange!

TYPES OF SOCKETS:
  STREAM SOCKETS (SOCK_STREAM):
  → Uses TCP
  → Reliable, ordered, bidirectional
  → Used for web browsers, email clients, SSH

  DATAGRAM SOCKETS (SOCK_DGRAM):
  → Uses UDP
  → Unreliable, unordered, connectionless
  → Used for DNS, video streaming, gaming

  RAW SOCKETS (SOCK_RAW):
  → Direct access to lower-level protocols
  → Used for network tools like ping (ICMP), network scanners

SOCKET PROGRAMMING CONCEPT:
  Every network application you use is built on sockets!
  → Browser = socket client connecting to web server sockets
  → WhatsApp = socket communication for real-time messaging
  → Online games = sockets for player position updates
  → Servers = constantly listening on specific sockets for clients

🎯 PYQ FACT: Socket = IP address + Port number (the combination)
🎯 PYQ FACT: Socket is the endpoint of a two-way communication channel
🎯 PYQ FACT: Stream socket uses TCP; Datagram socket uses UDP
🎯 PYQ FACT: Server must BIND and LISTEN; Client must CONNECT
```

---

## 🔷 SECTION 10: Client-Server Model

### Overview:
```
CLIENT-SERVER MODEL:
  The fundamental architecture of almost all network applications.
  
  CLIENT:     Device/software that REQUESTS a service
              (your browser, email app, WhatsApp)
              
  SERVER:     Device/software that PROVIDES a service
              (Google's web server, Gmail's mail server, WhatsApp's message server)

PROCESS:
  1. Client sends a REQUEST to the server
  2. Server processes the request
  3. Server sends a RESPONSE back to the client

EXAMPLES:
  Browser (client) → requests webpage → Web server (server)
  Email app (client) → sends email → SMTP server (server)
  WhatsApp (client) → sends message → WhatsApp server (server)
  ATM (client) → requests balance → Bank server (server)

DEDICATED SERVERS (always-on):
  Servers are typically:
  → Always running (24/7 availability)
  → Powerful hardware (handle thousands of simultaneous clients)
  → Have static IP addresses (clients need to find them!)
  → Located in DATA CENTRES (climate controlled, redundant power)

PEER-TO-PEER (P2P) — Alternative to Client-Server:
  In P2P: every device is BOTH client AND server!
  Examples: BitTorrent, blockchain networks
  
🎯 PYQ FACT: Client initiates request; Server responds to request
🎯 PYQ FACT: Servers have static IPs; clients can have dynamic IPs
```

---

## 🔷 SECTION 11: PYQ Traps — Network Protocols

```
🚨 TRAP 1: "TCP is faster than UDP" → FALSE!
   UDP is FASTER (no handshake, no ACK, no retransmission overhead).
   TCP is RELIABLE but SLOWER.

🚨 TRAP 2: "SMTP is used to receive emails" → FALSE!
   SMTP = SENDING emails ONLY.
   Receiving = POP3 (Port 110) or IMAP (Port 143).

🚨 TRAP 3: "Ping uses UDP" → FALSE!
   Ping uses ICMP (Internet Control Message Protocol), NOT UDP or TCP.

🚨 TRAP 4: "Ping full form = Packet Internet Generator" → FALSE!
   Ping = Packet Internet Groper.

🚨 TRAP 5: "HTTP is stateful — it remembers previous requests" → FALSE!
   HTTP is STATELESS — every request is independent.
   Cookies/Sessions are used to simulate state.

🚨 TRAP 6: "HTTPS uses a different transport layer than HTTP" → FALSE!
   Both HTTP and HTTPS use TCP. HTTPS just adds SSL/TLS encryption.

🚨 TRAP 7: "MQTT is used for web browsing" → FALSE!
   MQTT = for IoT devices (lightweight, publish-subscribe).
   HTTP = for web browsing (request-response).

🚨 TRAP 8: "Socket = just an IP address" → FALSE!
   Socket = IP address + Port number (the combination of both).

🚨 TRAP 9: "TCP uses 4-way handshake to establish connection" → FALSE!
   TCP ESTABLISHMENT = 3-way handshake (SYN, SYN-ACK, ACK).
   TCP TERMINATION = 4-way handshake (FIN, ACK, FIN, ACK).

🚨 TRAP 10: "Ping measures bandwidth/speed of internet connection" → FALSE!
   Ping measures LATENCY (round-trip time) and PACKET LOSS.
   Bandwidth measurement requires speed test tools (like Speedtest.net).

🚨 TRAP 11: "UDP segments" → WRONG TERMINOLOGY!
   TCP → SEGMENTS. UDP → DATAGRAMS. Use correct PDU names!

🚨 TRAP 12: "SMTP client = the device sending from a desktop app"
   In SERVER-TO-SERVER context, the SENDING server is the SMTP CLIENT.
   This is the most commonly tested nuance.
```

---

# PART 2: GENERAL STUDIES
## 🏛️ Current Affairs — Important Government Schemes of India

---

## 🔷 SECTION 1: Digital India Programme

```
SCHEME: Digital India
LAUNCHED: July 1, 2015
BY: Ministry of Electronics and Information Technology (MeitY)
    (under Prime Minister Modi's government)
TAGLINE: "Power to Empower"

PURPOSE: Transform India into a digitally empowered society and 
         knowledge economy by:
  → Providing digital infrastructure as a utility to every citizen
  → Digital governance and services on demand
  → Digital empowerment of citizens

THREE KEY PILLARS:
  1. Digital Infrastructure for Every Citizen:
     → High-speed internet (BharatNet for rural areas)
     → Common Service Centres (CSCs) in every village
     → Cyber-safe digital space
     
  2. Governance and Services on Demand:
     → E-governance — services digitally available
     → Online portals for government services
     → Mobile-first approach (mGovernance)
     → Cloud computing (MeghRaj — Government Cloud)
     
  3. Digital Literacy:
     → PMGDISHA (Pradhan Mantri Gramin Digital Saksharta Abhiyan)
     → Train rural citizens in basic digital skills

KEY INITIATIVES UNDER DIGITAL INDIA:
  → BharatNet: High-speed optical fiber to gram panchayats
  → DigiLocker: Digital document storage (avoid carrying physical docs)
  → UMANG: Unified Mobile Application for New-age Governance
  → e-Hospital: Online OPD appointment, blood availability
  → BHIM: Bharat Interface for Money (UPI payments)
  → Aadhaar: Biometric digital identity for all citizens
  → MyGov: Citizen engagement platform

🎯 PYQ FACT: Digital India launched = July 1, 2015
🎯 PYQ FACT: Digital India Ministry = MeitY (not IT Ministry alone)
🎯 PYQ FACT: BharatNet = rural broadband under Digital India
🎯 PYQ FACT: DigiLocker = digital document wallet under Digital India
```

---

## 🔷 SECTION 2: Ayushman Bharat — PM-JAY

```
SCHEME: Ayushman Bharat - Pradhan Mantri Jan Arogya Yojana (PM-JAY)
LAUNCHED: September 23, 2018
           (September 23 chosen because it's Pandit Deendayal Upadhyay's birth anniversary)
BY: Ministry of Health and Family Welfare
TAGLINE: "AB-PMJAY" | Also called "Modicare" (informal)

PURPOSE: Provide health insurance coverage to poor and vulnerable families
         → World's LARGEST government-funded health assurance scheme!

KEY FEATURES:
  → Health cover of ₹5 LAKH per family per year
  → Covers SECONDARY and TERTIARY hospitalisation
  → Covers 10.74 crore poor and vulnerable families (approximately 50 crore individuals)
  → CASHLESS treatment at empanelled hospitals (public and private)
  → NO restriction on family size, age, or gender
  → Covers pre-existing conditions from day one
  → Portability — can use benefits across India!

WHO BENEFITS:
  → Families listed in SECC 2011 (Socio-Economic Caste Census)
  → Construction workers, rag pickers, domestic workers, beggars,
    sanitation workers, tribal families, and other vulnerable groups

TWO COMPONENTS OF AYUSHMAN BHARAT:
  1. PM-JAY (Pradhan Mantri Jan Arogya Yojana): Health insurance (₹5 lakh)
  2. Health and Wellness Centres (HWCs): Primary health care at grassroots
     → 1.5 lakh HWCs planned across India
     → Near-to-home healthcare for common ailments

IMPLEMENTING BODY: NHA (National Health Authority)

🎯 PYQ FACT: PM-JAY coverage = ₹5 lakh per family per year
🎯 PYQ FACT: Launched = September 23, 2018
🎯 PYQ FACT: World's LARGEST government-funded health scheme
🎯 PYQ FACT: Beneficiaries = ~50 crore individuals (10.74 crore families)
🎯 PYQ FACT: Ministry = Ministry of Health and Family Welfare
🎯 PYQ FACT: Implementing body = NHA (National Health Authority)
```

---

## 🔷 SECTION 3: Startup India

```
SCHEME: Startup India
LAUNCHED: January 16, 2016
BY: Department for Promotion of Industry and Internal Trade (DPIIT)
    Ministry of Commerce and Industry
TAGLINE: "Start Up India, Stand Up India"

PURPOSE: Build a strong ecosystem for nurturing innovation and startups
         → Create employment
         → Promote sustainable economic growth
         → Make India a hub for innovation and entrepreneurship

KEY FEATURES / BENEFITS FOR STARTUPS:
  → 3-year TAX EXEMPTION (income tax free for first 3 years)
  → SELF-CERTIFICATION: Simplify compliance (labour + environment laws)
  → FAST EXIT: Wind up in 90 days (vs years before!)
  → FUND OF FUNDS: ₹10,000 crore Fund of Funds for investment in startups
  → IPR (Intellectual Property Rights) support: Fast-track patent filing
  → STARTUP INDIA HUB: Single platform for all startup needs
  → Government PROCUREMENT: Startups can sell directly to government
  → REGULATORY SANDBOX: Test innovations without full regulatory burden

STARTUP DEFINITION (as per DPIIT):
  → Incorporated/registered in India within 10 years
  → Turnover not exceeding ₹100 crore in any year
  → Working towards INNOVATION, development or improvement of products/services
  → NOT a subsidiary or spinoff of an existing large company

INDIA'S STARTUP ECOSYSTEM:
  → India = 3rd largest startup ecosystem globally (after USA and China)
  → 100+ UNICORNS (startups valued $1 billion+) as of 2023
  → Examples: Byju's, OYO, Swiggy, Zepto, Meesho, Razorpay

🎯 PYQ FACT: Startup India launched = January 16, 2016
🎯 PYQ FACT: Ministry = DPIIT under Commerce and Industry Ministry
🎯 PYQ FACT: Tax exemption = 3 years
🎯 PYQ FACT: Fund of Funds = ₹10,000 crore
🎯 PYQ FACT: India = 3rd largest startup ecosystem globally
```

---

## 🔷 SECTION 4: Make in India

```
SCHEME: Make in India
LAUNCHED: September 25, 2014 (one of Modi govt's FIRST major initiatives!)
BY: DPIIT (Department for Promotion of Industry and Internal Trade)
    Ministry of Commerce and Industry
SYMBOL: Lion made of GEARS (marching lion)
TAGLINE: "Make in India — Manufactured in India, Made for the World"

PURPOSE: Transform India into a global manufacturing hub
  → Increase manufacturing sector's contribution to GDP (target: 25%)
  → Create 100 million jobs in manufacturing by 2022
  → Attract Foreign Direct Investment (FDI)
  → Build world-class infrastructure

FOCUS SECTORS (25 sectors):
  Key ones: Defence manufacturing, Railways, Automobiles, Aviation,
  Pharmaceuticals, IT & Electronics, Food processing, Textiles,
  Renewable energy, Construction, Chemical & Petrochemicals

KEY ACHIEVEMENTS:
  → India became top FDI destination in various years
  → Record FDI inflows post-2014
  → Mobile phone manufacturing: India went from importing 80% to manufacturing 97%
    (Samsung, Apple, Xiaomi now manufacture in India)
  → PLI (Production Linked Incentive) scheme supports Make in India goals

🎯 PYQ FACT: Make in India launched = September 25, 2014
🎯 PYQ FACT: Symbol = Lion made of gears (marching lion!)
🎯 PYQ FACT: Ministry = DPIIT (same as Startup India)
🎯 PYQ FACT: Target manufacturing GDP share = 25%
```

---

## 🔷 SECTION 5: PM Kisan Samman Nidhi

```
SCHEME: Pradhan Mantri Kisan Samman Nidhi (PM-KISAN)
LAUNCHED: December 1, 2018 (announced); February 24, 2019 (formally launched)
BY: Ministry of Agriculture and Farmers' Welfare
PURPOSE: Provide income support to all landholding farmers

KEY FEATURES:
  → ₹6,000 per year income support to eligible farmer families
  → Paid in 3 equal INSTALMENTS of ₹2,000 each (every 4 months)
  → Directly transferred to bank accounts via DBT (Direct Benefit Transfer)
  → Covers all farmer families (small, marginal, large landholders)

ELIGIBILITY (post October 2019 revision):
  → All landholding farmer families (no income ceiling for most)
  → EXCLUSIONS: Income tax payers, government employees, professionals
    (doctors, lawyers, CAs), former/current MPs/MLAs/Ministers

BIHAR SPECIFIC:
  → Bihar has one of the highest PM-KISAN beneficiary counts
  → Farmers access benefits through Common Service Centres (CSC)

🎯 PYQ FACT: PM-KISAN = ₹6,000/year in 3 instalments of ₹2,000
🎯 PYQ FACT: Ministry = Agriculture and Farmers' Welfare
🎯 PYQ FACT: Launched formally = February 24, 2019
🎯 PYQ FACT: Direct Benefit Transfer (DBT) used for payments
```

---

## 🔷 SECTION 6: Swachh Bharat Mission

```
SCHEME: Swachh Bharat Mission (Clean India Mission)
LAUNCHED: October 2, 2014 (Gandhi Jayanti — symbolic!)
BY: Ministry of Jal Shakti (for rural); Ministry of Housing & Urban Affairs (urban)
PURPOSE: Achieve Open Defecation Free (ODF) India and improve solid waste management

TWO COMPONENTS:
  SBM-Gramin (Rural): Build household toilets, community toilets, eliminate open defecation
  SBM-Urban:          Solid waste management in cities, public toilets

KEY ACHIEVEMENT:
  → India declared ODF (Open Defecation Free) on October 2, 2019 (Gandhi Jayanti 2019)
  → 10+ crore toilets constructed under SBM
  → UN credited India for eliminating open defecation (near elimination)

SBM PHASE 2:
  → Launched 2020-2021 to sustain ODF status
  → Focus: ODF+, ODF++, solid/liquid waste management, plastic waste

🎯 PYQ FACT: Launched = October 2, 2014 (Gandhi Jayanti — 150th birth anniversary of Gandhi)
🎯 PYQ FACT: India declared ODF on = October 2, 2019
🎯 PYQ FACT: Target ambassador: Narendra Modi launched it at Rajpath
🎯 PYQ FACT: Rural = Ministry of Jal Shakti; Urban = Ministry of Housing
```

---

## 🔷 SECTION 7: Other Important Schemes — Quick Reference

```
┌────────────────────────────────┬──────────────┬─────────────────────────────────────────────────┐
│         SCHEME                 │   LAUNCHED   │              KEY PURPOSE / MINISTRY             │
├────────────────────────────────┼──────────────┼─────────────────────────────────────────────────┤
│ PMAY (PM Awas Yojana)          │  June 2015   │ "Housing for All by 2022" — affordable housing  │
│                                │              │ Ministry of Housing & Urban Affairs             │
├────────────────────────────────┼──────────────┼─────────────────────────────────────────────────┤
│ Jan Dhan Yojana                │ Aug 28, 2014 │ Financial inclusion — bank account for every    │
│                                │              │ household; DBT, insurance, overdraft facility   │
│                                │              │ Ministry of Finance                             │
├────────────────────────────────┼──────────────┼─────────────────────────────────────────────────┤
│ Beti Bachao Beti Padhao        │  Jan 2015    │ Address declining Child Sex Ratio; girls'       │
│                                │              │ education and welfare                           │
│                                │              │ Ministries: WCD + Health + Education            │
├────────────────────────────────┼──────────────┼─────────────────────────────────────────────────┤
│ Skill India / PMKVY            │  July 2015   │ Skill 40 crore Indians by 2022                 │
│ (PM Kaushal Vikas Yojana)      │              │ Ministry of Skill Development and               │
│                                │              │ Entrepreneurship                                │
├────────────────────────────────┼──────────────┼─────────────────────────────────────────────────┤
│ Pradhan Mantri Ujjwala Yojana  │  May 2016    │ Free LPG connections to BPL women              │
│ (PMUY)                        │              │ "Blue Flame, Not Smoke Flame"                   │
│                                │              │ Ministry of Petroleum and Natural Gas           │
├────────────────────────────────┼──────────────┼─────────────────────────────────────────────────┤
│ Jal Jeevan Mission             │ Aug 15, 2019 │ Tap water ("Har Ghar Jal") to every rural       │
│                                │              │ household by 2024                               │
│                                │              │ Ministry of Jal Shakti                          │
├────────────────────────────────┼──────────────┼─────────────────────────────────────────────────┤
│ PM Garib Kalyan Yojana         │  March 2020  │ COVID-19 economic relief — free ration,         │
│ (PMGKY)                        │              │ cash transfers for poor                         │
│                                │              │ Ministry of Finance                             │
├────────────────────────────────┼──────────────┼─────────────────────────────────────────────────┤
│ MGNREGS / MNREGA               │  Feb 2006    │ 100 days guaranteed rural employment            │
│                                │              │ Ministry of Rural Development                   │
├────────────────────────────────┼──────────────┼─────────────────────────────────────────────────┤
│ Atal Mission for Rejuvenation  │  June 2015   │ Urban renewal — basic services in 500 cities   │
│ and Urban Transformation(AMRUT)│              │ Ministry of Housing & Urban Affairs             │
├────────────────────────────────┼──────────────┼─────────────────────────────────────────────────┤
│ Smart Cities Mission           │  June 2015   │ Develop 100 smart cities with tech-driven       │
│                                │              │ infrastructure and citizen services              │
│                                │              │ Ministry of Housing & Urban Affairs             │
├────────────────────────────────┼──────────────┼─────────────────────────────────────────────────┤
│ PM Surya Ghar Muft             │  Feb 2024    │ Rooftop solar panels — 300 units free           │
│ Bijli Yojana                   │              │ electricity/month to 1 crore households         │
│                                │              │ Ministry of New & Renewable Energy              │
└────────────────────────────────┴──────────────┴─────────────────────────────────────────────────┘
```

---

## 🔷 SECTION 8: Bihar-Specific Government Schemes

```
BIHAR-SPECIFIC SCHEMES (Important for BPSC!):

1. MUKHYAMANTRI CYCLE YOJANA (now part of various education schemes):
   → Free cycles to girls in Class 9 (to improve school attendance)
   → Bihar's flagship education scheme

2. MUKHYAMANTRI KANYA UTTHAN YOJANA:
   → Financial assistance for girl child from birth to graduation
   → Birth of girl child → government deposited money
   → Incentive at Class 10, 12 passes, graduation
   → ₹50,000 total at graduation (for unmarried graduates)

3. MUKHYAMANTRI ALPSANKHYAK ROJAR LOAN YOJANA:
   → Loan for minority community entrepreneurs in Bihar

4. STUDENT CREDIT CARD SCHEME (Bihar):
   → Education loan of up to ₹4 lakh for higher education
   → Simple process, no collateral
   → Helps economically weaker students access higher education

5. SAAT NISHCHAY (Seven Resolves):
   → Bihar government's 7 commitments to development
   → Includes: Electricity to all homes, roads, clean water,
     skill development, girl empowerment, jobs for youth,
     toilets in all homes

🎯 PYQ FACT: Bihar's Kanya Utthan Yojana = financial support from birth to graduation
🎯 PYQ FACT: Student Credit Card (Bihar) = ₹4 lakh education loan
🎯 PYQ FACT: Saat Nishchay = Bihar government's 7-point development agenda
```

---

## 🔷 SECTION 9: Government Scheme — PYQ Traps

```
🚨 TRAP 1: "Jan Dhan Yojana was launched by the Finance Minister" → MISLEADING.
   PM Modi launched it directly as a national movement (Aug 28, 2014).

🚨 TRAP 2: "Ayushman Bharat covers only BPL families" → INCOMPLETE.
   It covers ~50 crore individuals from bottom 40% of population,
   based on SECC data — not strictly "BPL" classification.

🚨 TRAP 3: "Digital India was launched in 2016" → FALSE!
   Digital India launched = July 1, 2015.

🚨 TRAP 4: "Swachh Bharat was launched on Gandhi's death anniversary" → FALSE!
   Launched on Gandhi's BIRTH anniversary = October 2, 2014.

🚨 TRAP 5: "Make in India focuses only on food processing" → FALSE!
   Make in India covers 25 sectors including defence, IT, automobiles, etc.

🚨 TRAP 6: "PM-KISAN pays ₹6,000 in 6 equal instalments" → FALSE!
   PM-KISAN = ₹6,000 in 3 instalments of ₹2,000 each.

🚨 TRAP 7: "Startup India = Ministry of IT" → FALSE!
   Startup India and Make in India = DPIIT (Ministry of Commerce & Industry).

🚨 TRAP 8: "Jal Jeevan Mission = clean river water" → PARTIALLY WRONG!
   JJM = tap water (piped drinking water) to every rural HOUSEHOLD.
   River cleaning = Namami Gange Programme.

🚨 TRAP 9: "PMUY provides electricity to BPL families" → FALSE!
   PMUY (Ujjwala) = FREE LPG CONNECTIONS to BPL women.
   Electricity to all = Saubhagya Scheme (2017).

🚨 TRAP 10: "Beti Bachao Beti Padhao = Ministry of Women & Child Development only" → FALSE!
   It's a joint scheme of 3 ministries: WCD + Health + Education.
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: TCP, UDP, HTTP/HTTPS, SMTP, Ping, MQTT, Socket, Client-Server

---

**Q1.** A network protocol is best defined as:
(A) A physical cable connecting two computers
(B) A set of rules and conventions governing data transmission between devices
(C) A software program for browsing the internet
(D) More than one of the above
(E) None of the above

---

**Q2.** TCP (Transmission Control Protocol) is classified as:
(A) Connectionless and unreliable
(B) Connection-oriented and reliable
(C) Connectionless and reliable
(D) More than one of the above
(E) None of the above

---

**Q3.** The TCP three-way handshake occurs in which CORRECT sequence?
(A) ACK → SYN → SYN-ACK
(B) SYN → ACK → SYN-ACK
(C) SYN → SYN-ACK → ACK
(D) More than one of the above
(E) None of the above

---

**Q4.** TCP's FLOW CONTROL mechanism prevents:
(A) Hackers from intercepting data in transit
(B) A fast sender from overwhelming a slow receiver with too much data
(C) Duplicate IP addresses on the same network
(D) More than one of the above
(E) None of the above

---

**Q5.** UDP (User Datagram Protocol) is preferred over TCP when:
(A) Every byte of data must arrive in perfect sequence
(B) High reliability is needed at the cost of speed
(C) Speed is critical and occasional data loss is acceptable (e.g., video streaming)
(D) More than one of the above
(E) None of the above

---

**Q6.** The Protocol Data Unit (PDU) for UDP is called a:
(A) Segment
(B) Frame
(C) Datagram
(D) More than one of the above
(E) None of the above

---

**Q7.** HTTP (HyperText Transfer Protocol) is described as a STATELESS protocol. This means:
(A) HTTP maintains a permanent connection between browser and server
(B) Each HTTP request is independent — the server has no memory of previous requests
(C) HTTP cannot handle state changes in a web application
(D) More than one of the above
(E) None of the above

---

**Q8.** HTTPS differs from HTTP in that:
(A) HTTPS uses UDP while HTTP uses TCP
(B) HTTPS adds SSL/TLS encryption over HTTP (same TCP transport)
(C) HTTPS works only for downloading files, not web browsing
(D) More than one of the above
(E) None of the above

---

**Q9.** HTTP uses which Port Number?
(A) 443
(B) 25
(C) 80
(D) More than one of the above
(E) None of the above

---

**Q10.** HTTPS uses which Port Number?
(A) 80
(B) 443
(C) 110
(D) More than one of the above
(E) None of the above

---

**Q11.** SMTP (Simple Mail Transfer Protocol) is used for:
(A) Receiving and downloading emails to a client device
(B) Reading emails stored on a mail server
(C) Sending emails from client to mail server and between mail servers
(D) More than one of the above
(E) None of the above

---

**Q12.** In server-to-server email delivery, Gmail's server sends an email to Yahoo's server. In this scenario, Gmail's server is acting as:
(A) An SMTP Server (receiving emails)
(B) A POP3 Client (downloading emails)
(C) An SMTP Client (initiating the SMTP connection to deliver mail)
(D) More than one of the above
(E) None of the above

---

**Q13.** The FULL FORM of "Ping" is:
(A) Packet Internet Generator
(B) Packet Internet Groper
(C) Protocol Internet Gateway
(D) More than one of the above
(E) None of the above

---

**Q14.** The Ping command uses which network protocol to operate?
(A) TCP (Transmission Control Protocol)
(B) UDP (User Datagram Protocol)
(C) ICMP (Internet Control Message Protocol)
(D) More than one of the above
(E) None of the above

---

**Q15.** Ping primarily measures which TWO network parameters?
(A) Bandwidth and file transfer speed
(B) Round-trip time (latency) and packet loss
(C) IP address and MAC address of a host
(D) More than one of the above
(E) None of the above

---

**Q16.** MQTT (Message Queuing Telemetry Transport) was designed primarily for:
(A) High-bandwidth video streaming between powerful servers
(B) Secure file transfer between enterprise computers
(C) IoT (Internet of Things) devices — lightweight, low-bandwidth, low-power communication
(D) More than one of the above
(E) None of the above

---

**Q17.** MQTT uses which communication model?
(A) Request-Response model (like HTTP)
(B) Publish-Subscribe model (publisher → broker → subscriber)
(C) Point-to-Point direct model (no intermediary)
(D) More than one of the above
(E) None of the above

---

**Q18.** The central server in an MQTT architecture that routes messages between publishers and subscribers is called:
(A) Router
(B) Broker
(C) Gateway
(D) More than one of the above
(E) None of the above

---

**Q19.** MQTT operates on which default port number?
(A) 80
(B) 25
(C) 1883
(D) More than one of the above
(E) None of the above

---

**Q20.** A "Socket" in networking is defined as:
(A) A physical hardware port on a computer (like a USB or Ethernet port)
(B) The combination of an IP address and a Port number — an endpoint for communication
(C) A type of network cable connector
(D) More than one of the above
(E) None of the above

---

**Q21.** In the client-server model using sockets, which sequence does the SERVER follow?
(A) Connect → Send → Receive → Close
(B) Create socket → Connect to client → Send data → Close
(C) Create socket → Bind to port → Listen → Accept connection → Receive/Send → Close
(D) More than one of the above
(E) None of the above

---

**Q22.** A Stream Socket (SOCK_STREAM) uses which transport protocol?
(A) UDP
(B) ICMP
(C) TCP
(D) More than one of the above
(E) None of the above

---

**Q23.** Which HTTP status code indicates "Page Not Found"?
(A) 200
(B) 500
(C) 404
(D) More than one of the above
(E) None of the above

---

**Q24.** Consider the following protocol-use case pairings:
I.   TCP → Online banking (reliable, ordered delivery needed)
II.  UDP → Video streaming (speed preferred over guaranteed delivery)
III. SMTP → Receiving emails from a mail server to your device
IV.  ICMP → Ping command to test network connectivity

Which pairings are CORRECTLY matched?
(A) I, II, and IV only
(B) I, II, III, and IV all correct
(C) I and II only
(D) More than one of the above
(E) None of the above

---

**Q25.** Which statement about TCP vs UDP is CORRECT?
(A) TCP is faster than UDP because it checks for errors
(B) UDP is reliable and TCP is unreliable
(C) TCP is reliable but slower; UDP is faster but unreliable — choice depends on application needs
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: Government Schemes — Digital India, Ayushman Bharat, Startup India, others

---

**Q26.** "Digital India" programme was launched on:
(A) August 15, 2014
(B) July 1, 2015
(C) January 26, 2016
(D) More than one of the above
(E) None of the above

---

**Q27.** Digital India is implemented under which ministry?
(A) Ministry of Science and Technology
(B) Ministry of Electronics and Information Technology (MeitY)
(C) Ministry of Finance
(D) More than one of the above
(E) None of the above

---

**Q28.** "BharatNet" is an initiative under Digital India aimed at:
(A) Providing free smartphones to farmers
(B) Connecting gram panchayats with high-speed optical fiber internet
(C) Setting up IT parks in Tier-2 cities
(D) More than one of the above
(E) None of the above

---

**Q29.** Ayushman Bharat — PM-JAY was launched on:
(A) January 1, 2018
(B) August 15, 2018
(C) September 23, 2018
(D) More than one of the above
(E) None of the above

---

**Q30.** Under Ayushman Bharat (PM-JAY), the health insurance coverage per family per year is:
(A) ₹1 lakh
(B) ₹2 lakh
(C) ₹5 lakh
(D) More than one of the above
(E) None of the above

---

**Q31.** The implementing body for Ayushman Bharat — PM-JAY is:
(A) NITI Aayog
(B) National Health Authority (NHA)
(C) AIIMS
(D) More than one of the above
(E) None of the above

---

**Q32.** "Startup India" initiative was launched on:
(A) January 16, 2016
(B) September 25, 2014
(C) July 1, 2015
(D) More than one of the above
(E) None of the above

---

**Q33.** Which ministry governs the "Startup India" programme?
(A) Ministry of Finance
(B) Ministry of Electronics and Information Technology
(C) DPIIT — Department for Promotion of Industry and Internal Trade (Ministry of Commerce)
(D) More than one of the above
(E) None of the above

---

**Q34.** Under Startup India, eligible startups receive income tax exemption for:
(A) 1 year
(B) 3 years
(C) 5 years
(D) More than one of the above
(E) None of the above

---

**Q35.** "Make in India" was launched on:
(A) July 1, 2015
(B) September 25, 2014
(C) January 16, 2016
(D) More than one of the above
(E) None of the above

---

**Q36.** The symbol/logo of "Make in India" is:
(A) A spinning wheel (charkha)
(B) A marching lion made of gears
(C) A rising sun over factory chimneys
(D) More than one of the above
(E) None of the above

---

**Q37.** Pradhan Mantri Kisan Samman Nidhi (PM-KISAN) provides how much income support annually per farmer family?
(A) ₹2,000 per year
(B) ₹4,000 per year
(C) ₹6,000 per year
(D) More than one of the above
(E) None of the above

---

**Q38.** PM-KISAN payments are made in how many instalments per year?
(A) 2 instalments of ₹3,000 each
(B) 3 instalments of ₹2,000 each
(C) 6 instalments of ₹1,000 each
(D) More than one of the above
(E) None of the above

---

**Q39.** "Swachh Bharat Mission" was launched on which date, and why was that date chosen?
(A) January 26, 2014 — Republic Day
(B) October 2, 2014 — Gandhi Jayanti (150th birth anniversary of Mahatma Gandhi)
(C) August 15, 2014 — Independence Day
(D) More than one of the above
(E) None of the above

---

**Q40.** India was declared ODF (Open Defecation Free) under Swachh Bharat Mission on:
(A) October 2, 2019
(B) August 15, 2020
(C) January 26, 2022
(D) More than one of the above
(E) None of the above

---

**Q41.** "Pradhan Mantri Ujjwala Yojana" (PMUY) is associated with:
(A) Providing free electricity connections to BPL households
(B) Providing free LPG connections to women from BPL households
(C) Providing free drinking water to rural households
(D) More than one of the above
(E) None of the above

---

**Q42.** "Jal Jeevan Mission" was launched on August 15, 2019. Its goal is:
(A) Cleaning the river Ganga and its tributaries
(B) Building check dams in drought-prone areas
(C) Providing tap water (piped drinking water) to every rural household
(D) More than one of the above
(E) None of the above

---

**Q43.** "Jan Dhan Yojana" (PMJDY) was launched on August 28, 2014. Its PRIMARY purpose was:
(A) Providing free smartphones to rural citizens
(B) Financial inclusion — opening bank accounts for all unbanked households
(C) Providing loans to small businesses
(D) More than one of the above
(E) None of the above

---

**Q44.** "Beti Bachao Beti Padhao" scheme is a JOINT initiative of which three ministries?
(A) Finance + Education + Agriculture
(B) Women & Child Development + Health + Education
(C) Rural Development + Health + Finance
(D) More than one of the above
(E) None of the above

---

**Q45.** DigiLocker is an initiative under Digital India that:
(A) Provides physical locker facilities in digital post offices
(B) Allows citizens to store and share official digital documents (Aadhaar, driving license, etc.)
(C) Creates encrypted digital wallets for online payments
(D) More than one of the above
(E) None of the above

---

**Q46.** Which scheme provides up to ₹4 lakh education loan to students for higher education in Bihar?
(A) PM Vidya Lakshmi
(B) Bihar Student Credit Card Scheme
(C) PM Mudra Yojana
(D) More than one of the above
(E) None of the above

---

**Q47.** "Mukhyamantri Kanya Utthan Yojana" in Bihar is specifically aimed at:
(A) Providing employment to male youth in Bihar
(B) Financial support to girl children from birth to graduation
(C) Providing free laptops to boys in government schools
(D) More than one of the above
(E) None of the above

---

**Q48.** MGNREGS (Mahatma Gandhi National Rural Employment Guarantee Scheme) guarantees how many days of employment per year per rural household?
(A) 50 days
(B) 75 days
(C) 100 days
(D) More than one of the above
(E) None of the above

---

**Q49.** "PM Surya Ghar Muft Bijli Yojana" launched in February 2024 aims to:
(A) Provide free electricity to all households through nationalised supply
(B) Install rooftop solar panels on 1 crore homes providing 300 units free electricity/month
(C) Build solar power plants in all 100 Smart Cities
(D) More than one of the above
(E) None of the above

---

**Q50.** Consider these statements about government schemes:
I.  Digital India was launched in 2015, not 2014.
II. Ayushman Bharat covers ₹5 lakh per family per year.
III. Swachh Bharat was launched on Gandhi's death anniversary (January 30).
IV. PM-KISAN provides ₹6,000 in 3 equal instalments.

Which statements are CORRECT?
(A) I, II, and IV only
(B) I, II, III, and IV all correct
(C) II and III only
(D) More than one of the above
(E) None of the above

---

# ✅ ANSWER KEY

## ⚠️ ATTEMPT ALL 50 QUESTIONS BEFORE CHECKING ANSWERS

---

### CS Answers (Q1–Q25):

| Q  | Ans | Key Reason |
|----|-----|-----------|
| 1  | (B) | Protocol = set of rules governing data transmission |
| 2  | (B) | TCP = connection-oriented + reliable |
| 3  | (C) | 3-way handshake: SYN → SYN-ACK → ACK (always in this order) |
| 4  | (B) | Flow control = prevents fast sender overwhelming slow receiver (sliding window) |
| 5  | (C) | UDP preferred when speed > accuracy (streaming, gaming) |
| 6  | (C) | UDP PDU = Datagram; TCP PDU = Segment |
| 7  | (B) | HTTP stateless = each request independent, no server memory of previous requests |
| 8  | (B) | HTTPS = HTTP + SSL/TLS; both use TCP transport |
| 9  | (C) | HTTP = Port 80 |
| 10 | (B) | HTTPS = Port 443 |
| 11 | (C) | SMTP = SENDING emails only; POP3/IMAP = receiving |
| 12 | (C) | Sending server acts as SMTP CLIENT when it initiates delivery to another server |
| 13 | (B) | Ping = Packet Internet Groper (NOT Generator) |
| 14 | (C) | Ping uses ICMP — NOT TCP or UDP |
| 15 | (B) | Ping measures RTT (latency) and packet loss |
| 16 | (C) | MQTT designed for IoT — lightweight, low bandwidth, low power |
| 17 | (B) | MQTT = Publish-Subscribe model (via broker) |
| 18 | (B) | Broker = central router in MQTT architecture |
| 19 | (C) | MQTT default port = 1883 (8883 for encrypted) |
| 20 | (B) | Socket = IP address + Port number (communication endpoint) |
| 21 | (C) | Server: Create → Bind → Listen → Accept → Receive/Send → Close |
| 22 | (C) | Stream socket = TCP (reliable, ordered) |
| 23 | (C) | 404 = HTTP "Not Found" error |
| 24 | (A) | I correct (TCP=banking), II correct (UDP=streaming), III WRONG (SMTP=SENDING not receiving), IV correct (ICMP=ping) |
| 25 | (C) | TCP = reliable+slow; UDP = fast+unreliable; choice depends on application |

---

### GS Answers (Q26–Q50):

| Q  | Ans | Key Reason |
|----|-----|-----------|
| 26 | (B) | Digital India launched = July 1, 2015 |
| 27 | (B) | Digital India = MeitY (Ministry of Electronics and IT) |
| 28 | (B) | BharatNet = optical fiber internet to gram panchayats (rural broadband) |
| 29 | (C) | PM-JAY launched = September 23, 2018 (Deendayal Upadhyay's birthday) |
| 30 | (C) | Ayushman Bharat = ₹5 lakh per family per year |
| 31 | (B) | Implementing body = NHA (National Health Authority) |
| 32 | (A) | Startup India = January 16, 2016 |
| 33 | (C) | Startup India = DPIIT under Ministry of Commerce and Industry |
| 34 | (B) | Startup India = 3-year income tax exemption |
| 35 | (B) | Make in India = September 25, 2014 |
| 36 | (B) | Make in India logo = marching lion made of gears |
| 37 | (C) | PM-KISAN = ₹6,000 per year |
| 38 | (B) | PM-KISAN = 3 instalments of ₹2,000 each |
| 39 | (B) | Swachh Bharat = October 2, 2014 = Gandhi Jayanti |
| 40 | (A) | India declared ODF on October 2, 2019 (Gandhi Jayanti 2019) |
| 41 | (B) | PMUY = free LPG connections to BPL women (not electricity!) |
| 42 | (C) | Jal Jeevan Mission = tap water (piped) to every rural household |
| 43 | (B) | Jan Dhan Yojana = financial inclusion / bank accounts for all |
| 44 | (B) | Beti Bachao Beti Padhao = WCD + Health + Education (3 ministries) |
| 45 | (B) | DigiLocker = digital document storage/sharing (official documents) |
| 46 | (B) | Bihar Student Credit Card = ₹4 lakh education loan |
| 47 | (B) | Mukhyamantri Kanya Utthan Yojana = girl child financial support birth to graduation |
| 48 | (C) | MGNREGS = 100 days guaranteed employment |
| 49 | (B) | PM Surya Ghar = rooftop solar on 1 crore homes, 300 units free/month |
| 50 | (A) | I correct (Digital India = 2015), II correct (₹5 lakh), III WRONG (Swachh Bharat = birth anniversary Oct 2, not death Jan 30), IV correct (3 × ₹2,000) |

---

# 🔁 DAY 46 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Network Protocols

### TCP vs UDP — 5 Key Differences:
```
FEATURE          │  TCP                    │  UDP
─────────────────┼─────────────────────────┼──────────────────────────
Connection       │  Connection-oriented    │  Connectionless
Reliability      │  RELIABLE (ACK+retransmit)│  UNRELIABLE (no ACK)
Speed            │  SLOWER (overhead)      │  FASTER (no overhead)
PDU              │  Segment               │  Datagram
Use Cases        │  Web, Email, FTP, SSH  │  Streaming, Gaming, DNS, VoIP

TRICK: TCP = "Takes Care Perfectly" | UDP = "Ultra Direct & Primitive"
```

### Protocol Quick Reference:
```
HTTP   = Port 80  → Web browsing (stateless, request-response)
HTTPS  = Port 443 → Encrypted web (HTTP + SSL/TLS)
FTP    = Port 21  → File transfer (control); Port 20 (data)
SMTP   = Port 25  → SEND emails (outgoing ONLY)
POP3   = Port 110 → Download emails to device
IMAP   = Port 143 → Read emails on server
DNS    = Port 53  → Domain name → IP (uses UDP)
SSH    = Port 22  → Secure remote access
MQTT   = Port 1883→ IoT lightweight messaging (publish-subscribe)
```

### Key Facts — One Liner:
```
TCP Handshake:   SYN → SYN-ACK → ACK (3 steps)
Ping Protocol:   ICMP (NOT TCP, NOT UDP)
Ping Full Form:  Packet Internet Groper (NOT Generator!)
Ping Measures:   RTT (latency) + Packet Loss
SMTP Trap:       SMTP CLIENT = SENDING server (server-to-server)
Socket:          IP address + Port number
MQTT model:      Publish-Subscribe (via Broker)
HTTP:            Stateless — no memory between requests
```

### PYQ Trap List — Protocols:
```
✅ TCP = reliable + slower; UDP = unreliable + faster
✅ SMTP = SEND emails only (POP3/IMAP = receive)
✅ SMTP client = SENDING mail server (server-to-server)
✅ Ping = ICMP (not UDP, not TCP)
✅ Ping = Packet Internet GROPER (not Generator)
✅ Ping measures LATENCY + PACKET LOSS (not bandwidth/speed)
✅ HTTPS = HTTP + SSL/TLS on TCP (same transport, different encryption)
✅ HTTP = stateless (uses cookies to simulate state)
✅ Socket = IP + Port combination (not just IP)
✅ MQTT = IoT protocol, Publish-Subscribe model, Port 1883
✅ TCP termination = 4-way (FIN,ACK,FIN,ACK); establishment = 3-way
✅ UDP PDU = Datagram; TCP PDU = Segment
```

---

## ⚡ RAPID FIRE — Government Schemes

### Must-Know Scheme Grid:
```
SCHEME              │ LAUNCH DATE     │ KEY FACT
────────────────────┼─────────────────┼──────────────────────────────────────
Digital India       │ July 1, 2015    │ MeitY; BharatNet; DigiLocker
Ayushman Bharat     │ Sep 23, 2018    │ ₹5 lakh/family; NHA; 50 cr people
Startup India       │ Jan 16, 2016    │ DPIIT; 3yr tax exemption; ₹10K cr fund
Make in India       │ Sep 25, 2014    │ DPIIT; Lion+gears logo; 25 sectors
Swachh Bharat       │ Oct 2, 2014     │ Gandhi Jayanti; ODF Oct 2, 2019
PM-KISAN            │ Feb 24, 2019    │ ₹6,000/yr = 3×₹2,000; Agriculture Min
PMUY (Ujjwala)      │ May 2016        │ Free LPG to BPL women; Petroleum Min
Jan Dhan Yojana     │ Aug 28, 2014    │ Financial inclusion; bank accounts
Jal Jeevan Mission  │ Aug 15, 2019    │ Tap water to every rural household
MGNREGS             │ Feb 2006        │ 100 days guaranteed rural employment
```

### PYQ Trap List — Schemes:
```
✅ Digital India = 2015 (NOT 2014)
✅ Ayushman Bharat = ₹5 lakh (NOT ₹2 lakh)
✅ Swachh Bharat = Gandhi BIRTH anniversary (Oct 2) NOT death (Jan 30)
✅ PM-KISAN = 3 instalments of ₹2,000 (NOT 6 or 2 instalments)
✅ PMUY = LPG connections (NOT electricity — that's Saubhagya scheme!)
✅ Make in India = Sep 25, 2014; Startup India = Jan 16, 2016 (different dates!)
✅ Beti Bachao = 3 ministries (WCD + Health + Education)
✅ NHA = implementing body of Ayushman Bharat
✅ Bihar Student Credit Card = ₹4 lakh (NOT ₹2 lakh or ₹6 lakh)
✅ India ODF declared = October 2, 2019 (exactly 5 years after launch)
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **TCP vs UDP**: TCP = reliable, connection-oriented, 3-way handshake (SYN→SYN-ACK→ACK), slower, used for web/email/banking; UDP = unreliable, connectionless, faster, used for streaming/gaming/DNS/VoIP.
2. **Protocol traps**: SMTP (Port 25) = SEND only; SMTP client = sending server; Ping = ICMP = Packet Internet Groper = measures RTT + packet loss; HTTPS = HTTP + SSL/TLS on Port 443; Socket = IP + Port combination.
3. **MQTT**: IoT protocol, lightweight (2-byte header), Publish-Subscribe model, central Broker routes messages, Port 1883; designed for low-power, low-bandwidth devices; QoS 0/1/2 levels.
4. **Digital India (July 2015) + Ayushman Bharat (Sep 23, 2018)**: Digital India = MeitY, BharatNet, DigiLocker; Ayushman Bharat = ₹5 lakh/family, ~50 crore people, NHA implements, world's largest health scheme.
5. **Scheme launch dates trap**: Make in India (Sep 25, 2014), Swachh Bharat (Oct 2, 2014 = Gandhi Jayanti), Startup India (Jan 16, 2016); PM-KISAN = 3 × ₹2,000 = ₹6,000/year; ODF declared Oct 2, 2019.

---

## 📅 DAY 47 PREVIEW — What's Coming Next:
**CS**: Computer Networks — Network Security Basics: Firewall, Encryption (Symmetric/Asymmetric), SSL/TLS, VPN, Types of Cyber Attacks (Phishing, DDoS, Man-in-the-Middle, SQL Injection), Malware types
**GS**: Indian Polity — Fundamental Rights (Articles 12–35): Right to Equality, Right to Freedom, Right Against Exploitation, Cultural & Educational Rights, Right to Constitutional Remedies

---

*🚀 Day 46 of 170 — You're 27% through the journey. Network protocols are the APPLICATION of everything you've learned in OSI/TCP-IP. Master the SMTP trap and TCP handshake — both appear in almost every PYQ paper. For schemes, make a quick table and revise the launch dates daily. You're building serious momentum!*
