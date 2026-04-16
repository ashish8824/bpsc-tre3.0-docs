# 📅 BPSC TRE 4.0 — DAY 47
## CS Topic: Network Topologies & Network Devices
## GS Topic: Bihar GK — Famous Personalities, Nicknames & Contributions
### 🎯 Target: 130+/150 | TOP 50 RANK

---

> **Topper Benchmark:** Network Topologies appear in 2–3 questions EVERY TRE paper.
> The classic trap — "Peer-to-Peer is NOT a topology" — has appeared in TRE 1.0, 2.0, and 3.0.
> Bihar GK (Famous Personalities) is Bihar-specific and high-value — 3–5 marks guaranteed if prepared.
> This day alone can secure you 6–8 marks in the actual exam. Don't skip!

---

## ⏰ TODAY'S STUDY SCHEDULE

| Slot | Duration | Activity |
|------|----------|----------|
| Morning | 1.5 hrs | CS: Network Topologies + Devices — full mastery |
| Afternoon | 1 hr | GS: Bihar Famous Personalities — nicknames, works, institutions |
| Evening | 1 hr | Solve all 50 MCQs (25 CS + 25 GS) |
| Night | 30 min | Write your 5-bullet summary for each section |

---

---

# 🖥️ PART A — COMPUTER SCIENCE
# NETWORK TOPOLOGIES & NETWORK DEVICES

---

## 🔑 WHY THIS TOPIC MATTERS FOR BPSC TRE 4.0

| Exam | Topology/Device Questions |
|------|--------------------------|
| TRE 1.0 | 2 questions — Star topology, hub vs switch |
| TRE 2.0 | 3 questions — Mesh topology, peer-to-peer trap, router |
| TRE 3.0 | 3 questions — Bus topology, bridge, WWW definition |
| **TRE 4.0 Expected** | **3–4 questions** |

---

## 🌐 WHAT IS NETWORK TOPOLOGY?

**Network Topology** = The **physical or logical arrangement** of computers and devices in a network.

Think of it like the **floor plan of a building** — it shows how all the rooms (devices) are connected to each other.

### Two Types:
```
┌─────────────────────────────────────────────────────────┐
│ PHYSICAL TOPOLOGY  │ How cables/devices are physically  │
│                    │ laid out in real space              │
├─────────────────────────────────────────────────────────┤
│ LOGICAL TOPOLOGY   │ How data actually FLOWS through    │
│                    │ the network (may differ from       │
│                    │ physical layout)                    │
└─────────────────────────────────────────────────────────┘
```

---

## 📡 THE 6 MAIN NETWORK TOPOLOGIES

---

### 1. 🚌 BUS TOPOLOGY

```
         ALL DEVICES CONNECTED TO ONE CENTRAL CABLE (BUS/BACKBONE)

   PC1    PC2    PC3    PC4    PC5
    │      │      │      │      │
────┴──────┴──────┴──────┴──────┴──── ◄── BACKBONE CABLE (Bus)
                                    ▲
                               TERMINATOR
                           (prevents signal bounce)
```

**Key Features:**
```
┌────────────────────────────────────────────────────────┐
│ Cable used       │ Single backbone cable (coaxial)     │
│ Data flow        │ Both directions on same cable       │
│ Terminators      │ REQUIRED at both ends               │
│ Failure effect   │ If backbone fails → ENTIRE network  │
│                  │ goes down                           │
│ Device failure   │ Only THAT device fails              │
│ Cost             │ CHEAPEST topology                   │
│ Installation     │ Easy — just connect to backbone     │
│ Scalability      │ Difficult to expand                 │
│ Signal collision │ YES — only one device can send      │
│                  │ at a time (CSMA/CD protocol)        │
└────────────────────────────────────────────────────────┘
```

**Real-World Analogy:** Like a train line — all stations connect to ONE track. If the track breaks, no trains move.

**🚨 PYQ TRAPS for Bus Topology:**
- If backbone cable breaks → **entire network fails**
- Terminators are **mandatory** at both ends
- Bus is the **cheapest** to install but has **highest collision rate**

---

### 2. ⭐ STAR TOPOLOGY

```
                  ┌─────────┐
                  │   HUB/  │
                  │ SWITCH  │  ◄── CENTRAL DEVICE (Required!)
                  │(Center) │
                  └────┬────┘
           ┌───────────┼───────────┐
           │           │           │
          PC1         PC2         PC3
           │                       │
          PC4                     PC5

    All devices connect ONLY to the central hub/switch.
    Devices do NOT connect directly to each other.
```

**Key Features:**
```
┌────────────────────────────────────────────────────────┐
│ Central device   │ Hub or Switch (MANDATORY)           │
│ Device failure   │ Only that device fails              │
│ Central failure  │ ENTIRE network goes down            │
│ Cost             │ More cable needed than Bus          │
│ Scalability      │ EASY — just add to hub/switch       │
│ Performance      │ BETTER than Bus (less collision)    │
│ Maintenance      │ EASY — isolate faulty device        │
│ Most common?     │ YES — most popular in modern LANs   │
└────────────────────────────────────────────────────────┘
```

**Real-World Analogy:** Like a flight hub (Delhi airport) — all cities connect TO Delhi. If Delhi airport closes, all connections break.

**🚨 PYQ TRAP:** Star topology **REQUIRES a central controller (Hub/Switch)**. Without it, there is NO star topology!

---

### 3. 💍 RING TOPOLOGY

```
        PC1
       /    \
     PC5    PC2
      |      |
     PC4    PC3
       \    /
        ────

   Data travels in ONE direction (unidirectional) or both (bidirectional)
   Each device connects to EXACTLY two neighbors
```

**Key Features:**
```
┌────────────────────────────────────────────────────────┐
│ Direction        │ Unidirectional (usually clockwise)  │
│ Token            │ Token Ring uses TOKEN passing       │
│ Device failure   │ Can affect entire network           │
│ Performance      │ Better than Bus under heavy load    │
│ Failure handling │ DUAL ring (FDDI) = fault tolerant   │
│ Installation     │ More complex than Bus/Star          │
└────────────────────────────────────────────────────────┘
```

**Special Types:**
- **Token Ring (IEEE 802.5):** Uses token passing — only device with token can send
- **FDDI (Fiber Distributed Data Interface):** Dual ring — if one ring fails, other works

---

### 4. 🕸️ MESH TOPOLOGY

```
    PC1 ──────── PC2
     │ \        / │
     │  \      /  │
     │   \    /   │
     │    \  /    │
    PC4 ──────── PC3

  EVERY device connects to EVERY other device
```

**Two Types:**
```
┌─────────────────┬──────────────────────────────────────┐
│ FULL MESH       │ Every device connects to every other │
│                 │ Number of links = n(n-1)/2           │
│                 │ (n = number of devices)              │
├─────────────────┼──────────────────────────────────────┤
│ PARTIAL MESH    │ Some devices connect to all,         │
│                 │ some connect to only a few           │
└─────────────────┴──────────────────────────────────────┘
```

**Number of Links Formula (VERY IMPORTANT FOR BPSC!):**
```
For n devices in Full Mesh:
Number of links = n × (n-1) / 2

Examples:
  4 devices → 4×3/2 = 6 links
  5 devices → 5×4/2 = 10 links
  6 devices → 6×5/2 = 15 links
```

**Key Features:**
```
┌────────────────────────────────────────────────────────┐
│ Reliability      │ HIGHEST — multiple paths exist      │
│ Fault tolerance  │ HIGHEST — if one link fails,        │
│                  │ data uses another path              │
│ Cost             │ MOST EXPENSIVE topology             │
│ Cabling          │ MAXIMUM cable required              │
│ Use case         │ Military, banks, critical systems   │
│ Privacy          │ HIGH — dedicated point-to-point     │
└────────────────────────────────────────────────────────┘
```

---

### 5. 🌳 TREE TOPOLOGY (Hierarchical)

```
                    ROOT (Top Hub)
                   /              \
             Hub A                Hub B
            /     \              /     \
          PC1    PC2           PC3    PC4
          / \                  / \
        PC5 PC6             PC7 PC8

   Combination of Star topologies in a hierarchy.
   Also called HIERARCHICAL topology.
```

**Key Features:**
```
┌────────────────────────────────────────────────────────┐
│ Structure        │ Hierarchical — parent-child nodes   │
│ Root failure     │ ENTIRE network goes down            │
│ Branch failure   │ Only that branch's devices fail     │
│ Scalability      │ GOOD — can add branches easily      │
│ Use case         │ Wide Area Networks (WAN), Corporate │
│ Combination of   │ Multiple Star topologies connected  │
└────────────────────────────────────────────────────────┘
```

---

### 6. 🔀 HYBRID TOPOLOGY

```
   HYBRID = Two or more different topologies combined

   Example:
   ┌─────────────────────────────────┐
   │    STAR topology in Office A    │
   │    PC1──HUB──PC2                │
   └──────────────┬──────────────────┘
                  │  (BUS backbone)
   ┌──────────────┴──────────────────┐
   │    RING topology in Office B    │
   │    PC3──PC4──PC5──PC3           │
   └─────────────────────────────────┘
```

**Key Fact:** Hybrid = combination of 2+ topologies. Used in large organizations.

---

## 📊 MASTER TOPOLOGY COMPARISON TABLE

```
┌──────────┬─────────┬──────────────┬────────────┬──────────────────────┐
│ Topology │  Cost   │ Reliability  │ Scalability│ Key Feature          │
├──────────┼─────────┼──────────────┼────────────┼──────────────────────┤
│ Bus      │ Lowest  │ Lowest       │ Hard       │ Single backbone;     │
│          │         │              │            │ backbone fail=all    │
│          │         │              │            │ down                 │
├──────────┼─────────┼──────────────┼────────────┼──────────────────────┤
│ Star     │ Medium  │ Medium       │ Easy       │ Central hub needed;  │
│          │         │              │            │ most popular today   │
├──────────┼─────────┼──────────────┼────────────┼──────────────────────┤
│ Ring     │ Medium  │ Medium       │ Medium     │ Token passing;       │
│          │         │              │            │ unidirectional       │
├──────────┼─────────┼──────────────┼────────────┼──────────────────────┤
│ Mesh     │ Highest │ Highest      │ Difficult  │ Every device to every│
│          │         │              │            │ device; n(n-1)/2     │
│          │         │              │            │ links                │
├──────────┼─────────┼──────────────┼────────────┼──────────────────────┤
│ Tree     │ Medium  │ Medium       │ Good       │ Hierarchical;        │
│          │         │              │            │ root failure=all     │
├──────────┼─────────┼──────────────┼────────────┼──────────────────────┤
│ Hybrid   │ Varies  │ Varies       │ Good       │ Combination of 2+    │
└──────────┴─────────┴──────────────┴────────────┴──────────────────────┘
```

---

## 🚨 CRITICAL BPSC TRAP — PEER-TO-PEER IS NOT A TOPOLOGY!

```
┌─────────────────────────────────────────────────────────────┐
│                    ❌ COMMON EXAM TRAP                       │
│                                                             │
│  Question: "Which of the following is NOT a network         │
│  topology?"                                                 │
│                                                             │
│  Options include: Bus, Star, Ring, Peer-to-Peer, Mesh       │
│                                                             │
│  ANSWER: Peer-to-Peer (P2P)                                 │
│                                                             │
│  WHY? Peer-to-Peer is a NETWORK MODEL/TYPE,                 │
│  NOT a physical or logical topology!                        │
│                                                             │
│  P2P = Each computer acts as both client AND server         │
│  Topology = Physical/logical arrangement of connections     │
│                                                             │
│  These are DIFFERENT concepts!                              │
└─────────────────────────────────────────────────────────────┘
```

**Other Non-Topologies (also used as traps):**
- Client-Server → Network model, NOT topology
- Peer-to-Peer → Network model, NOT topology
- Intranet/Internet → Network type, NOT topology

---

## 🖥️ NETWORK DEVICES — COMPLETE GUIDE

---

### Device 1: HUB 📡

```
        PC1 ──┐
        PC2 ──┤── HUB ──── All devices receive
        PC3 ──┤            ALL data (broadcast)
        PC4 ──┘
```

```
┌────────────────────────────────────────────────────────┐
│ OSI Layer        │ Physical Layer (Layer 1)            │
│ Function         │ Broadcasts data to ALL ports        │
│ Intelligence     │ NONE — dumb device                  │
│ MAC Address?     │ No — does not read MAC addresses    │
│ Collision        │ YES — creates collision domain      │
│ Security         │ LOW — all devices see all data      │
│ Type             │ Active Hub (with power) or          │
│                  │ Passive Hub (no power)              │
│ Status           │ Mostly OBSOLETE now (replaced by   │
│                  │ switches)                           │
└────────────────────────────────────────────────────────┘
```

---

### Device 2: SWITCH 🔀

```
        PC1 ──┐                PC1 sends to PC3
        PC2 ──┤── SWITCH ──── Switch reads MAC address
        PC3 ──┤               and forwards ONLY to PC3
        PC4 ──┘               (not to PC2 and PC4)
```

```
┌────────────────────────────────────────────────────────┐
│ OSI Layer        │ Data Link Layer (Layer 2)           │
│ Function         │ Forwards data to SPECIFIC device    │
│ Intelligence     │ YES — reads MAC addresses           │
│ MAC Address?     │ YES — maintains MAC address table  │
│ Collision        │ NO — eliminates collision domains   │
│ Security         │ HIGHER than hub                     │
│ Use              │ Connects devices in a LAN           │
│ Status           │ MODERN standard device              │
└────────────────────────────────────────────────────────┘
```

**🚨 Key Difference — Hub vs Switch:**
```
HUB    → Broadcasts to ALL → creates collisions → Layer 1
SWITCH → Sends to SPECIFIC device → eliminates collisions → Layer 2
```

---

### Device 3: ROUTER 🌐

```
        NETWORK A                    NETWORK B
      192.168.1.x                   10.0.0.x
      PC1, PC2, PC3  ──── ROUTER ── PC4, PC5, PC6
                                         │
                                    INTERNET
```

```
┌────────────────────────────────────────────────────────┐
│ OSI Layer        │ Network Layer (Layer 3)             │
│ Function         │ Routes packets between NETWORKS     │
│ Address used     │ IP Address (logical address)        │
│ Intelligence     │ HIGH — uses routing tables          │
│ Use              │ Connect different networks,         │
│                  │ connect LAN to internet             │
│ Protocols        │ OSPF, RIP, BGP (routing protocols) │
│ NAT              │ Yes — Network Address Translation   │
└────────────────────────────────────────────────────────┘
```

---

### Device 4: BRIDGE 🌉

```
      LAN A                              LAN B
   (192.168.1.x)                      (192.168.1.x)
   PC1──PC2──PC3  ──── BRIDGE ────  PC4──PC5──PC6

   Bridge connects TWO LANs of SAME type.
   Works at Layer 2 (Data Link).
```

```
┌────────────────────────────────────────────────────────┐
│ OSI Layer        │ Data Link Layer (Layer 2)           │
│ Function         │ Connects two similar LANs           │
│ Filter           │ Filters traffic based on MAC        │
│ Collision domain │ Separates collision domains         │
│ Difference from  │ Router connects DIFFERENT networks; │
│ Router           │ Bridge connects SAME type LANs      │
└────────────────────────────────────────────────────────┘
```

---

### Device 5: REPEATER 📶

```
   PC1 ────────────── REPEATER ─────────────────── PC2
          (weak signal)           (signal boosted)
```

```
┌────────────────────────────────────────────────────────┐
│ OSI Layer        │ Physical Layer (Layer 1)            │
│ Function         │ Amplifies/regenerates signal        │
│ Purpose          │ Extend network over long distances  │
│ Intelligence     │ NONE — just boosts signal           │
│ Type             │ 2-port device                       │
└────────────────────────────────────────────────────────┘
```

---

### Device 6: GATEWAY 🚪

```
   Corporate LAN  ──── GATEWAY ──── Internet/Different Protocol Network

   Gateway connects networks using DIFFERENT PROTOCOLS.
   Example: Connecting IPv4 network to IPv6 network.
```

```
┌────────────────────────────────────────────────────────┐
│ OSI Layer        │ ALL layers (full protocol           │
│                  │ translation)                        │
│ Function         │ Protocol conversion between         │
│                  │ different network types             │
│ Intelligence     │ HIGHEST among network devices       │
│ Difference from  │ Router connects same-protocol nets; │
│ Router           │ Gateway converts protocols          │
└────────────────────────────────────────────────────────┘
```

---

### Device 7: MODEM 📞

```
   Computer ──── MODEM ──── Phone Line/Cable ──── MODEM ──── Computer
            Digital   Analog/Digital               Digital
```

```
┌────────────────────────────────────────────────────────┐
│ Full form        │ MOdulator-DEModulator               │
│ OSI Layer        │ Physical Layer (Layer 1)            │
│ Function         │ Converts digital ↔ analog signals   │
│ Modulation       │ Digital → Analog (for transmission) │
│ Demodulation     │ Analog → Digital (for reception)   │
│ Use              │ Internet over telephone lines       │
└────────────────────────────────────────────────────────┘
```

**Memory:** MODEM = **MO**dulate + **DEM**odulate

---

## 📊 MASTER DEVICE COMPARISON TABLE

```
┌───────────┬─────────┬────────────────────────────────────────┐
│ Device    │ OSI     │ Key Function                           │
│           │ Layer   │                                        │
├───────────┼─────────┼────────────────────────────────────────┤
│ Hub       │ Layer 1 │ Broadcasts to ALL ports                │
│           │Physical │ (dumb, creates collisions)             │
├───────────┼─────────┼────────────────────────────────────────┤
│ Repeater  │ Layer 1 │ Boosts/regenerates signal              │
│           │Physical │ (extends cable distance)               │
├───────────┼─────────┼────────────────────────────────────────┤
│ Modem     │ Layer 1 │ Digital ↔ Analog conversion           │
│           │Physical │                                        │
├───────────┼─────────┼────────────────────────────────────────┤
│ Bridge    │ Layer 2 │ Connects two similar LANs              │
│           │Data Link│ (uses MAC address)                     │
├───────────┼─────────┼────────────────────────────────────────┤
│ Switch    │ Layer 2 │ Sends to specific device               │
│           │Data Link│ (eliminates collisions)                │
├───────────┼─────────┼────────────────────────────────────────┤
│ Router    │ Layer 3 │ Routes between different networks      │
│           │Network  │ (uses IP address)                      │
├───────────┼─────────┼────────────────────────────────────────┤
│ Gateway   │ All     │ Protocol conversion between networks   │
│           │Layers   │ (highest intelligence)                 │
└───────────┴─────────┴────────────────────────────────────────┘
```

---

## 🌍 WHAT IS WWW?

**WWW = World Wide Web**

```
┌─────────────────────────────────────────────────────────────┐
│ IMPORTANT DISTINCTION — Very common PYQ trap:               │
│                                                             │
│  INTERNET ≠ WWW                                             │
│                                                             │
│  INTERNET = The global network infrastructure              │
│             (physical hardware, cables, routers)            │
│                                                             │
│  WWW = A SERVICE running ON the Internet                   │
│        = Collection of hyperlinked documents (web pages)   │
│          accessible via web browsers using HTTP            │
│                                                             │
│  Created by: Tim Berners-Lee (1989–1991) at CERN           │
│                                                             │
│  Other services on Internet: Email, FTP, Telnet, DNS       │
│  → These are NOT part of WWW but use the Internet          │
└─────────────────────────────────────────────────────────────┘
```

**Key WWW Facts:**
- WWW = collection of **hyperlinked documents** on the Internet
- Accessed using **web browsers** (Chrome, Firefox, etc.)
- Uses **HTTP/HTTPS** protocol
- Created by **Tim Berners-Lee** in **1989**
- First website went live: **August 6, 1991**

---

## 🌐 TYPES OF NETWORKS

```
┌──────┬───────────────┬──────────────┬──────────────────────────┐
│ Type │ Full Form     │ Coverage     │ Example                  │
├──────┼───────────────┼──────────────┼──────────────────────────┤
│ PAN  │ Personal Area │ 1–10 meters  │ Bluetooth, USB           │
│      │ Network       │              │                          │
├──────┼───────────────┼──────────────┼──────────────────────────┤
│ LAN  │ Local Area    │ Building/    │ Office network, School   │
│      │ Network       │ Campus       │ computer lab             │
├──────┼───────────────┼──────────────┼──────────────────────────┤
│ MAN  │ Metropolitan  │ City-wide    │ Cable TV network,        │
│      │ Area Network  │              │ city government network  │
├──────┼───────────────┼──────────────┼──────────────────────────┤
│ WAN  │ Wide Area     │ Country/     │ Internet, bank networks  │
│      │ Network       │ Global       │ across states            │
└──────┴───────────────┴──────────────┴──────────────────────────┘
```

---

## ✅ CS CONCEPT SUMMARY — DAY 47

| # | Key Fact | Never Forget |
|---|----------|-------------|
| 1 | Bus topology = single backbone | Backbone breaks → ALL devices fail |
| 2 | Star topology = central hub/switch | Without hub/switch, no star topology |
| 3 | Ring topology = token passing | Data flows in ONE direction |
| 4 | Mesh topology = n(n-1)/2 links | Most expensive, most reliable |
| 5 | Tree = hierarchical | Root fails → entire network down |
| 6 | Peer-to-Peer = NOT a topology | It is a network MODEL |
| 7 | Hub = Layer 1 = broadcasts ALL | Creates collision domain |
| 8 | Switch = Layer 2 = specific MAC | Eliminates collisions |
| 9 | Router = Layer 3 = IP routing | Connects different networks |
| 10 | WWW ≠ Internet | WWW = collection of hyperlinked docs on Internet |

---

---

# 📚 PART B — GENERAL STUDIES (GS)
# BIHAR GK — FAMOUS PERSONALITIES, NICKNAMES & CONTRIBUTIONS

---

## 🔑 WHY THIS TOPIC MATTERS FOR BPSC TRE 4.0

Bihar GK is tested directly in TRE exams. Famous personalities from Bihar — their:
- **Nicknames / Titles**
- **Known for / Major works**
- **Institutions they founded**
- **Bihar-specific achievements**

This topic consistently yields **3–5 questions** in GS of BPSC TRE.

---

## 🏛️ SECTION 1: NATIONAL LEADERS FROM BIHAR

---

### 1. DR. RAJENDRA PRASAD (1884–1963)

```
┌─────────────────────────────────────────────────────────────┐
│ Born              │ Ziradei, Siwan District, Bihar          │
│ Nickname          │ "Deshratna" (Jewel of the Nation)       │
│ Known for         │ First President of India (1950–1962)    │
│ Role in Congress  │ President of Indian National Congress   │
│                   │ multiple times                          │
│ Role in Const.    │ Chairman of Constituent Assembly        │
│ Education         │ Studied at Calcutta University          │
│ First Prez tenure │ Longest-serving President (12 years)   │
│ Award             │ Bharat Ratna (1962)                     │
│ Death             │ February 28, 1963                       │
└─────────────────────────────────────────────────────────────┘
```

**Key Facts for Exam:**
- Only person to serve as **both President AND Congress President** simultaneously
- Chairman of the **Constituent Assembly** — drafted Indian Constitution
- Born in **Ziradei, Siwan** (not Patna — common trap!)
- Received **Bharat Ratna** posthumously

---

### 2. JAYAPRAKASH NARAYAN — "JP" (1902–1979)

```
┌─────────────────────────────────────────────────────────────┐
│ Born              │ Sitab Diara, Saran District, Bihar      │
│ Nickname          │ "Lok Nayak" (People's Hero)             │
│ Also called       │ "JP"                                    │
│ Known for         │ JP Movement (1974) against Emergency    │
│ Role              │ Socialistic leader; against corruption  │
│ Movement          │ Total Revolution (Sampoorna Kranti)     │
│ Slogan            │ "Singhasan Khali Karo, Janta Ayee Hai" │
│ Award             │ Bharat Ratna (1999 — posthumously)      │
│ Association       │ Founded Socialist Party of India        │
└─────────────────────────────────────────────────────────────┘
```

**Key Facts for Exam:**
- Title "**Lok Nayak**" = People's Hero
- Led the **JP Movement (1974)** against Indira Gandhi's government
- His call for "**Total Revolution (Sampoorna Kranti)**" inspired the post-Emergency political change
- Born in **Sitab Diara, Saran** district

---

### 3. BABU KUNWAR SINGH (1777–1858)

```
┌─────────────────────────────────────────────────────────────┐
│ Born              │ Jagdishpur, Bhojpur District, Bihar     │
│ Nickname          │ "Veer Kunwar Singh" / "Lion of 1857"   │
│ Known for         │ Leading revolt of 1857 in Bihar         │
│ Age during revolt │ ~80 years old — still fought bravely!  │
│ Famous battle     │ Battle of Jagdishpur (April 1858)       │
│ Tribute           │ Kunwar Singh's birthday = "Veer Kunwar  │
│                   │ Singh Jayanti" celebrated in Bihar      │
└─────────────────────────────────────────────────────────────┘
```

**Key Facts for Exam:**
- Fought the 1857 revolt at **age ~80** — most remarkable Bihar hero
- **Jagdishpur, Bhojpur** district is his birthplace — frequently asked
- Won the **Battle of Jagdishpur** against the British

---

### 4. MAULANA MAZHARUL HAQ (1866–1930)

```
┌─────────────────────────────────────────────────────────────┐
│ Born              │ Patna, Bihar                            │
│ Nickname          │ "Father of Sadaqat Ashram"              │
│ Known for         │ Founded Sadaqat Ashram, Patna           │
│                   │ Important Congress leader from Bihar    │
│ Role              │ Participated in Non-Cooperation Movement│
│ Key event         │ Champaran (1917) — with Gandhi          │
└─────────────────────────────────────────────────────────────┘
```

---

### 5. SACHIDANANDA SINHA (1871–1950)

```
┌─────────────────────────────────────────────────────────────┐
│ Known for         │ First Speaker (President) of            │
│                   │ Constituent Assembly (briefly)          │
│                   │ (Before Rajendra Prasad took over)      │
│ Role              │ Temporary Chairman of Constituent       │
│                   │ Assembly when it first met              │
│ From              │ Bihar                                   │
└─────────────────────────────────────────────────────────────┘
```

---

## 🏛️ SECTION 2: SAINTS, SCHOLARS & REFORMERS FROM BIHAR

---

### 6. CHANAKYA / KAUTILYA (350–275 BC)

```
┌─────────────────────────────────────────────────────────────┐
│ Real Name         │ Vishnugupta (also Kautilya, Chanakya)  │
│ Known for         │ Wrote Arthashastra (economics/polity)  │
│                   │ Guided Chandragupta Maurya              │
│ Birthplace        │ Near Pataliputra (ancient Patna), Bihar │
│ Arthashastra      │ Ancient treatise on statecraft,         │
│                   │ economics, and military strategy        │
│ Called            │ "Indian Machiavelli"                   │
│ Role              │ Prime Minister (Amatya) to             │
│                   │ Chandragupta Maurya                    │
└─────────────────────────────────────────────────────────────┘
```

**Key Facts:** Arthashastra = economics + politics + military strategy. Chanakya = "Indian Machiavelli."

---

### 7. ARYABHATA (476–550 AD)

```
┌─────────────────────────────────────────────────────────────┐
│ Born              │ Kusumapura (modern Patna), Bihar        │
│ Known for         │ Discovered ZERO (0)                    │
│                   │ Calculated value of π (pi)             │
│                   │ Heliocentric theory (Earth revolves    │
│                   │ around Sun)                            │
│                   │ Aryabhatiya — mathematical treatise    │
│ ISRO tribute      │ India's first satellite named          │
│                   │ "Aryabhata" (1975) in his honor        │
└─────────────────────────────────────────────────────────────┘
```

**🚨 KEY EXAM FACT:** Aryabhata is from Bihar (Kusumapura = Patna area). First Indian satellite = Aryabhata (1975).

---

### 8. SURDAS (15th–16th Century)

```
┌─────────────────────────────────────────────────────────────┐
│ Known for         │ Devotional poet — Krishna Bhakti        │
│ Major Work        │ Sursagar (devotional songs on Krishna) │
│ Language          │ Braj Bhasha                            │
│ Disciple of       │ Vallabhacharya                         │
│ Style             │ Bhakti movement poet; blind poet       │
└─────────────────────────────────────────────────────────────┘
```

---

## 🏛️ SECTION 3: MODERN BIHAR — CHIEF MINISTERS & ADMINISTRATORS

---

### 9. SRI KRISHNA SINHA (1887–1961)

```
┌─────────────────────────────────────────────────────────────┐
│ Known as          │ "Bihar Kesari" (Lion of Bihar)          │
│ Role              │ First Chief Minister of Bihar           │
│                   │ (1946–1961) — longest serving CM Bihar │
│ Born              │ Munger District, Bihar                  │
│ Freedom struggle  │ Active participant; jailed by British  │
│ Legacy            │ Served as CM for 15 years              │
└─────────────────────────────────────────────────────────────┘
```

**🚨 KEY EXAM FACT:** Sri Krishna Sinha = "Bihar Kesari" = First CM of Bihar.

---

### 10. KARPOORI THAKUR (1924–1988)

```
┌─────────────────────────────────────────────────────────────┐
│ Known as          │ "Jan Nayak" (People's Leader)           │
│ Role              │ Chief Minister of Bihar (twice)         │
│                   │ (1970–71 and 1977–79)                   │
│ Known for         │ OBC reservations in Bihar               │
│                   │ Education for weaker sections           │
│ Award             │ Bharat Ratna (2024 — posthumously)      │
│ Born              │ Pitaunjhia, Samastipur, Bihar           │
└─────────────────────────────────────────────────────────────┘
```

**🚨 KEY EXAM FACT:** Karpoori Thakur received **Bharat Ratna in 2024** — this is VERY recent and likely in TRE 4.0!

---

## 🏛️ SECTION 4: SCIENTISTS & ACADEMICS FROM BIHAR

---

### 11. JAGADISH CHANDRA BOSE (connection to Bihar)

- Not from Bihar but frequently associated in Bihar exams
- Proved plants have life (sensitivity)

---

### 12. BIHAR-ASSOCIATED SCIENTISTS

```
┌──────────────────┬──────────────────────────────────────────┐
│ Name             │ Known For                                │
├──────────────────┼──────────────────────────────────────────┤
│ Aryabhata        │ Zero, Pi, Solar system — Patna/Bihar     │
│ Chanakya         │ Arthashastra — near Patna                │
│ Vatsyayana       │ Kamasutra — from Pataliputra (Bihar)     │
│ Nagarjuna        │ Buddhist philosopher; Nalanda            │
└──────────────────┴──────────────────────────────────────────┘
```

---

## 🏛️ SECTION 5: NICKNAMES — THE MOST IMPORTANT LIST FOR EXAM

### Bihar-Specific Nicknames:
```
┌──────────────────────────┬──────────────────────────────────┐
│ Nickname                 │ Person                           │
├──────────────────────────┼──────────────────────────────────┤
│ Bihar Kesari             │ Sri Krishna Sinha (1st CM Bihar) │
│ Lok Nayak                │ Jayaprakash Narayan (JP)         │
│ Jan Nayak                │ Karpoori Thakur                  │
│ Deshratna                │ Dr. Rajendra Prasad              │
│ Veer Kunwar Singh        │ Kunwar Singh (1857 hero)         │
│ Lion of 1857 (Bihar)     │ Kunwar Singh                     │
│ Indian Machiavelli       │ Chanakya / Kautilya              │
└──────────────────────────┴──────────────────────────────────┘
```

### National Nicknames (Frequently Asked in Bihar Exams):
```
┌───────────────────────────┬──────────────────────────────────┐
│ Nickname                  │ Person                           │
├───────────────────────────┼──────────────────────────────────┤
│ Father of the Nation      │ Mahatma Gandhi                   │
│ Mahatma                   │ Mahatma Gandhi                   │
│ Bapu                      │ Mahatma Gandhi                   │
│ Chacha (Uncle of India)   │ Jawaharlal Nehru                 │
│ Panditji                  │ Jawaharlal Nehru                 │
│ Netaji                    │ Subhas Chandra Bose              │
│ Iron Man of India         │ Sardar Vallabhbhai Patel         │
│ Sardar                    │ Sardar Vallabhbhai Patel         │
│ Frontier Gandhi           │ Khan Abdul Ghaffar Khan          │
│ Bihar Gandhi              │ Dr. Rajendra Prasad              │
│ Grand Old Man of India    │ Dadabhai Naoroji                 │
│ Nightingale of India      │ Sarojini Naidu                   │
│ Father of Indian Const.   │ B.R. Ambedkar                   │
│ Lal Bal Pal               │ Lala Lajpat Rai, Bal G. Tilak,  │
│                           │ Bipin Chandra Pal                │
│ Lokmanya                  │ Bal Gangadhar Tilak              │
│ Father of White Revolution│ Verghese Kurien                  │
│ Father of Green Revolution│ M.S. Swaminathan (India)         │
│ Father of Atomic Energy   │ Homi Jehangir Bhabha             │
│ Father of ISRO            │ Vikram Sarabhai                  │
│ Missile Man of India      │ Dr. A.P.J. Abdul Kalam           │
│ People's President        │ Dr. A.P.J. Abdul Kalam           │
└───────────────────────────┴──────────────────────────────────┘
```

---

## 🏛️ SECTION 6: IMPORTANT INSTITUTIONS IN BIHAR

```
┌─────────────────────────────────────────────────────────────────────┐
│ Institution              │ Location      │ Significance             │
├─────────────────────────────────────────────────────────────────────┤
│ Nalanda University       │ Rajgir, Nalanda│ Ancient center of      │
│ (Ancient)                │               │ learning (5th–12th c.) │
│ Nalanda University       │ Rajgir        │ Revived in 2014         │
│ (Modern)                 │               │                         │
├─────────────────────────────────────────────────────────────────────┤
│ Vikramshila University   │ Bhagalpur     │ Ancient Buddhist        │
│ (Ancient ruins)          │               │ university             │
├─────────────────────────────────────────────────────────────────────┤
│ Patna University         │ Patna         │ Oldest university in   │
│                          │               │ Bihar (est. 1917)      │
├─────────────────────────────────────────────────────────────────────┤
│ Bihar Vidhan Sabha       │ Patna         │ State legislature       │
├─────────────────────────────────────────────────────────────────────┤
│ Sadaqat Ashram           │ Patna         │ Founded by Maulana     │
│                          │               │ Mazharul Haq           │
├─────────────────────────────────────────────────────────────────────┤
│ IIT Patna                │ Bihta, Patna  │ Premier engineering    │
│                          │               │ institute              │
├─────────────────────────────────────────────────────────────────────┤
│ NIT Patna                │ Patna         │ National Inst. of Tech  │
├─────────────────────────────────────────────────────────────────────┤
│ AIIMS Patna              │ Patna         │ Premier medical college │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 🏛️ SECTION 7: BHARAT RATNA AWARDEES FROM BIHAR

```
┌────────────────────────┬──────────┬───────────────────────────┐
│ Name                   │ Year     │ Known For                 │
├────────────────────────┼──────────┼───────────────────────────┤
│ Dr. Rajendra Prasad    │ 1962     │ First President of India  │
│ Jayaprakash Narayan    │ 1999*    │ JP Movement, Lok Nayak    │
│ Karpoori Thakur        │ 2024*    │ Jan Nayak, Bihar CM       │
└────────────────────────┴──────────┴───────────────────────────┘
* = Posthumously awarded
```

**🚨 EXAM ALERT:** Karpoori Thakur's Bharat Ratna (2024) is a **recent current affairs fact** — very likely to appear in TRE 4.0!

---

## 🏛️ SECTION 8: IMPORTANT PLACES IN BIHAR & THEIR SIGNIFICANCE

```
┌──────────────────────────────────────────────────────────────────┐
│ Place              │ District       │ Significance               │
├──────────────────────────────────────────────────────────────────┤
│ Bodh Gaya          │ Gaya           │ Buddha's enlightenment     │
│ Vaishali           │ Vaishali       │ World's 1st Republic       │
│                    │                │ (Licchavi clan)            │
│ Rajgir             │ Nalanda        │ Buddha preached here;      │
│                    │                │ Nalanda University         │
│ Nalanda            │ Nalanda        │ Ancient university ruins   │
│ Pataliputra        │ Patna          │ Capital of Magadha/Maurya  │
│ Vikramshila        │ Bhagalpur      │ Ancient Buddhist university│
│ Sonepur            │ Saran          │ Asia's largest cattle fair │
│ Sitab Diara        │ Saran          │ Birthplace of JP Narayan   │
│ Jagdishpur         │ Bhojpur        │ Kunwar Singh's base        │
│ Ziradei            │ Siwan          │ Birthplace of Raj. Prasad  │
│ Champaran          │ WC/EC Champaran│ Gandhi's 1st Satyagraha    │
└──────────────────────────────────────────────────────────────────┘
```

---

## 🚨 BPSC TOPPER TRAP CARD — GS BIHAR GK

| Wrong Fact | Correct Fact |
|-----------|-------------|
| Rajendra Prasad born in Patna | ❌ WRONG — Born in Ziradei, Siwan |
| JP Narayan's title = "Jan Nayak" | ❌ WRONG — JP = "Lok Nayak" (Karpoori = Jan Nayak) |
| Kunwar Singh was 40 years old in 1857 | ❌ WRONG — He was ~80 years old |
| Sri Krishna Sinha = 2nd CM of Bihar | ❌ WRONG — He was 1st CM of Bihar |
| "Bihar Kesari" = JP Narayan | ❌ WRONG — Bihar Kesari = Sri Krishna Sinha |
| Nalanda University is in Patna | ❌ WRONG — It is in Rajgir, Nalanda district |
| Karpoori Thakur's Bharat Ratna = 1999 | ❌ WRONG — He received it in 2024 |
| Sonepur fair = India's largest | ❌ WRONG — It's Asia's largest cattle fair |

---

## ✅ GS CONCEPT SUMMARY — DAY 47

| # | Person | Key Fact |
|---|--------|---------|
| 1 | Dr. Rajendra Prasad | 1st President + Chairman Constituent Assembly; Born Ziradei, Siwan; "Deshratna" |
| 2 | Jayaprakash Narayan | "Lok Nayak"; JP Movement 1974; Sampoorna Kranti; Sitab Diara, Saran |
| 3 | Kunwar Singh | 1857 revolt at age ~80; Jagdishpur, Bhojpur; "Veer Kunwar Singh" |
| 4 | Sri Krishna Sinha | 1st CM of Bihar; "Bihar Kesari"; 15 years as CM |
| 5 | Karpoori Thakur | "Jan Nayak"; CM Bihar twice; Bharat Ratna 2024 |
| 6 | Aryabhata | From Kusumapura (Patna); discovered Zero; India's 1st satellite named after him |
| 7 | Chanakya | From near Patna; wrote Arthashastra; "Indian Machiavelli" |
| 8 | Nalanda University | Rajgir, Nalanda; ancient center; revived 2014 |
| 9 | Bodh Gaya | Gaya district; Buddha's enlightenment |
| 10 | Vaishali | World's first Republic (Licchavi) |

---

---

# 📝 PRACTICE QUESTIONS

> ⚠️ **INSTRUCTION:** Attempt ALL 50 questions FIRST. Answers are provided at the END of the file.
> Do NOT scroll down to the answer key while attempting questions.
> Use paper to cover the answers section below.
> BPSC Five-Option Format: (A), (B), (C), (D) More than one of the above, (E) None of the above

---

## 🖥️ CS PRACTICE QUESTIONS (Q1–Q25)
### Topic: Network Topologies & Network Devices

---

**Q1.** In a BUS topology, if the central backbone cable fails, what happens?

(A) Only the device nearest to the failure point stops working  
(B) The network automatically reroutes through an alternate path  
(C) The entire network goes down as all devices share the same cable  
(D) More than one of the above  
(E) None of the above  

---

**Q2.** Which of the following is MANDATORY for a Star topology to function?

(A) A terminator at both ends of the cable  
(B) Token passing between devices  
(C) A central hub or switch connecting all devices  
(D) More than one of the above  
(E) None of the above  

---

**Q3.** Which of the following is NOT a network topology?

(A) Bus  
(B) Ring  
(C) Peer-to-Peer  
(D) More than one of the above  
(E) None of the above  

---

**Q4.** In a Full Mesh topology with 5 devices, how many links (connections) are needed?

(A) 5  
(B) 8  
(C) 10  
(D) More than one of the above  
(E) None of the above  

---

**Q5.** Tree topology is also known as:

(A) Hybrid topology  
(B) Ring-bus topology  
(C) Hierarchical topology  
(D) More than one of the above  
(E) None of the above  

---

**Q6.** In Ring topology, data typically travels in:

(A) All directions simultaneously  
(B) One direction (unidirectional)  
(C) Only from one endpoint to another endpoint  
(D) More than one of the above  
(E) None of the above  

---

**Q7.** Which network topology offers the HIGHEST reliability due to multiple paths between devices?

(A) Bus topology  
(B) Star topology  
(C) Mesh topology  
(D) More than one of the above  
(E) None of the above  

---

**Q8.** A HUB operates at which layer of the OSI model?

(A) Data Link Layer (Layer 2)  
(B) Network Layer (Layer 3)  
(C) Physical Layer (Layer 1)  
(D) More than one of the above  
(E) None of the above  

---

**Q9.** The primary difference between a HUB and a SWITCH is:

(A) Hub operates at Layer 2; Switch operates at Layer 1  
(B) Hub broadcasts to all ports; Switch sends data only to the specific destination device  
(C) Hub uses IP addresses; Switch uses MAC addresses  
(D) More than one of the above  
(E) None of the above  

---

**Q10.** A SWITCH uses which type of address to forward data to the correct destination?

(A) IP Address  
(B) MAC Address (Physical Address)  
(C) Port number  
(D) More than one of the above  
(E) None of the above  

---

**Q11.** A ROUTER operates at which layer of the OSI model?

(A) Physical Layer (Layer 1)  
(B) Data Link Layer (Layer 2)  
(C) Network Layer (Layer 3)  
(D) More than one of the above  
(E) None of the above  

---

**Q12.** Which network device connects multiple networks and routes data packets using IP addresses?

(A) Hub  
(B) Switch  
(C) Router  
(D) More than one of the above  
(E) None of the above  

---

**Q13.** A BRIDGE is used to:

(A) Connect two different networks using different protocols  
(B) Amplify a weak network signal over a long distance  
(C) Connect two similar LANs and filter traffic by MAC address  
(D) More than one of the above  
(E) None of the above  

---

**Q14.** The full form of MODEM is:

(A) Modern Demodulation  
(B) Modulator-Demodulator  
(C) Multiple Operations Data Exchange Module  
(D) More than one of the above  
(E) None of the above  

---

**Q15.** A REPEATER's primary function in a network is to:

(A) Route data between different networks  
(B) Filter traffic based on MAC address  
(C) Amplify or regenerate a weakening signal to extend the network range  
(D) More than one of the above  
(E) None of the above  

---

**Q16.** Which device performs protocol conversion between two different types of networks?

(A) Router  
(B) Switch  
(C) Gateway  
(D) More than one of the above  
(E) None of the above  

---

**Q17.** The World Wide Web (WWW) was created by:

(A) Bill Gates in 1993  
(B) Tim Berners-Lee in 1989  
(C) Vint Cerf in 1983  
(D) More than one of the above  
(E) None of the above  

---

**Q18.** Which of the following CORRECTLY distinguishes the Internet from the WWW?

(A) Internet and WWW are exactly the same thing  
(B) WWW is the global physical network; Internet is a service on top of it  
(C) Internet is the global network infrastructure; WWW is a collection of hyperlinked documents (service) that runs on the Internet  
(D) More than one of the above  
(E) None of the above  

---

**Q19.** In Bus topology, TERMINATORS are placed:

(A) At every device connecting to the bus  
(B) Only at the center of the cable  
(C) At both ends of the backbone cable  
(D) More than one of the above  
(E) None of the above  

---

**Q20.** Which topology requires the MOST cabling?

(A) Bus topology  
(B) Star topology  
(C) Full Mesh topology  
(D) More than one of the above  
(E) None of the above  

---

**Q21.** Consider the following statements about Star topology:
1. If a single device fails, only that device is affected.
2. If the central hub/switch fails, the entire network goes down.
3. Star topology is the most commonly used topology in modern LANs.

Which of the above statements are CORRECT?

(A) Only 1  
(B) Only 1 and 2  
(C) 1, 2, and 3 — all correct  
(D) More than one of the above  
(E) None of the above  

---

**Q22.** A network device that converts digital signals to analog signals for transmission over telephone lines is:

(A) Router  
(B) Switch  
(C) Modem  
(D) More than one of the above  
(E) None of the above  

---

**Q23.** PAN (Personal Area Network) typically covers a range of:

(A) A single city  
(B) An entire campus or building  
(C) A few meters (personal space — Bluetooth range)  
(D) More than one of the above  
(E) None of the above  

---

**Q24.** Which of the following is an example of a MAN (Metropolitan Area Network)?

(A) A company's internal network across one floor  
(B) A cable TV network covering an entire city  
(C) The global Internet  
(D) More than one of the above  
(E) None of the above  

---

**Q25.** Consider the following device-to-OSI-layer mappings:
1. Hub → Physical Layer (Layer 1) ✓
2. Switch → Data Link Layer (Layer 2) ✓
3. Router → Network Layer (Layer 3) ✓
4. Bridge → Network Layer (Layer 3) ✗

Which of the above are CORRECTLY mapped?

(A) Only 1 and 2  
(B) Only 1, 2, and 3  
(C) Only 2 and 3  
(D) More than one of the above (1, 2, 3 are correct; 4 is wrong)  
(E) None of the above  

---

---

## 📚 GS PRACTICE QUESTIONS (Q26–Q50)
### Topic: Bihar GK — Famous Personalities, Nicknames & Key Facts

---

**Q26.** Who was the First President of India and from which district of Bihar did he belong?

(A) Jawaharlal Nehru from Patna, Bihar  
(B) Dr. Rajendra Prasad from Ziradei, Siwan district  
(C) Sardar Patel from Champaran, Bihar  
(D) More than one of the above  
(E) None of the above  

---

**Q27.** Dr. Rajendra Prasad served as the President of India for how long?

(A) 5 years (one term)  
(B) 10 years (two terms)  
(C) 12 years — the longest serving President of India  
(D) More than one of the above  
(E) None of the above  

---

**Q28.** The nickname "Lok Nayak" (People's Hero) belongs to which leader from Bihar?

(A) Dr. Rajendra Prasad  
(B) Jayaprakash Narayan (JP)  
(C) Karpoori Thakur  
(D) More than one of the above  
(E) None of the above  

---

**Q29.** Jayaprakash Narayan's movement in 1974 is associated with which slogan/concept?

(A) "Poorna Swaraj" (Complete Independence)  
(B) "Total Revolution" (Sampoorna Kranti)  
(C) "Jai Jawan Jai Kisan"  
(D) More than one of the above  
(E) None of the above  

---

**Q30.** Jayaprakash Narayan was born at which place in Bihar?

(A) Patna  
(B) Sitab Diara, Saran district  
(C) Ziradei, Siwan  
(D) More than one of the above  
(E) None of the above  

---

**Q31.** Veer Kunwar Singh, who led the revolt of 1857 in Bihar, was approximately how old at the time of the revolt?

(A) Around 40 years old  
(B) Around 60 years old  
(C) Around 80 years old — making him the oldest 1857 hero  
(D) More than one of the above  
(E) None of the above  

---

**Q32.** Kunwar Singh's base and final victory in 1858 was at:

(A) Patna  
(B) Muzaffarpur  
(C) Jagdishpur, Bhojpur district  
(D) More than one of the above  
(E) None of the above  

---

**Q33.** Who was the First Chief Minister of Bihar and what was his nickname?

(A) Karpoori Thakur — "Jan Nayak"  
(B) Sri Krishna Sinha — "Bihar Kesari"  
(C) Jagannath Mishra — "Bihar Ratna"  
(D) More than one of the above  
(E) None of the above  

---

**Q34.** Karpoori Thakur is known by which title and received which award in 2024?

(A) "Bihar Kesari"; Padma Bhushan  
(B) "Jan Nayak"; Bharat Ratna (posthumously)  
(C) "Lok Nayak"; Bharat Ratna  
(D) More than one of the above  
(E) None of the above  

---

**Q35.** Aryabhata, the ancient Indian mathematician-astronomer, is primarily associated with which place in Bihar?

(A) Nalanda  
(B) Bodh Gaya  
(C) Kusumapura (modern-day Patna area)  
(D) More than one of the above  
(E) None of the above  

---

**Q36.** India's first satellite launched in 1975 was named after which person connected to Bihar?

(A) Chanakya  
(B) Aryabhata  
(C) Rajendra Prasad  
(D) More than one of the above  
(E) None of the above  

---

**Q37.** Chanakya is also known by which other names?

(A) Kautilya and Vishnugupta  
(B) Vatsyayana and Nagarjuna  
(C) Aryabhata and Varahamihira  
(D) More than one of the above  
(E) None of the above  

---

**Q38.** What is the significance of Vaishali in Bihar?

(A) It is where Mahatma Gandhi was born  
(B) It is regarded as the world's first republic (Licchavi clan's democratic assembly)  
(C) It is where the first Battle of Panipat was fought  
(D) More than one of the above  
(E) None of the above  

---

**Q39.** The ancient Nalanda University (ruins) is located in which district of Bihar?

(A) Patna district  
(B) Gaya district  
(C) Nalanda district (near Rajgir)  
(D) More than one of the above  
(E) None of the above  

---

**Q40.** The "Nightingale of India" refers to which personality?

(A) Indira Gandhi  
(B) Sarojini Naidu  
(C) Lata Mangeshkar  
(D) More than one of the above  
(E) None of the above  

---

**Q41.** Who is called the "Iron Man of India"?

(A) Jawaharlal Nehru  
(B) Bal Gangadhar Tilak  
(C) Sardar Vallabhbhai Patel  
(D) More than one of the above  
(E) None of the above  

---

**Q42.** "Missile Man of India" is the title given to:

(A) Dr. Homi Jehangir Bhabha  
(B) Dr. Vikram Sarabhai  
(C) Dr. A.P.J. Abdul Kalam  
(D) More than one of the above  
(E) None of the above  

---

**Q43.** Dr. Rajendra Prasad was the Chairman of which important constitutional body?

(A) Planning Commission of India  
(B) Constituent Assembly of India  
(C) Election Commission of India  
(D) More than one of the above  
(E) None of the above  

---

**Q44.** Sonepur Mela (fair) in Bihar holds which significant distinction?

(A) It is India's largest religious gathering  
(B) It is Asia's largest cattle fair  
(C) It is the world's oldest trade fair  
(D) More than one of the above  
(E) None of the above  

---

**Q45.** Bodh Gaya, the place where Buddha attained enlightenment, is in which district of Bihar?

(A) Nalanda district  
(B) Vaishali district  
(C) Gaya district  
(D) More than one of the above  
(E) None of the above  

---

**Q46.** "Father of the Indian Constitution" refers to:

(A) Jawaharlal Nehru  
(B) B.R. Ambedkar  
(C) Dr. Rajendra Prasad  
(D) More than one of the above  
(E) None of the above  

---

**Q47.** The Arthashastra, an ancient treatise on statecraft and economics, was written by:

(A) Aryabhata  
(B) Vatsyayana  
(C) Chanakya (Kautilya)  
(D) More than one of the above  
(E) None of the above  

---

**Q48.** "Frontier Gandhi" is the nickname of:

(A) Jawaharlal Nehru  
(B) Khan Abdul Ghaffar Khan  
(C) Maulana Abul Kalam Azad  
(D) More than one of the above  
(E) None of the above  

---

**Q49.** Consider the following nickname-person pairs:
1. Lok Nayak — Jayaprakash Narayan ✓
2. Bihar Kesari — Sri Krishna Sinha ✓
3. Jan Nayak — Jayaprakash Narayan ✗ (correct: Karpoori Thakur)
4. Deshratna — Dr. Rajendra Prasad ✓

Which of the above are CORRECTLY matched?

(A) Only 1 and 4  
(B) Only 1, 2, and 4  
(C) Only 2 and 3  
(D) More than one of the above  
(E) None of the above  

---

**Q50.** Dr. Rajendra Prasad received which award from the Government of India and in which year?

(A) Padma Vibhushan in 1960  
(B) Bharat Ratna in 1962  
(C) Bharat Ratna in 1947  
(D) More than one of the above  
(E) None of the above  

---

---

# 🔑 ANSWER KEY

> ✅ Attempt ALL 50 questions BEFORE checking answers below!
> Check your score: 45–50 = Topper | 38–44 = Good | 30–37 = Needs revision | Below 30 = Re-study

---

## CS ANSWERS (Q1–Q25)

| Q | Ans | Explanation |
|---|-----|-------------|
| Q1 | **(C)** | Bus topology: single backbone — if it breaks, ALL devices lose connectivity |
| Q2 | **(C)** | Star topology REQUIRES a central hub or switch — cannot function without it |
| Q3 | **(C)** | Peer-to-Peer is a NETWORK MODEL (type), NOT a topology — classic PYQ trap! |
| Q4 | **(C)** | Full mesh: n(n-1)/2 = 5×4/2 = 10 links |
| Q5 | **(C)** | Tree topology = Hierarchical topology |
| Q6 | **(B)** | Ring topology: data flows in ONE direction (unidirectional) |
| Q7 | **(C)** | Mesh topology: highest reliability (multiple paths between every device) |
| Q8 | **(C)** | Hub operates at Physical Layer (Layer 1) |
| Q9 | **(B)** | Hub → broadcasts to ALL; Switch → sends only to specific destination device |
| Q10 | **(B)** | Switch reads and uses MAC (Media Access Control) addresses |
| Q11 | **(C)** | Router operates at Network Layer (Layer 3) |
| Q12 | **(C)** | Router routes packets between multiple networks using IP addresses |
| Q13 | **(C)** | Bridge connects two similar LANs and filters by MAC address (Layer 2) |
| Q14 | **(B)** | MODEM = MOdulator-DEModulator |
| Q15 | **(C)** | Repeater amplifies/regenerates signal to extend network distance |
| Q16 | **(C)** | Gateway performs protocol conversion — connects networks with different protocols |
| Q17 | **(B)** | Tim Berners-Lee created WWW in 1989 at CERN |
| Q18 | **(C)** | Internet = global network infrastructure; WWW = service (hyperlinked docs) on Internet |
| Q19 | **(C)** | Terminators are placed at BOTH ENDS of the bus backbone cable |
| Q20 | **(C)** | Full Mesh requires n(n-1)/2 links — maximum cabling of any topology |
| Q21 | **(C)** | All three statements are correct — this is the standard behavior of Star topology |
| Q22 | **(C)** | Modem converts digital ↔ analog signals for telephone line transmission |
| Q23 | **(C)** | PAN = Personal Area Network, covers ~1–10 meters (Bluetooth range) |
| Q24 | **(B)** | Cable TV network covering a city = MAN (Metropolitan Area Network) |
| Q25 | **(D)** | Statements 1, 2, 3 are correct; Statement 4 is WRONG (Bridge is Layer 2, not Layer 3) → "More than one" (1, 2, 3 correct) |

---

## GS ANSWERS (Q26–Q50)

| Q | Ans | Explanation |
|---|-----|-------------|
| Q26 | **(B)** | Dr. Rajendra Prasad — First President; born Ziradei, Siwan district |
| Q27 | **(C)** | Rajendra Prasad served 12 years (1950–1962) — longest-serving President |
| Q28 | **(B)** | "Lok Nayak" = Jayaprakash Narayan (JP); Karpoori = "Jan Nayak" |
| Q29 | **(B)** | JP's 1974 movement = "Total Revolution" / "Sampoorna Kranti" |
| Q30 | **(B)** | JP Narayan born at Sitab Diara, Saran district |
| Q31 | **(C)** | Kunwar Singh was ~80 years old during the 1857 revolt |
| Q32 | **(C)** | Jagdishpur, Bhojpur district — site of Kunwar Singh's famous 1858 victory |
| Q33 | **(B)** | Sri Krishna Sinha = First CM of Bihar; Nickname = "Bihar Kesari" |
| Q34 | **(B)** | Karpoori Thakur = "Jan Nayak"; received Bharat Ratna posthumously in 2024 |
| Q35 | **(C)** | Aryabhata is associated with Kusumapura (modern Patna area, Bihar) |
| Q36 | **(B)** | India's first satellite (1975) was named "Aryabhata" after the Bihar mathematician |
| Q37 | **(A)** | Chanakya's other names are Kautilya and Vishnugupta |
| Q38 | **(B)** | Vaishali = world's first republic (Licchavi clan's democratic assembly) |
| Q39 | **(C)** | Ancient Nalanda University ruins are in Nalanda district, near Rajgir |
| Q40 | **(B)** | "Nightingale of India" = Sarojini Naidu |
| Q41 | **(C)** | "Iron Man of India" = Sardar Vallabhbhai Patel |
| Q42 | **(C)** | "Missile Man of India" = Dr. A.P.J. Abdul Kalam |
| Q43 | **(B)** | Dr. Rajendra Prasad was Chairman of the Constituent Assembly |
| Q44 | **(B)** | Sonepur Mela = Asia's LARGEST cattle fair (not India's largest religious gathering) |
| Q45 | **(C)** | Bodh Gaya is in Gaya district, Bihar |
| Q46 | **(B)** | "Father of Indian Constitution" = B.R. Ambedkar |
| Q47 | **(C)** | Arthashastra = written by Chanakya (Kautilya) |
| Q48 | **(B)** | "Frontier Gandhi" = Khan Abdul Ghaffar Khan (from NWFP/Khyber Pakhtunkhwa) |
| Q49 | **(B)** | Pairs 1, 2, 4 are correct; Pair 3 is wrong (Jan Nayak = Karpoori Thakur, not JP) |
| Q50 | **(B)** | Bharat Ratna in 1962 (the year before his death in 1963) |

---

---

# 📌 DAILY NIGHT REVISION — 5-BULLET SUMMARY

Write these from memory before sleeping tonight:

## CS — Topology & Device Key Facts:
1. Bus = cheapest, single backbone; backbone fails → all fail; needs terminators at both ends
2. Star = central hub/switch required; hub fails → all fail; most popular today
3. Mesh = n(n-1)/2 links; most expensive + most reliable; full/partial types
4. Peer-to-Peer = NOT a topology; it is a network MODEL (most common BPSC trap!)
5. Hub=Layer1 broadcasts all; Switch=Layer2 specific MAC; Router=Layer3 IP routing

## GS — Bihar Famous Personalities Key Facts:
1. Rajendra Prasad = 1st President, Deshratna, Ziradei Siwan, Chairman Constituent Assembly
2. JP Narayan = Lok Nayak, Sitab Diara Saran, Total Revolution 1974, Bharat Ratna 1999
3. Kunwar Singh = ~80 years old in 1857, Jagdishpur Bhojpur, Veer Kunwar Singh
4. Sri Krishna Sinha = 1st CM Bihar, Bihar Kesari; Karpoori Thakur = Jan Nayak, Bharat Ratna 2024
5. Aryabhata = Zero + Pi, Kusumapura (Patna), India's 1st satellite named after him (1975)

---

## ⚡ TOPPER'S SELF-ASSESSMENT CHECKLIST

After completing Day 47, verify:

- [ ] Can you explain why Bus topology fails completely when backbone breaks?
- [ ] Can you calculate Mesh links for 4 and 6 devices using n(n-1)/2?
- [ ] Do you know why Peer-to-Peer is NOT a topology?
- [ ] Can you state which OSI layer Hub, Switch, Router, and Bridge operate at?
- [ ] Can you distinguish Internet from WWW?
- [ ] Can you name the First CM of Bihar and his nickname?
- [ ] Do you know the correct birthplace of Dr. Rajendra Prasad?
- [ ] Can you differentiate "Lok Nayak" (JP) from "Jan Nayak" (Karpoori)?
- [ ] Do you know why Kunwar Singh is remarkable (age ~80 in 1857)?
- [ ] Do you know Karpoori Thakur's Bharat Ratna year (2024)?

**Score yourself:** 9–10 ✅ = Ready for next day | 6–8 = Quick re-read | Below 6 = Re-study today

---

*Day 47 Complete | Next: Day 48 — Transmission Media & Network Security + Bihar GK (Silk, Paddy districts)*
*Running Total: Phase 1 (Day 1–60) | Networks Week (Day 43–49)*
*BPSC TRE 4.0 Target: 130+/150 | YOU ARE ON TRACK — KEEP GOING! 🎯*
