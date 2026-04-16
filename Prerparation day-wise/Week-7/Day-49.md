# 📅 BPSC TRE 4.0 — DAY 49
## CS Topic: 🔄 FULL REVISION — Computer Networks (Days 43–48)
## GS Topic: 🌍 Indian Geography — Physical Features, Rivers, Climate & Soil
### 🎯 Target: 130+/150 | TOP 50 RANK

---

> **Topper Benchmark:** Day 49 is your POWER REVISION day — the entire Computer Networks unit ends here.
> This day consolidates 6 days of Networks learning into one ultra-dense revision session.
> Geography is one of the **highest-ROI** GS topics — 6–8 marks are always available here.
> Revise hard today. Tomorrow (Day 50) begins PYQ Paper practice — you need to be ready!

---

## ⏰ TODAY'S STUDY SCHEDULE

| Slot | Duration | Activity |
|------|----------|----------|
| Morning | 2 hrs | CS: Full Networks Revision — all 6 days in one sweep |
| Afternoon | 1.5 hrs | GS: Indian + Bihar Geography — physical features, rivers, soil |
| Evening | 1 hr | Solve all 50 MCQs (25 CS + 25 GS) |
| Night | 30 min | Write your Master Revision Checklist — tick each item |

---

---

# 🖥️ PART A — COMPUTER SCIENCE
# 🔄 FULL COMPUTER NETWORKS REVISION (Days 43–48)

---

## 🔑 NETWORKS IN BPSC TRE 4.0 — WHAT TO EXPECT

```
┌─────────────────────────────────────────────────────────────────┐
│       NETWORKS TOPIC DISTRIBUTION IN TRE PAPERS                 │
├───────────────────┬──────────┬──────────┬──────────┬────────────┤
│ Sub-topic         │ TRE 1.0  │ TRE 2.0  │ TRE 3.0  │ TRE 4.0   │
│                   │          │          │          │ Expected   │
├───────────────────┼──────────┼──────────┼──────────┼────────────┤
│ OSI/TCP-IP Model  │ 2 Q      │ 2 Q      │ 1 Q      │ 2–3 Q      │
│ IP Addressing     │ 1 Q      │ 1 Q      │ 1 Q      │ 1–2 Q      │
│ Protocols (TCP/   │ 3 Q      │ 4 Q      │ 2 Q      │ 3–4 Q      │
│ UDP/SMTP/HTTP)    │          │          │          │            │
│ Topologies/Devices│ 2 Q      │ 2 Q      │ 1 Q      │ 2 Q        │
│ Transmission Media│ 1 Q      │ 1 Q      │ 1 Q      │ 1–2 Q      │
│ Security/Crypto   │ 1 Q      │ 0 Q      │ 1 Q      │ 1–2 Q      │
├───────────────────┼──────────┼──────────┼──────────┼────────────┤
│ TOTAL Networks    │ 10 Q     │ 10 Q     │ 7 Q      │ 10–14 Q    │
└───────────────────┴──────────┴──────────┴──────────┴────────────┘
```

**Strategy:** Networks is ~10% of CS paper. Mastering these 6 days = ~10 guaranteed marks!

---

## 📋 MASTER REVISION CARD 1 — OSI MODEL (Day 43)

```
┌────────────────────────────────────────────────────────────────────┐
│                OSI MODEL — 7 LAYERS COMPLETE REFERENCE             │
├────────┬──────────────────┬──────────┬──────────────────────────── │
│ Layer# │ Layer Name       │ PDU      │ Protocols/Devices           │
├────────┼──────────────────┼──────────┼──────────────────────────── │
│   7    │ APPLICATION      │ Data     │ HTTP, FTP, SMTP, DNS, DHCP  │
│   6    │ PRESENTATION     │ Data     │ SSL/TLS, JPEG, ASCII, MPEG  │
│   5    │ SESSION          │ Data     │ NetBIOS, RPC, SAP           │
│   4    │ TRANSPORT        │ Segment  │ TCP, UDP                    │
│   3    │ NETWORK          │ Packet   │ IP, ICMP, ARP, Router       │
│   2    │ DATA LINK        │ Frame    │ Ethernet, Switch, Bridge    │
│   1    │ PHYSICAL         │ Bits     │ Hub, Repeater, Cables       │
└────────┴──────────────────┴──────────┴─────────────────────────────┘

Memory: "All People Seem To Need Data Processing" (top→bottom: 7 to 1)
Reverse: "Please Do Not Throw Sausage Pizza Away" (bottom→top: 1 to 7)
```

### KEY PYQ FACTS — OSI:
```
┌─────────────────────────────────────────────────────────────────┐
│ ✅ Physical layer PDU   = BITS                                   │
│ ✅ Transport layer PDU  = SEGMENT                                │
│ ✅ Network layer PDU    = PACKET                                 │
│ ✅ Data Link layer PDU  = FRAME                                  │
│ ✅ Data Link sublayers  = LLC (upper) + MAC (lower)              │
│ ✅ Hub = Layer 1 | Switch = Layer 2 | Router = Layer 3           │
│ ✅ OSI = CONCEPTUAL framework (NOT an actual protocol!)          │
│ ✅ OSI was created by ISO in 1984                                │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📋 MASTER REVISION CARD 2 — TCP/IP MODEL (Day 44)

```
┌─────────────────────────────────────────────────────────────┐
│         TCP/IP (4 LAYERS) vs OSI (7 LAYERS) MAPPING         │
├─────────────────────────┬───────────────────────────────────┤
│ TCP/IP Layer            │ Corresponding OSI Layers          │
├─────────────────────────┼───────────────────────────────────┤
│ Application             │ Application + Presentation +      │
│                         │ Session (Layers 7+6+5)            │
├─────────────────────────┼───────────────────────────────────┤
│ Transport               │ Transport (Layer 4)               │
│ (Host-to-Host)          │ ← "HOST-TO-HOST" is TCP/IP name  │
├─────────────────────────┼───────────────────────────────────┤
│ Internet                │ Network (Layer 3)                 │
├─────────────────────────┼───────────────────────────────────┤
│ Network Access          │ Data Link + Physical (Layers 2+1) │
│ (Link Layer)            │                                   │
└─────────────────────────┴───────────────────────────────────┘
```

### KEY PYQ FACTS — TCP/IP:
```
┌─────────────────────────────────────────────────────────────────┐
│ ✅ TCP/IP has 4 layers (OSI has 7)                               │
│ ✅ TCP/IP "Host-to-Host" = OSI Transport layer (Layer 4)         │
│ ✅ MAC sublayer performs functions depending on medium type       │
│ ✅ LLC = upper sublayer of Data Link                             │
│ ✅ Network layer responsibility = routing and forwarding packets  │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📋 MASTER REVISION CARD 3 — IP ADDRESSING (Day 45)

```
┌──────────────────────────────────────────────────────────────────┐
│                  IPv4 vs IPv6 COMPARISON                         │
├──────────────────────┬──────────────────┬───────────────────────┤
│ Feature              │ IPv4             │ IPv6                  │
├──────────────────────┼──────────────────┼───────────────────────┤
│ Address length       │ 32 bits          │ 128 bits              │
│ Format               │ Dotted decimal   │ Hexadecimal (colons)  │
│ Example              │ 192.168.1.1      │ 2001:0db8::1          │
│ Classes              │ A, B, C, D, E    │ No classes            │
│ No. of addresses     │ ~4.3 billion     │ 3.4 × 10³⁸            │
│ Security             │ Optional (IPSec) │ Built-in IPSec        │
│ Flow label           │ Not present      │ Present (CONSIDERED,  │
│                      │                  │ not discarded!)       │
└──────────────────────┴──────────────────┴───────────────────────┘
```

```
IPv4 CLASS RANGES:
┌──────────┬────────────────────┬──────────────┬────────────────┐
│ Class    │ First Octet Range  │ Default Mask │ Use            │
├──────────┼────────────────────┼──────────────┼────────────────┤
│ A        │ 1 – 126            │ /8           │ Large networks │
│ B        │ 128 – 191          │ /16          │ Medium networks│
│ C        │ 192 – 223          │ /24          │ Small networks │
│ D        │ 224 – 239          │ –            │ Multicast      │
│ E        │ 240 – 255          │ –            │ Research/Exp.  │
└──────────┴────────────────────┴──────────────┴────────────────┘

Private IP Ranges (NOT routable on Internet):
  Class A: 10.0.0.0 – 10.255.255.255
  Class B: 172.16.0.0 – 172.31.255.255
  Class C: 192.168.0.0 – 192.168.255.255
```

### KEY PYQ FACTS — IP:
```
┌─────────────────────────────────────────────────────────────────┐
│ ✅ IPv4 = 32 bits | IPv6 = 128 bits (NOT 64 or 256!)             │
│ ✅ IPv6 Flow Label is CONSIDERED in header translation           │
│ ✅ Subnet mask identifies the NETWORK portion of IP address      │
│ ✅ 127.x.x.x = Loopback address (localhost)                      │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📋 MASTER REVISION CARD 4 — PROTOCOLS (Day 46)

```
┌──────────────────────────────────────────────────────────────────┐
│              PROTOCOL MASTER REFERENCE TABLE                     │
├──────────┬──────┬────────────┬───────────────────────────────── │
│ Protocol │ Port │ Transport  │ Purpose + Key Fact               │
├──────────┼──────┼────────────┼────────────────────────────────── │
│ FTP      │20/21 │ TCP        │ File Transfer; TWO ports (unique!)│
│ SSH      │ 22   │ TCP        │ Secure remote login              │
│ Telnet   │ 23   │ TCP        │ Remote login (insecure!)         │
│ SMTP     │ 25   │ TCP        │ Send email; server→server=CLIENT │
│ DNS      │ 53   │ UDP (TCP*) │ Domain→IP; *TCP for zone transfer│
│ DHCP     │67/68 │ UDP        │ Auto IP assignment; DORA process │
│ HTTP     │ 80   │ TCP        │ Web browsing; STATELESS          │
│ POP3     │ 110  │ TCP        │ Receive email (download+delete)  │
│ IMAP     │ 143  │ TCP        │ Receive email (sync+keep)        │
│ HTTPS    │ 443  │ TCP        │ Secure web (HTTP + SSL/TLS)      │
│ MQTT     │1883  │ TCP        │ IoT protocol; Pub-Sub model      │
└──────────┴──────┴────────────┴───────────────────────────────────┘
```

### KEY PYQ FACTS — PROTOCOLS:
```
┌─────────────────────────────────────────────────────────────────┐
│ ✅ TCP = Connection-oriented + Reliable + 3-way handshake        │
│    3-way handshake: SYN → SYN-ACK → ACK                         │
│ ✅ UDP = Connectionless + Unreliable + Faster than TCP           │
│ ✅ SMTP server sending to another server = SMTP CLIENT           │
│ ✅ HTTP = STATELESS (no memory between requests), Port 80        │
│ ✅ FTP = TWO ports: 20 (data) + 21 (control)                    │
│ ✅ DNS uses UDP for queries; TCP only for zone transfers          │
│ ✅ DHCP process = DORA (Discover→Offer→Request→Acknowledge)      │
│ ✅ MQTT = IoT, Publish-Subscribe model, uses TCP                 │
│ ✅ Ping uses ICMP (NOT TCP or UDP)                               │
│ ✅ Ping = NOT "Packet Internet Groper" (common wrong option)     │
│ ✅ Ping reports: Packet loss + Round-trip delay                  │
│ ✅ Socket = IP Address + Port Number (endpoint of IPC)           │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📋 MASTER REVISION CARD 5 — TOPOLOGIES & DEVICES (Day 47)

```
┌─────────────────────────────────────────────────────────────────┐
│           NETWORK TOPOLOGY QUICK REFERENCE                      │
├────────────┬──────────────┬───────────────────────────────────── │
│ Topology   │ Key Feature  │ Critical Fact                        │
├────────────┼──────────────┼───────────────────────────────────── │
│ Bus        │ Single cable │ Backbone breaks → ALL devices fail   │
│            │ backbone     │ Needs TERMINATORS at both ends        │
│            │              │ CHEAPEST topology                     │
├────────────┼──────────────┼───────────────────────────────────── │
│ Star       │ Central hub  │ Central hub/switch is MANDATORY       │
│            │ or switch    │ Hub fails → ALL fail                  │
│            │              │ MOST POPULAR modern LAN topology      │
├────────────┼──────────────┼───────────────────────────────────── │
│ Ring       │ Circular     │ Data flows UNIDIRECTIONALLY           │
│            │ connection   │ Token Ring = token passing            │
├────────────┼──────────────┼───────────────────────────────────── │
│ Mesh       │ Every-to-    │ Links = n(n-1)/2                     │
│            │ every        │ MOST RELIABLE, MOST EXPENSIVE         │
├────────────┼──────────────┼───────────────────────────────────── │
│ Tree       │ Hierarchical │ Root failure = entire network down    │
│ (Hybrid)   │ (star of     │ Good scalability                      │
│            │ stars)       │                                       │
└────────────┴──────────────┴───────────────────────────────────── │

🚨 PEER-TO-PEER = NOT A TOPOLOGY — it is a NETWORK MODEL!
```

```
┌─────────────────────────────────────────────────────────────────┐
│         NETWORK DEVICES QUICK REFERENCE                         │
├──────────────┬──────────┬──────────────────────────────────── │
│ Device       │ OSI Layer│ Key Function                         │
├──────────────┼──────────┼──────────────────────────────────── │
│ Hub          │ Layer 1  │ Broadcasts to ALL ports (dumb)       │
│ Repeater     │ Layer 1  │ Amplifies/regenerates signal         │
│ Modem        │ Layer 1  │ Digital ↔ Analog conversion         │
│ Bridge       │ Layer 2  │ Connects two similar LANs by MAC     │
│ Switch       │ Layer 2  │ Forwards to SPECIFIC device by MAC   │
│ Router       │ Layer 3  │ Routes between NETWORKS using IP     │
│ Gateway      │ All      │ Protocol conversion between networks │
└──────────────┴──────────┴──────────────────────────────────── │

🚨 WWW ≠ Internet
  Internet = global physical network infrastructure
  WWW = collection of hyperlinked documents ON the Internet
  WWW created by Tim Berners-Lee in 1989 at CERN
```

---

## 📋 MASTER REVISION CARD 6 — TRANSMISSION MEDIA & SECURITY (Day 48)

```
┌─────────────────────────────────────────────────────────────────┐
│         TRANSMISSION MEDIA QUICK REFERENCE                      │
├──────────────┬──────────┬──────────────┬────────────────────── │
│ Media Type   │ Speed    │ EM Immunity  │ Key Fact              │
├──────────────┼──────────┼──────────────┼──────────────────────  │
│ UTP          │ Moderate │ VULNERABLE   │ Cheapest; most common │
│ STP          │ Moderate │ Good         │ Metal braid shielding │
│ Coaxial      │ Good     │ Good         │ Cable TV; 2 conductors│
│ Optical Fiber│ HIGHEST  │ IMMUNE(100%) │ Uses light; no copper │
└──────────────┴──────────┴──────────────┴──────────────────────  │

🚨 Optical Fiber = HIGHEST SPEED + IMMUNE to EM Interference
   These are the 2 MUST-KNOW facts about Optical Fiber!
```

```
┌─────────────────────────────────────────────────────────────────┐
│              CRYPTOGRAPHY QUICK REFERENCE                       │
├───────────────────────┬─────────────────┬─────────────────────  │
│ Feature               │ Symmetric       │ Asymmetric            │
├───────────────────────┼─────────────────┼─────────────────────  │
│ Keys used             │ SAME key        │ Two different keys     │
│ Speed                 │ FASTER          │ SLOWER                 │
│ Private key owner     │ Both parties    │ RECEIVER keeps it      │
│ Public key            │ N/A             │ Shared openly          │
│ Examples              │ AES, DES, RC4   │ RSA, DSA, ECC          │
└───────────────────────┴─────────────────┴─────────────────────  │

🚨 #1 TRAP: Private key in asymmetric crypto = kept by RECEIVER
🚨 #2 TRAP: Sniffers prevented by SWITCHED network (not hub!)
🚨 #3 TRAP: Full access rights to all users = integrity BREACH
```

---

## ⚡ COMPLETE NETWORKS PYQ TRAP CARD

```
┌──────────────────────────────────────────────────────────────────┐
│ ❌ WRONG (Commonly Set as Trap)   │ ✅ CORRECT Answer             │
├──────────────────────────────────────────────────────────────────┤
│ IPv6 = 64 bits                    │ IPv6 = 128 bits               │
│ IPv6 flow label is discarded      │ Flow label is CONSIDERED       │
│ TCP/IP Host-to-Host = OSI Network │ Host-to-Host = OSI TRANSPORT   │
│ Ping = "Packet Internet Groper"   │ Ping has NO such expansion      │
│ SMTP server sending = SMTP Server │ Sending server = SMTP CLIENT    │
│ DNS uses TCP for all queries      │ DNS uses UDP for queries        │
│ FTP uses single port (21)         │ FTP uses TWO ports (20+21)     │
│ HTTP is stateful                  │ HTTP is STATELESS               │
│ HTTPS uses port 80                │ HTTPS uses port 443             │
│ MQTT uses UDP                     │ MQTT uses TCP                   │
│ Peer-to-Peer = network topology   │ P2P = network MODEL, not topo  │
│ Hub = Layer 2 device              │ Hub = Layer 1 (Physical)        │
│ Router connects devices in LAN    │ Switch connects LAN devices     │
│ Bridge connects different networks│ Bridge connects SIMILAR LANs   │
│ UTP is immune to EM interference  │ UTP is VULNERABLE to EM        │
│ Optical fiber has no EM immunity  │ Optical fiber is FULLY immune  │
│ Private key in asymmetric = sender│ Private key = RECEIVER          │
│ Sniffer prevented by hub network  │ Sniffer prevented by SWITCH    │
│ Full access rights = good practice│ Full access rights = BREACH    │
│ Circular queue = random access    │ Circular queue = Ring buffer    │
│ WWW = same as Internet            │ WWW ≠ Internet (service on it) │
└──────────────────────────────────────────────────────────────────┘
```

---

## 📊 NETWORKS MASTER SUMMARY — ONE PAGE REVISION

```
┌─────────────────────────────────────────────────────────────────┐
│                  COMPUTER NETWORKS AT A GLANCE                   │
│                      (Days 43–48 Summary)                        │
├──────────────────────────────────────────────────────────────────┤
│ 1. OSI = 7 layers | TCP/IP = 4 layers                           │
│ 2. Physical=Bits, DataLink=Frames, Network=Packets, Tport=Segments│
│ 3. Hub=L1, Switch=L2, Router=L3, Gateway=All Layers             │
│ 4. IPv4=32bits | IPv6=128bits | IPv6 Flow Label = CONSIDERED     │
│ 5. TCP=Connection-oriented, Reliable | UDP=Connectionless, Fast  │
│ 6. 3-way handshake = SYN → SYN-ACK → ACK                        │
│ 7. SMTP sending server → it is SMTP CLIENT                       │
│ 8. FTP = TWO ports (20+21) | DNS = UDP (TCP for zone transfers)  │
│ 9. MQTT = IoT, Publish-Subscribe | Ping = ICMP, NOT TCP          │
│ 10. DHCP = DORA process | Socket = IP + Port                     │
│ 11. Bus cheap; Star popular; Mesh most reliable; P2P NOT topology│
│ 12. n(n-1)/2 = number of links in full mesh                      │
│ 13. Optical Fiber = HIGHEST speed + IMMUNE to EM interference    │
│ 14. UTP = VULNERABLE to EM | STP has shielding                   │
│ 15. Asymmetric crypto: PRIVATE KEY = kept by RECEIVER             │
│ 16. Symmetric crypto = SAME KEY for both encryption/decryption   │
│ 17. Sniffer prevention = use SWITCHED network                     │
│ 18. System integrity breach = Full access rights to all users    │
│ 19. SSL/TLS = HTTPS encryption | CIA Triad = Conf+Int+Avail       │
│ 20. WWW ≠ Internet | Tim Berners-Lee created WWW in 1989         │
└──────────────────────────────────────────────────────────────────┘
```

---

---

# 📚 PART B — GENERAL STUDIES (GS)
# 🌍 INDIAN GEOGRAPHY — PHYSICAL FEATURES, RIVERS, CLIMATE & SOIL

---

## 🔑 WHY THIS TOPIC MATTERS FOR BPSC TRE 4.0

Geography consistently accounts for **6–8 marks** in the GS section of BPSC TRE.
Key areas tested:
- Physical divisions of India (Himalayas, Plains, Plateau, Coastal, Islands)
- Major rivers — their tributaries, origins, and states
- Climate and rainfall (highest/lowest rainfall areas)
- Soil types and their crop associations
- Bihar's specific geographical position and rivers

---

## 🏔️ SECTION 1: PHYSICAL DIVISIONS OF INDIA

India is divided into **6 major physical divisions**:

```
┌──────────────────────────────────────────────────────────────────┐
│            PHYSICAL MAP OF INDIA — DIVISIONS                     │
│                                                                  │
│  ╔══════════════════════╗                                        │
│  ║  THE HIMALAYAS       ║ ← North — young fold mountains        │
│  ╚══════════════════════╝                                        │
│           ↓                                                      │
│  ╔══════════════════════╗                                        │
│  ║  NORTHERN PLAINS     ║ ← Indus-Ganga-Brahmaputra basin       │
│  ║  (Great Plains)      ║   Bihar is here!                      │
│  ╚══════════════════════╝                                        │
│           ↓                                                      │
│  ╔════════════╗  ╔══════╗                                        │
│  ║  PENINSULAR║  ║THAR  ║ ← Plateau (Deccan) + Desert (Rajasthan│
│  ║  PLATEAU   ║  ║DESERT║                                        │
│  ╚════════════╝  ╚══════╝                                        │
│     ↙         ↘                                                  │
│ ╔════════╗ ╔════════╗                                            │
│ ║WESTERN ║ ║EASTERN ║ ← Coastal Plains (both sides)             │
│ ║COASTAL ║ ║COASTAL ║                                            │
│ ╚════════╝ ╚════════╝                                            │
│                                                                  │
│  + ISLANDS: Andaman & Nicobar (Bay of Bengal)                   │
│           + Lakshadweep (Arabian Sea)                            │
└──────────────────────────────────────────────────────────────────┘
```

---

### 1.1 THE HIMALAYAS

```
┌──────────────────────────────────────────────────────────────────┐
│              HIMALAYAN RANGES (North to South)                   │
├─────────────────────────────────────────────────────────────────┤
│ INNER HIMALAYAS   │ Himadri           │ Highest peaks; Mt Everest│
│ (Greater)         │                   │ K2, Kangchenjunga        │
├─────────────────────────────────────────────────────────────────┤
│ MIDDLE HIMALAYAS  │ Himachal          │ Hill stations: Shimla,   │
│ (Lesser)          │                   │ Mussoorie, Nainital      │
├─────────────────────────────────────────────────────────────────┤
│ OUTER HIMALAYAS   │ Shiwaliks         │ Youngest; most recent;   │
│ (Sub-Himalaya)    │ (Foothills)       │ Terai region below       │
└─────────────────────────────────────────────────────────────────┘
```

**Important Himalayan Peaks:**
```
┌─────────────────────────────────────────────────────────────┐
│ Mt. Everest      │ 8,849 m  │ Nepal-China border            │
│                  │          │ Highest peak in world         │
│ K2 (Godwin-      │ 8,611 m  │ Pakistan-China border         │
│ Austen)          │          │ 2nd highest; in India's POK   │
│ Kangchenjunga    │ 8,586 m  │ India (Sikkim)-Nepal          │
│                  │          │ 3rd highest; HIGHEST IN INDIA │
│ Nanda Devi       │ 7,816 m  │ Uttarakhand, India            │
│                  │          │ Highest entirely within India │
└─────────────────────────────────────────────────────────────┘
```

**🚨 EXAM TRAP:** K2 is taller than Kangchenjunga but K2 is on the Pakistan-China border (in PoK). **Kangchenjunga** is the highest peak located within India's territory.

---

### 1.2 NORTHERN PLAINS (GREAT PLAINS)

```
┌─────────────────────────────────────────────────────────────────┐
│              NORTHERN PLAINS — KEY FACTS                        │
├─────────────────────────────────────────────────────────────────┤
│ Formation     │ Alluvial deposits of Indus, Ganga,              │
│               │ Brahmaputra rivers over millions of years       │
│ Length        │ ~2400 km (E-W) | Width: ~240–320 km             │
│ Area          │ ~7 lakh sq km                                    │
│ Soil          │ Alluvial (most fertile soil in India)           │
│ Bihar         │ ENTIRELY in the Northern Plains                 │
│ Importance    │ Most densely populated region of India          │
│               │ "Granary of India" (wheat + rice production)    │
├─────────────────────────────────────────────────────────────────┤
│ Sub-divisions │ Punjab Plains | Haryana Plains |                │
│               │ Ganga Plains (UP, Bihar) |                      │
│               │ Brahmaputra Plains (Assam)                      │
├─────────────────────────────────────────────────────────────────┤
│ Two alluvial  │ Khadar = new alluvial (near rivers; fertile)    │
│ types         │ Bhangar = old alluvial (elevated; less fertile) │
└─────────────────────────────────────────────────────────────────┘
```

---

### 1.3 PENINSULAR PLATEAU (DECCAN PLATEAU)

```
┌─────────────────────────────────────────────────────────────────┐
│ Oldest landmass in India; made of very old crystalline rocks    │
│ Average height: 600–900 metres above sea level                  │
│ Bounded by: Vindhya Range (N), Western Ghats (W),               │
│             Eastern Ghats (E)                                   │
├─────────────────────────────────────────────────────────────────┤
│ Western Ghats │ Higher (900–2000m); continuous range            │
│               │ Highest peak: Anamudi (2695m) — Kerala          │
│               │ Creates rain-shadow on eastern side             │
│               │ Called "Sahyadri"                               │
├─────────────────────────────────────────────────────────────────┤
│ Eastern Ghats │ Lower, discontinuous (broken by rivers)         │
│               │ Highest peak: Jindhagada (1690m)                │
│               │ Less rainfall (rain shadow of W. Ghats)         │
└─────────────────────────────────────────────────────────────────┘
```

**🚨 EXAM TRAP:** Western Ghats are **higher** than Eastern Ghats. Anamudi (Kerala) = highest peak in South India.

---

## 🏞️ SECTION 2: MAJOR RIVERS OF INDIA

### Rivers FLOW DIRECTION:
```
HIMALAYAN RIVERS → Flow from North to South/Southeast → perennial
PENINSULAR RIVERS → Flow from West to East (into Bay of Bengal) mostly

EXCEPTION: Narmada and Tapi → Flow West (into Arabian Sea) — important!
```

### 2.1 HIMALAYAN RIVER SYSTEMS

```
┌──────────────────────────────────────────────────────────────────┐
│                   GANGA RIVER SYSTEM                             │
├─────────────────────────────────────────────────────────────────┤
│ Origin        │ Gangotri Glacier, Uttarakhand (Gaumukh)         │
│ Total length  │ ~2,525 km (India's longest river within India)  │
│ Holy points   │ Haridwar, Allahabad (Prayagraj), Varanasi       │
│ Tributaries   │ Right bank: Yamuna, Son, Damodar, Rupnarayan    │
│               │ Left bank: Ramganga, Gomti, Ghaghara,           │
│               │           Gandak, Kosi                          │
│ Delta         │ Sundarbans (world's largest delta, shared with  │
│               │ Bangladesh)                                     │
│ Bihar rivers  │ Ganga flows through ENTIRE Bihar from W to E    │
└─────────────────────────────────────────────────────────────────┘
```

**Rivers of Bihar — Important Details:**

```
┌──────────────────────────────────────────────────────────────────┐
│ River        │ Origin               │ Significance in Bihar      │
├──────────────┼──────────────────────┼────────────────────────────┤
│ Ganga        │ Gangotri Glacier      │ Main river; flows W to E  │
│ Son          │ Amarkantak (MP)       │ Meets Ganga near Patna    │
│              │                      │ (Right bank tributary)    │
│ Gandak       │ Nepal Himalayas       │ Enters W. Champaran;      │
│ (Narayani)   │                      │ Left bank tributary       │
│ Kosi         │ Nepal (Tibetan        │ Called "Sorrow of Bihar"  │
│              │ plateau)              │ due to frequent floods    │
│ Ghaghara     │ Tibet (via Nepal)     │ Left bank; joins Ganga    │
│ Bagmati      │ Kathmandu Valley      │ Floods Sitamarhi/Darbhanga│
│              │ Nepal                 │                           │
│ Punpun       │ Chhota Nagpur Plateau │ Meets Ganga south of      │
│              │                      │ Patna                     │
└──────────────────────────────────────────────────────────────────┘
```

**🚨 EXAM FACT:** **Kosi River** = "Sorrow of Bihar" (शोक की नदी) — due to changing course & devastating floods every year. This fact is tested in every Bihar exam!

---

### 2.2 PENINSULAR RIVERS

```
┌──────────────────────────────────────────────────────────────────┐
│ River        │ Origin        │ Flows to        │ Key Fact        │
├──────────────┼───────────────┼─────────────────┼─────────────────┤
│ Godavari     │ Nashik, Mah.  │ Bay of Bengal   │ Longest Penin.  │
│              │               │                 │ river; "Dakshin │
│              │               │                 │ Ganga"          │
│ Krishna      │ Mah. plateau  │ Bay of Bengal   │ 2nd longest     │
│              │               │                 │ peninsular      │
│ Kaveri       │ Coorg (Kar.)  │ Bay of Bengal   │ "Dakshin Ganga" │
│              │               │                 │ of South India  │
│ Mahanadi     │ Chhattisgarh  │ Bay of Bengal   │ Odisha river;   │
│              │               │                 │ Hirakud dam     │
│ Narmada      │ Amarkantak    │ ARABIAN SEA      │ Flows WESTWARD! │
│              │ (MP)          │                 │ (exceptional)   │
│ Tapi (Tapti) │ Betul, MP     │ ARABIAN SEA      │ Also flows West!│
└──────────────┴───────────────┴─────────────────┴─────────────────┘
```

**🚨 KEY FACT:** Narmada and Tapi are the ONLY major peninsular rivers that flow **WESTWARD** into the Arabian Sea. All others flow east into Bay of Bengal!

---

## 🌦️ SECTION 3: CLIMATE OF INDIA

### India's Climate = Tropical Monsoon Climate

```
┌──────────────────────────────────────────────────────────────────┐
│             INDIA'S 4 SEASONS                                    │
├──────────────────┬───────────────┬──────────────────────────────┤
│ Season           │ Months        │ Key Characteristics          │
├──────────────────┼───────────────┼──────────────────────────────┤
│ WINTER           │ Dec – Feb     │ NE winds; cold in North India│
│ (Cold Weather)   │               │ SW India is warm             │
├──────────────────┼───────────────┼──────────────────────────────┤
│ PRE-MONSOON      │ Mar – May     │ Hot, dry; dust storms (Loo)  │
│ (Hot Weather)    │               │ Highest temp: May-June       │
├──────────────────┼───────────────┼──────────────────────────────┤
│ SOUTHWEST        │ Jun – Sep     │ Main rainy season; comes from│
│ MONSOON          │               │ SW direction; causes 70-90%  │
│                  │               │ of India's annual rainfall   │
├──────────────────┼───────────────┼──────────────────────────────┤
│ RETREATING       │ Oct – Nov     │ Monsoon withdraws; NE India  │
│ MONSOON          │               │ gets rain; Tamil Nadu gets   │
│                  │               │ NE monsoon rains             │
└──────────────────┴───────────────┴──────────────────────────────┘
```

### RAINFALL DISTRIBUTION:
```
┌─────────────────────────────────────────────────────────────────┐
│ HIGHEST RAINFALL IN INDIA:                                      │
│   Mawsynram (Meghalaya) = Highest rainfall in world             │
│   (~11,872 mm/year) — near Cherrapunji                          │
│   Cherrapunji = earlier record holder (still very high)         │
│                                                                 │
│ LOWEST RAINFALL IN INDIA:                                       │
│   Leh (Ladakh) = Driest place in India (< 100 mm/year)         │
│   Jaisalmer (Rajasthan) also very low rainfall                  │
│                                                                 │
│ BIHAR RAINFALL:                                                 │
│   Average annual rainfall: 1000–1200 mm                        │
│   North Bihar gets more rainfall than South Bihar              │
│   Receives SW Monsoon (June-September)                         │
└─────────────────────────────────────────────────────────────────┘
```

**🚨 EXAM TRAP:** Mawsynram ≠ Cherrapunji. **Mawsynram** is the current record holder for highest rainfall. Cherrapunji is nearby but second.

---

## 🌱 SECTION 4: SOIL TYPES OF INDIA

```
┌──────────────────────────────────────────────────────────────────┐
│                    SOIL TYPES OF INDIA                           │
├─────────────────┬─────────────────────┬───────────────────────── │
│ Soil Type       │ Region / States     │ Crops Grown              │
├─────────────────┼─────────────────────┼──────────────────────────┤
│ ALLUVIAL SOIL   │ Northern Plains     │ Wheat, Rice, Sugarcane,  │
│ (most fertile)  │ (UP, Bihar, Punjab, │ Maize, Jute              │
│                 │ West Bengal, Assam) │                          │
├─────────────────┼─────────────────────┼──────────────────────────┤
│ BLACK SOIL      │ Maharashtra, MP,    │ COTTON (mainly)          │
│ (Regur Soil)    │ Gujarat, AP         │ Also: Wheat, Sorghum     │
│                 │ (Deccan Plateau)    │ "Cotton Soil" or         │
│                 │                     │ "Regur Soil"             │
├─────────────────┼─────────────────────┼──────────────────────────┤
│ RED SOIL        │ Eastern Deccan,     │ Groundnut, Millet,       │
│                 │ Odisha, parts of    │ Wheat, Cotton            │
│                 │ TN, Karnataka       │ (less fertile than       │
│                 │                     │ alluvial/black)          │
├─────────────────┼─────────────────────┼──────────────────────────┤
│ LATERITE SOIL   │ Western Ghats,      │ Tea, Coffee, Cashew,     │
│                 │ Eastern Ghats,      │ Rubber (plantation)      │
│                 │ NE India, Kerala    │ Low fertility; leached   │
├─────────────────┼─────────────────────┼──────────────────────────┤
│ DESERT SOIL     │ Rajasthan, Gujarat  │ Bajra, Guar, Dates       │
│ (Arid soil)     │ (Thar Desert)       │ Low humus, high sand     │
├─────────────────┼─────────────────────┼──────────────────────────┤
│ MOUNTAIN SOIL   │ Himalayas, NE India │ Tea, Temperate fruits    │
│ (Forest soil)   │                     │ Low-temp crops           │
└─────────────────┴─────────────────────┴──────────────────────────┘
```

**🚨 KEY EXAM ASSOCIATIONS:**
- Black soil = Cotton → "Regur" or "Black Cotton Soil"
- Laterite soil = Tea, Coffee, Rubber (plantation crops)
- Alluvial soil = Bihar's soil = Wheat + Rice + Sugarcane
- Red soil = low fertility compared to alluvial

---

## 🌍 SECTION 5: WORLD GEOGRAPHY SUPERLATIVES

```
┌──────────────────────────────────────────────────────────────────┐
│                WORLD GEOGRAPHY — EXAM FACTS                      │
├─────────────────────────────────────────────────────────────────┤
│ Largest continent         │ Asia                                │
│ Smallest continent        │ Australia                           │
│ Largest country by area   │ Russia                              │
│ Largest country by pop.   │ India (surpassed China 2023)        │
│ Largest ocean             │ Pacific Ocean                       │
│ Deepest ocean trench      │ Mariana Trench (Pacific)            │
│ Longest river             │ Nile (Africa) — traditionally       │
│                           │ Amazon also disputed                │
│ Highest mountain          │ Mt. Everest (8,849 m)               │
│ Largest desert            │ Sahara (hot) | Antarctic (cold)     │
│ Largest island            │ Greenland                           │
│ Largest freshwater lake   │ Lake Superior (North America)       │
│ Deepest lake              │ Lake Baikal (Russia)                │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🏔️ SECTION 6: BIHAR — GEOGRAPHIC POSITION

```
┌──────────────────────────────────────────────────────────────────┐
│              BIHAR — GEOGRAPHIC KEY FACTS                        │
├─────────────────────────────────────────────────────────────────┤
│ Location          │ 24°20' – 27°31' N latitude                  │
│                   │ 83°19' – 88°17' E longitude                 │
│ Area              │ 94,163 sq km (13th largest state)           │
│ Borders           │ N: Nepal | E: West Bengal                   │
│                   │ S: Jharkhand | W: Uttar Pradesh             │
│ Physical region   │ Entirely in Gangetic Plain                  │
│ Capital           │ Patna (on Ganga's south bank)               │
│ Districts         │ 38 districts                                │
│ Highest point     │ Someshwar Hills (West Champaran)            │
│ Main rivers       │ Ganga, Son, Gandak, Kosi, Ghaghara, Bagmati│
│ Soil type         │ Alluvial soil (Khadar + Bhangar)            │
│ Climate           │ Subtropical; Monsoon type                   │
│ Forest cover      │ ~7% of area (very low)                      │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🚨 BPSC TOPPER TRAP CARD — GS GEOGRAPHY

| Wrong Statement | Correct Answer |
|----------------|----------------|
| Cherrapunji = highest rainfall in world | ❌ WRONG — Mawsynram (both in Meghalaya) |
| K2 is the highest peak in India | ❌ WRONG — Kangchenjunga is highest IN India |
| Narmada flows into Bay of Bengal | ❌ WRONG — Narmada flows into Arabian Sea |
| Kosi = "Life-giving river of Bihar" | ❌ WRONG — Kosi = "Sorrow of Bihar" |
| Eastern Ghats are higher than Western | ❌ WRONG — Western Ghats are HIGHER |
| Anamudi is in Tamil Nadu | ❌ WRONG — Anamudi (2695m) is in Kerala |
| Godavari flows west into Arabian Sea | ❌ WRONG — Godavari flows east into Bay of Bengal |
| Bihar is bordered by Maharashtra | ❌ WRONG — Bihar borders Nepal, WB, Jharkhand, UP |
| Black soil = best for Rice | ❌ WRONG — Black soil is best for COTTON |
| Laterite soil = most fertile | ❌ WRONG — Alluvial soil is most fertile |

---

## ✅ GS CONCEPT SUMMARY — DAY 49

| # | Topic | Key Fact |
|---|-------|---------|
| 1 | Himalayas | 3 ranges: Greater→Lesser→Shiwaliks (N to S) |
| 2 | Kangchenjunga | Highest peak IN India (K2 is in PoK) |
| 3 | Kosi River | "Sorrow of Bihar" — floods Bihar every year |
| 4 | Northern Plains | Bihar entirely in Gangetic Plains; Alluvial soil |
| 5 | Narmada & Tapi | Flow WESTWARD (exception among peninsular rivers) |
| 6 | Highest rainfall | Mawsynram, Meghalaya (not Cherrapunji) |
| 7 | Black soil | Best for Cotton; Regur soil; Deccan Plateau |
| 8 | Alluvial soil | Most fertile; Bihar's main soil |
| 9 | Laterite soil | Tea, Coffee, Rubber; low fertility |
| 10 | Sundarbans | World's largest delta; Ganga+Brahmaputra |

---

---

# 📝 PRACTICE QUESTIONS

> ⚠️ **CRITICAL INSTRUCTION:** Attempt ALL 50 questions FIRST.
> Answers are at the VERY END — do NOT look ahead!
> This is a FULL REVISION session — these questions cover ALL networks topics from Days 43–48.
> BPSC Five-Option Format: (A), (B), (C), (D) More than one of the above, (E) None of the above

---

## 🖥️ CS PRACTICE QUESTIONS (Q1–Q25)
### Full Revision: Computer Networks (Days 43–48)

---

**Q1.** The OSI model was developed by the International Organization for Standardization (ISO) and has how many layers?

(A) 4 layers  
(B) 5 layers  
(C) 7 layers  
(D) More than one of the above  
(E) None of the above  

---

**Q2.** Which layer of the OSI model is responsible for converting data into bits for physical transmission?

(A) Data Link Layer  
(B) Network Layer  
(C) Physical Layer  
(D) More than one of the above  
(E) None of the above  

---

**Q3.** In the TCP/IP model, the "Host-to-Host" layer corresponds to which layer in the OSI model?

(A) Session Layer  
(B) Network Layer  
(C) Transport Layer  
(D) More than one of the above  
(E) None of the above  

---

**Q4.** IPv6 address length is:

(A) 32 bits  
(B) 64 bits  
(C) 128 bits  
(D) More than one of the above  
(E) None of the above  

---

**Q5.** During IPv6 to IPv4 header translation, the flow label of IPv6 is:

(A) Discarded as it has no equivalent in IPv4  
(B) Converted to a random value  
(C) Considered during translation  
(D) More than one of the above  
(E) None of the above  

---

**Q6.** The THREE-WAY HANDSHAKE in TCP follows which sequence?

(A) ACK → SYN → SYN-ACK  
(B) SYN → ACK → SYN-ACK  
(C) SYN → SYN-ACK → ACK  
(D) More than one of the above  
(E) None of the above  

---

**Q7.** When a mail server sends an email to another mail server, what role does the sending server play?

(A) SMTP Server  
(B) IMAP Client  
(C) SMTP Client  
(D) More than one of the above  
(E) None of the above  

---

**Q8.** Which of the following statements about HTTP is CORRECT?

(A) HTTP is a stateful protocol that remembers past requests  
(B) HTTP uses port 443 by default  
(C) HTTP is a stateless application layer protocol using port 80  
(D) More than one of the above  
(E) None of the above  

---

**Q9.** FTP (File Transfer Protocol) uses which port numbers?

(A) Only port 21 for all operations  
(B) Port 80 and port 443  
(C) Port 20 (data) and Port 21 (control/commands)  
(D) More than one of the above  
(E) None of the above  

---

**Q10.** The Ping utility uses which protocol?

(A) TCP  
(B) UDP  
(C) ICMP  
(D) More than one of the above  
(E) None of the above  

---

**Q11.** MQTT protocol is designed for which type of network communication?

(A) Email communication between servers  
(B) Secure web browsing  
(C) IoT (Internet of Things) device communication using Publish-Subscribe model  
(D) More than one of the above  
(E) None of the above  

---

**Q12.** "Peer-to-Peer" in the context of computer networks is:

(A) A network topology like Bus or Star  
(B) A type of routing protocol  
(C) A network model/type (NOT a topology)  
(D) More than one of the above  
(E) None of the above  

---

**Q13.** In a FULL MESH topology with 6 computers, how many links (connections) are needed?

(A) 6 links  
(B) 12 links  
(C) 15 links  
(D) More than one of the above  
(E) None of the above  

---

**Q14.** Which device operates at the DATA LINK LAYER (Layer 2) and forwards data only to the specific destination device based on MAC address?

(A) Hub  
(B) Router  
(C) Switch  
(D) More than one of the above  
(E) None of the above  

---

**Q15.** The World Wide Web (WWW) is CORRECTLY defined as:

(A) The global physical network of computers (same as Internet)  
(B) A collection of hyperlinked documents accessible over the Internet via web browsers  
(C) An email communication system  
(D) More than one of the above  
(E) None of the above  

---

**Q16.** Which transmission medium is completely immune to electromagnetic interference and offers the highest data transmission speed?

(A) Coaxial Cable  
(B) STP (Shielded Twisted Pair)  
(C) Optical Fiber  
(D) More than one of the above  
(E) None of the above  

---

**Q17.** UTP (Unshielded Twisted Pair) cable's main weakness is its vulnerability to:

(A) Water damage  
(B) Electromagnetic and electrical interference  
(C) Optical signal degradation  
(D) More than one of the above  
(E) None of the above  

---

**Q18.** Packet sniffing (eavesdropping on network traffic) is best PREVENTED by:

(A) Using a faster hub with higher bandwidth  
(B) Using a hub-based network architecture  
(C) Using a switched network architecture  
(D) More than one of the above  
(E) None of the above  

---

**Q19.** In ASYMMETRIC KEY CRYPTOGRAPHY, the PRIVATE KEY is kept by:

(A) The sender (encryptor)  
(B) A trusted Certificate Authority  
(C) The receiver (decryptor)  
(D) More than one of the above  
(E) None of the above  

---

**Q20.** Which of the following is an example of a SYSTEM INTEGRITY BREACH?

(A) Using HTTPS for secure web communication  
(B) Encrypting data before transmission  
(C) Providing full access rights to ALL users on a shared network  
(D) More than one of the above  
(E) None of the above  

---

**Q21.** The LLC (Logical Link Control) sublayer is part of which OSI layer?

(A) Physical Layer  
(B) Network Layer  
(C) Data Link Layer  
(D) More than one of the above  
(E) None of the above  

---

**Q22.** DNS primarily uses which protocol for standard (non-zone-transfer) queries?

(A) TCP  
(B) UDP  
(C) SMTP  
(D) More than one of the above  
(E) None of the above  

---

**Q23.** The DHCP process follows the DORA sequence. What does DORA stand for?

(A) Data, Open, Relay, Acknowledge  
(B) Discover, Offer, Request, Acknowledge  
(C) Direct, Obtain, Route, Assign  
(D) More than one of the above  
(E) None of the above  

---

**Q24.** Consider these statements about Bus topology:
1. A single backbone cable connects all devices.
2. If the backbone cable fails, only the nearest device fails.
3. Terminators are required at both ends of the backbone.
4. Bus topology is the cheapest to install.

Which statements are CORRECT?

(A) Only 1 and 2  
(B) Only 1, 3, and 4  
(C) 1, 2, 3, and 4 — all correct  
(D) More than one of the above (1, 3, 4 correct; 2 is wrong)  
(E) None of the above  

---

**Q25.** Consider the following protocol-to-port mappings:
1. SMTP → Port 25 ✓
2. HTTP → Port 80 ✓
3. HTTPS → Port 80 ✗ (correct: 443)
4. SSH → Port 22 ✓

Which mappings are CORRECTLY stated?

(A) Only 1 and 2  
(B) Only 1, 2, and 4  
(C) All four  
(D) More than one of the above (1, 2, 4 are correct)  
(E) None of the above  

---

---

## 📚 GS PRACTICE QUESTIONS (Q26–Q50)
### Topic: Indian Geography — Physical Features, Rivers, Climate & Soil

---

**Q26.** India is divided into how many major physical divisions?

(A) 4  
(B) 5  
(C) 6  
(D) More than one of the above  
(E) None of the above  

---

**Q27.** The highest peak entirely within the political territory of India is:

(A) K2 (8,611 m)  
(B) Mt. Everest (8,849 m)  
(C) Kangchenjunga (8,586 m)  
(D) More than one of the above  
(E) None of the above  

---

**Q28.** The Himalayas are classified as which type of mountains?

(A) Block mountains  
(B) Volcanic mountains  
(C) Young fold mountains  
(D) More than one of the above  
(E) None of the above  

---

**Q29.** The Northern Plains of India were formed by the alluvial deposits of which river systems?

(A) Godavari, Krishna, and Kaveri rivers  
(B) Indus, Ganga, and Brahmaputra river systems  
(C) Narmada, Tapi, and Mahanadi rivers  
(D) More than one of the above  
(E) None of the above  

---

**Q30.** Bihar is entirely located in which physical division of India?

(A) Peninsular Plateau  
(B) Coastal Plains  
(C) Northern (Gangetic) Plains  
(D) More than one of the above  
(E) None of the above  

---

**Q31.** The Kosi River is nicknamed "Sorrow of Bihar" because:

(A) It dries up completely in summer causing drought  
(B) It frequently changes its course and causes devastating floods in Bihar  
(C) It flows through the poorest districts of Bihar  
(D) More than one of the above  
(E) None of the above  

---

**Q32.** The Son River joins the Ganga near Patna and is which type of tributary?

(A) Left bank tributary  
(B) Right bank tributary  
(C) Distributary (not a tributary)  
(D) More than one of the above  
(E) None of the above  

---

**Q33.** Which major peninsular rivers flow WESTWARD into the Arabian Sea (unlike most peninsular rivers)?

(A) Godavari and Krishna  
(B) Mahanadi and Kaveri  
(C) Narmada and Tapi (Tapti)  
(D) More than one of the above  
(E) None of the above  

---

**Q34.** The Godavari River is also known as:

(A) "Dakshin Ganga" (Ganga of the South)  
(B) "Sorrow of Andhra Pradesh"  
(C) "Sacred river of Kerala"  
(D) More than one of the above  
(E) None of the above  

---

**Q35.** Which place in India receives the HIGHEST annual rainfall in the world?

(A) Cherrapunji, Meghalaya  
(B) Mawsynram, Meghalaya  
(C) Shillong, Meghalaya  
(D) More than one of the above  
(E) None of the above  

---

**Q36.** The DRIEST place in India with the lowest rainfall is:

(A) Jaisalmer, Rajasthan  
(B) Bikaner, Rajasthan  
(C) Leh, Ladakh  
(D) More than one of the above  
(E) None of the above  

---

**Q37.** Which soil type in India is best suited for Cotton cultivation and is found mainly on the Deccan Plateau?

(A) Red soil  
(B) Alluvial soil  
(C) Black soil (Regur soil)  
(D) More than one of the above  
(E) None of the above  

---

**Q38.** Alluvial soil is found predominantly in:

(A) Deccan Plateau of Maharashtra and Gujarat  
(B) Himalayan mountain slopes  
(C) Northern Plains (Ganga-Indus-Brahmaputra plains)  
(D) More than one of the above  
(E) None of the above  

---

**Q39.** Laterite soil in India is best suited for which crops?

(A) Wheat and rice  
(B) Tea, Coffee, Rubber, and Cashew  
(C) Cotton and Sugarcane  
(D) More than one of the above  
(E) None of the above  

---

**Q40.** The Sundarbans delta (world's largest delta) is formed by which river system?

(A) Indus and its tributaries  
(B) Narmada and Tapi  
(C) Ganga and Brahmaputra  
(D) More than one of the above  
(E) None of the above  

---

**Q41.** The highest peak in South India, located in Kerala, is:

(A) Doddabetta (Tamil Nadu)  
(B) Anamudi (2,695 m) in Kerala  
(C) Mahendragiri (Odisha)  
(D) More than one of the above  
(E) None of the above  

---

**Q42.** Western Ghats are also known as:

(A) Vindhyas  
(B) Sahyadri  
(C) Aravalli  
(D) More than one of the above  
(E) None of the above  

---

**Q43.** India is bordered by how many neighboring countries on land?

(A) 5 countries  
(B) 6 countries  
(C) 7 countries  
(D) More than one of the above  
(E) None of the above  

---

**Q44.** Bihar shares its border with which of the following states?

(A) Madhya Pradesh and Rajasthan  
(B) Uttar Pradesh, Jharkhand, and West Bengal  
(C) Odisha and Assam  
(D) More than one of the above  
(E) None of the above  

---

**Q45.** The Thar Desert is located primarily in which Indian state?

(A) Gujarat  
(B) Haryana  
(C) Rajasthan  
(D) More than one of the above  
(E) None of the above  

---

**Q46.** The Southwest Monsoon in India arrives from which direction and brings rainfall to most of India during:

(A) Northeast direction; December–February  
(B) Southwest direction; June–September  
(C) Northwest direction; March–May  
(D) More than one of the above  
(E) None of the above  

---

**Q47.** Which physical division of India is considered the OLDEST landmass?

(A) The Himalayas  
(B) The Northern Plains  
(C) The Peninsular Plateau  
(D) More than one of the above  
(E) None of the above  

---

**Q48.** The deepest lake in the world is:

(A) Lake Superior (North America)  
(B) Caspian Sea (Central Asia)  
(C) Lake Baikal (Russia)  
(D) More than one of the above  
(E) None of the above  

---

**Q49.** Consider the following soil-crop associations:
1. Black soil → Cotton ✓
2. Alluvial soil → Wheat and Rice ✓
3. Laterite soil → Wheat ✗ (Laterite = Tea, Coffee, Rubber)
4. Red soil → Groundnut and Millet ✓

Which of the above are CORRECTLY matched?

(A) Only 1 and 2  
(B) Only 1, 2, and 4  
(C) All four  
(D) More than one of the above  
(E) None of the above  

---

**Q50.** Bihar's most significant river, which flows from west to east through the entire state, is:

(A) Son River  
(B) Gandak River  
(C) Ganga River  
(D) More than one of the above  
(E) None of the above  

---

---

# 🔑 ANSWER KEY

> ✅ STOP! Did you attempt ALL 50 questions first?
> Score Guide: 45–50 = Topper Level 🏆 | 38–44 = Strong | 30–37 = Quick Revision Needed | Below 30 = Re-study

---

## CS ANSWERS (Q1–Q25)

| Q | Ans | Explanation |
|---|-----|-------------|
| Q1 | **(C)** | OSI model has 7 layers (Application, Presentation, Session, Transport, Network, Data Link, Physical) |
| Q2 | **(C)** | Physical Layer converts data to bits for physical transmission |
| Q3 | **(C)** | TCP/IP "Host-to-Host" = OSI Transport Layer (Layer 4) — direct mapping |
| Q4 | **(C)** | IPv6 = 128 bits (NOT 32 bits which is IPv4, NOT 64, NOT 256) |
| Q5 | **(C)** | IPv6 flow label is CONSIDERED (not discarded) during header translation |
| Q6 | **(C)** | TCP 3-way: SYN → SYN-ACK → ACK (in that exact order!) |
| Q7 | **(C)** | Sending server acts as SMTP CLIENT — classic PYQ trap! |
| Q8 | **(C)** | HTTP = stateless, port 80 (HTTPS is port 443) |
| Q9 | **(C)** | FTP = TWO ports: 20 for data, 21 for control (unique among protocols!) |
| Q10 | **(C)** | Ping uses ICMP — NOT TCP or UDP |
| Q11 | **(C)** | MQTT = IoT protocol using Publish-Subscribe model over TCP |
| Q12 | **(C)** | P2P = network model/type — NOT a topology (Bus, Star, Ring are topologies) |
| Q13 | **(C)** | Full mesh: n(n-1)/2 = 6×5/2 = 15 links |
| Q14 | **(C)** | Switch = Layer 2, uses MAC addresses to forward to specific device |
| Q15 | **(B)** | WWW = collection of hyperlinked documents on the Internet (NOT same as Internet!) |
| Q16 | **(C)** | Optical Fiber = highest speed + complete EM immunity (uses light, not electricity) |
| Q17 | **(B)** | UTP = Unshielded = no metal protection = vulnerable to EM/electrical interference |
| Q18 | **(C)** | Switched network prevents sniffing; switch sends only to intended device |
| Q19 | **(C)** | Private key = kept by RECEIVER for decryption |
| Q20 | **(C)** | Full access rights to ALL users = system integrity breach |
| Q21 | **(C)** | LLC = upper sublayer of Data Link Layer (Layer 2) |
| Q22 | **(B)** | DNS uses UDP for standard queries (TCP only for zone transfers) |
| Q23 | **(B)** | DORA = Discover → Offer → Request → Acknowledge |
| Q24 | **(D)** | Statements 1, 3, 4 are correct; Statement 2 is WRONG (backbone fails → ALL devices fail) → "More than one" (1, 3, 4 are correct) |
| Q25 | **(D)** | Statements 1, 2, 4 are correct; Statement 3 is WRONG (HTTPS = 443, not 80) → "More than one" (1, 2, 4 correct) |

---

## GS ANSWERS (Q26–Q50)

| Q | Ans | Explanation |
|---|-----|-------------|
| Q26 | **(C)** | India has 6 physical divisions: Himalayas, N. Plains, Thar Desert, Peninsular Plateau, Coastal Plains, Islands |
| Q27 | **(C)** | Kangchenjunga (8,586m) = highest IN India; K2 is in PoK (disputed territory) |
| Q28 | **(C)** | Himalayas = young fold mountains (formed by tectonic plate collision) |
| Q29 | **(B)** | Northern Plains = alluvial deposits of Indus + Ganga + Brahmaputra systems |
| Q30 | **(C)** | Bihar = entirely in Gangetic Plains (Northern Plains) |
| Q31 | **(B)** | Kosi = "Sorrow of Bihar" — frequent course changes cause devastating floods |
| Q32 | **(B)** | Son River = RIGHT bank tributary of Ganga (joins near Patna from the south) |
| Q33 | **(C)** | Narmada and Tapi flow WESTWARD into Arabian Sea (exceptional among peninsular rivers) |
| Q34 | **(A)** | Godavari = "Dakshin Ganga" — Ganga of the South; longest peninsular river |
| Q35 | **(B)** | Mawsynram, Meghalaya = current world record for highest rainfall |
| Q36 | **(C)** | Leh (Ladakh) = driest place in India; less than 100mm/year |
| Q37 | **(C)** | Black soil (Regur) = best for Cotton; found in Deccan Plateau |
| Q38 | **(C)** | Alluvial soil = Northern Plains (Ganga-Indus-Brahmaputra plains) |
| Q39 | **(B)** | Laterite soil = Tea, Coffee, Rubber, Cashew (plantation crops) |
| Q40 | **(C)** | Sundarbans delta = formed by Ganga + Brahmaputra (shared with Bangladesh) |
| Q41 | **(B)** | Anamudi (2,695 m) in Kerala = highest peak in South India |
| Q42 | **(B)** | Western Ghats = Sahyadri (traditional/local name) |
| Q43 | **(C)** | India has 7 land neighbors: Pakistan, Afghanistan, China, Nepal, Bhutan, Bangladesh, Myanmar |
| Q44 | **(B)** | Bihar borders: N→Nepal, E→West Bengal, S→Jharkhand, W→Uttar Pradesh |
| Q45 | **(C)** | Thar Desert = primarily in Rajasthan (some part in Gujarat also) |
| Q46 | **(B)** | SW Monsoon = from Southwest direction; June–September; 70–90% of India's rainfall |
| Q47 | **(C)** | Peninsular Plateau = oldest landmass in India (ancient crystalline rocks) |
| Q48 | **(C)** | Lake Baikal (Russia) = deepest lake in the world |
| Q49 | **(B)** | Items 1, 2, 4 correct; Item 3 is WRONG (Laterite soil → NOT wheat; → Tea/Coffee/Rubber) |
| Q50 | **(C)** | Ganga River flows through entire Bihar from west to east — most significant river |

---

---

# 📌 DAILY NIGHT REVISION — 5-BULLET SUMMARY

Write these from memory. If you can't, re-read that section!

## CS — Networks Complete Revision:
1. OSI=7 layers; TCP/IP=4 layers; Host-to-Host=Transport; LLC+MAC=DataLink sublayers
2. IPv4=32bits; IPv6=128bits; Flow label CONSIDERED; TCP=3-way SYN-SYN/ACK-ACK
3. SMTP sending server=CLIENT; FTP=ports 20+21; DNS=UDP; DHCP=DORA; Ping=ICMP
4. Bus=single cable+terminators; Star=hub mandatory; Mesh=n(n-1)/2; P2P≠topology
5. Optical Fiber=highest speed+EM immune; Private key=RECEIVER; Sniffer=switched network

## GS — Geography Key Facts:
1. Himalayas=fold mountains; Kangchenjunga=highest IN India; Kosi=Sorrow of Bihar
2. Narmada+Tapi=flow WEST into Arabian Sea (ALL other peninsular rivers flow East)
3. Highest rainfall=Mawsynram(not Cherrapunji); Driest=Leh Ladakh
4. Black soil=Cotton(Deccan Plateau); Alluvial=most fertile(Bihar); Laterite=Tea/Coffee/Rubber
5. Bihar=entirely in Gangetic Plains; borders Nepal(N), WB(E), Jharkhand(S), UP(W)

---

## ⚡ NETWORKS CHECKLIST — BEFORE YOU CLOSE TODAY

Tick each item from memory (this is from the study plan itself!):

- [ ] OSI = 7 layers ✓ | TCP/IP = 4 layers ✓
- [ ] IPv4 = 32 bits ✓ | IPv6 = 128 bits ✓
- [ ] Host-to-Host = Transport layer ✓
- [ ] TCP = connection-oriented ✓
- [ ] SMTP client = sending server ✓
- [ ] Peer-to-peer is NOT a topology ✓
- [ ] Optical fiber = highest speed ✓
- [ ] Private key = kept by RECEIVER ✓
- [ ] Ping = ICMP (NOT "Packet Internet Groper") ✓
- [ ] n(n-1)/2 = Mesh links formula ✓
- [ ] FTP = ports 20 + 21 ✓
- [ ] DNS = UDP for queries ✓
- [ ] DORA = DHCP process ✓
- [ ] Sniffer prevention = switched network ✓
- [ ] Full access rights = integrity breach ✓

**Score: 15/15 = NETWORKS MASTER! 🏆**

---

*Day 49 Complete! Networks Unit DONE! ✅*
*Next: Day 50 — TRE 1.0 FULL PYQ PAPER (CS Section — 80 Questions) — Exam Simulation!*
*You have completed Phase 1 Week 7 of 9! Keep the momentum! 💪*
*BPSC TRE 4.0 Target: 130+/150 — YOU ARE BUILDING A WINNING EXAM SYSTEM! 🎯*
