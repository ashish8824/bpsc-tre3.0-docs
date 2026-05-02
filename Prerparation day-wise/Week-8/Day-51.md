# 📅 BPSC TRE 4.0 — DAY 51 COMPLETE STUDY MODULE
### Computer Networks Quick Revision (CS) + Tribal Movements & INC Sessions (GS)
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Computer Networks — rapid-fire shortcuts on all PYQ-tested facts
> - Afternoon (1 hr): Tribal Movements + INC Sessions — story-based deep learning
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5-bullet revision notes in your notebook

---

# PART 1: COMPUTER SCIENCE
## 📘 Computer Networks — Quick Revision Shortcuts for Day 51

> **Day 51 Context:** Networks was covered in depth on Days 43–49. Today is a *light revision* day — speed-drill every PYQ-tested fact. No new theory. Pure recall mode. If any block feels shaky → mark it for tonight's notebook.

---

## 🔷 BLOCK 1: OSI vs TCP/IP Models

```
OSI MODEL (7 LAYERS) — Mnemonic: "Please Do Not Throw Sausage Pizza Away"
┌─────────────────────────────────────────────────────────────┐
│  Layer 7 → Application  (HTTP, FTP, SMTP, DNS)              │
│  Layer 6 → Presentation (Encryption, Compression, Formats)  │
│  Layer 5 → Session      (Session management, dialog control)│
│  Layer 4 → Transport    (TCP, UDP — end-to-end delivery)    │
│  Layer 3 → Network      (IP — routing, forwarding)          │
│  Layer 2 → Data Link    (MAC, LLC — framing, error detect)  │
│  Layer 1 → Physical     (Bits, cables, signals)             │
└─────────────────────────────────────────────────────────────┘

TCP/IP MODEL (4 LAYERS):
  Application → Combines OSI layers 5, 6, 7
  Transport   → Same as OSI Transport (Layer 4)
  Internet    → Same as OSI Network (Layer 3)
  Network Access → Combines OSI layers 1 and 2

KEY MAPPING (PYQ TESTED):
  OSI Transport layer = TCP/IP "Host-to-Host" layer
  OSI Network layer   = TCP/IP "Internet" layer
```

### 🚨 PYQ TRAP #1:
> TCP/IP "Host-to-Host" layer = OSI **Transport** layer.
> OSI has **7** layers; TCP/IP has **4** layers.
> Both distinctions are heavily tested!

---

## 🔷 BLOCK 2: Data Link Layer — MAC vs LLC

```
DATA LINK LAYER has TWO SUBLAYERS:

LLC (Logical Link Control) — UPPER sublayer
  → Interface between Network layer and MAC layer
  → Error detection at frame level

MAC (Media Access Control) — LOWER sublayer
  → Performs functions depending on MEDIUM TYPE ← PYQ exact phrase
  → Hardware addresses (MAC addresses) live here
  → Controls access to the physical transmission medium
  → Examples: Ethernet MAC, Wi-Fi MAC (802.11)
```

### 🚨 PYQ TRAP #2:
> MAC sublayer = performs functions depending on **medium type**.
> This exact phrase appeared in TRE paper — "medium-dependent functions."

---

## 🔷 BLOCK 3: IP Addressing

```
IPv4:
  → 32 bits (4 bytes)
  → Written as four octets: e.g., 192.168.1.1
  → Total addresses: 2³² = ~4.3 billion

IPv6:
  → 128 bits ← MEMORIZE THIS
  → NOT 32, NOT 64, NOT 256 — always 128 bits
  → Written in hexadecimal: e.g., 2001:0db8:85a3::8a2e:0370:7334
  → IPv6 header: Flow label is CONSIDERED (not discarded) ← PYQ trap

Subnet Mask:
  → Identifies the NETWORK PORTION of an IP address
  → Separates network bits from host bits
```

### 🚨 PYQ TRAP #3:
> IPv6 = **128 bits**. The options always include 32, 64, 256 as distractors.
> IPv6 flow label = CONSIDERED (not discarded) in routing.

---

## 🔷 BLOCK 4: Protocols — The PYQ-Tested List

```
TCP (Transmission Control Protocol):
  → CONNECTION-ORIENTED protocol
  → Uses THREE-WAY HANDSHAKE (SYN → SYN-ACK → ACK)
  → Reliable, ordered, error-checked delivery
  → Single stream of data

UDP (User Datagram Protocol):
  → CONNECTIONLESS protocol
  → No handshake, no guarantee of delivery
  → Faster, used for: DNS, streaming, VoIP

SMTP (Simple Mail Transfer Protocol):
  → Used for SENDING email
  → When one mail server sends email to another → it acts as SMTP CLIENT ← PYQ trap
  → Port 25

HTTP / HTTPS:
  → Used for web page transfer (Application layer)

DNS (Domain Name System):
  → Converts domain names to IP addresses
  → Uses both TCP and UDP (port 53)

PING:
  → Summarizes PACKET LOSS and ROUND-TRIP DELAY ← PYQ exact fact
  → NOT "Packet Internet Generator" (that's a wrong option planted in PYQs)

MQTT (Message Queuing Telemetry Transport):
  → Protocol for IoT DEVICE COMMUNICATION ← TRE 3.0 PYQ
  → Lightweight publish/subscribe protocol

SOCKET:
  → Endpoint of an inter-process communication flow ← PYQ definition
  → Not a physical device — it's a software endpoint
```

### 🚨 PYQ TRAP #4:
> When a mail server sends mail to another mail server → it acts as **SMTP client**.
> PING = packet loss + round-trip delay (NOT "Packet Internet Generator").
> MQTT = IoT protocol.

---

## 🔷 BLOCK 5: Network Topologies & Devices

```
TOPOLOGIES:
  Bus      → single cable; all devices connected to it; one failure = all fail
  Star     → requires CENTRAL CONTROLLER/HUB; if hub fails, all fail
  Ring     → data travels in a ring; token-based access
  Mesh     → every device connected to every other device; most reliable
  Hybrid   → combination of above

⚠️ PYQ TRAP: "Peer-to-peer" is NOT a network topology
             It is a NETWORK TYPE (model of sharing), not a physical topology

DEVICES:
  Hub     → Physical layer; broadcasts to ALL ports (dumb device)
  Switch  → Data Link layer; connects devices in LAN; sends to SPECIFIC port
  Router  → Network layer; connects MULTIPLE NETWORKS; routes packets by IP
  Bridge  → Data Link layer; connects two LAN segments
  Gateway → connects networks using DIFFERENT protocols

WWW:
  → World Wide Web = collection of HYPERLINKED DOCUMENTS on the Internet
  → Internet ≠ WWW (Internet is the infrastructure; WWW runs on top of it)
```

### 🚨 PYQ TRAP #5:
> **Peer-to-peer is NOT a topology.** It always appears as a wrong option in topology questions.
> Switch = Data Link layer | Router = Network layer.

---

## 🔷 BLOCK 6: Transmission Media

```
WIRED MEDIA (fastest to slowest):
  Optical Fiber   → HIGHEST speed + immune to electromagnetic interference ← PYQ
  Coaxial Cable   → moderate speed, moderate interference resistance
  UTP (Twisted Pair) → most common LAN cable; VULNERABLE to EM interference

WIRELESS MEDIA:
  Radio waves     → long distance, low frequency
  Microwaves      → line-of-sight, used in satellite communication
  Infrared        → short range, no obstacles allowed (TV remotes, IR ports)

SNIFFERS:
  → Packet-sniffing attacks (eavesdropping on network traffic)
  → SWITCHED NETWORKS prevent sniffers ← PYQ tested
  → Reason: switch sends packets only to intended recipient port
```

### 🚨 PYQ TRAP #6:
> Optical fiber = **highest transmission speed** AND **immune to electromagnetic interference**.
> Both facts are tested — optical fiber is the answer to BOTH types of questions.
> Sniffers are prevented by **switched networks** (not hubs, not routers).

---

## 🔷 BLOCK 7: Security & I/O Addressing

```
ASYMMETRIC KEY CRYPTOGRAPHY (Public-Private Key):
  Public Key  = shared openly (anyone can use to ENCRYPT)
  Private Key = kept secret by the RECEIVER (used to DECRYPT) ← PYQ key fact

  Sender    → encrypts with receiver's PUBLIC key
  Receiver  → decrypts with their own PRIVATE key

System Integrity Breach:
  → FULL ACCESS RIGHTS FOR ALL USERS is an integrity risk ← PYQ

MEMORY-MAPPED I/O:
  → I/O and MEMORY share SAME ADDRESS SPACE
  → I/O devices are accessed using memory instructions

I/O-MAPPED I/O:
  → SEPARATE address spaces for I/O and memory
  → Special IN/OUT instructions needed

Program-controlled I/O:
  → = POLLING (CPU repeatedly checks device status flags)
  → CPU is busy-waiting — wasteful

SIMPLEX vs DUPLEX:
  Simplex     → data flows in ONE DIRECTION only
  Half-duplex → BOTH directions, but NOT simultaneously
  Full-duplex → BOTH directions simultaneously

  Computer ↔ Keyboard = SIMPLEX (keyboard sends to computer only) ← PYQ trap
```

### 🚨 PYQ TRAP #7:
> Private key in asymmetric cryptography = kept by the **RECEIVER** (not sender).
> Computer ↔ Keyboard communication = **SIMPLEX** (one direction only).

---

## 🔷 BLOCK 8: TDM, Multiplexing & Subnetting

```
MULTIPLEXING = combining multiple signals into one channel

TDM (Time Division Multiplexing):
  → Each channel gets a TIME SLOT
  → Time slots are grouped into FRAMES ← PYQ exact phrase
  → "TDM slots → FRAMES"

FDM (Frequency Division Multiplexing):
  → Each channel gets its own FREQUENCY BAND
  → Used in traditional cable TV, radio

WDM (Wavelength Division Multiplexing):
  → Used with OPTICAL FIBER
  → Each signal uses a different wavelength of light

SUBNETTING:
  → Dividing one large network into smaller sub-networks
  → VLSM = Variable Length Subnet Masking
  → Subnet mask identifies network portion of IP
```

---

## 📊 NETWORKS RAPID FIRE — 1-LINE RECALL TABLE

| Concept | Key Fact |
|---------|----------|
| OSI layers | 7 |
| TCP/IP layers | 4 |
| Host-to-Host = | Transport layer (OSI Layer 4) |
| MAC sublayer | Medium-dependent functions |
| IPv4 | 32 bits |
| IPv6 | **128 bits** |
| TCP | Connection-oriented, 3-way handshake |
| SMTP client | Mail server sending to another server |
| PING | Packet loss + round-trip delay |
| MQTT | IoT communication protocol |
| Socket | Endpoint of inter-process communication |
| Peer-to-peer | NOT a topology (it's a network type) |
| Optical fiber | Highest speed + immune to EM interference |
| UTP | Vulnerable to EM interference |
| Sniffers prevented by | Switched networks |
| Private key | Kept by RECEIVER |
| Computer ↔ Keyboard | Simplex |
| Program-controlled I/O | Polling |
| Memory-mapped I/O | I/O + memory share same address space |
| TDM → | Slots → Frames |
| WWW | Collection of hyperlinked documents |
| Switch | Data Link layer; LAN devices |
| Router | Network layer; connects multiple networks |

---
---

# PART 2: GENERAL STUDIES
## 🏛️ Tribal Movements + INC Sessions — Deep Dive

---

## 🔷 SECTION 1: THE THREE TRIBAL MOVEMENTS — Complete Story

> **Why this matters for BPSC TRE:** Bihar/Jharkhand tribal history is extremely high-priority for this exam. The chronological order of these three movements — and what makes each unique — has been tested across multiple papers.

---

### 1.1 SANTHAL REBELLION (1855–56) — The First and Earliest

#### Setting the Scene:
```
WHO: Santhal tribe (also called Santhals)
WHERE: Rajmahal Hills region — then part of Bengal (now Jharkhand-Bihar border area)
WHEN: 1855–56 (specifically June 30, 1855 is the traditional start date)
```

#### Background — Why the Santhals Revolted:
```
The Santhals were cultivators and forest-dwellers in the Rajmahal Hills.

Their problems:
  → ZAMINDARS (landlords) charging excessive rent
  → MONEYLENDERS (mahajans/sahukaras) charging 50–500% interest
  → Fake accounting — moneylenders manipulated records so debts never cleared
  → BRITISH revenue policies disrupted traditional Santhal life
  → Loss of land through debt bondage
  → Santhal women subjected to harassment by landlords

The Santhal cry: "WE WILL PAY NO MORE RENT. THE RULE OF THE DIKU MUST END."
(Diku = outsiders/exploiters — zamindars, moneylenders, British officials)
```

#### Leaders — SIDHU and KANHU MURMU:
```
Sidhu Murmu  → Elder brother, primary leader, claimed divine inspiration
Kanhu Murmu  → Younger brother, military commander
               (Two other brothers: Chand and Bhairav also participated)

Their claim: They received a message from GOD (Thakur) to revolt
             "Thakur has given us the order — rise up against injustice"
             This gave the movement a RELIGIOUS and MESSIANIC character

Military method: Bows, arrows, traditional weapons
                 Cut telegraph lines, destroyed railway properties
```

#### Outcome:
```
British response: Sent armed troops (including cavalry)
Result: Brutal suppression
        Sidhu killed — July 1855
        Kanhu captured and executed — 1856

Significance:
  → FIRST organized tribal uprising against British colonial rule in this region
  → Inspired later tribal movements
  → The Santhal Parganas Tenancy Act (1876) was passed partly in response
     (gave Santhals some land rights protection)
  → The region "Santhal Parganas" (now in Jharkhand) is named after this uprising
```

---

### 1.2 BIRSA MUNDA REVOLT — "ULGULAN" (1899–1900)

#### Background:
```
WHO: Munda tribe (also called Mundas)
WHERE: Chota Nagpur region (now Jharkhand)
WHEN: 1899–1900
NAME: "Ulgulan" = "Great Tumult" or "Great Disturbance" in Mundari language
```

#### The Context — Land Problem:
```
Traditional Munda land system: "Khuntkatti" system
  → Munda communities collectively owned forest land
  → This was their ancestral, community-held land

What happened under British rule:
  → Landlords (thikadars/jagirdars) introduced INDIVIDUAL land ownership
  → Mundas' communal land was taken away
  → Munda men forced into bonded labour (bethi/chakri system)
  → Christian missionaries converting Mundas (Birsa initially converted, then rejected)
  → Forests were taken over by the British
```

#### Birsa Munda — The Man, The Myth:
```
Born: 1875 (approximately), Ulihatu village, Chota Nagpur
Early life: 
  → Initially educated at a mission school
  → Converted to Christianity briefly
  → Eventually rejected Christianity AND traditional tribal religion
  → Created his OWN RELIGION — "Birsait"

Birsait Religion:
  → Monotheistic — worship ONE God ("Singbonga" = Sun God)
  → Rejected idol worship, animal sacrifice
  → Preached purity, sobriety, brotherhood
  → Combined elements of Vaishnavism, Christianity, tribal beliefs

Why Birsa became a SUPERHUMAN figure:
  → Claimed to be an AVATAR (divine incarnation) — "Dharti Aba" (Father of the Earth)
  → Claimed miraculous powers: healing the sick, making crops grow
  → Thousands of Mundas became devoted followers
  → "Birsa is God" became a common belief

⚠️ THIS GAVE THE MOVEMENT A RELIGIOUS + POLITICAL + ECONOMIC dimension — unique!
```

#### The Ulgulan — The Revolt:
```
1895:   Birsa declared himself God and leader; started gathering followers
1897–98: First confrontation with British (arrested briefly, released 1897)
December 24, 1899: THE UPRISING BEGINS (Christmas Eve — symbolic)
                   Birsa chose this date to show defiance against Christianity
                   Munda warriors attacked police stations, churches
                   Used bows, arrows, axes (traditional weapons)

Key Military Commander appointed by Birsa:
  → GAYA MUNDA ← (PYQ tested from Day 50 — reinforced here)

January 1900: British sent forces; Mundas suffered heavy defeats at Doumbari Hill
              (Doumbari Hill = site of the decisive battle)
              Many Mundas killed including women and children

February 3, 1900: Birsa Munda CAPTURED (arrested at Jamkopai forest)
June 9, 1900: Birsa Munda DIED in British custody (Ranchi Jail)
              Official cause: Cholera
              Many believe: He was poisoned (never proven)
              Age: approximately 25 years
```

#### Outcome and Legacy:
```
Immediate: Revolt suppressed
Long-term:
  → Chota Nagpur Tenancy Act, 1908 — gave Mundas land rights protection
  → British recognized the legitimacy of Khuntkatti (communal land ownership)
  → Birsa Munda became a LEGENDARY FIGURE
  → Jharkhand state's NATIONAL HERO — appears on currency, stamps
  → His birth anniversary (November 15) = JHARKHAND FOUNDATION DAY
  → "Ulgulan" still used as a symbol of resistance in Jharkhand
```

---

### 1.3 TANA BHAGAT MOVEMENT (1914) — The Most Misidentified

#### The Core PYQ Trap:
```
⚠️ MOST COMMON BPSC TRAP:
   "Tana Bhagat Movement was a _____ movement?"
   WRONG answers students write: Peasant movement / Dalit movement
   CORRECT answer: TRIBAL MOVEMENT ← Always and only this
```

#### Background:
```
WHO: Oraon tribe (also called Oraons or Kurukhs)
WHERE: Chota Nagpur region, Jharkhand (then Bengal-Bihar)
WHEN: Started 1914
LED BY: JATRA BHAGAT (Jatra Oraon) ← Key name to remember
```

#### The Oraon Problem:
```
The Oraons faced:
  → Land alienation — their land taken by outsiders (Diku)
  → Forced labour (beth-begari) for landlords
  → Exploitation by moneylenders
  → Disruption of their traditional forest-based life
  → Both Christian missionaries and Hindu zamindars exploiting them
```

#### Jatra Bhagat — The Religious Leader:
```
Background:
  → Ordinary Oraon farmer
  → Claimed to have received DIVINE REVELATION from God (Dharmesh)
  → Said he was sent to purify the Oraon community

His message — TRIPLE REFORM:
  1. SOCIAL: Give up alcohol, meat, singing/dancing at impure occasions
  2. RELIGIOUS: Worship only ONE God (Dharmesh), give up animal sacrifice
  3. POLITICAL: Non-violent resistance to British rule and landlords
                DO NOT PAY RENT to zamindars
                DO NOT DO FORCED LABOUR (beth-begari)

Key Feature: NON-VIOLENT character ← distinguishes it from Birsa's armed revolt
             Tana Bhagat = PASSIVE RESISTANCE + social purification
```

#### Tana Bhagat + Gandhi Connection:
```
When Gandhi launched NON-COOPERATION MOVEMENT (1920):
  → Tana Bhagat followers JOINED Gandhi's movement enthusiastically
  → They saw similarities: non-violence, purity, resistance to British
  → Tana Bhagats marched with Gandhi, wore khadi
  → They became among the most loyal Gandhian followers in Jharkhand

This connection is HISTORICALLY SIGNIFICANT but not heavily PYQ-tested.
```

#### Why "Tana" Bhagat?
```
"Tana" = derived from "Tanana" (Oraon word for stretching/pulling)
         OR simply the name of the village/area
"Bhagat" = devotee/saint (used for the followers)
So Tana Bhagat = Devotees of the Tana faith

Followers were called: TANA BHAGATS
```

---

### 1.4 CHRONOLOGICAL MASTER TABLE — The Most Tested Order

```
CORRECT CHRONOLOGICAL ORDER:
══════════════════════════════════════════════════════════

1855–56 → SANTHAL REBELLION (HUL)
          Leaders: Sidhu and Kanhu Murmu
          Tribe: Santhal
          Area: Rajmahal Hills (now Jharkhand-Bihar border)
          Against: Zamindars + moneylenders + British
          Type: ARMED revolt

          ↓

1899–1900 → BIRSA MUNDA REVOLT (ULGULAN)
             Leader: Birsa Munda
             Military commander: GAYA MUNDA
             Tribe: Munda
             Area: Chota Nagpur (now Jharkhand)
             Against: Land alienation + forced labour + British
             Type: ARMED revolt (religious + political character)

          ↓

1914 → TANA BHAGAT MOVEMENT
        Leader: JATRA BHAGAT
        Tribe: ORAON (Kurukh)
        Area: Chota Nagpur (Jharkhand)
        Against: Landlords + forced labour + British
        Type: NON-VIOLENT (religious reform + passive resistance)

══════════════════════════════════════════════════════════
Santhal (1855) → Birsa (1899) → Tana Bhagat (1914)
MEMORIZE THIS ORDER ← It is PYQ-tested directly!
```

---

### 1.5 COMPARISON TABLE — Three Movements

| Feature | Santhal Rebellion | Birsa Munda (Ulgulan) | Tana Bhagat |
|---------|------------------|----------------------|-------------|
| Year | 1855–56 | 1899–1900 | 1914 |
| Tribe | Santhal | Munda | Oraon (Kurukh) |
| Leaders | Sidhu + Kanhu Murmu | Birsa Munda | Jatra Bhagat |
| Military commander | Sidhu/Kanhu | **Gaya Munda** | — |
| Area | Rajmahal Hills | Chota Nagpur | Chota Nagpur |
| Nature | Armed revolt | Armed + religious | Non-violent |
| Against | Zamindars + moneylenders + British | Land alienation + forced labour | Forced labour + British |
| Type | Tribal movement | Tribal movement | **Tribal movement** |
| Special character | First organized tribal revolt | Religious (Birsa = avatar) | Non-violent + Gandhian |
| Act passed after | Santhal Parganas Tenancy Act (1876) | Chota Nagpur Tenancy Act (1908) | — |

---

## 🔷 SECTION 2: SWADESHI AND BOYCOTT — Origins

```
Swadeshi = "of one's own country" → use Indian-made goods, reject British goods
Boycott  = refuse to buy/use British goods

WHEN WERE THESE METHODS FIRST ADOPTED?
→ PARTITION OF BENGAL — 1905 ← PYQ TESTED

Timeline:
  July 19, 1905: Viceroy Lord Curzon announced Partition of Bengal
                 Bengal divided into East Bengal (Muslim majority) + West Bengal
                 Nationalist India saw this as "divide and rule"
  August 7, 1905: Town Hall meeting in Calcutta
                  SWADESHI and BOYCOTT formally adopted as methods of protest
  October 16, 1905: Partition officially took effect
                    The day was observed as a day of mourning
                    People tied Rakhi on each other's wrists as a symbol of unity
                    Rabindranath Tagore composed songs for the occasion

Result: Partition annulled in 1911 (due to massive protest)
Significance: Swadeshi became a PERMANENT weapon in India's freedom struggle
              Used again in Non-Cooperation (1920), Civil Disobedience (1930)
```

### 🚨 PYQ TRAP #8:
> "Swadeshi and Boycott methods were FIRST used during ___?"
> Answer = **PARTITION OF BENGAL (1905)**
> NOT during Non-Cooperation (1920) — that's when Gandhi popularised it again.
> First use = Bengal Partition.

---

## 🔷 SECTION 3: INC SESSIONS — PYQ-Tested Facts

### 3.1 First INC Session (1885):

```
Year:     1885
City:     BOMBAY (Mumbai)
Venue:    Gokuldas Tejpal Sanskrit College
President: W.C. BONNERJEE (Womesh Chandra Bonnerjee)
           ← FIRST PRESIDENT of Indian National Congress
           → He was a lawyer; born in Bengal

⚠️ TRAP: Some students write "A.O. Hume founded INC, so he was first president"
         WRONG! A.O. Hume was the ORGANIZER/FOUNDER, not the president.
         First president = W.C. BONNERJEE (1885, Bombay)
```

### 3.2 INC Gaya Session (1922):

```
Year:     1922
City:     GAYA, BIHAR (very relevant for BPSC!)
President: CHITTARANJAN DAS (also called "Deshbandhu")

Why this session matters:
  → This was the year AFTER Gandhi suspended the Non-Cooperation Movement
    (Gandhi suspended NCM after Chauri Chaura violence, February 1922)
  → Chittaranjan Das wanted to work WITHIN the legislatures (oppose from inside)
  → This led to the formation of the SWARAJ PARTY (1923) by C.R. Das and Motilal Nehru

⚠️ PYQ TRAP: INC Gaya Session 1922 President = CHITTARANJAN DAS
              NOT Gandhi (he was arrested in 1922)
              NOT Hakim Ajmal Khan
              NOT Motilal Nehru
              → CHITTARANJAN DAS ← Only this
```

### 3.3 Bihar Peasants in Non-Cooperation Movement:

```
Non-Cooperation Movement: 1920–1922 (launched by Gandhi)

Bihar's peasants during Non-Cooperation Movement:
  → Led by SWAMI VIDYANAND ← PYQ tested

Context:
  → Swami Vidyanand was a religious leader who joined the political movement
  → Organized Bihar's peasant participation in non-cooperation
  → Peasants boycotted British goods, schools, courts under his leadership
```

### 3.4 Lord Curzon's Quote about Congress:

```
"The Congress is tottering to its fall and one of my great ambitions
while in India is to assist it to a peaceful demise."

Said by: LORD CURZON (Viceroy of India, 1899–1905) ← PYQ tested

Context:
  → Lord Curzon was extremely dismissive of the Indian National Congress
  → He believed the Congress was a dying, unimportant organization
  → He was WRONG — Congress grew stronger after Partition of Bengal (1905)
  → His own Partition of Bengal backfired and strengthened Indian nationalism

⚠️ TRAP: If question asks "Who made this statement about Congress tottering?" → LORD CURZON
```

---

## 🔷 SECTION 4: RAKSHA BANDHAN AS TREE SAFETY DAY

```
In which state is Raksha Bandhan observed as "Tree Safety Day"
(also called Van Mahotsav / Van Raksha Diwas)?

Answer: MADHYA PRADESH ← PYQ tested

Practice: Tying Rakhi on trees as a symbol of protecting them
Origin: Connected to Chipko movement spirit + local tribal traditions
State where this is officially celebrated: MADHYA PRADESH
```

---

## 🔷 SECTION 5: MEMORY TRICKS FOR TODAY

```
THREE MOVEMENTS TRICK — "SBT" (Santhal → Birsa → Tana)
  S = Santhal (1855) — FIRST
  B = Birsa Munda (1899) — SECOND
  T = Tana Bhagat (1914) — THIRD
  "Students Become Teachers" — in order: S(1855) B(1899) T(1914)

TANA BHAGAT = TRIBAL (not Peasant, not Dalit)
  "T-T Rule": TANA = TRIBAL. Both start with T. Never forget.

JATRA BHAGAT started TANA BHAGAT:
  "JATRA started with a JOURNEY (jatra = journey in Bengali/Hindi)"
  He took his people on a journey from exploitation to resistance.

INC GAYA 1922 = CHITTARANJAN DAS (not Gandhi):
  "GayaCD" → Gaya session → CD = Chittaranjan Das
  (Think of it like a music CD from Gaya)

FIRST INC PRESIDENT = W.C. BONNERJEE (Bombay 1885):
  "WCBB85" → W.C. Bonnerjee, Bombay, 1885
  The first W is for Womesh + the B is for Bombay + 85 is the year

SWADESHI FIRST = BENGAL PARTITION (1905):
  "Curzon cut Bengal → India cut British cloth"
  Partition (cutting Bengal) → Swadeshi (cutting ties with British goods)

LORD CURZON'S QUOTE:
  "Congress tottering" = CURZON said it (he tottered INDIA instead)
```

---

## 🔷 SECTION 6: COMPLETE MASTER TABLE — Today's GS Facts

| Question | Answer |
|----------|--------|
| Santhal Rebellion leaders | Sidhu and Kanhu Murmu |
| Santhal Rebellion year | 1855–56 |
| Santhal Rebellion area | Rajmahal Hills |
| "Ulgulan" meaning | Great Tumult |
| Birsa Munda revolt year | 1899–1900 |
| Birsa Munda's tribe | Munda |
| Birsa Munda's C-in-C | Gaya Munda |
| Birsa Munda died | June 9, 1900 (Ranchi Jail) |
| Tana Bhagat leader | **Jatra Bhagat** |
| Tana Bhagat tribe | **Oraon (Kurukh)** |
| Tana Bhagat type | **Tribal movement (NOT Peasant, NOT Dalit)** |
| Tana Bhagat year | **1914** |
| Tana Bhagat nature | Non-violent |
| Chronological order | Santhal (1855) → Birsa (1899) → Tana Bhagat (1914) |
| First use of Swadeshi & Boycott | Partition of Bengal (1905) |
| First INC President | W.C. Bonnerjee (Bombay, 1885) |
| INC Gaya Session 1922 president | **Chittaranjan Das** |
| Bihar peasants in NCM led by | Swami Vidyanand |
| "Congress tottering" quote | Lord Curzon |
| Raksha Bandhan as Tree Day | Madhya Pradesh |
| Santhal Parganas Tenancy Act | 1876 |
| Chota Nagpur Tenancy Act | 1908 |

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topic: Computer Networks — All PYQ-Tested Concepts

---

**Q1.** The OSI model has how many layers, and the TCP/IP model has how many?
(A) OSI = 5 layers; TCP/IP = 7 layers
(B) OSI = 7 layers; TCP/IP = 4 layers
(C) OSI = 4 layers; TCP/IP = 7 layers
(D) More than one of the above
(E) None of the above

---

**Q2.** The TCP/IP "Host-to-Host" layer corresponds to which OSI layer?
(A) Session layer
(B) Network layer
(C) Transport layer
(D) More than one of the above
(E) None of the above

---

**Q3.** The MAC (Media Access Control) sublayer of the Data Link layer performs:
(A) Routing functions between different networks
(B) Functions that depend on the type of medium used
(C) Session management between applications
(D) More than one of the above
(E) None of the above

---

**Q4.** IPv6 addresses are how many bits long?
(A) 32 bits
(B) 64 bits
(C) 128 bits
(D) More than one of the above
(E) None of the above

---

**Q5.** TCP (Transmission Control Protocol) is described as:
(A) A connectionless protocol with no guarantee of delivery
(B) A connection-oriented protocol using a three-way handshake
(C) A protocol used only for email transmission
(D) More than one of the above
(E) None of the above

---

**Q6.** When a mail server sends email to another mail server, it acts as:
(A) SMTP server
(B) SMTP client
(C) POP3 client
(D) More than one of the above
(E) None of the above

---

**Q7.** The PING utility summarizes which of the following?
(A) Bandwidth of a network connection
(B) Packet loss and round-trip delay
(C) The number of hops to a destination
(D) More than one of the above
(E) None of the above

---

**Q8.** MQTT is a protocol specifically designed for:
(A) Secure email transmission
(B) Video streaming over the internet
(C) IoT device communication
(D) More than one of the above
(E) None of the above

---

**Q9.** A SOCKET is defined as:
(A) A physical network connector on a computer
(B) An endpoint of an inter-process communication flow
(C) A type of network topology
(D) More than one of the above
(E) None of the above

---

**Q10.** Which of the following is NOT a network topology?
(A) Star topology
(B) Ring topology
(C) Peer-to-peer
(D) More than one of the above
(E) None of the above

---

**Q11.** Which transmission medium offers the HIGHEST transmission speed and is also immune to electromagnetic interference?
(A) UTP (Unshielded Twisted Pair)
(B) Coaxial cable
(C) Optical fiber
(D) More than one of the above
(E) None of the above

---

**Q12.** Packet-sniffing attacks are prevented by using:
(A) Hub-based networks
(B) Wireless networks
(C) Switched networks
(D) More than one of the above
(E) None of the above

---

**Q13.** In asymmetric key cryptography, the private key is:
(A) Shared publicly with all communicating parties
(B) Kept secret by the SENDER
(C) Kept secret by the RECEIVER
(D) More than one of the above
(E) None of the above

---

**Q14.** Communication between a computer and its keyboard is an example of:
(A) Full-duplex transmission
(B) Half-duplex transmission
(C) Simplex transmission
(D) More than one of the above
(E) None of the above

---

**Q15.** In Time Division Multiplexing (TDM), time slots are grouped into:
(A) Packets
(B) Frames
(C) Segments
(D) More than one of the above
(E) None of the above

---

**Q16.** Memory-mapped I/O is characterized by:
(A) Separate address spaces for I/O and memory
(B) I/O and memory sharing the SAME address space
(C) Using special IN/OUT instructions for I/O operations
(D) More than one of the above
(E) None of the above

---

**Q17.** Program-controlled I/O (CPU repeatedly checks device status) is also known as:
(A) Interrupt-driven I/O
(B) DMA (Direct Memory Access)
(C) Polling
(D) More than one of the above
(E) None of the above

---

**Q18.** The subnet mask in networking is used to identify:
(A) The default gateway address
(B) The network portion of an IP address
(C) The MAC address of a device
(D) More than one of the above
(E) None of the above

---

**Q19.** Which device operates at the Network layer and connects multiple networks together?
(A) Switch
(B) Hub
(C) Router
(D) More than one of the above
(E) None of the above

---

**Q20.** The World Wide Web (WWW) is best described as:
(A) The same as the Internet
(B) A collection of hyperlinked documents accessible over the Internet
(C) A type of network topology
(D) More than one of the above
(E) None of the above

---

**Q21.** Which of the following statements about UTP cable is TRUE?
(A) It offers the highest speed among all transmission media
(B) It is immune to electromagnetic interference
(C) It is vulnerable to electromagnetic interference
(D) More than one of the above
(E) None of the above

---

**Q22.** The three-way handshake in TCP consists of which sequence?
(A) SYN → ACK → SYN-ACK
(B) SYN → SYN-ACK → ACK
(C) ACK → SYN → SYN-ACK
(D) More than one of the above
(E) None of the above

---

**Q23.** In OSI model, routing and forwarding of packets is the function of which layer?
(A) Data Link layer
(B) Transport layer
(C) Network layer
(D) More than one of the above
(E) None of the above

---

**Q24.** Which multiplexing technique uses different wavelengths of light and is used with optical fiber?
(A) TDM (Time Division Multiplexing)
(B) FDM (Frequency Division Multiplexing)
(C) WDM (Wavelength Division Multiplexing)
(D) More than one of the above
(E) None of the above

---

**Q25.** "Full access rights for all users" in a system is an example of:
(A) Best practice for data sharing
(B) System integrity breach (security risk)
(C) Redundancy planning
(D) More than one of the above
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 MCQs
### Tribal Movements + Swadeshi Origins + INC Sessions

---

**Q26.** The Santhal Rebellion (Hul) of 1855–56 was led by:
(A) Birsa Munda and Gaya Munda
(B) Sidhu and Kanhu Murmu
(C) Jatra Bhagat and Sidhu Murmu
(D) More than one of the above
(E) None of the above

---

**Q27.** The Santhal Rebellion was primarily directed against:
(A) Salt tax imposed by the British government
(B) Forced indigo cultivation under the Tinkathia system
(C) Zamindars, moneylenders, and British colonial policies
(D) More than one of the above
(E) None of the above

---

**Q28.** Birsa Munda's revolt "Ulgulan" (1899–1900) belonged to which tribe?
(A) Santhal tribe
(B) Oraon (Kurukh) tribe
(C) Munda tribe
(D) More than one of the above
(E) None of the above

---

**Q29.** "Ulgulan" in the context of Birsa Munda's revolt means:
(A) Revolt against land taxes
(B) Great Tumult (Great Disturbance)
(C) Silent resistance
(D) More than one of the above
(E) None of the above

---

**Q30.** The TANA BHAGAT MOVEMENT (1914) is categorised as which type of movement?
(A) Peasant movement
(B) Dalit movement
(C) Tribal movement
(D) More than one of the above
(E) None of the above

---

**Q31.** The Tana Bhagat Movement was led by:
(A) Birsa Munda
(B) Sidhu Murmu
(C) Jatra Bhagat
(D) More than one of the above
(E) None of the above

---

**Q32.** The Tana Bhagat Movement was associated with which tribe?
(A) Santhal tribe
(B) Munda tribe
(C) Oraon (Kurukh) tribe
(D) More than one of the above
(E) None of the above

---

**Q33.** Which of the following is TRUE about the Tana Bhagat movement?
(A) It was a violent armed revolt against the British
(B) It was a non-violent movement combining religious reform and passive resistance
(C) It was mainly about demanding Dalit rights
(D) More than one of the above
(E) None of the above

---

**Q34.** The correct CHRONOLOGICAL ORDER of the three tribal movements is:
(A) Birsa Munda → Santhal Rebellion → Tana Bhagat
(B) Tana Bhagat → Santhal Rebellion → Birsa Munda
(C) Santhal Rebellion → Birsa Munda → Tana Bhagat
(D) More than one of the above
(E) None of the above

---

**Q35.** The Santhal Rebellion of 1855–56 took place in which region?
(A) Chota Nagpur plateau
(B) Rajmahal Hills (now Jharkhand-Bihar border area)
(C) Champaran plains, Bihar
(D) More than one of the above
(E) None of the above

---

**Q36.** The Chota Nagpur Tenancy Act (1908) was passed primarily as a response to:
(A) Santhal Rebellion (1855–56)
(B) Champaran Satyagraha (1917)
(C) Birsa Munda's Ulgulan (1899–1900)
(D) More than one of the above
(E) None of the above

---

**Q37.** The Swadeshi and Boycott movements were FIRST formally adopted during:
(A) Non-Cooperation Movement (1920)
(B) Partition of Bengal (1905)
(C) Quit India Movement (1942)
(D) More than one of the above
(E) None of the above

---

**Q38.** The Partition of Bengal (1905) was announced by which British official?
(A) Lord Irwin
(B) Lord Chelmsford
(C) Lord Curzon
(D) More than one of the above
(E) None of the above

---

**Q39.** The first President of the Indian National Congress (1885, Bombay) was:
(A) A.O. Hume
(B) Bal Gangadhar Tilak
(C) W.C. Bonnerjee (Womesh Chandra Bonnerjee)
(D) More than one of the above
(E) None of the above

---

**Q40.** Who was the President of the INC Gaya Session (1922)?
(A) Mahatma Gandhi
(B) Motilal Nehru
(C) Chittaranjan Das
(D) More than one of the above
(E) None of the above

---

**Q41.** Bihar's peasants during the Non-Cooperation Movement (1920–22) were led by:
(A) Rajendra Prasad
(B) Swami Vidyanand
(C) Jayaprakash Narayan
(D) More than one of the above
(E) None of the above

---

**Q42.** "The Congress is tottering to its fall and one of my great ambitions while in India is to assist it to a peaceful demise." — who said this?
(A) Lord Irwin
(B) Lord Dalhousie
(C) Lord Curzon
(D) More than one of the above
(E) None of the above

---

**Q43.** Raksha Bandhan is observed as "Tree Safety Day" (Van Raksha Diwas) in which state?
(A) Rajasthan
(B) Jharkhand
(C) Madhya Pradesh
(D) More than one of the above
(E) None of the above

---

**Q44.** Birsa Munda claimed to be:
(A) A representative of the British government
(B) An avatar (divine incarnation) called "Dharti Aba" (Father of the Earth)
(C) A leader of the Santhal tribe
(D) More than one of the above
(E) None of the above

---

**Q45.** The Santhal Parganas Tenancy Act (1876) was a direct response to which revolt?
(A) Birsa Munda's Ulgulan
(B) Tana Bhagat Movement
(C) Santhal Rebellion (Hul) of 1855–56
(D) More than one of the above
(E) None of the above

---

**Q46.** Which of the following correctly matches tribal movements with their leaders?
(A) Santhal Rebellion — Sidhu & Kanhu Murmu | Ulgulan — Birsa Munda | Tana Bhagat — Jatra Bhagat
(B) Santhal Rebellion — Birsa Munda | Ulgulan — Jatra Bhagat | Tana Bhagat — Sidhu Murmu
(C) All three movements were led by the same Munda tribe
(D) More than one of the above
(E) None of the above

---

**Q47.** Birsa Munda died on June 9, 1900, in which jail?
(A) Patna Central Jail
(B) Ranchi Jail
(C) Hazaribagh Jail
(D) More than one of the above
(E) None of the above

---

**Q48.** The Swaraj Party (1923) was formed by Chittaranjan Das and Motilal Nehru after the:
(A) Champaran Satyagraha (1917)
(B) INC Gaya Session (1922), following suspension of Non-Cooperation Movement
(C) Quit India Movement (1942)
(D) More than one of the above
(E) None of the above

---

**Q49.** Which of the following CORRECTLY identifies the Tana Bhagat movement?
1. It started in 1914
2. It involved the Oraon tribe
3. It was led by Jatra Bhagat
4. It was a non-violent movement

(A) Only 1 and 2 are correct
(B) Only 1, 2, and 3 are correct
(C) All four are correct — answer is (D) More than one of the above
(D) More than one of the above
(E) None of the above

---

**Q50.** The landmark event of October 16, 1905 (day Bengal Partition took effect) was observed by the Indian public by:
(A) A general strike across all of British India
(B) Tying Rakhi on each other's wrists as a symbol of Hindu-Muslim unity
(C) Burning British goods publicly
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY

## ⚠️ Attempt all 50 questions BEFORE checking answers!

---

### CS Answers (Q1–Q25):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 1 | (B) | OSI = 7 layers; TCP/IP = 4 layers |
| 2 | (C) | Host-to-Host = Transport layer (OSI Layer 4) |
| 3 | (B) | MAC performs medium-dependent functions |
| 4 | (C) | IPv6 = 128 bits |
| 5 | (B) | TCP = connection-oriented + 3-way handshake |
| 6 | (B) | Mail server sending to another = SMTP CLIENT |
| 7 | (B) | PING = packet loss + round-trip delay |
| 8 | (C) | MQTT = IoT device communication protocol |
| 9 | (B) | Socket = endpoint of inter-process communication |
| 10 | (C) | Peer-to-peer is NOT a topology |
| 11 | (C) | Optical fiber = highest speed + EM immune |
| 12 | (C) | Switched networks prevent packet sniffing |
| 13 | (C) | Private key kept by RECEIVER |
| 14 | (C) | Computer ↔ Keyboard = SIMPLEX |
| 15 | (B) | TDM: time slots → FRAMES |
| 16 | (B) | Memory-mapped I/O = shared address space |
| 17 | (C) | Program-controlled I/O = POLLING |
| 18 | (B) | Subnet mask = identifies network portion of IP |
| 19 | (C) | Router = Network layer, connects multiple networks |
| 20 | (B) | WWW = collection of hyperlinked documents |
| 21 | (C) | UTP = vulnerable to EM interference |
| 22 | (B) | 3-way handshake: SYN → SYN-ACK → ACK |
| 23 | (C) | Network layer = routing and forwarding |
| 24 | (C) | WDM = wavelength-based, used with optical fiber |
| 25 | (B) | Full access rights for all = system integrity breach |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | Santhal Rebellion = Sidhu and Kanhu Murmu |
| 27 | (C) | Against zamindars + moneylenders + British |
| 28 | (C) | Birsa Munda = Munda tribe |
| 29 | (B) | Ulgulan = Great Tumult |
| 30 | (C) | Tana Bhagat = TRIBAL movement (not peasant, not Dalit) |
| 31 | (C) | Tana Bhagat led by JATRA BHAGAT |
| 32 | (C) | Tana Bhagat = Oraon (Kurukh) tribe |
| 33 | (B) | Tana Bhagat = non-violent, religious reform + passive resistance |
| 34 | (C) | Santhal (1855) → Birsa (1899) → Tana Bhagat (1914) |
| 35 | (B) | Santhal Rebellion = Rajmahal Hills |
| 36 | (C) | Chota Nagpur Tenancy Act 1908 = after Birsa's Ulgulan |
| 37 | (B) | Swadeshi + Boycott FIRST used during Bengal Partition (1905) |
| 38 | (C) | Bengal Partition announced by LORD CURZON |
| 39 | (C) | First INC President = W.C. Bonnerjee (1885, Bombay) |
| 40 | (C) | INC Gaya Session 1922 = CHITTARANJAN DAS |
| 41 | (B) | Bihar peasants in NCM = SWAMI VIDYANAND |
| 42 | (C) | "Congress tottering" = LORD CURZON |
| 43 | (C) | Raksha Bandhan as Tree Day = MADHYA PRADESH |
| 44 | (B) | Birsa claimed to be avatar "Dharti Aba" |
| 45 | (C) | Santhal Parganas Tenancy Act (1876) = after Santhal Rebellion |
| 46 | (A) | All three matches are correct |
| 47 | (B) | Birsa Munda died in RANCHI JAIL |
| 48 | (B) | Swaraj Party formed after INC Gaya Session 1922 |
| 49 | (D) | All four statements about Tana Bhagat are correct |
| 50 | (B) | Oct 16, 1905: people tied Rakhi as a symbol of unity |

---
---

# 🔁 DAY 51 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Computer Networks

```
Layer counts: OSI = 7 | TCP/IP = 4
Host-to-Host   = Transport layer (OSI Layer 4)
MAC sublayer   = medium-dependent functions
IPv6           = 128 bits (NOT 32, 64, or 256)
TCP            = connection-oriented + 3-way handshake (SYN→SYN-ACK→ACK)
SMTP client    = mail server SENDING to another server
PING           = packet loss + round-trip delay
MQTT           = IoT protocol
Socket         = endpoint of inter-process communication
Peer-to-peer   = NOT a topology (network type, not topology)
Optical fiber  = highest speed + immune to EM interference
UTP            = vulnerable to EM interference
Switched ntwk  = prevents packet sniffing
Private key    = kept by RECEIVER
Simplex        = one-way only (keyboard → computer)
TDM            = time slots → FRAMES
Memory-mapped I/O = I/O + memory share SAME address space
Polling        = program-controlled I/O
Router         = Network layer (connects networks)
Switch         = Data Link layer (connects LAN devices)
```

---

## ⚡ RAPID FIRE — Tribal Movements & INC Sessions

```
CHRONOLOGICAL ORDER (MEMORIZE):
  Santhal (1855) → Birsa Munda (1899) → Tana Bhagat (1914)

SANTHAL REBELLION:
  Year: 1855–56 | Leaders: Sidhu + Kanhu Murmu | Area: Rajmahal Hills
  Result → Santhal Parganas Tenancy Act (1876)

BIRSA MUNDA (ULGULAN):
  Year: 1899–1900 | Tribe: Munda | C-in-C: Gaya Munda
  Birsa = "Dharti Aba" (avatar) | Died: Ranchi Jail, June 9, 1900
  Result → Chota Nagpur Tenancy Act (1908)

TANA BHAGAT:
  Year: 1914 | Tribe: ORAON | Leader: JATRA BHAGAT
  Type: TRIBAL (NOT peasant, NOT Dalit) ← #1 PYQ trap
  Nature: NON-VIOLENT (religious reform + passive resistance)

SWADESHI + BOYCOTT first used = BENGAL PARTITION (1905), NOT NCM 1920
CURZON partitioned Bengal AND said "Congress tottering" → both = CURZON

INC SESSIONS:
  First INC President  = W.C. BONNERJEE (Bombay, 1885)
  INC Gaya 1922        = CHITTARANJAN DAS
  Bihar NCM peasants   = SWAMI VIDYANAND led them
  "Congress tottering" = LORD CURZON said it

Raksha Bandhan as Tree Day = MADHYA PRADESH
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. Tribal movements in order: **Santhal (1855) → Birsa Munda (1899) → Tana Bhagat (1914)** — all tribal, not peasant
2. Tana Bhagat = **Oraon tribe** + **Jatra Bhagat** as leader + **non-violent** + **TRIBAL** (never write peasant in exam)
3. Swadeshi and Boycott **first** adopted during **Bengal Partition (1905)** — NOT during NCM 1920
4. INC Gaya Session 1922 president = **Chittaranjan Das**; First INC president = **W.C. Bonnerjee** (1885)
5. Networks: IPv6 = **128 bits**; MQTT = IoT; Private key = kept by **Receiver**; Peer-to-peer = NOT a topology

---

*Next: Day 52 — Ancient Indian History (Indus Valley, Mauryas, Guptas) + OOP Quick Revision*
