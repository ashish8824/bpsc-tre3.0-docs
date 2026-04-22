# 📅 BPSC TRE 4.0 — DAY 47 COMPLETE STUDY MODULE
### Computer Networks: Topologies, Networking Devices & WWW + Bihar GK — Famous Personalities
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Network Topologies (Bus/Star/Ring/Mesh/Tree/Hybrid) + Devices (Hub/Switch/Router/Bridge/Gateway)
> - Afternoon (1 hr): Bihar GK — Famous Personalities and Their Contributions
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Network Topologies, Devices & World Wide Web

---

## 🔷 SECTION 1: What is Network Topology?

### Real-Life Analogy — Road Network Design:

How you connect cities with roads is a TOPOLOGY decision:
- One main highway with branch roads = **Bus Topology**
- All roads going to a central hub airport = **Star Topology**
- A circular ring road connecting all cities = **Ring Topology**
- Every city directly connected to every other = **Mesh Topology**

The DESIGN of connections matters enormously — it affects speed, reliability, cost, and what happens when one road is blocked.

> **Network Topology is the arrangement or layout of nodes (devices) and links (connections) in a computer network — both physically (how cables are laid) and logically (how data flows).**

### Physical vs Logical Topology:
```
┌──────────────────────────────────────────────────────────────────────┐
│              PHYSICAL vs LOGICAL TOPOLOGY                            │
├─────────────────────────────┬────────────────────────────────────────┤
│    PHYSICAL TOPOLOGY        │         LOGICAL TOPOLOGY               │
├─────────────────────────────┼────────────────────────────────────────┤
│ How cables and devices are  │ How data ACTUALLY flows through        │
│ PHYSICALLY arranged         │ the network                            │
├─────────────────────────────┼────────────────────────────────────────┤
│ What you see if you walk    │ What you see in a network diagram      │
│ around the office           │ showing data paths                     │
├─────────────────────────────┼────────────────────────────────────────┤
│ Example: Star physical      │ Example: Even if physically star,      │
│ (all cables to central hub) │ data may flow logically like a bus     │
│                             │ (Ethernet hub broadcasts to all)       │
├─────────────────────────────┼────────────────────────────────────────┤
│ Determined by cable layout  │ Determined by protocols and devices    │
└─────────────────────────────┴────────────────────────────────────────┘

IMPORTANT EXAMPLE:
  Traditional Ethernet (Hub-based):
    Physical = STAR (all cables run to central hub)
    Logical  = BUS (hub broadcasts to all — data flows like a bus!)
  
  Token Ring network:
    Physical = STAR (all cables to a central MAU device)
    Logical  = RING (data flows in a ring token-passing pattern)

🎯 PYQ FACT: Physical topology = actual cable layout; Logical topology = data flow
🎯 PYQ FACT: A network can have DIFFERENT physical and logical topologies
```

### Why Topology Matters:
```
TOPOLOGY AFFECTS:
  ✅ Cost:          How much cable/equipment needed?
  ✅ Speed:         How efficiently does data travel?
  ✅ Reliability:   If one link fails, does the whole network crash?
  ✅ Scalability:   How easy is it to add new devices?
  ✅ Troubleshooting: How easy to find and fix problems?
  ✅ Security:      How isolated are devices from each other?
```

---

## 🔷 SECTION 2: BUS TOPOLOGY

### Structure:
```
BUS TOPOLOGY — THE BACKBONE DESIGN

     ┌──────────────────────────────────────────────────────┐
     │               BACKBONE CABLE (BUS)                   │
     └───┬───────────┬──────────────┬──────────────┬────────┘
         │           │              │              │
    ┌────┴────┐ ┌────┴────┐  ┌─────┴────┐  ┌─────┴────┐
    │ Device1 │ │ Device2 │  │ Device3  │  │ Device4  │
    └─────────┘ └─────────┘  └──────────┘  └──────────┘
    
    Terminator ◀─────────────────────────────────▶ Terminator
    (Left end)                                     (Right end)

KEY FEATURE: ONE single shared cable (backbone/bus) to which ALL devices connect.
             TERMINATORS at each end absorb signals and prevent reflection.

HOW DATA TRAVELS:
  Device1 wants to send to Device3:
  → Device1 broadcasts data on the bus
  → ALL devices hear the data (Device2, Device3, Device4)
  → ONLY Device3 recognises its address and accepts it
  → Others IGNORE the data
  → This shared access creates potential COLLISIONS!

COLLISION HANDLING:
  CSMA/CD (Carrier Sense Multiple Access / Collision Detection):
  → Before sending: "Listen" to check if bus is free (Carrier Sense)
  → If free: Send. If busy: Wait.
  → If two devices send simultaneously: COLLISION!
  → Both stop, wait random time, retry
```

### Advantages and Disadvantages:
```
ADVANTAGES:
  ✅ CHEAP — minimal cable required (one line for all)
  ✅ SIMPLE — easy to install and extend
  ✅ SUITABLE for small, temporary networks
  ✅ Less cable than star topology for small networks

DISADVANTAGES:
  ❌ SINGLE POINT OF FAILURE — if backbone cable breaks, ENTIRE NETWORK fails
  ❌ PERFORMANCE DEGRADES as more devices added (more collisions!)
  ❌ DIFFICULT TO TROUBLESHOOT — hard to find cable break
  ❌ LIMITED LENGTH — signal weakens over distance
  ❌ COLLISIONS — multiple devices sharing one medium
  ❌ NOT SUITABLE for large networks

REAL-LIFE USE:
  → Early Ethernet networks (10BASE2 "thinnet" coaxial cable)
  → Simple, small lab setups
  → Largely OBSOLETE today (replaced by switch-based star topology)

🎯 PYQ FACT: Bus topology = single backbone cable + terminators at both ends
🎯 PYQ FACT: Bus topology failure = one cable break = whole network down
🎯 PYQ FACT: Bus uses CSMA/CD for collision detection
```

---

## 🔷 SECTION 3: STAR TOPOLOGY

### Structure:
```
STAR TOPOLOGY — THE HUB-AND-SPOKE DESIGN

                        ┌──────────────┐
                        │   CENTRAL    │
                  ┌────▶│  HUB /       │◀────┐
                  │     │  SWITCH      │     │
                  │     └──────┬───────┘     │
                  │            │             │
             ┌────┴────┐  ┌────┴────┐  ┌────┴────┐
             │ Device1 │  │ Device2 │  │ Device3 │
             └─────────┘  └─────────┘  └─────────┘
                  │
             ┌────┴────┐
             │ Device4 │
             └─────────┘

KEY FEATURE: ALL devices connected to ONE CENTRAL DEVICE (Hub or Switch).
             No device connects directly to another — all traffic goes through centre.

HOW DATA TRAVELS (with Hub — old):
  Device1 sends to Device3:
  → Data goes to Hub
  → Hub BROADCASTS to ALL devices (Device2, Device3, Device4)
  → Device3 accepts; others ignore
  (Hub = unintelligent, broadcasts to everyone)

HOW DATA TRAVELS (with Switch — modern):
  Device1 sends to Device3:
  → Data goes to Switch
  → Switch reads MAC address, sends ONLY to Device3
  → Device2 and Device4 don't see this data
  (Switch = intelligent, unicasts to specific device — MUCH BETTER!)
```

### Advantages and Disadvantages:
```
ADVANTAGES:
  ✅ EASY TO TROUBLESHOOT — centralised; if one cable fails, only that device affected
  ✅ EASY TO ADD/REMOVE devices — just plug/unplug from central switch
  ✅ BETTER PERFORMANCE with Switch — no unnecessary broadcasts
  ✅ FAULT ISOLATION — individual device failure doesn't affect others
  ✅ MOST POPULAR topology for modern LANs!

DISADVANTAGES:
  ❌ CENTRAL DEVICE = SINGLE POINT OF FAILURE
     If Hub/Switch fails → ENTIRE NETWORK goes down!
  ❌ MORE CABLE NEEDED — each device needs its own cable to centre
  ❌ CENTRAL DEVICE COST — hub/switch required (additional expense)
  ❌ PERFORMANCE LIMITED by central device capacity

🚨 PYQ TRAP: "In Star topology, if ONE device fails, the whole network goes down"
   → FALSE! Only the central hub/switch failure kills the whole network.
   → Individual device/cable failure affects ONLY that device.

🎯 PYQ FACT: Star topology = central hub/switch is mandatory
🎯 PYQ FACT: Star = most commonly used LAN topology today
🎯 PYQ FACT: Star's weakness = central device failure = full network failure
🎯 PYQ FACT: Modern Star uses Switch (intelligent) not Hub (broadcasts to all)

REAL-LIFE USE:
  → School computer labs (all PCs connected to a central switch)
  → Home networks (all devices connected to Wi-Fi router = star topology!)
  → Office LANs (the most common setup today)
```

---

## 🔷 SECTION 4: RING TOPOLOGY

### Structure:
```
RING TOPOLOGY — THE CIRCULAR DESIGN

              ┌─────────────┐
         ┌───▶│  Device 1   │───┐
         │    └─────────────┘   │
         │                      ▼
    ┌────┴────┐           ┌─────────────┐
    │ Device 4│           │  Device 2   │
    └────┬────┘           └──────┬──────┘
         │                       │
         └──────────┐  ┌─────────┘
                    ▼  ▼
               ┌─────────────┐
               │  Device 3   │
               └─────────────┘

Data flows in ONE DIRECTION around the ring (unidirectional)
(Some rings are bidirectional — SONET/SDH rings used in telecom)

HOW DATA TRAVELS:
  Device1 sends to Device3:
  → Token (permission to send) passes around ring
  → When Device1 gets the token, it attaches data + destination address
  → Data passes: Device1 → Device2 → Device3
  → Device3 reads data, sends acknowledgment
  → Data continues: Device3 → Device4 → Device1 (back to sender)
  → Device1 removes data from ring

TOKEN RING:
  Uses a special "TOKEN" — only the device holding the token can send.
  Prevents collisions (no two devices send simultaneously)!
  More ordered than Bus topology's CSMA/CD.
```

### Advantages and Disadvantages:
```
ADVANTAGES:
  ✅ NO COLLISIONS — token passing ensures only one sender at a time
  ✅ ORDERLY DATA TRANSMISSION — fair access for all devices
  ✅ PERFORMANCE stays consistent as load increases
  ✅ Easy to identify which device has the token (good for monitoring)

DISADVANTAGES:
  ❌ SINGLE POINT OF FAILURE — one broken cable or failed device = ring broken = network down!
  ❌ SLOW — data must pass through each intermediate device
  ❌ ADDING/REMOVING devices DISRUPTS the network
  ❌ TROUBLESHOOTING DIFFICULT — must trace around the whole ring
  ❌ LARGELY OBSOLETE for LANs (replaced by star+switch)

🎯 PYQ FACT: Ring topology = unidirectional data flow (usually)
🎯 PYQ FACT: Token Ring = uses token-passing access control
🎯 PYQ FACT: Ring = no collisions (unlike Bus CSMA/CD)
🎯 PYQ FACT: Ring failure = one break = whole network down

REAL-LIFE USE:
  → Token Ring LANs (IBM's Token Ring — largely obsolete)
  → SONET/SDH rings (backbone telecom networks — still used!)
  → Metropolitan Area Networks (MAN)
  → FDDI (Fiber Distributed Data Interface) — dual ring for fault tolerance
```

---

## 🔷 SECTION 5: MESH TOPOLOGY

### Structure:
```
MESH TOPOLOGY — THE FULLY CONNECTED DESIGN

FULL MESH (every device connected to EVERY other device):

    ┌─────────┐────────────────────┌─────────┐
    │Device 1 │                    │Device 2 │
    └────┬────┘                    └────┬────┘
         │  ╲                      ╱   │
         │    ╲                  ╱     │
         │      ╲              ╱       │
         │        ╲          ╱         │
         │          ╲      ╱           │
    ┌────┴────┐      ╲  ╱      ┌────┴────┐
    │Device 4 │────────╳────────│Device 3 │
    └─────────┘                └─────────┘

EVERY device has a DIRECT connection to EVERY other device.
For 4 devices: 4×3/2 = 6 links
For 5 devices: 5×4/2 = 10 links
For n devices: n(n-1)/2 links

PARTIAL MESH:
  Some (not all) devices are fully interconnected.
  More practical — used in the real Internet backbone!

HOW DATA TRAVELS:
  Multiple paths between ANY two devices.
  If Device1 → Device2 direct link fails:
  → Traffic reroutes: Device1 → Device3 → Device2
  → OR: Device1 → Device4 → Device2
  → Network CONTINUES to function!
```

### Advantages and Disadvantages:
```
ADVANTAGES:
  ✅ HIGHEST RELIABILITY — multiple paths; no single point of failure!
  ✅ FAULT TOLERANT — link failure just uses alternate path
  ✅ SECURITY — dedicated links, data doesn't pass through other devices
  ✅ HIGH PERFORMANCE — each connection dedicated, no shared bandwidth
  ✅ NO TRAFFIC CONGESTION — separate paths for each connection
  ✅ EASY FAULT IDENTIFICATION — each link is independent

DISADVANTAGES:
  ❌ MOST EXPENSIVE — n(n-1)/2 cables needed (grows rapidly!)
  ❌ COMPLEX INSTALLATION — many cables and ports
  ❌ DIFFICULT TO MANAGE as network grows
  ❌ EACH DEVICE NEEDS MANY PORTS — one for every other device

COST FORMULA:
  For n devices: n(n-1)/2 links needed
  4 devices  → 6 links
  10 devices → 45 links
  100 devices → 4,950 links! (impractical for large networks)

🎯 PYQ FACT: Mesh topology = HIGHEST reliability (fault tolerant — multiple paths)
🎯 PYQ FACT: Mesh = most expensive (n(n-1)/2 links)
🎯 PYQ FACT: Internet backbone uses PARTIAL MESH topology

REAL-LIFE USE:
  → Internet backbone (ISP interconnections — partial mesh)
  → Military/critical infrastructure networks (needs high reliability)
  → WAN connections between corporate offices
  → Wireless mesh networks (urban Wi-Fi coverage)
```

---

## 🔷 SECTION 6: TREE TOPOLOGY

### Structure:
```
TREE TOPOLOGY — THE HIERARCHICAL DESIGN
(Also called "Hierarchical Topology" or "Star-Bus Topology")

THINK OF: A real tree — one root, branches spreading out

                     [ROOT SWITCH]
                          │
              ┌───────────┴───────────┐
         [Switch A]             [Switch B]
         /    │    \             /    │    \
      [D1]  [D2]  [D3]       [D4]  [D5]  [D6]
      
IT'S STAR TOPOLOGY + BUS TOPOLOGY combined:
  → Individual groups connected in STAR (devices to local switch)
  → Local switches connected in BUS-like hierarchy (to root switch)
  → Hence also called "Star-Bus" topology

HOW DATA TRAVELS:
  D1 sends to D4:
  → D1 → Switch A → Root Switch → Switch B → D4
  Data travels UP the tree, then DOWN to destination
```

### Advantages and Disadvantages:
```
ADVANTAGES:
  ✅ HIERARCHICAL — easy management and expansion
  ✅ SCALABLE — add more branches (switches) easily
  ✅ ISOLATION — fault in one branch doesn't affect others
  ✅ SUITABLE for large organisations (floors, departments as branches)

DISADVANTAGES:
  ❌ ROOT NODE = SINGLE POINT OF FAILURE
     If root switch fails → ENTIRE NETWORK down!
  ❌ COMPLEX configuration and cabling
  ❌ BOTTLENECK at root node (all traffic passes through it)

🎯 PYQ FACT: Tree topology = Star topology + Bus topology combined
🎯 PYQ FACT: Tree = hierarchical structure (root → branches → leaves)

REAL-LIFE USE:
  → Large office buildings (floor switches connected to main switch)
  → University networks (department networks connected to central)
  → Cable TV distribution networks
```

---

## 🔷 SECTION 7: HYBRID TOPOLOGY

### Structure:
```
HYBRID TOPOLOGY — MIX OF MULTIPLE TOPOLOGIES

DEFINITION: A combination of TWO OR MORE different topologies.
            The most complex but MOST FLEXIBLE topology.

EXAMPLE:
  Large corporation:
    ┌────────────────────────────────────────────┐
    │              HEADQUARTERS                   │
    │  [Star topology inside — floor switches]    │
    │         ╱           │         ╲            │
    │      ╱              │            ╲         │
    │  [Branch A]    [Branch B]    [Branch C]    │
    │  (Ring inside) (Bus inside)  (Star inside) │
    └────────────────────────────────────────────┘
    
    HQ uses Star internally + connects to branches via different topologies
    = HYBRID TOPOLOGY

WHY HYBRID?
  → Real-world networks rarely fit ONE topology perfectly
  → Different departments may have different needs
  → Hybrid gives flexibility to use best topology for each part

ADVANTAGES:
  ✅ FLEXIBLE — use best topology for each part of network
  ✅ SCALABLE — add any topology as needed
  ✅ RELIABLE — critical sections can use mesh

DISADVANTAGES:
  ❌ COMPLEX to design and manage
  ❌ EXPENSIVE — multiple types of infrastructure

🎯 PYQ FACT: Hybrid = combination of 2 or more different topologies
🎯 PYQ FACT: The Internet itself is a HYBRID topology (global scale)
```

---

## 🔷 SECTION 8: Topology Comparison — Master Table

```
┌───────────────┬──────────────────┬─────────────────────┬─────────────────────┬──────────────────┐
│   TOPOLOGY    │   STRUCTURE      │    ADVANTAGES       │   DISADVANTAGES     │  REAL USE        │
├───────────────┼──────────────────┼─────────────────────┼─────────────────────┼──────────────────┤
│    BUS        │ All on one       │ Cheap, simple       │ Single cable break  │ Early Ethernet   │
│               │ backbone cable   │                     │ kills network;      │ (obsolete now)   │
│               │                  │                     │ collisions          │                  │
├───────────────┼──────────────────┼─────────────────────┼─────────────────────┼──────────────────┤
│    STAR       │ All to central   │ Easy fault          │ Central device      │ Modern LAN       │
│               │ hub/switch       │ isolation; easy     │ failure = network   │ (home, office,   │
│               │                  │ management; MOST    │ down                │ school)          │
│               │                  │ POPULAR             │                     │ Most common!     │
├───────────────┼──────────────────┼─────────────────────┼─────────────────────┼──────────────────┤
│    RING       │ Circular;        │ No collisions;      │ One break = whole   │ Token Ring;      │
│               │ token passing    │ orderly access      │ network down;       │ SONET/SDH        │
│               │                  │                     │ slow; obsolete      │ backbone         │
├───────────────┼──────────────────┼─────────────────────┼─────────────────────┼──────────────────┤
│    MESH       │ Every device     │ HIGHEST             │ MOST EXPENSIVE;     │ Internet         │
│               │ to every other   │ reliability;        │ complex;            │ backbone;        │
│               │ (n(n-1)/2 links) │ no single failure   │ many cables         │ military         │
├───────────────┼──────────────────┼─────────────────────┼─────────────────────┼──────────────────┤
│    TREE       │ Hierarchical;    │ Scalable;           │ Root failure =      │ Large buildings; │
│               │ Star + Bus       │ manageable;         │ total failure;      │ universities     │
│               │                  │ organized           │ bottleneck at root  │                  │
├───────────────┼──────────────────┼─────────────────────┼─────────────────────┼──────────────────┤
│    HYBRID     │ Mix of 2+        │ Flexible;           │ Complex; expensive  │ Internet;        │
│               │ topologies       │ scalable            │                     │ large corps      │
└───────────────┴──────────────────┴─────────────────────┴─────────────────────┴──────────────────┘

RELIABILITY RANKING (Highest to Lowest):
  Mesh > Tree > Star > Ring > Bus

COST RANKING (Highest to Lowest):
  Mesh > Tree > Star > Ring > Bus

🧠 MEMORY TRICK:
  "Big Stars Ring My Tree Hybrid"
  B = Bus     (cheapest, least reliable)
  S = Star    (most popular for LAN)
  R = Ring    (circular, token passing)
  M = Mesh    (most reliable, most expensive)
  T = Tree    (hierarchical)
  H = Hybrid  (combination)
```

---

## 🔷 SECTION 9: Peer-to-Peer — NOT a Topology!

```
🚨 CRITICAL PYQ TRAP: "Peer-to-Peer is a Network Topology"

ANSWER: FALSE! Peer-to-Peer (P2P) is a NETWORK MODEL, not a topology!

PEER-TO-PEER NETWORK MODEL:
  → Every device acts as BOTH client AND server
  → No dedicated server — all devices share resources equally
  → Examples: BitTorrent (file sharing), Blockchain networks,
             early Napster (music sharing), Skype (originally)

CLIENT-SERVER NETWORK MODEL (the alternative):
  → Dedicated servers provide services to clients
  → Clients request; servers respond
  → Examples: The Web (your browser = client; Google = server)

TOPOLOGY = Physical/logical arrangement of connections
  (Bus, Star, Ring, Mesh, Tree, Hybrid = topologies)

NETWORK MODEL = How devices interact (roles they play)
  (P2P, Client-Server = network models)

P2P can be implemented on ANY physical topology!
  → P2P on Star physical = P2P model on star cable layout
  → These are independent concepts!

🎯 PYQ ANSWER: If asked "which of these is a topology?" — P2P is NOT one.
🎯 PYQ ANSWER: P2P = network architecture/model, not topology type.
```

---

## 🔷 SECTION 10: Networking Devices — Deep Explanation

### DEVICE 1 — HUB

```
HUB
OSI LAYER:  Layer 1 — PHYSICAL LAYER
TYPE:       Unintelligent/Dumb device

FUNCTION:
  → Connects multiple devices in a Star topology physically
  → When it receives a signal on any port, it BROADCASTS (repeats) that
    signal to ALL other ports
  → Has NO intelligence — cannot read MAC or IP addresses
  → Simply amplifies and repeats the electrical signal

HOW IT WORKS:
  Device1 sends data to Device3:
  → Hub receives signal
  → Hub sends IDENTICAL copies to ALL ports (Device2, Device3, Device4, Device5)
  → All devices must check: "Is this for me?"
  → Only Device3 processes it; others discard

PROBLEMS WITH HUB:
  → BANDWIDTH WASTE — all devices see all traffic
  → SECURITY RISK — Device2 can capture Device1→Device3 traffic!
  → COLLISION DOMAIN — all devices share one collision domain
  → SLOW — as more devices added, more collisions, slower network

TYPES:
  Passive Hub: Just distributes signal (no amplification)
  Active Hub: Regenerates and amplifies signal (also called "multiport repeater")
  Smart Hub: Adds management capabilities

🎯 PYQ FACT: Hub = Physical Layer (Layer 1) device
🎯 PYQ FACT: Hub broadcasts to ALL ports (no intelligence, no MAC reading)
🎯 PYQ FACT: Hub is a multiport repeater
🚨 TRAP: "Hub works at Data Link Layer" → FALSE! Hub = Layer 1 (Physical)
```

---

### DEVICE 2 — SWITCH

```
SWITCH
OSI LAYER:  Layer 2 — DATA LINK LAYER
TYPE:       Intelligent device

FUNCTION:
  → Connects multiple devices in a LAN (usually in Star topology)
  → READS MAC addresses of devices connected to each port
  → Maintains a MAC Address Table (CAM table):
    "Port 1 → MAC AA:BB:CC:DD:EE:FF (Device1)"
    "Port 3 → MAC 11:22:33:44:55:66 (Device3)"
  → When data arrives: reads DESTINATION MAC, sends ONLY to correct port!

HOW IT WORKS:
  Device1 sends data to Device3:
  → Switch receives frame, reads Destination MAC address
  → Looks up MAC Table: "Device3 is on Port 3"
  → Sends data ONLY to Port 3 (Device3)
  → Device2, Device4 NEVER see this traffic!

SWITCH vs HUB:
  Hub → broadcasts to ALL → like shouting in a room (everyone hears)
  Switch → unicasts to ONE → like whispering directly to one person

ADVANTAGES OVER HUB:
  → Better SECURITY (traffic isolation — only sender and receiver see data)
  → Better PERFORMANCE (no unnecessary traffic to wrong devices)
  → No collisions between different device pairs (can send simultaneously!)
  → Each port = its own collision domain (full-duplex possible!)

MAC ADDRESS TABLE LEARNING:
  Switch learns MAC addresses DYNAMICALLY:
  → When Device1 sends, switch records: "Port 1 has MAC of Device1"
  → First time to unknown MAC → switch "floods" (like hub, temporarily)
  → Once learned → unicasts efficiently

LAYER 3 SWITCH:
  Some switches can also do routing (Layer 3 functions)
  = "Multilayer Switch" or "Layer 3 Switch"
  More expensive, used in enterprise networks

🎯 PYQ FACT: Switch = Data Link Layer (Layer 2)
🎯 PYQ FACT: Switch uses MAC addresses; reads MAC to forward to correct port only
🎯 PYQ FACT: Switch maintains MAC Address Table (CAM table)
🎯 PYQ FACT: Switch = LAN device (connects devices within the same network)
🚨 TRAP: "Switch connects different networks" → FALSE! That's a ROUTER's job.
🚨 TRAP: "Switch works at Network Layer" → FALSE! Switch = Layer 2 (Data Link)
```

---

### DEVICE 3 — ROUTER

```
ROUTER
OSI LAYER:  Layer 3 — NETWORK LAYER
TYPE:       Intelligent device for inter-network routing

FUNCTION:
  → Connects DIFFERENT NETWORKS together (unlike switch which connects devices on SAME network)
  → READS IP addresses and determines best PATH for packet to reach destination
  → Maintains a ROUTING TABLE: maps destination networks to outgoing interfaces
  → Makes intelligent forwarding decisions (chooses best route)

HOW IT WORKS:
  Your home PC wants to access Google.com:
  → Your PC sends packet to HOME ROUTER (default gateway)
  → Home Router checks routing table: "Google's IP (142.250.x.x) → goes to ISP"
  → Packet forwarded to ISP Router
  → ISP Router → another router → eventually reaches Google's server
  → Response follows reverse path back to your PC

ROUTING TABLE (example):
  ┌──────────────────┬────────────────┬──────────────────┐
  │  DESTINATION     │   NEXT HOP     │   INTERFACE      │
  │  NETWORK         │   (Router IP)  │                  │
  ├──────────────────┼────────────────┼──────────────────┤
  │  192.168.1.0/24  │  Direct        │  eth0 (LAN)      │
  │  10.0.0.0/8      │  10.10.1.1     │  eth1 (WAN)      │
  │  0.0.0.0/0       │  203.0.113.1   │  eth2 (Internet) │
  └──────────────────┴────────────────┴──────────────────┘

HOME ROUTER:
  Your home Wi-Fi router actually has TWO interfaces:
  → LAN side: 192.168.1.1 (connects your devices — switch function)
  → WAN side: Public IP from ISP (connects to internet — router function)
  Home router = Router + Switch + Wi-Fi Access Point combined!

TYPES OF ROUTING:
  Static Routing: Admin manually enters routes (small networks)
  Dynamic Routing: Routers automatically share routing info using protocols
    → RIP, OSPF, BGP (routing protocols)

🎯 PYQ FACT: Router = Network Layer (Layer 3) device
🎯 PYQ FACT: Router CONNECTS DIFFERENT NETWORKS (not just devices on same network)
🎯 PYQ FACT: Router uses IP addresses; Switch uses MAC addresses
🎯 PYQ FACT: Router maintains Routing Table; Switch maintains MAC Address Table
🚨 TRAP: "Router works at Data Link Layer" → FALSE! Router = Layer 3 (Network)
🚨 TRAP: "Switch connects different networks" → FALSE! Switch = same network (LAN)
```

---

### DEVICE 4 — BRIDGE

```
BRIDGE
OSI LAYER:  Layer 2 — DATA LINK LAYER
TYPE:       Intelligent device for connecting LANs

FUNCTION:
  → Connects TWO or more LAN segments
  → Divides a large network into smaller SEGMENTS (reduces collision domains)
  → Like a Switch, reads MAC addresses to decide forwarding
  → Can connect networks with different media (e.g., coaxial + twisted pair)

BRIDGE vs SWITCH:
  Bridge: Older technology; typically 2-4 ports; software-based forwarding
  Switch: Modern; many ports (24, 48 ports); hardware-based (faster!)
  
  Switch is essentially a MULTIPORT BRIDGE (bridge with many ports)
  In modern networking: Switches have almost entirely REPLACED bridges

HOW IT REDUCES COLLISION DOMAINS:
  Without Bridge:
  [10 devices all on one bus] → all in ONE collision domain → lots of collisions!
  
  With Bridge:
  [5 devices] ──── Bridge ──── [5 devices]
  → Two separate collision domains → fewer collisions per segment!

🎯 PYQ FACT: Bridge = Data Link Layer (Layer 2)
🎯 PYQ FACT: Bridge connects two LAN segments; reduces collision domains
🎯 PYQ FACT: Switch = multiport bridge (modern replacement for bridges)
```

---

### DEVICE 5 — GATEWAY

```
GATEWAY
OSI LAYER:  Application Layer (Layer 7) — or sometimes all layers!
            (Works at ALL layers — a full protocol conversion device)
TYPE:       Protocol translator / Network entry-exit point

FUNCTION:
  → Connects networks that use DIFFERENT PROTOCOLS
  → Translates between completely different network architectures
  → Acts as the "gate" between two incompatible networks

HOW IT DIFFERS FROM ROUTER:
  Router: Connects networks using the SAME protocol suite (IP)
  Gateway: Connects networks using DIFFERENT protocols altogether
  
EXAMPLE — Email Gateway:
  Corporate office uses X.400 email protocol
  Internet uses SMTP email protocol
  Gateway TRANSLATES between X.400 and SMTP!
  
EXAMPLE — VoIP Gateway:
  Traditional telephone network (analog/PSTN)
  Internet (digital VoIP)
  Gateway converts between analog voice signals and digital VoIP packets!

EXAMPLE — Default Gateway:
  Your HOME ROUTER is your "default gateway"
  → It's the "gate" your traffic passes through to reach the Internet
  → Different network (192.168.1.x home) → Internet (public IPs)

TYPES:
  → Network Gateway: Connects different network architectures
  → Email Gateway: Protocol conversion for email (X.400 ↔ SMTP)
  → VoIP Gateway: Voice calls over internet
  → IoT Gateway: Connects IoT devices to cloud (protocol conversion)
  → Payment Gateway: Connects merchants to banks (e-commerce)

🎯 PYQ FACT: Gateway = Application Layer (Layer 7) in OSI terms
🎯 PYQ FACT: Gateway connects networks with DIFFERENT PROTOCOLS (router connects same protocol)
🎯 PYQ FACT: Default Gateway = your router's IP from your device's perspective
🚨 TRAP: "Gateway and Router do the same thing" → FALSE!
         Router = same protocol networks; Gateway = different protocols
```

---

### DEVICE 6 — REPEATER and MODEM

```
REPEATER
OSI LAYER: Layer 1 — PHYSICAL LAYER
FUNCTION:
  → Regenerates and amplifies a weakening signal to extend cable distance
  → Receives weak signal, cleans it, amplifies it, retransmits
  → Allows LANs to extend beyond normal cable distance limits
  → Works on RAW BITS — no reading of addresses
  
ANALOGY: Like a relay race baton pass — carries the signal forward and 
         hands it to the next stretch of cable fresh and strong!

🎯 PYQ FACT: Repeater = Layer 1 (Physical); regenerates signal
🎯 PYQ FACT: Hub = multiport repeater (repeater with multiple ports)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
MODEM (Modulator-Demodulator)
OSI LAYER: Layer 1 — PHYSICAL LAYER
FUNCTION:
  → Converts DIGITAL signals (computer) ↔ ANALOG signals (phone line/cable)
  → MODULATION: Digital → Analog (for transmission over analog medium)
  → DEMODULATION: Analog → Digital (when received by computer)

WHY NEEDED:
  Computers speak DIGITAL (binary 0s and 1s)
  Traditional phone lines / cable TV lines carry ANALOG signals
  Modem bridges this gap!

TYPES:
  → Dial-up Modem: Old telephone modems (very slow — 56 Kbps max)
  → ADSL Modem: Broadband over phone line (asymmetric — faster download)
  → Cable Modem: Broadband over cable TV lines
  → Fiber Modem (ONT): For fiber optic internet

🎯 PYQ FACT: Modem = Modulator + Demodulator (from the full form)
🎯 PYQ FACT: Modem converts digital ↔ analog signals
```

---

## 🔷 SECTION 11: Devices vs OSI Layer — Master Reference Table

```
┌───────────────────────┬────────────────────────┬────────────────────────────────────────────┐
│       DEVICE          │      OSI LAYER         │         KEY FUNCTION                       │
├───────────────────────┼────────────────────────┼────────────────────────────────────────────┤
│ Repeater              │ Layer 1 — Physical      │ Regenerates/amplifies signal               │
├───────────────────────┼────────────────────────┼────────────────────────────────────────────┤
│ Hub                   │ Layer 1 — Physical      │ Broadcasts to all ports (multiport repeater)│
├───────────────────────┼────────────────────────┼────────────────────────────────────────────┤
│ Modem                 │ Layer 1 — Physical      │ Digital ↔ Analog conversion               │
├───────────────────────┼────────────────────────┼────────────────────────────────────────────┤
│ NIC (Network          │ Layer 2 — Data Link     │ Connects device to network; has MAC address│
│ Interface Card)       │                        │                                            │
├───────────────────────┼────────────────────────┼────────────────────────────────────────────┤
│ Bridge                │ Layer 2 — Data Link     │ Connects two LAN segments; reduces collision│
├───────────────────────┼────────────────────────┼────────────────────────────────────────────┤
│ Switch                │ Layer 2 — Data Link     │ Connects LAN devices; unicasts via MAC table│
├───────────────────────┼────────────────────────┼────────────────────────────────────────────┤
│ Router                │ Layer 3 — Network       │ Connects different networks; routes via IP │
├───────────────────────┼────────────────────────┼────────────────────────────────────────────┤
│ Layer 3 Switch        │ Layers 2 + 3            │ Switch + Routing capabilities              │
├───────────────────────┼────────────────────────┼────────────────────────────────────────────┤
│ Gateway               │ Layer 7 — Application   │ Connects different protocol networks       │
│                       │ (all layers)           │                                            │
└───────────────────────┴────────────────────────┴────────────────────────────────────────────┘

MEMORY TRICK for Layer Mapping:
  Layer 1 devices: "Really Hot Machines" (Repeater, Hub, Modem)
  Layer 2 devices: "Big Switches Need" (Bridge, Switch, NIC)
  Layer 3 devices: "Routers Rule" (Router)
  Layer 7 devices: "Gateways Go" (Gateway)
```

---

## 🔷 SECTION 12: World Wide Web (WWW)

```
WWW = World Wide Web
INVENTED BY: Tim Berners-Lee (1989-1991) at CERN, Switzerland
             Tim Berners-Lee = "Father of the World Wide Web"
FIRST WEBSITE: info.cern.ch (still accessible today!)

DEFINITION:
  The World Wide Web is a system of interlinked HYPERTEXT documents
  and resources accessible via the INTERNET using a web BROWSER.

WWW ≠ INTERNET (Common confusion!):
  INTERNET = the global network infrastructure (the "roads and cables")
             All connected computers, servers, routers — the physical network
  WWW = a SERVICE that runs ON the internet (the "vehicles on those roads")
        Collection of web pages, hyperlinks, browsers, web servers
        ONE of many services on the internet (others: email, FTP, VoIP, etc.)

WWW COMPONENTS:
  1. HTML (HyperText Markup Language): Language for creating web pages
  2. HTTP/HTTPS: Protocol for sending web pages
  3. URL (Uniform Resource Locator): Web address (e.g., https://www.google.com)
  4. Web Browser: Client software to view web pages (Chrome, Firefox, Edge)
  5. Web Server: Server software serving web pages (Apache, Nginx, IIS)
  6. Hyperlinks: Clickable links connecting one web page to another

URL STRUCTURE:
  https://www.example.com/path/to/page.html
  ─────   ───────────────  ───────────────
  Protocol  Domain name     Path/Resource

WEB BROWSER vs WEB SERVER:
  Browser (Client): Chrome, Firefox, Safari, Edge — requests web pages
  Web Server: Apache, Nginx — serves web pages to browsers

🎯 PYQ FACT: WWW invented by Tim Berners-Lee (1989) at CERN
🎯 PYQ FACT: WWW ≠ Internet (WWW is a service that runs on the Internet)
🎯 PYQ FACT: HTML = language for web pages; HTTP = protocol for sending them
🎯 PYQ FACT: URL = Uniform Resource Locator (web address)
🚨 TRAP: "The Internet and WWW are the same thing" → FALSE!
         Internet = infrastructure; WWW = a service using that infrastructure.
```

---

## 🔷 SECTION 13: PYQ Traps — Topologies and Devices

```
🚨 TRAP 1: "Peer-to-Peer is a network topology" → FALSE!
   P2P = network architecture/model, NOT a topology.
   Topologies = Bus, Star, Ring, Mesh, Tree, Hybrid.

🚨 TRAP 2: "In Star topology, one device failing kills the whole network" → FALSE!
   Only the CENTRAL HUB/SWITCH failure kills the Star network.
   Individual device/cable failure only affects that one device.

🚨 TRAP 3: "Bus topology is most reliable" → FALSE!
   Bus = LEAST reliable (one cable break = whole network down).
   Mesh = MOST reliable.

🚨 TRAP 4: "Switch connects different networks" → FALSE!
   Switch = same network (LAN). Router = different networks.

🚨 TRAP 5: "Hub reads MAC addresses and sends to correct port" → FALSE!
   Hub = BROADCASTS to ALL ports (no address reading).
   Switch = reads MAC, sends to CORRECT port only.

🚨 TRAP 6: "Router works at Data Link Layer (Layer 2)" → FALSE!
   Router = Layer 3 (Network Layer).
   Switch = Layer 2 (Data Link Layer).

🚨 TRAP 7: "Gateway does the same job as Router" → FALSE!
   Router = connects networks using SAME protocol (IP routing).
   Gateway = connects networks using DIFFERENT protocols (protocol translation).

🚨 TRAP 8: "Ring topology has the most collisions" → FALSE!
   Ring uses TOKEN PASSING — NO collisions!
   Bus topology has collision problems (uses CSMA/CD).

🚨 TRAP 9: "Tree topology = Mesh topology" → FALSE!
   Tree = hierarchical, root failure = network failure.
   Mesh = every device to every device, highest redundancy.

🚨 TRAP 10: "WWW = Internet" → FALSE!
   WWW = a service ON the Internet (not the Internet itself).
   Tim Berners-Lee invented WWW, NOT the Internet.
   (Internet developed by DARPA; WWW by Tim Berners-Lee)

🚨 TRAP 11: "Modem = Switch" → FALSE!
   Modem = converts digital ↔ analog (Layer 1).
   Switch = MAC-based LAN device (Layer 2).

🚨 TRAP 12: "Mesh topology is cheapest" → FALSE!
   Mesh = MOST EXPENSIVE (needs n(n-1)/2 links).
   Bus = cheapest.
```

---

# PART 2: GENERAL STUDIES
## 🌟 Bihar GK — Famous Personalities of Bihar

---

## 🔷 SECTION 1: Dr. Rajendra Prasad — First President of India

```
DR. RAJENDRA PRASAD
BORN:        December 3, 1884, Ziradei, Siwan district, Bihar
DIED:        February 28, 1963, Patna
EDUCATION:   Law degree from Calcutta University; later earned doctorate

MAJOR CONTRIBUTIONS:

1. FIRST PRESIDENT OF INDIA:
   → Served as President from January 26, 1950 to May 13, 1962
   → The ONLY person to serve TWO FULL TERMS as President of India!
   → Presided over India's first Republic Day on January 26, 1950

2. CONSTITUENT ASSEMBLY:
   → PRESIDENT of the Constituent Assembly of India
   → Oversaw the drafting and adoption of the Indian Constitution
   → Signed the Constitution on behalf of the Constituent Assembly

3. FREEDOM MOVEMENT:
   → Active in Non-Cooperation Movement (1920-22)
   → Active in Civil Disobedience Movement (1930-31)
   → Participated in Quit India Movement (1942)
   → Close associate of Mahatma Gandhi

4. CHAMPARAN SATYAGRAHA (1917):
   → Worked with Gandhi in Bihar's Champaran Satyagraha
   → First major satyagraha of Gandhi in India — against indigo planters

5. BOOKS WRITTEN:
   → "Autobiography" (autobiography)
   → "India Divided" (critique of partition)
   → "Satyagraha in Champaran"
   → "Mahatma Gandhi and Bihar"

AWARDS:
   → Bharat Ratna (1962) — India's highest civilian honour

LEGACY:
   → His statue stands in many places across Bihar
   → Rajendra Prasad's birthday (December 3) is celebrated in Bihar
   → Rajendra Memorial Museum in Patna

🎯 PYQ FACT: Rajendra Prasad = First President of India (1950-1962)
🎯 PYQ FACT: Only President to serve TWO FULL TERMS
🎯 PYQ FACT: President of Constituent Assembly
🎯 PYQ FACT: Bharat Ratna recipient (1962)
🎯 PYQ FACT: Born in Ziradei, Siwan district, Bihar
```

---

## 🔷 SECTION 2: Jayaprakash Narayan (JP) — Loknayak

```
JAYAPRAKASH NARAYAN (J.P.)
BORN:        October 11, 1902, Sitabdiara, Saran district, Bihar
DIED:        October 8, 1979, Patna
KNOWN AS:    "Loknayak" (People's Leader)

MAJOR CONTRIBUTIONS:

1. SOCIALIST FREEDOM FIGHTER:
   → Active in Non-Cooperation Movement
   → Participated in Quit India Movement (1942) — went underground
   → Escaped from Hazaribagh Central Jail during British rule!
   → Co-founder of Congress Socialist Party (1934)
   
2. JP MOVEMENT (1974-1977):
   → LED the movement against Indira Gandhi's Emergency!
   → "Total Revolution" (Sampurna Kranti) call — demand for fundamental change
   → Students and masses rallied around him across India
   → Led to formation of Janata Party and defeat of Indira Gandhi in 1977 election
   → Post-Emergency: JP is credited with RESTORING DEMOCRACY to India!

3. FOUNDER OF SARVODAYA MOVEMENT:
   → Gave up active politics post-independence
   → Worked with Vinoba Bhave in the Bhoodan (land gift) and Sarvodaya movement
   → "Sarvodaya" = welfare of all; grassroots non-violent social movement

4. ANTI-CORRUPTION STAND:
   → Opposed Indira Gandhi's autocratic Emergency rule (1975-77)
   → Symbol of democratic resistance and civil liberties
   → Arrested during Emergency

AWARDS:
   → Bharat Ratna (1999) — posthumously

LEGACY:
   → Patna's Jai Prakash Narayan International Airport named after him
   → JP Narayan is an icon of Bihar and Indian democracy
   → October 11 = Jayaprakash Narayan Jayanti (celebrated in Bihar)

🎯 PYQ FACT: JP = "Loknayak" = born Sitabdiara, Saran district, Bihar
🎯 PYQ FACT: Led JP Movement / Total Revolution (Sampurna Kranti) against Emergency
🎯 PYQ FACT: Bharat Ratna (posthumous, 1999)
🎯 PYQ FACT: Patna airport = Jai Prakash Narayan International Airport
🎯 PYQ FACT: Co-founded Congress Socialist Party (1934)
```

---

## 🔷 SECTION 3: Chanakya (Kautilya / Vishnugupta)

```
CHANAKYA
ALSO KNOWN AS: Kautilya, Vishnugupta
ERA:           ~350–275 BCE (4th century BCE)
BIRTHPLACE:    Various accounts — traditionally Taxila (now Pakistan) or Pataliputra (Patna)
               Most accounts link him to Magadha (Bihar) as his place of work

MAJOR CONTRIBUTIONS:

1. ARTHASHASTRA:
   → Wrote the "Arthashastra" — world's FIRST systematic treatise on:
     State administration, economic policy, military strategy,
     law, diplomacy, and espionage!
   → Considered the "first political economist"
   → Rediscovered in 1905 by Rudrapatna Shamasastry (after being "lost" for centuries)
   
2. CHANDRAGUPTA MAURYA'S MENTOR:
   → The KINGMAKER — identified, trained, and guided Chandragupta Maurya
   → Helped Chandragupta DEFEAT the Nanda dynasty and establish Maurya Empire
   → Prime Minister (Mahamantri) of the Maurya Empire
   → The MAURYA EMPIRE (322–185 BCE) became one of ancient India's greatest empires

3. POLITICAL PHILOSOPHY:
   → "An eye for an eye, a tooth for a tooth" — practical realpolitik
   → "The end justifies the means" — pragmatic statecraft
   → Compared to Machiavelli ("India's Machiavelli") for practical political wisdom
   → Arthashastra covers: taxation, law, war, espionage — highly modern concepts!

4. NALANDA CONNECTION:
   → Associated with Takshashila (Taxila) university as a teacher
   → Educated at Takshashila, one of the world's earliest universities

CHANAKYA QUOTES (exam-worthy):
   "A person should not be too honest. Straight trees are cut first."
   "Education is the best friend. An educated person is respected everywhere."
   "The biggest guru-mantra is: never share your secrets with anybody."

🎯 PYQ FACT: Chanakya = author of Arthashastra (economics + politics + military)
🎯 PYQ FACT: Chanakya's other names = Kautilya, Vishnugupta
🎯 PYQ FACT: Chanakya was Prime Minister (Mahamantri) of Maurya Empire
🎯 PYQ FACT: Chanakya = kingmaker of Chandragupta Maurya
🎯 PYQ FACT: Arthashastra rediscovered in 1905 by R. Shamasastry
```

---

## 🔷 SECTION 4: Other Prominent Bihar Personalities

### Sher Shah Suri:
```
SHER SHAH SURI
BORN:  1486, Sasaram, Rohtas district, Bihar
DIED:  1545, Kalinjar, Madhya Pradesh
DYNASTY: Sur Dynasty (1540-1555)

MAJOR CONTRIBUTIONS:
1. GRAND TRUNK ROAD:
   → Built the Sadak-e-Azam (now Grand Trunk Road / NH-19)
   → Stretched from Kabul (Afghanistan) to Bengal
   → One of the world's oldest and longest roads!
   → Made with milestones (kos minar), caravanserais (rest houses), wells
   
2. ADMINISTRATION:
   → Land revenue reform (Sur administration basis for Akbar's later reforms)
   → Postal system improvements
   → Introduced Rupiya (silver coin) — precursor to modern RUPEE!
   
3. DEFEATED HUMAYUN:
   → Defeated Mughal Emperor Humayun at Battle of Chausa (1539) and
     Battle of Kanauj (1540) — forced Humayun into 15 years of exile

4. SASARAM TOMB:
   → His magnificent tomb in Sasaram (Rohtas district) is a UNESCO candidate
   → Called the "gem of the Indo-Afghan architectural style"

🎯 PYQ FACT: Sher Shah Suri = born Sasaram, Rohtas district, Bihar
🎯 PYQ FACT: Built Grand Trunk Road (Sadak-e-Azam)
🎯 PYQ FACT: Introduced Rupiya (silver coin) — origin of Indian Rupee
🎯 PYQ FACT: Defeated Humayun (Battle of Chausa 1539, Kanauj 1540)
```

### Kunwar Singh:
```
KUNWAR SINGH (Babu Veer Kunwar Singh)
BORN:  1777, Jagdishpur, Bhojpur district, Bihar
DIED:  April 26, 1858, Jagdishpur
AGE AT REVOLT: ~80 years old! (inspiring story)

MAJOR CONTRIBUTION:
→ HERO OF 1857 REVOLT IN BIHAR
→ Led the uprising against British in Bihar during 1857 First War of Independence
→ Won SEVERAL battles against British forces despite old age and injury
→ He was shot in the arm during battle — cut off his own arm and offered it to the Ganga!
   (A legendary act of patriotism and courage)
→ Died just days after winning the final battle at Jagdishpur (April 23 = victory,
   died April 26, 1858)

LEGACY:
→ April 23 = Vijayotsav (Victory celebration) in Bihar
→ "Veer Babu Kunwar Singh" or "Babu Kunwar Singh" — revered in Bhojpur region
→ His statue at Jagdishpur; Veer Kunwar Singh University in Ara named after him

🎯 PYQ FACT: Kunwar Singh = hero of 1857 revolt in Bihar
🎯 PYQ FACT: Born in Jagdishpur, Bhojpur district
🎯 PYQ FACT: Led revolt at age ~80 — symbol of undying patriotism
🎯 PYQ FACT: April 23 = Vijayotsav in Bihar (Kunwar Singh's victory day)
```

### Birsa Munda (Brief — covered in detail on Day 36):
```
BIRSA MUNDA
BORN:  November 15, 1875, Ulihatu, Khunti (Ranchi district) — now Jharkhand
DIED:  June 9, 1900 (age 25), Ranchi Jail

KEY FACTS:
→ Called "Dharti Abba" (Father of the Earth) by Munda tribals
→ Led "ULGULAN" (Great Revolt) 1899-1900 against British + landlords
→ Legacy: Chota Nagpur Tenancy Act (1908) — protects tribal land rights
→ November 15 = Jharkhand Foundation Day (his birthday)
→ Portrait in Central Hall of Indian Parliament

🎯 PYQ FACT (Bihar context): Though Birsa's revolt is now in Jharkhand territory,
   it was historically part of Bihar's freedom struggle and BPSC asks about him.
```

### Dr. A.P.J. Abdul Kalam — (Connected to Bihar through Nalanda and respect):
```
Note: Kalam is from Tamil Nadu (Rameswaram), NOT Bihar.
But he is relevant as a science/technology figure — don't confuse him as a Bihar personality!

GENUINE BIHAR PERSONALITIES (Summary):
  RAJENDRA PRASAD — Ziradei, Siwan (First President, Bharat Ratna)
  J.P. NARAYAN    — Sitabdiara, Saran (Loknayak, JP Movement, Bharat Ratna)
  CHANAKYA        — Associated with Pataliputra/Magadha (Arthashastra)
  SHER SHAH SURI  — Sasaram, Rohtas (Grand Trunk Road, Rupiya, defeated Humayun)
  KUNWAR SINGH    — Jagdishpur, Bhojpur (1857 revolt hero)
  BIRSA MUNDA     — (now Jharkhand) tribal freedom fighter
```

---

## 🔷 SECTION 5: Bihar Personalities — Quick Reference Table

```
┌───────────────────────┬─────────────────────────┬────────────────────────────────────────────┐
│     PERSONALITY       │   BIRTHPLACE (Bihar)    │          KEY CONTRIBUTION                  │
├───────────────────────┼─────────────────────────┼────────────────────────────────────────────┤
│ Dr. Rajendra Prasad   │ Ziradei, Siwan           │ 1st President; Constituent Assembly Head; │
│                       │                          │ Bharat Ratna (1962)                        │
├───────────────────────┼─────────────────────────┼────────────────────────────────────────────┤
│ Jayaprakash Narayan   │ Sitabdiara, Saran        │ Loknayak; JP Movement / Total Revolution; │
│ (J.P.)                │                          │ Anti-Emergency; Bharat Ratna (1999, posth.)│
├───────────────────────┼─────────────────────────┼────────────────────────────────────────────┤
│ Chanakya              │ Magadha / Taxila area    │ Arthashastra; Kingmaker of Chandragupta;  │
│ (Kautilya)            │                          │ Mahamantri of Maurya Empire                │
├───────────────────────┼─────────────────────────┼────────────────────────────────────────────┤
│ Sher Shah Suri        │ Sasaram, Rohtas          │ Grand Trunk Road; Rupiya (Rupee origin);  │
│                       │                          │ Defeated Humayun; Sur Dynasty founder      │
├───────────────────────┼─────────────────────────┼────────────────────────────────────────────┤
│ Kunwar Singh          │ Jagdishpur, Bhojpur      │ 1857 revolt hero in Bihar; fought at ~80; │
│                       │                          │ Apr 23 = Vijayotsav in Bihar               │
├───────────────────────┼─────────────────────────┼────────────────────────────────────────────┤
│ Birsa Munda           │ Ulihatu, Khunti (now     │ Tribal revolt (Ulgulan 1899-1900);         │
│                       │ Jharkhand)               │ "Dharti Abba"; CNT Act 1908 legacy         │
├───────────────────────┼─────────────────────────┼────────────────────────────────────────────┤
│ Aryabhata             │ Kusumapura (Pataliputra /│ Zero; decimal system; pi approximation;   │
│                       │ Patna area) — ancient    │ heliocentric model; Aryabhatiya             │
├───────────────────────┼─────────────────────────┼────────────────────────────────────────────┤
│ Shrikrishna Singh     │ Mashrakh, Saran          │ First Chief Minister of Bihar;            │
│ (Sri Babu)            │                          │ "Mahamahopadhyay"; development of Bihar   │
└───────────────────────┴─────────────────────────┴────────────────────────────────────────────┘
```

### Aryabhata — The Mathematical Genius:
```
ARYABHATA
ERA:   476 CE – 550 CE
BIRTHPLACE: Kusumapura (identified with Pataliputra = ancient Patna)

CONTRIBUTIONS:
1. ZERO: Conceptualised and used ZERO as a number
   (though Brahmagupta later formalized it)
2. DECIMAL SYSTEM: Place value system using 1-9 and zero
3. PI (π): Calculated pi = 3.1416 (remarkably accurate for the era!)
4. ARYABHATIYA (499 CE): His major work — covers arithmetic, algebra,
   trigonometry, and spherical astronomy
5. HELIOCENTRIC IDEA: Suggested Earth rotates on its axis
   (revolutionary — 1000 years before Copernicus in Europe!)
6. SOLAR/LUNAR ECLIPSES: Correctly explained eclipses as shadows
   (rejected the mythological "Rahu-Ketu" explanation)
7. ALGEBRA: Advanced algebraic techniques

INDIA'S TRIBUTE:
→ India's first satellite = ARYABHATA (launched 1975 by ISRO)
→ Named in honour of this Bihar mathematician!
→ Aryabhata Research Institute of Observational Sciences in Nainital

🎯 PYQ FACT: Aryabhata = from Kusumapura (ancient Patna/Bihar area)
🎯 PYQ FACT: Aryabhatiya (499 CE) = his major mathematical work
🎯 PYQ FACT: India's first satellite = Aryabhata (1975)
🎯 PYQ FACT: Aryabhata suggested Earth rotates (heliocentric idea)
```

---

## 🔷 SECTION 6: Bihar Personalities — PYQ Traps

```
🚨 TRAP 1: "Rajendra Prasad was the first Prime Minister of India" → FALSE!
   First PM = Jawaharlal Nehru.
   Rajendra Prasad = first PRESIDENT of India.

🚨 TRAP 2: "JP Narayan received Bharat Ratna during his lifetime" → FALSE!
   JP = Bharat Ratna in 1999 — POSTHUMOUSLY (he died in 1979).

🚨 TRAP 3: "Chanakya wrote the Mahabharata" → FALSE!
   Chanakya wrote ARTHASHASTRA.
   Mahabharata = attributed to Vyasa.

🚨 TRAP 4: "Sher Shah Suri was a Mughal emperor" → FALSE!
   Sher Shah Suri = founder of Sur Dynasty, a rival to Mughals.
   He DEFEATED Mughal Humayun and ruled for 5 years (1540-1545).

🚨 TRAP 5: "Kunwar Singh was a young man during the 1857 revolt" → FALSE!
   He was approximately 80 years old! His age = what makes him extraordinary.

🚨 TRAP 6: "Grand Trunk Road was built by Akbar" → FALSE!
   Grand Trunk Road = built by SHER SHAH SURI (Sadak-e-Azam).
   Akbar improved Sher Shah Suri's administrative systems.

🚨 TRAP 7: "Aryabhata invented zero absolutely" → NUANCED!
   Aryabhata used zero and the decimal system conceptually.
   But Brahmagupta (7th century) formalized zero rules in arithmetic.
   For BPSC context: Aryabhata is credited with early concept of zero.

🚨 TRAP 8: "Rajendra Prasad served only one term as President" → FALSE!
   He served TWO FULL TERMS (1950-1952 and 1952-1957 and part of 1957-1962).
   = Only president to serve TWO FULL TERMS.

🚨 TRAP 9: "JP Movement was against the Emergency (declared in 1975)" → NUANCED!
   JP Movement STARTED in 1974 (before Emergency).
   It TRIGGERED Indira Gandhi to declare Emergency in June 1975.
   JP led the anti-Emergency resistance throughout 1975-77.

🚨 TRAP 10: "Birsa Munda was from Bihar" → TECHNICALLY NOW JHARKHAND!
   Birsa Munda's homeland is now in Jharkhand (separated from Bihar in 2000).
   But historically it was Bihar — BPSC includes him in Bihar's freedom struggle.
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Network Topologies, Devices, OSI Layer Mapping, WWW

---

**Q1.** A network where all devices connect to a single central switch is called:
(A) Bus Topology
(B) Ring Topology
(C) Star Topology
(D) More than one of the above
(E) None of the above

---

**Q2.** In which topology does a single cable break cause the ENTIRE network to fail?
(A) Star Topology
(B) Mesh Topology
(C) Bus Topology
(D) More than one of the above
(E) None of the above

---

**Q3.** Which topology offers the HIGHEST fault tolerance and reliability?
(A) Bus Topology
(B) Star Topology
(C) Mesh Topology
(D) More than one of the above
(E) None of the above

---

**Q4.** In Ring Topology, data transmission is controlled by:
(A) CSMA/CD (Carrier Sense Multiple Access / Collision Detection)
(B) Token Passing — only the device holding the token can send
(C) Broadcasting from a central hub
(D) More than one of the above
(E) None of the above

---

**Q5.** Tree Topology is BEST described as:
(A) A combination of Ring and Bus topologies
(B) A combination of Star and Bus topologies in a hierarchical structure
(C) A combination of Star and Mesh topologies
(D) More than one of the above
(E) None of the above

---

**Q6.** "Peer-to-Peer" in networking is:
(A) A type of network topology (like Bus or Ring)
(B) A network architecture/model where each device acts as both client and server
(C) Another name for Star topology
(D) More than one of the above
(E) None of the above

---

**Q7.** For a network of 5 devices in a FULL MESH topology, how many links (connections) are required?
(A) 5
(B) 8
(C) 10
(D) More than one of the above
(E) None of the above

---

**Q8.** A HUB operates at which OSI layer and how does it handle incoming data?
(A) Layer 2; reads MAC addresses and forwards to correct port
(B) Layer 3; reads IP addresses and routes to destination
(C) Layer 1; broadcasts to ALL ports without reading any addresses
(D) More than one of the above
(E) None of the above

---

**Q9.** A SWITCH primarily operates at which OSI layer?
(A) Physical Layer (Layer 1)
(B) Data Link Layer (Layer 2)
(C) Network Layer (Layer 3)
(D) More than one of the above
(E) None of the above

---

**Q10.** A Switch decides where to forward data using:
(A) IP addresses from its routing table
(B) MAC addresses from its MAC address table (CAM table)
(C) Port numbers from its TCP/UDP table
(D) More than one of the above
(E) None of the above

---

**Q11.** A ROUTER primarily operates at which OSI layer?
(A) Data Link Layer (Layer 2)
(B) Network Layer (Layer 3)
(C) Transport Layer (Layer 4)
(D) More than one of the above
(E) None of the above

---

**Q12.** The key DIFFERENCE between a Router and a Switch is:
(A) Router uses MAC addresses; Switch uses IP addresses
(B) Switch connects devices within the SAME network; Router connects DIFFERENT networks
(C) Router is slower than Switch in all cases
(D) More than one of the above
(E) None of the above

---

**Q13.** A BRIDGE in networking:
(A) Connects two LANs at the Data Link Layer; reduces collision domains
(B) Connects networks with different protocols at Layer 7
(C) Broadcasts data to all connected networks
(D) More than one of the above
(E) None of the above

---

**Q14.** A GATEWAY is BEST described as:
(A) A device that broadcasts data to all nodes on a network
(B) A device that connects networks using DIFFERENT protocols (protocol translator)
(C) A device identical to a Router that only connects IP networks
(D) More than one of the above
(E) None of the above

---

**Q15.** A REPEATER's primary function is:
(A) Read MAC addresses and forward to correct port
(B) Regenerate and amplify weakening network signals to extend cable distance
(C) Convert digital signals to analog for telephone transmission
(D) More than one of the above
(E) None of the above

---

**Q16.** A MODEM is used for:
(A) Connecting multiple devices in a LAN using MAC addresses
(B) Converting digital computer data to analog signals (and vice versa) for transmission
(C) Routing packets between different IP networks
(D) More than one of the above
(E) None of the above

---

**Q17.** Which of the following correctly maps devices to their OSI layers?
I.   Hub → Layer 1 (Physical)
II.  Switch → Layer 2 (Data Link)
III. Router → Layer 3 (Network)
IV.  Gateway → Layer 2 (Data Link)

(A) I, II, and III only
(B) All four are correct
(C) I and III only
(D) More than one of the above
(E) None of the above

---

**Q18.** The World Wide Web (WWW) was invented by:
(A) Vinton Cerf and Robert Kahn
(B) Tim Berners-Lee (at CERN, 1989)
(C) Bill Gates (at Microsoft, 1991)
(D) More than one of the above
(E) None of the above

---

**Q19.** Which statement CORRECTLY distinguishes the Internet from the World Wide Web?
(A) They are the same — Internet and WWW are interchangeable terms
(B) Internet = global network infrastructure; WWW = a service (websites/hyperlinks) running ON the Internet
(C) WWW is larger than the Internet
(D) More than one of the above
(E) None of the above

---

**Q20.** A logical topology can DIFFER from the physical topology. Which example correctly demonstrates this?
(A) Star physical layout = always star logical flow
(B) Traditional Ethernet hub network: physical = Star (all cables to hub), logical = Bus (hub broadcasts like bus)
(C) Ring physical = always ring logical flow
(D) More than one of the above
(E) None of the above

---

**Q21.** In a Star topology, which scenario causes the ENTIRE NETWORK to fail?
(A) A single end-device (like one computer) or its cable fails
(B) The central hub or switch fails
(C) Two end-devices fail simultaneously
(D) More than one of the above
(E) None of the above

---

**Q22.** Bus topology uses which access control mechanism to handle multiple devices sharing the same medium?
(A) Token Passing
(B) TDMA (Time Division Multiple Access)
(C) CSMA/CD (Carrier Sense Multiple Access / Collision Detection)
(D) More than one of the above
(E) None of the above

---

**Q23.** Which networking device is described as a "multiport repeater" that broadcasts to all ports?
(A) Router
(B) Switch
(C) Hub
(D) More than one of the above
(E) None of the above

---

**Q24.** The Internet backbone connecting major ISPs (Internet Service Providers) worldwide typically uses which topology?
(A) Full Mesh Topology (every ISP directly connected to every other)
(B) Ring Topology (ISPs form a global ring)
(C) Partial Mesh Topology (multiple redundant connections but not every pair directly connected)
(D) More than one of the above
(E) None of the above

---

**Q25.** Consider these statements:
I.   Bus topology requires terminators at both ends of the cable.
II.  Mesh topology is the most expensive but most fault-tolerant topology.
III. A Switch reads IP addresses; a Router reads MAC addresses.
IV.  Tree topology is also called Hierarchical topology.

Which are CORRECT?
(A) I, II, and IV only
(B) I, II, III, and IV all correct
(C) II and III only
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: Bihar GK — Famous Personalities and Their Contributions

---

**Q26.** Who was the FIRST President of India?
(A) Jawaharlal Nehru
(B) Sardar Vallabhbhai Patel
(C) Dr. Rajendra Prasad
(D) More than one of the above
(E) None of the above

---

**Q27.** Dr. Rajendra Prasad was born in which district of Bihar?
(A) Patna
(B) Saran
(C) Siwan
(D) More than one of the above
(E) None of the above

---

**Q28.** Dr. Rajendra Prasad was the President of which important national body that drafted India's Constitution?
(A) Planning Commission
(B) Constituent Assembly of India
(C) Rajya Sabha
(D) More than one of the above
(E) None of the above

---

**Q29.** Dr. Rajendra Prasad is the ONLY person to have served:
(A) As both Prime Minister and President of India
(B) Two full terms as President of India
(C) As the first Chief Minister and President of Bihar
(D) More than one of the above
(E) None of the above

---

**Q30.** Dr. Rajendra Prasad received which India's highest civilian honour?
(A) Padma Vibhushan
(B) Padma Bhushan
(C) Bharat Ratna (1962)
(D) More than one of the above
(E) None of the above

---

**Q31.** Jayaprakash Narayan was born in which district of Bihar?
(A) Patna
(B) Saran
(C) Gaya
(D) More than one of the above
(E) None of the above

---

**Q32.** Jayaprakash Narayan is popularly known as:
(A) "Deshratna" (Jewel of the Nation)
(B) "Loknayak" (People's Leader)
(C) "Sardar" (Brave Commander)
(D) More than one of the above
(E) None of the above

---

**Q33.** JP Narayan's "Total Revolution" (Sampurna Kranti) movement of 1974-77 was primarily:
(A) A movement for Bihar's separation into smaller states
(B) A movement against Indira Gandhi's authoritarian Emergency rule, demanding fundamental democratic change
(C) A movement for the rights of agricultural workers in Bihar
(D) More than one of the above
(E) None of the above

---

**Q34.** Patna's international airport is named after:
(A) Dr. Rajendra Prasad
(B) Jai Prakash Narayan
(C) Chandragupta Maurya
(D) More than one of the above
(E) None of the above

---

**Q35.** Chanakya (Kautilya) is famous for writing:
(A) Ramayana — the epic story of Lord Rama
(B) Arthashastra — a treatise on statecraft, economics, and military strategy
(C) Mahabharata — the great Indian epic
(D) More than one of the above
(E) None of the above

---

**Q36.** Chanakya served as which position in the Maurya Empire?
(A) Commander-in-Chief (Senapati)
(B) Chief Justice (Dharmadhikari)
(C) Prime Minister (Mahamantri) under Chandragupta Maurya
(D) More than one of the above
(E) None of the above

---

**Q37.** The "Arthashastra" was rediscovered in modern times by:
(A) Rabindranath Tagore in 1901
(B) Rudrapatna Shamasastry in 1905
(C) Bal Gangadhar Tilak in 1907
(D) More than one of the above
(E) None of the above

---

**Q38.** Sher Shah Suri was born in which district of Bihar?
(A) Patna
(B) Bhojpur
(C) Sasaram (Rohtas district)
(D) More than one of the above
(E) None of the above

---

**Q39.** Which MAJOR infrastructure work is attributed to Sher Shah Suri?
(A) The Qutub Minar in Delhi
(B) Grand Trunk Road (Sadak-e-Azam) — from Bengal to Kabul
(C) The Taj Mahal in Agra
(D) More than one of the above
(E) None of the above

---

**Q40.** Sher Shah Suri introduced which currency that is the origin of the modern Indian Rupee?
(A) Gold Dinar
(B) Copper Paisa
(C) Silver Rupiya (Rupee)
(D) More than one of the above
(E) None of the above

---

**Q41.** Babu Kunwar Singh, the 1857 revolt hero, was born in which district of Bihar?
(A) Saran
(B) Bhojpur (Jagdishpur)
(C) Rohtas
(D) More than one of the above
(E) None of the above

---

**Q42.** Which date is celebrated as "Vijayotsav" (Victory Celebration) in Bihar in honour of Babu Kunwar Singh?
(A) March 23 (Bhagat Singh's martyrdom day)
(B) April 23 (Kunwar Singh's victory at Jagdishpur)
(C) November 15 (Birsa Munda's birthday)
(D) More than one of the above
(E) None of the above

---

**Q43.** Aryabhata, the ancient Indian mathematician-astronomer, is associated with which modern city in Bihar?
(A) Muzaffarpur
(B) Patna (ancient Kusumapura/Pataliputra)
(C) Nalanda
(D) More than one of the above
(E) None of the above

---

**Q44.** India's first satellite, launched in 1975, was named:
(A) Bhaskara
(B) Rohini
(C) Aryabhata
(D) More than one of the above
(E) None of the above

---

**Q45.** Birsa Munda's armed tribal revolt against British rule (1899-1900) is known as:
(A) Sanyasi Revolt
(B) Ulgulan (The Great Tumult)
(C) Indigo Revolt
(D) More than one of the above
(E) None of the above

---

**Q46.** The Chota Nagpur Tenancy Act (1908), which protects tribal land rights, was a direct result of:
(A) JP Narayan's total revolution movement
(B) Birsa Munda's Ulgulan revolt (1899-1900)
(C) Kunwar Singh's resistance in 1857
(D) More than one of the above
(E) None of the above

---

**Q47.** Which of the following pairs is CORRECTLY matched?
(A) Rajendra Prasad — Arthashastra
(B) Chanakya — First President of India
(C) Sher Shah Suri — Grand Trunk Road
(D) More than one of the above
(E) None of the above

---

**Q48.** JP Narayan received the Bharat Ratna in which year, and under what circumstances?
(A) 1962, during his lifetime, for freedom struggle contribution
(B) 1999, posthumously (he had died in 1979)
(C) 1977, for leading the anti-Emergency movement
(D) More than one of the above
(E) None of the above

---

**Q49.** Which of these Bihar personalities is associated with the CHAMPARAN SATYAGRAHA (1917)?
(A) Kunwar Singh
(B) Chanakya
(C) Rajendra Prasad (worked with Gandhi in the Champaran Satyagraha)
(D) More than one of the above
(E) None of the above

---

**Q50.** Consider these statements about Bihar personalities:
I.  Dr. Rajendra Prasad = First President; born in Siwan; Bharat Ratna 1962.
II. JP Narayan = "Loknayak"; born in Saran; led Total Revolution; Bharat Ratna posthumously.
III. Sher Shah Suri was a Mughal emperor who built the Taj Mahal.
IV. Aryabhata was associated with ancient Kusumapura (Patna area).

Which statements are CORRECT?
(A) I and II only
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
| 1  | (C) | All devices to one central switch = Star topology |
| 2  | (C) | Bus = single backbone; one break = whole network down |
| 3  | (C) | Mesh = highest reliability (multiple paths, no single failure point) |
| 4  | (B) | Ring uses token passing — prevents collisions |
| 5  | (B) | Tree = Star + Bus, hierarchical (devices→switches→root switch) |
| 6  | (B) | P2P = network model/architecture, NOT a topology |
| 7  | (C) | Full mesh links = n(n-1)/2 = 5×4/2 = 10 links |
| 8  | (C) | Hub = Layer 1, broadcasts to ALL ports (no intelligence) |
| 9  | (B) | Switch = Data Link Layer (Layer 2) |
| 10 | (B) | Switch uses MAC address table (CAM table) for forwarding |
| 11 | (B) | Router = Network Layer (Layer 3) |
| 12 | (B) | Switch = same network (LAN); Router = different networks |
| 13 | (A) | Bridge = Data Link Layer; connects two LANs; reduces collisions |
| 14 | (B) | Gateway = protocol translator; connects networks with DIFFERENT protocols |
| 15 | (B) | Repeater = regenerates/amplifies signal to extend distance |
| 16 | (B) | Modem = converts digital ↔ analog (Modulator-Demodulator) |
| 17 | (A) | I,II,III correct; IV WRONG (Gateway = Layer 7 Application, not Layer 2) |
| 18 | (B) | WWW invented by Tim Berners-Lee at CERN, 1989 |
| 19 | (B) | Internet = infrastructure; WWW = service running on that infrastructure |
| 20 | (B) | Classic example: Hub-based Ethernet = Star physical, Bus logical |
| 21 | (B) | Central hub/switch failure = entire Star network fails |
| 22 | (C) | Bus topology uses CSMA/CD for collision handling |
| 23 | (C) | Hub = multiport repeater (broadcasts to all = like a repeater with many ports) |
| 24 | (C) | Internet backbone = partial mesh (redundant but not full mesh) |
| 25 | (A) | I correct (terminators on bus), II correct (mesh=most expensive+reliable), III WRONG (Switch=MAC, Router=IP), IV correct (Tree=hierarchical) |

---

### GS Answers (Q26–Q50):

| Q  | Ans | Key Reason |
|----|-----|-----------|
| 26 | (C) | Dr. Rajendra Prasad = First President of India |
| 27 | (C) | Born in Ziradei, Siwan district, Bihar |
| 28 | (B) | Rajendra Prasad = President of Constituent Assembly |
| 29 | (B) | Only person to serve TWO full terms as President |
| 30 | (C) | Bharat Ratna (1962) |
| 31 | (B) | JP born in Sitabdiara, Saran district, Bihar |
| 32 | (B) | JP = "Loknayak" (People's Leader) |
| 33 | (B) | JP Movement = against Indira Gandhi's Emergency; demand for Total Revolution |
| 34 | (B) | Patna airport = Jai Prakash Narayan International Airport |
| 35 | (B) | Chanakya = Arthashastra (economics, statecraft, military) |
| 36 | (C) | Chanakya = Mahamantri (Prime Minister) under Chandragupta Maurya |
| 37 | (B) | Arthashastra rediscovered by Rudrapatna Shamasastry in 1905 |
| 38 | (C) | Sher Shah Suri born in Sasaram, Rohtas district, Bihar |
| 39 | (B) | Grand Trunk Road (Sadak-e-Azam) = Sher Shah Suri's greatest contribution |
| 40 | (C) | Silver Rupiya = introduced by Sher Shah Suri (origin of Indian Rupee) |
| 41 | (B) | Kunwar Singh born in Jagdishpur, Bhojpur district |
| 42 | (B) | April 23 = Vijayotsav in Bihar (Kunwar Singh's 1857 victory) |
| 43 | (B) | Aryabhata = from Kusumapura = ancient Patna/Pataliputra |
| 44 | (C) | India's first satellite (1975) = Aryabhata |
| 45 | (B) | Birsa Munda's revolt = Ulgulan (The Great Tumult) |
| 46 | (B) | CNT Act 1908 = direct result of Birsa Munda's Ulgulan (1899-1900) |
| 47 | (C) | Only C is correct: Sher Shah Suri → Grand Trunk Road |
| 48 | (B) | JP = Bharat Ratna 1999, posthumously (died 1979) |
| 49 | (C) | Rajendra Prasad worked with Gandhi in Champaran Satyagraha 1917 |
| 50 | (B) | I correct, II correct, III WRONG (Sher Shah Suri ≠ Mughal; Taj Mahal = Shah Jahan), IV correct |

---

# 🔁 DAY 47 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Network Topologies

### Topology Quick Reference:
```
BUS:    One backbone → cheap → one break = total failure → terminators
STAR:   Central hub/switch → MOST POPULAR → hub/switch failure = down
RING:   Circular → token passing → no collisions → one break = down
MESH:   All to all → MOST RELIABLE → n(n-1)/2 links → MOST EXPENSIVE
TREE:   Hierarchical (Star+Bus) → root failure = total failure
HYBRID: Mix of 2+ topologies → Internet is hybrid

RELIABILITY (high→low): Mesh > Tree > Star > Ring > Bus
COST (high→low):        Mesh > Tree > Star > Ring > Bus
```

### Device-Layer Mapping:
```
LAYER 1 (Physical):   Repeater, Hub (multiport repeater), Modem
LAYER 2 (Data Link):  Bridge, Switch, NIC
LAYER 3 (Network):    Router
LAYER 7 (Application):Gateway

SWITCH uses:  MAC addresses (CAM/MAC Address Table)
ROUTER uses:  IP addresses (Routing Table)
HUB uses:     Nothing — just broadcasts to all!
```

### Key Traps:
```
✅ P2P = network model (NOT topology!)
✅ Bus = collisions (CSMA/CD); Ring = token passing (no collisions)
✅ Switch = LAN (same network); Router = connects DIFFERENT networks
✅ Hub = Layer 1 broadcasts; Switch = Layer 2 unicasts to correct MAC
✅ Gateway ≠ Router (Gateway = different protocols; Router = same protocol)
✅ WWW ≠ Internet (WWW is a service ON the Internet)
✅ Tim Berners-Lee = WWW inventor; DARPA = Internet creator
✅ Mesh links formula = n(n-1)/2
```

---

## ⚡ RAPID FIRE — Bihar Personalities

### Personality-Fact Grid:
```
RAJENDRA PRASAD: Ziradei/Siwan → 1st President → 2 full terms → Bharat Ratna 1962
                 → President of Constituent Assembly → Champaran with Gandhi

JP NARAYAN:      Sitabdiara/Saran → "Loknayak" → Total Revolution/JP Movement
                 → Anti-Emergency → Bharat Ratna 1999 (posthumous)
                 → Patna airport named after him

CHANAKYA:        Magadha/Pataliputra → Arthashastra → Mahamantri Maurya Empire
                 → Kingmaker of Chandragupta Maurya

SHER SHAH SURI:  Sasaram/Rohtas → Grand Trunk Road (Sadak-e-Azam)
                 → Silver Rupiya (origin of Rupee) → Defeated Humayun

KUNWAR SINGH:    Jagdishpur/Bhojpur → 1857 revolt hero in Bihar → ~80 years old
                 → April 23 = Vijayotsav in Bihar

ARYABHATA:       Kusumapura (ancient Patna) → Zero, π, decimal system
                 → Heliocentric idea → India's 1st satellite named "Aryabhata" (1975)
```

### Key Traps — Bihar GK:
```
✅ Rajendra Prasad = PRESIDENT (not PM — Nehru was PM)
✅ JP Bharat Ratna = 1999 POSTHUMOUS (died 1979)
✅ Sher Shah Suri ≠ Mughal (he DEFEATED Mughals!)
✅ Grand Trunk Road = SHER SHAH SURI (not Akbar, not British)
✅ Kunwar Singh was ~80 years old in 1857 (not young)
✅ Rajendra Prasad = TWO full terms as President (unique!)
✅ Arthashastra rediscovered 1905 by Rudrapatna Shamasastry
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **Topologies**: Bus=backbone+terminators+collisions; Star=central switch (MOST COMMON); Ring=token passing; Mesh=n(n-1)/2 links (MOST RELIABLE+EXPENSIVE); Tree=Star+Bus hierarchical; Hybrid=combination; P2P≠topology.
2. **Devices**: Layer1=Repeater/Hub/Modem; Layer2=Bridge/Switch(MAC table); Layer3=Router(IP/routing table); Layer7=Gateway(protocol conversion); Hub broadcasts ALL; Switch unicasts to correct MAC; Router connects different networks.
3. **Traps**: Switch=LAN device; Router=different networks; Bus collision=CSMA/CD; Ring=token passing(no collision); Gateway≠Router; WWW≠Internet; Tim Berners-Lee=WWW inventor.
4. **Rajendra Prasad + JP**: Prasad=Ziradei/Siwan, 1st President, 2 full terms, Bharat Ratna 1962, Constituent Assembly President; JP=Sitabdiara/Saran, Loknayak, Total Revolution, Bharat Ratna 1999 (posthumous), Patna airport.
5. **Chanakya + Sher Shah Suri**: Chanakya=Arthashastra+Mahamantri Maurya Empire+kingmaker; Sher Shah=Sasaram/Rohtas+Grand Trunk Road+Silver Rupiya+defeated Humayun(1540); Kunwar Singh=Jagdishpur/Bhojpur+1857 hero at age 80+April 23=Vijayotsav.

---

## 📅 DAY 48 PREVIEW — What's Coming Next:
**CS**: Computer Networks — Network Security Basics: Firewall, Encryption (Symmetric/Asymmetric), SSL/TLS, VPN, Types of Cyber Attacks (Phishing, DDoS, SQL Injection, Man-in-Middle), Malware types (Virus, Worm, Trojan, Ransomware)
**GS**: Indian Geography — Rivers of India (Himalayan vs Peninsular rivers, tributaries, dams) + Bihar's major rivers

---

*🚀 Day 47 of 170 — You're 27.6% through the journey. Topologies + Devices is one of the most visual and memorable topics in the entire Networks section — the ASCII diagrams will help you draw and recall. For Bihar GK, focus on the "trap" pairs: Rajendra Prasad=President (NOT PM), Sher Shah Suri≠Mughal, JP Bharat Ratna=posthumous 1999. You're building an unbeatable foundation!*
