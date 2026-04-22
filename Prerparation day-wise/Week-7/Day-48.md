# 📅 BPSC TRE 4.0 — DAY 48 COMPLETE STUDY MODULE
### Computer Networks: Transmission Media, Network Security & Cryptography + Bihar GK — Agriculture & Production
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): Transmission Media (Guided/Unguided) + Network Security + Cryptography
> - Afternoon (1 hr): Bihar GK — Major Crops, Production Districts, Agriculture Facts
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5 bullet revision points from today's notes

---

# PART 1: COMPUTER SCIENCE
## 📘 Transmission Media, Network Security & Cryptography

---

## 🔷 SECTION 1: What is Transmission Media?

### Real-Life Analogy — Roads for Data:

Data is like traffic, and transmission media are the ROADS it travels on:
- A narrow village road (twisted pair copper) — cheap, handles local traffic
- A 4-lane highway (coaxial cable) — faster, carries more traffic
- A bullet-train rail line (optical fiber) — fastest, high capacity, long distance
- Open sky (wireless) — no physical road, signals travel freely through air

> **Transmission Media is the physical pathway (or channel) through which data signals travel from one device to another in a network.**

### Types of Transmission Media:
```
                    TRANSMISSION MEDIA
                           │
          ┌────────────────┴────────────────┐
          │                                 │
   GUIDED MEDIA                    UNGUIDED MEDIA
   (Wired — signal travels          (Wireless — signal travels
    through physical medium)         through air/space)
          │                                 │
    ┌─────┼─────┐                 ┌─────────┼──────────┐
    │     │     │                 │         │          │
 Twisted Coaxial Optical       Radio     Micro-     Infrared
  Pair   Cable   Fiber          Waves      waves
```

---

## 🔷 SECTION 2: GUIDED MEDIA (Wired Transmission)

### TYPE 1 — TWISTED PAIR CABLE

```
STRUCTURE:
  Two insulated copper wires TWISTED together in a spiral pattern.
  The twisting is KEY — it cancels out electromagnetic interference
  from neighboring pairs (called EMI cancellation or crosstalk reduction).
  
  VISUAL CROSS-SECTION:
  ┌────────────────────────────────────────────────────────────────┐
  │  Wire 1 (copper) ──╮  ╭──╮  ╭──  (twisted around each other)│
  │                     ╰──╯  ╰──╯                                │
  │  Wire 2 (copper) ──╮  ╭──╮  ╭──                              │
  │                     ╰──╯  ╰──╯                                │
  │  [Both wrapped in plastic insulation]                         │
  └────────────────────────────────────────────────────────────────┘
  
  A CABLE contains multiple twisted pairs bundled together.
  
TWO TYPES:
  ┌────────────────────────────┬────────────────────────────────────┐
  │   UTP (Unshielded TP)      │      STP (Shielded TP)            │
  ├────────────────────────────┼────────────────────────────────────┤
  │ No extra shielding         │ Metal foil/braid shielding around  │
  │                            │ each pair AND outer bundle         │
  ├────────────────────────────┼────────────────────────────────────┤
  │ CHEAPER                    │ MORE EXPENSIVE                     │
  ├────────────────────────────┼────────────────────────────────────┤
  │ MORE VULNERABLE to EMI     │ BETTER protection from EMI         │
  │ (electromagnetic           │                                    │
  │  interference)             │                                    │
  ├────────────────────────────┼────────────────────────────────────┤
  │ Suitable for most offices  │ For high-interference environments │
  │ and homes                  │ (near factories, hospitals)        │
  ├────────────────────────────┼────────────────────────────────────┤
  │ MOST COMMON type of        │ Less common                        │
  │ networking cable!          │                                    │
  └────────────────────────────┴────────────────────────────────────┘

CATEGORIES OF UTP CABLE (Cat ratings):
  Cat 3:  Up to 10 Mbps  (old telephone, 10BASE-T Ethernet)
  Cat 5:  Up to 100 Mbps (Fast Ethernet — 100BASE-TX)
  Cat 5e: Up to 1 Gbps   (Gigabit Ethernet — enhanced Cat5)
  Cat 6:  Up to 10 Gbps  (for short distances; most modern offices use this)
  Cat 6a: Up to 10 Gbps  (longer distances than Cat6)
  Cat 7:  Up to 10 Gbps+ (shielded, premium)
  Cat 8:  Up to 40 Gbps  (data centres)

CONNECTORS:
  RJ-45 connector used with twisted pair for Ethernet (LAN) connections
  RJ-11 connector for telephone connections

ADVANTAGES:
  ✅ Cheap and widely available
  ✅ Easy to install and terminate
  ✅ Flexible — can bend around corners
  ✅ Suitable for most LAN environments

DISADVANTAGES:
  ❌ UTP = vulnerable to EMI (electromagnetic interference)
  ❌ Limited distance (~100 metres for Ethernet without repeaters)
  ❌ Lower bandwidth than coaxial or fiber
  ❌ Susceptible to eavesdropping (easier to tap than fiber)

USE CASES:
  → Telephone networks (original use — hence "twisted pair")
  → LAN connections (most common — Cat5e/Cat6 in offices)
  → DSL broadband over existing telephone lines

🎯 PYQ FACT: Twisted pair = MOST COMMON wired LAN medium (in offices/homes)
🎯 PYQ FACT: UTP = vulnerable/susceptible to EMI; STP = shielded (better EMI protection)
🎯 PYQ FACT: RJ-45 connector = used for twisted pair Ethernet connections
🚨 TRAP: "STP is cheaper than UTP" → FALSE! STP is MORE expensive.
🚨 TRAP: "Twisted pair = highest speed transmission medium" → FALSE! Fiber = highest speed.
```

---

### TYPE 2 — COAXIAL CABLE

```
STRUCTURE:
  
  ┌──────────────────────────────────────────────────────────────────┐
  │    [Outer plastic jacket]                                        │
  │      [Braided metal shield / outer conductor]                    │
  │        [Insulating dielectric layer]                             │
  │          [Central copper conductor] ←── carries signal          │
  └──────────────────────────────────────────────────────────────────┘

  Cross-section (center outward):
  1. CORE: Central copper conductor (carries the signal)
  2. DIELECTRIC: Insulating layer (separates core from shield)
  3. SHIELD: Braided metal mesh (blocks external interference)
  4. JACKET: Outer protective plastic covering

  The name "co-axial" = both conductors share the SAME AXIS (center line)

HOW IT'S BETTER THAN TWISTED PAIR:
  The outer metal SHIELD acts like a FARADAY CAGE — blocks electromagnetic
  interference from outside AND keeps signal from radiating outward.
  
  Much BETTER EMI protection than UTP (but not as good as fiber)!

TYPES:
  Thin Coax (Thinnet / RG-58): 10BASE2 Ethernet (obsolete) 
  Thick Coax (Thicknet / RG-8): 10BASE5 Ethernet (obsolete)
  RG-6: Cable TV, cable internet (DOCSIS standard)
  RG-11: Long distance cable TV runs

ADVANTAGES:
  ✅ BETTER shielding than twisted pair → less interference
  ✅ Higher bandwidth than twisted pair
  ✅ Longer distance than twisted pair (before needing repeater)
  ✅ Good for cable TV distribution (wide use)

DISADVANTAGES:
  ❌ More expensive than twisted pair
  ❌ Less flexible (harder to bend) — bulkier
  ❌ More expensive to install
  ❌ MUCH slower than optical fiber
  ❌ Largely obsolete for networking (replaced by twisted pair + switches)

USE CASES:
  → Cable TV distribution (most common current use!)
  → Cable Internet (broadband via DOCSIS technology)
  → Radio antenna connections (coax = standard for RF)
  → Early Ethernet (10BASE2 "thinnet" — now obsolete)
  → CCTV/Security camera systems

🎯 PYQ FACT: Coaxial cable = central conductor + insulator + metal shield + outer jacket
🎯 PYQ FACT: Coaxial = BETTER EMI protection than twisted pair; LESS than fiber
🎯 PYQ FACT: Cable TV uses coaxial cable (RG-6)
🚨 TRAP: "Coaxial has highest transmission speed" → FALSE! Fiber has highest speed.
```

---

### TYPE 3 — OPTICAL FIBER (Most Important!)

```
STRUCTURE:
  
  ┌──────────────────────────────────────────────────────────────────┐
  │  [Outer jacket — protective polymer]                             │
  │    [Buffer coating — protects fiber]                             │
  │      [Cladding — lower refractive index glass/plastic]          │
  │        [CORE — thin glass/plastic fiber, carries light signal]  │
  └──────────────────────────────────────────────────────────────────┘

  THE CORE is INCREDIBLY thin:
  → Single-mode fiber core: ~8-10 micrometers (thinner than human hair!)
  → Multi-mode fiber core: ~50-62.5 micrometers
  
  PRINCIPLE: Total Internal Reflection
  Light bounces off the cladding walls (which have lower refractive index)
  and stays within the core, traveling the full length of the fiber!
  
  Like light in a bouncy tube:
  Light enters ──▶╲                   ╱─▶ light out
                   ╲─────────────────╱
                   ↑     CORE        ↑
                CLADDING          CLADDING
  (light bounces between cladding walls — stays inside!)

TWO TYPES:
  SINGLE-MODE FIBER (SMF):
  → Very thin core (~8-10 μm)
  → Laser light source (single wavelength)
  → Less signal dispersion → travels much LONGER distances!
  → Higher bandwidth
  → MORE EXPENSIVE
  → Use: Long-haul Internet backbone, telephone networks,
          submarine cables (under oceans!)
  
  MULTI-MODE FIBER (MMF):
  → Wider core (~50-62.5 μm)
  → LED light source (multiple wavelengths/paths)
  → More signal dispersion → shorter distances
  → CHEAPER than single-mode
  → Use: Short distances (data centres, within buildings)

ADVANTAGES:
  ✅ HIGHEST TRANSMISSION SPEED (terabits per second possible!)
  ✅ LONGEST DISTANCE without repeaters
  ✅ IMMUNE TO EMI (electromagnetic interference) — light, not electricity!
  ✅ NO CROSSTALK between fiber cables (no EM fields)
  ✅ MOST SECURE — extremely difficult to tap (tapping disturbs light)
  ✅ THIN AND LIGHTWEIGHT (though fragile)
  ✅ NO ELECTRICAL SPARKS — safe in explosive environments

DISADVANTAGES:
  ❌ MOST EXPENSIVE installation (skilled technicians, special equipment)
  ❌ FRAGILE — glass core breaks if bent sharply
  ❌ DIFFICULT to splice/repair (requires precision fusion splicing)
  ❌ Cannot carry electrical power (need separate power cables)

USE CASES:
  → Internet backbone (submarine cables under Pacific, Atlantic oceans!)
  → BharatNet (India's rural broadband project)
  → Long-distance telephone networks
  → Data centres (high-speed connections between servers)
  → FTTH (Fiber To The Home) — Jio Fiber, Airtel Xstream fiber
  → Medical: Endoscopes (fiber optic cameras inside the body!)
  → Military: Secure, EMI-immune communications

🎯 PYQ FACT: Optical fiber = HIGHEST transmission speed AND longest distance
🎯 PYQ FACT: Optical fiber = IMMUNE to EMI (uses light, not electricity!)
🎯 PYQ FACT: Fiber = MOST SECURE wired medium (hardest to tap)
🎯 PYQ FACT: Fiber uses Total Internal Reflection principle
🎯 PYQ FACT: BharatNet uses optical fiber to connect rural areas in India
🚨 TRAP: "Optical fiber is affected by electromagnetic interference" → FALSE!
         Fiber uses LIGHT signals — completely immune to EMI.
🚨 TRAP: "Twisted pair has higher speed than fiber" → FALSE! Fiber >> Twisted Pair.
```

---

## 🔷 SECTION 3: UNGUIDED MEDIA (Wireless Transmission)

### TYPE 1 — RADIO WAVES

```
FREQUENCY RANGE: 3 kHz to 1 GHz
PROPAGATION:     Omnidirectional (travels in all directions from antenna)
                 Can penetrate walls and obstacles

CHARACTERISTICS:
  → LOW FREQUENCY: travels long distances, can penetrate buildings
  → BROADCAST medium: one transmitter, many receivers simultaneously
  → SUSCEPTIBLE to interference from other radio sources
  → Licensed spectrum (governments regulate who uses which frequency)

USE CASES:
  → AM/FM Radio broadcasting (music, news)
  → Television broadcasting (analogue TV)
  → Mobile phones (cellular networks) — 2G/3G/4G/5G all use radio waves
  → Wi-Fi (802.11 — 2.4 GHz and 5 GHz bands)
  → Bluetooth (2.4 GHz)
  → Walkie-talkies, CB radio
  → GPS signals

FREQUENCY BANDS:
  LF (Low Freq): Submarine communication (can penetrate seawater!)
  HF:            Shortwave radio (international broadcasts, ham radio)
  VHF:           FM radio, TV, aviation communication
  UHF:           TV, 4G/LTE, Wi-Fi, Bluetooth

🎯 PYQ FACT: Radio waves = omnidirectional (spreads in all directions)
🎯 PYQ FACT: Radio waves used in: broadcast, mobile phones, Wi-Fi, Bluetooth
🎯 PYQ FACT: Radio waves can penetrate walls and obstacles
```

---

### TYPE 2 — MICROWAVES

```
FREQUENCY RANGE: 1 GHz to 300 GHz
PROPAGATION:     LINE-OF-SIGHT — transmitter and receiver must be
                 in direct visual alignment (no obstacles!)

TWO TYPES:

TERRESTRIAL MICROWAVE:
  → Ground-based towers (microwave towers) spaced 20-30 km apart
  → Earth's curvature limits distance → need relay towers for long-distance
  → Antennas: Parabolic dish antennas pointed precisely at each other
  → Use: Long-distance telephone (trunk lines), TV broadcast relay,
         utility company communications

SATELLITE MICROWAVE:
  → One station sends signal UP to satellite
  → Satellite amplifies and redirects signal DOWN to receiving station
  → Can cover vast distances (entire countries, hemispheres!)
  
  SATELLITE TYPES by orbit:
    GEO (Geostationary): 36,000 km altitude; FIXED position over equator
      → Appears stationary (rotates with Earth)
      → HIGH LATENCY (signal takes ~240ms round trip)
      → Use: TV broadcasting (Doordarshan, DTH), weather satellites
      
    LEO (Low Earth Orbit): 500-2000 km altitude
      → MUCH LOWER LATENCY
      → Moves quickly (need many satellites for continuous coverage)
      → Use: Starlink (SpaceX), GPS, Iridium satellite phones
    
    MEO: 2000-35,786 km (between LEO and GEO)
      → GPS satellites are in MEO orbit!

ADVANTAGES:
  ✅ High bandwidth (multi-GHz capacity)
  ✅ Long-distance communication (satellite covers entire regions)
  ✅ No wired infrastructure needed in remote areas

DISADVANTAGES:
  ❌ LINE-OF-SIGHT required (terrestrial) — buildings/hills block signal
  ❌ HIGH LATENCY for satellite (especially GEO)
  ❌ Weather affected (heavy rain causes "rain fade")
  ❌ Expensive satellite infrastructure

🎯 PYQ FACT: Microwaves = LINE-OF-SIGHT communication (must see each other!)
🎯 PYQ FACT: Satellite communication uses microwave frequencies
🎯 PYQ FACT: GEO satellites = 36,000 km altitude (TV/weather); GPS = MEO orbit
🚨 TRAP: "Microwaves penetrate obstacles like radio waves" → FALSE!
         Microwaves require LINE-OF-SIGHT (blocked by obstacles).
```

---

### TYPE 3 — INFRARED

```
FREQUENCY RANGE: 300 GHz to 400 THz (above microwave, below visible light)
PROPAGATION:     Line-of-sight, SHORT RANGE (few metres to tens of metres)

CHARACTERISTICS:
  → CANNOT penetrate walls (blocked by solid objects)
  → Directional — must aim at receiver
  → No government licensing (low-power)
  → Short range only

USE CASES:
  → TV/Air Conditioner/Set-top box REMOTE CONTROLS
  → Old-style data transfer between devices (IrDA standard)
  → Short-range device-to-device transfer (older phones)
  → Industrial temperature sensing
  → Night vision cameras/goggles
  → Thermal imaging

WHY NOT USED FOR NETWORKING:
  → Cannot penetrate walls (useless for whole-building coverage)
  → Very short range (unlike Wi-Fi which covers entire floors)
  → Today largely replaced by Bluetooth/Wi-Fi for device communication

🎯 PYQ FACT: Infrared = used in REMOTE CONTROLS (TV, AC, set-top box)
🎯 PYQ FACT: Infrared = SHORT RANGE, cannot penetrate walls
🎯 PYQ FACT: Infrared = no wall penetration (unlike radio waves which can)
🚨 TRAP: "Infrared is used for long-distance communication" → FALSE!
         Infrared = short range only; microwaves for long distance.
```

---

## 🔷 SECTION 4: Transmission Media Comparison — Master Table

```
┌────────────────────┬───────────┬────────────────┬──────────────────┬─────────────────┬───────────────────┐
│      MEDIUM        │   SPEED   │   DISTANCE     │   INTERFERENCE   │     COST        │   MAIN USE        │
├────────────────────┼───────────┼────────────────┼──────────────────┼─────────────────┼───────────────────┤
│ UTP (Twisted Pair) │ Moderate  │ ~100m max      │ HIGH (EMI        │ CHEAPEST        │ Office LAN,       │
│                    │ (1-10Gbps)│ (Ethernet)     │ susceptible)     │                 │ Home networks     │
├────────────────────┼───────────┼────────────────┼──────────────────┼─────────────────┼───────────────────┤
│ STP (Shielded TP)  │ Moderate  │ ~100m max      │ Medium (shielded)│ Moderate        │ Industrial LAN    │
├────────────────────┼───────────┼────────────────┼──────────────────┼─────────────────┼───────────────────┤
│ Coaxial Cable      │ Moderate  │ ~500m (coax TV)│ LOW (metal       │ Moderate        │ Cable TV,         │
│                    │ (up to    │                │ shield)          │                 │ Cable Internet    │
│                    │ few Gbps) │                │                  │                 │                   │
├────────────────────┼───────────┼────────────────┼──────────────────┼─────────────────┼───────────────────┤
│ OPTICAL FIBER      │ HIGHEST   │ LONGEST        │ ZERO (immune!    │ MOST            │ Internet backbone,│
│                    │ (Tbps     │ (km–hundreds   │ Uses LIGHT,      │ EXPENSIVE       │ long distance,    │
│                    │ possible!)│ of km)         │ not electricity) │                 │ FTTH              │
├────────────────────┼───────────┼────────────────┼──────────────────┼─────────────────┼───────────────────┤
│ Radio Waves        │ Varies    │ Very Long      │ HIGH (crowded    │ Low (no wires)  │ Broadcasting,     │
│                    │           │ (omnidirect.)  │ spectrum)        │ but spectrum    │ Wi-Fi, Mobile     │
│                    │           │                │                  │ license costly  │                   │
├────────────────────┼───────────┼────────────────┼──────────────────┼─────────────────┼───────────────────┤
│ Microwaves         │ HIGH      │ Medium-Long    │ MEDIUM           │ High (dish      │ Satellite,        │
│                    │           │ (line-of-sight)│ (line of sight   │ antennas,       │ Long-distance     │
│                    │           │                │ affected)        │ satellites)     │ telephone relay   │
├────────────────────┼───────────┼────────────────┼──────────────────┼─────────────────┼───────────────────┤
│ Infrared           │ Low-Med   │ SHORT          │ LOW (indoor      │ Very Low        │ Remote controls,  │
│                    │           │ (~few metres)  │ walls block)     │                 │ short-range comms │
└────────────────────┴───────────┴────────────────┴──────────────────┴─────────────────┴───────────────────┘

SPEED RANKING: Optical Fiber > Coaxial > Twisted Pair (guided)
SPEED RANKING: Microwave > Radio Waves > Infrared (unguided)
OVERALL FASTEST: Optical Fiber

INTERFERENCE RANKING (worst to best): Radio Waves > UTP > Coaxial > STP > Fiber
SECURITY RANKING (most to least secure): Fiber > STP > Coaxial > UTP > Wireless
```

---

## 🔷 SECTION 5: Network Security — Overview

### What is Network Security?
```
NETWORK SECURITY = Set of policies, procedures, and technologies designed
                   to PROTECT network infrastructure, data, and communications
                   from unauthorized access, misuse, or attacks.

THREE GOALS OF NETWORK SECURITY (CIA Triad):
  C = CONFIDENTIALITY: Only authorized persons can access data
                        (Encryption ensures unauthorized readers see garbage)
  I = INTEGRITY:       Data is not tampered with during transit
                        (Checksums, digital signatures detect modification)
  A = AVAILABILITY:    Network resources are available to authorized users
                        (Prevention of DoS attacks ensures uptime)

"CIA Triad" = The three pillars of information security
(Not the intelligence agency! C=Confidentiality, I=Integrity, A=Availability)

🎯 PYQ FACT: CIA Triad = Confidentiality + Integrity + Availability
🎯 PYQ FACT: Encryption → Confidentiality; Checksums → Integrity; Anti-DoS → Availability
```

---

## 🔷 SECTION 6: Common Network Threats

### SNIFFING (Packet Sniffing):
```
WHAT IS SNIFFING?
  A SNIFFER (Packet Sniffer) = a program or device that captures and
  analyses data packets traveling through a network.

LEGITIMATE USE (Network Analysis):
  → Network administrators use sniffers like Wireshark to:
    → Diagnose network problems
    → Monitor traffic patterns
    → Detect bottlenecks

MALICIOUS USE (Network Attack):
  → Attacker places a sniffer on the network to CAPTURE passwords,
    credit card numbers, emails, and other sensitive data IN TRANSIT
  → On a HUB-based network: easy! Hub broadcasts to all — sniffer gets everything.

HOW SNIFFING WORKS ON HUB vs SWITCH:
  HUB NETWORK:
  → Hub broadcasts ALL packets to ALL ports
  → Attacker's device connected to any hub port
  → Sniffer captures ALL traffic passing through hub
  → VERY EASY to sniff on hub networks!
  
  SWITCH NETWORK:
  → Switch sends data ONLY to the intended recipient's port
  → Attacker sees ONLY their own traffic
  → MUCH HARDER to sniff!
  → Switch-based networks significantly reduce sniffing risk

🎯 PYQ CRITICAL FACT: Sniffers are most effective on HUB networks
🎯 PYQ CRITICAL FACT: Switching to SWITCH-BASED networks REDUCES sniffing risk
                      (because switch only sends data to the correct port)
🎯 PYQ FACT: Wireshark = popular legitimate network analyser/sniffer tool
🚨 TRAP: "Sniffing is completely prevented by switches" → NUANCED!
         Switches greatly REDUCE sniffing but don't completely eliminate it.
         ARP poisoning can force a switch to act like a hub.
         For BPSC exam: "Switch-based networks PREVENT/REDUCE sniffing" is the expected answer.
```

### Other Common Threats:
```
HACKING:
  Unauthorized access to computer systems/networks.
  Types:
  → Phishing: Fake emails/websites trick users into revealing credentials
  → Brute Force: Try all possible passwords systematically
  → Social Engineering: Manipulating people to reveal confidential info
  → Zero-day Exploit: Attacking a vulnerability before it's patched

MALWARE (Malicious Software):
  → VIRUS: Self-replicating code that ATTACHES to host files
            Spreads when infected files are shared/executed
  → WORM: Self-replicating, spreads INDEPENDENTLY through networks
           (doesn't need a host file — spreads on its own!)
  → TROJAN HORSE: Disguises itself as legitimate software
                  "Trojan Horse" — looks like a gift, contains attack!
  → RANSOMWARE: Encrypts victim's files, demands ransom for decryption key
                 Example: WannaCry (2017), REvil
  → SPYWARE: Secretly monitors and reports user activity
  → ADWARE: Displays unwanted ads, often bundled with free software
  → ROOTKIT: Hides deep in OS, gives attacker persistent access

DoS / DDoS ATTACK:
  → DoS (Denial of Service): Attacker floods server with requests
    → Server overwhelmed → legitimate users can't access it
  → DDoS (Distributed DoS): Same but from THOUSANDS of compromised devices
    → Botnets of infected computers all attack simultaneously
    → Much harder to defend against

MAN-IN-THE-MIDDLE (MitM):
  → Attacker secretly intercepts communication between two parties
  → Each party thinks they're talking directly to the other
  → Attacker reads and possibly modifies data in transit
  → PREVENTED by: Encryption (HTTPS/SSL), Certificate verification

SQL INJECTION:
  → Attacker inserts malicious SQL code into input fields
  → Database executes attacker's SQL commands
  → Can read/delete/modify the entire database!
  → PREVENTED by: Input validation, parameterized queries

FIREWALL:
  → Hardware/software that monitors and controls incoming/outgoing traffic
  → Based on predefined security RULES
  → Like a security guard — checks every packet entering/leaving network
  → Types: Packet filtering, Stateful inspection, Application-level proxy

🎯 PYQ FACT: Virus attaches to files; Worm spreads independently
🎯 PYQ FACT: Ransomware = encrypts files + demands ransom
🎯 PYQ FACT: Firewall = monitors and filters network traffic
```

---

## 🔷 SECTION 7: Cryptography — The Art of Secret Writing

### What is Cryptography?
```
CRYPTOGRAPHY = The science of securing information by converting it into
               an unreadable format (ciphertext) so only authorized parties
               with the KEY can read it (plaintext).

KEY TERMS:
  PLAINTEXT:   Original, readable message ("Hello, how are you?")
  CIPHERTEXT:  Encrypted, unreadable message ("Xyzab, cdz efg abc?")
  ENCRYPTION:  Converting plaintext → ciphertext (using a KEY)
  DECRYPTION:  Converting ciphertext → plaintext (using a KEY)
  KEY:         The secret value used to encrypt/decrypt
  CIPHER:      The algorithm/method used for encryption

PROCESS:
  SENDER:
  Plaintext ──[ENCRYPT with KEY]──▶ Ciphertext ──▶ (sends over network)
  
  RECEIVER:
  Ciphertext ──[DECRYPT with KEY]──▶ Plaintext ──▶ (reads message)
  
  ATTACKER who intercepts:
  Ciphertext ──[No KEY = ??????????]──▶ Sees only garbage!
```

### TYPE 1 — SYMMETRIC KEY CRYPTOGRAPHY

```
SYMMETRIC KEY = SAME KEY used for BOTH encryption AND decryption

ANALOGY: A single padlock key:
  You lock a box with YOUR key (encrypt)
  You give the box to your friend
  Your friend unlocks it with the SAME key (decrypt)
  → Both sender and receiver must have the SAME key!

PROCESS:
  
  SENDER                              RECEIVER
    │                                     │
    │  Plaintext                          │
    │     ↓                               │
    │  [ENCRYPT with Key K]               │
    │     ↓                               │
    │  Ciphertext ──── network ──────────▶│ Ciphertext
    │                                     │     ↓
    │                                     │  [DECRYPT with Key K]
    │                                     │     ↓
    │                                     │  Plaintext
    
  KEY DISTRIBUTION PROBLEM:
  How do sender and receiver SHARE the secret key securely?
  If you send the key over the internet → attacker intercepts the key!
  → This is the main weakness of symmetric encryption

POPULAR SYMMETRIC ALGORITHMS:
  → DES (Data Encryption Standard): 56-bit key (now considered WEAK — cracked!)
  → 3DES (Triple DES): Applies DES 3 times — more secure but slow
  → AES (Advanced Encryption Standard): 128/192/256-bit key
    → Current gold standard! Used in WPA2 Wi-Fi, disk encryption, HTTPS
    → Fast, strong, widely adopted
  → Blowfish, RC4, ChaCha20 (streaming cipher)

ADVANTAGES:
  ✅ FAST — much faster than asymmetric encryption
  ✅ Simple concept — one key for everything
  ✅ Good for encrypting large volumes of data

DISADVANTAGES:
  ❌ KEY DISTRIBUTION PROBLEM — how to securely share the key?
  ❌ SCALABILITY — with n users needing pairwise keys: n(n-1)/2 keys needed!
  ❌ No non-repudiation (can't prove who sent what — both have same key)

🎯 PYQ FACT: Symmetric = same key for encrypt and decrypt
🎯 PYQ FACT: AES = most widely used symmetric algorithm today
🎯 PYQ FACT: DES = old, weak (56-bit key); AES = strong (128/256-bit)
🎯 PYQ FACT: Symmetric's weakness = key distribution problem
```

---

### TYPE 2 — ASYMMETRIC KEY CRYPTOGRAPHY (Public Key Cryptography)

```
ASYMMETRIC KEY = TWO DIFFERENT but mathematically RELATED KEYS:
  → PUBLIC KEY: Shared openly with everyone (anyone can see it!)
  → PRIVATE KEY: Kept SECRET by the owner (NEVER shared!)
  
  KEY PAIR PROPERTY: What one key ENCRYPTS, only the OTHER key can DECRYPT!
  
  PUBLIC KEY encrypts → PRIVATE KEY decrypts (and vice versa)

🎯 CRITICAL PYQ FACT: PRIVATE KEY is KEPT by the RECEIVER (never shared!)
                       PUBLIC KEY is distributed freely to everyone

FOR SECURE COMMUNICATION (Encryption):
  
  SENDER (Alice)                    RECEIVER (Bob)
      │                                   │
      │ ◀── Bob's PUBLIC KEY ─────────── │ (Bob shares his public key freely)
      │                                   │
      │ [Encrypt with Bob's PUBLIC KEY]   │
      │                                   │
      │ Ciphertext ──── network ─────────▶│
      │                                   │ [Decrypt with Bob's PRIVATE KEY]
      │                                   │ Only Bob can decrypt — he's the
      │                                   │ only one with his private key!
  
  WHY SECURE:
  Anyone can encrypt using Bob's public key.
  ONLY Bob can decrypt using his private key.
  Even if attacker intercepts ciphertext — they have no private key!

FOR DIGITAL SIGNATURES (Authentication):
  
  SENDER (Alice)                    RECEIVER (Bob)
      │                                   │
      │ [Sign with Alice's PRIVATE KEY]   │
      │                                   │
      │ Message + Signature ─────────────▶│
      │                                   │ [Verify with Alice's PUBLIC KEY]
      │                                   │ If valid → proved Alice sent it!
      │                                   │ (Only Alice has her private key)
  
  WHY: Alice's private key creates signature. Her public key verifies it.
       ONLY Alice could have created that signature → proves authenticity!

POPULAR ASYMMETRIC ALGORITHMS:
  → RSA (Rivest-Shamir-Adleman): Most widely used (key size 2048/4096 bits)
  → ECC (Elliptic Curve Cryptography): Smaller keys, equally strong
  → Diffie-Hellman: Key exchange protocol (not encryption directly)
  → DSA (Digital Signature Algorithm): For signatures only
  → PGP (Pretty Good Privacy): Email encryption (uses hybrid approach)

ADVANTAGES:
  ✅ SOLVES KEY DISTRIBUTION PROBLEM
     → No need to securely share a secret key beforehand!
     → Just publish your public key openly
  ✅ DIGITAL SIGNATURES — non-repudiation (proves who sent)
  ✅ Scalable — each user needs only ONE key pair

DISADVANTAGES:
  ❌ MUCH SLOWER than symmetric encryption (mathematically complex)
  ❌ Not suitable for encrypting large data (use symmetric for bulk data)
  ❌ Computationally expensive

HOW HTTPS/SSL USES BOTH (Hybrid Approach):
  1. Asymmetric encryption to SECURELY EXCHANGE a session key
  2. Symmetric encryption for the ACTUAL DATA transfer (faster!)
  
  "Best of both worlds!"
  Asymmetric = solves key distribution
  Symmetric = fast bulk encryption

🎯 PYQ FACT: Asymmetric = two keys (public + private)
🎯 PYQ FACT: PUBLIC key = freely shared; PRIVATE key = kept SECRET by RECEIVER/OWNER
🎯 PYQ FACT: RSA = most popular asymmetric algorithm
🎯 PYQ FACT: HTTPS uses HYBRID (asymmetric to exchange keys + symmetric for data)
🎯 PYQ FACT: Private key is used to CREATE digital signatures; Public key to VERIFY
🚨 TRAP: "Private key is shared publicly" → FALSE! Private key is NEVER shared.
🚨 TRAP: "Asymmetric is faster than symmetric" → FALSE! Symmetric is FASTER.
🚨 TRAP: "Public key decrypts what public key encrypted" → FALSE!
         Public encrypts → Private decrypts (and vice versa; OPPOSITE keys)
```

### Symmetric vs Asymmetric — Comparison Table:
```
┌──────────────────────────┬───────────────────────────────┬──────────────────────────────┐
│         FEATURE          │       SYMMETRIC               │       ASYMMETRIC             │
├──────────────────────────┼───────────────────────────────┼──────────────────────────────┤
│ Number of Keys           │ ONE key (same for both)       │ TWO keys (public + private)  │
├──────────────────────────┼───────────────────────────────┼──────────────────────────────┤
│ Key Sharing              │ Same key shared by BOTH       │ Public key shared; private   │
│                          │ sender and receiver           │ key NEVER shared             │
├──────────────────────────┼───────────────────────────────┼──────────────────────────────┤
│ Speed                    │ FAST                          │ SLOW (computationally heavy) │
├──────────────────────────┼───────────────────────────────┼──────────────────────────────┤
│ Key Distribution         │ PROBLEM (insecure sharing)    │ SOLVED (public key open)     │
├──────────────────────────┼───────────────────────────────┼──────────────────────────────┤
│ Security                 │ Weaker (key sharing risk)     │ Stronger (private key safe)  │
├──────────────────────────┼───────────────────────────────┼──────────────────────────────┤
│ Digital Signatures       │ NOT possible                  │ YES (private key signs)      │
├──────────────────────────┼───────────────────────────────┼──────────────────────────────┤
│ Examples                 │ AES, DES, 3DES, Blowfish      │ RSA, ECC, DSA, Diffie-Hellman│
├──────────────────────────┼───────────────────────────────┼──────────────────────────────┤
│ Best Use                 │ Encrypting large data         │ Key exchange, authentication │
├──────────────────────────┼───────────────────────────────┼──────────────────────────────┤
│ Analogy                  │ One PADLOCK KEY               │ MAILBOX (anyone puts mail in │
│                          │ (both have same key)          │ with public slot; only owner │
│                          │                               │ opens with private key)      │
└──────────────────────────┴───────────────────────────────┴──────────────────────────────┘
```

---

## 🔷 SECTION 8: Additional Security Concepts

```
FIREWALL:
  → Network security device (hardware or software)
  → Monitors ALL incoming AND outgoing network traffic
  → Applies rules: allow or block specific traffic
  → Types:
    Packet Filter: Checks IP/port in packet header (fast but simple)
    Stateful Inspection: Tracks connection state (smarter)
    Application Gateway (Proxy Firewall): Inspects application content

VPN (Virtual Private Network):
  → Creates an ENCRYPTED "tunnel" through the public internet
  → Your data travels encrypted — even ISP can't see contents
  → Makes you appear to be in a different location (IP masking)
  → Use: Remote workers accessing company network securely,
          privacy protection, bypassing geo-restrictions
  → Protocols: IPSec, OpenVPN, WireGuard, L2TP

DIGITAL CERTIFICATE:
  → Electronic document proving identity of a website/person/organization
  → Issued by a Certificate Authority (CA) like DigiCert, Let's Encrypt
  → Contains: Public key, owner identity, CA signature, expiry date
  → HTTPS websites have digital certificates (the padlock 🔒 you see!)
  → Your browser checks certificate to confirm "this is really Google.com"

HASHING (One-Way Function):
  → Converting ANY data into a FIXED-LENGTH hash value
  → ONE-WAY: You can't reverse a hash to get original data!
  → SAME INPUT → ALWAYS SAME HASH
  → Used for: Password storage (never store plain passwords!),
               file integrity checking, digital signatures
  → Algorithms: MD5 (old, broken), SHA-1 (deprecated), SHA-256 (current standard)
  → Example: SHA-256("hello") = 2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824

🎯 PYQ FACT: VPN = encrypted tunnel through public internet
🎯 PYQ FACT: Hash = one-way function; cannot be reversed
🎯 PYQ FACT: Digital Certificate issued by CA (Certificate Authority)
🎯 PYQ FACT: SHA-256 = current standard hashing algorithm
```

---

## 🔷 SECTION 9: PYQ Traps — Transmission Media & Security

```
🚨 TRAP 1: "Twisted pair has highest transmission speed" → FALSE!
   Optical Fiber = HIGHEST speed and longest distance.

🚨 TRAP 2: "Optical fiber is affected by EMI" → FALSE!
   Fiber uses LIGHT — completely IMMUNE to electromagnetic interference.

🚨 TRAP 3: "UTP provides better EMI protection than STP" → FALSE!
   STP (Shielded) is better protected. UTP is MOST VULNERABLE.

🚨 TRAP 4: "Coaxial cable has zero EMI" → FALSE (nuanced)!
   Coaxial is BETTER than UTP but fiber has ZERO EMI susceptibility.

🚨 TRAP 5: "Infrared is used for long-distance communication" → FALSE!
   Infrared = SHORT RANGE only (remote controls).
   Long distance = Microwave/Satellite.

🚨 TRAP 6: "Microwaves can penetrate walls like radio waves" → FALSE!
   Microwaves = LINE-OF-SIGHT (blocked by obstacles).
   Radio waves = penetrate obstacles.

🚨 TRAP 7: "Private key should be shared publicly" → FALSE!
   Private key is NEVER shared — kept SECRET by the owner/receiver.
   PUBLIC key is shared openly.

🚨 TRAP 8: "Symmetric encryption is slower than asymmetric" → FALSE!
   Symmetric is FASTER. Asymmetric is SLOWER (mathematically complex).

🚨 TRAP 9: "Sniffing is most effective on switch-based networks" → FALSE!
   Sniffing is most effective on HUB networks (hub broadcasts to all).
   Switch-based networks PREVENT/REDUCE sniffing.

🚨 TRAP 10: "AES is an asymmetric algorithm" → FALSE!
   AES = symmetric. RSA = asymmetric.

🚨 TRAP 11: "Public key encrypts → Public key decrypts" → FALSE!
   Public key encrypts → PRIVATE key decrypts (opposite key pair!)

🚨 TRAP 12: "Coaxial cable is used in modern office LANs" → FALSE (largely)!
   Modern LANs use Twisted Pair (Cat5e/Cat6).
   Coaxial mainly used for cable TV/cable internet today.
```

---

# PART 2: GENERAL STUDIES
## 🌾 Bihar GK — Agriculture, Major Crops & Production Districts

---

## 🔷 SECTION 1: Bihar — Agricultural Overview

```
BIHAR = One of India's most agriculture-dependent states

KEY AGRICULTURAL FACTS:
  → About 76-80% of Bihar's population depends on agriculture
  → Agriculture contributes ~18-20% to Bihar's GSDP
  → Bihar = GANGETIC PLAIN (highly fertile alluvial soil)
  → TWO MAIN CROP SEASONS:
    KHARIF: Sown in monsoon (June-July), harvested Sept-Oct
            → Paddy (Rice), Maize, Jute, Sugarcane
    RABI:   Sown in winter (Oct-Nov), harvested March-April
            → Wheat, Mustard, Potato, Peas, Gram

MAJOR RIVERS PROVIDING IRRIGATION:
  → Ganga (main river — central Bihar)
  → Gandak (west Bihar)
  → Kosi (north-east Bihar — "Bihar's sorrow" but also fertile)
  → Sone (south Bihar — major irrigation)
  → Bagmati, Kamla, Burhi Gandak (north Bihar)

SOIL TYPES:
  → Alluvial soil (most of Bihar) — highly fertile
  → Old alluvium (Bhangar) and new alluvium (Khadar)
  → Sandy loam in North Bihar
  → Clay-loam in South Bihar

🎯 PYQ FACT: Kosi River = "Bihar's Sorrow" (causes frequent floods)
🎯 PYQ FACT: Ganga divides Bihar into North Bihar and South Bihar
```

---

## 🔷 SECTION 2: Major Crops of Bihar — District-wise Mapping

### PADDY (Rice) — Kharif Crop:
```
BIHAR'S POSITION: Bihar is a MAJOR rice producing state of India

MAJOR RICE PRODUCING DISTRICTS:
  → ROHTAS DISTRICT — Highest rice producing district in Bihar!
  → Nalanda, Patna, Gaya, Aurangabad (South Bihar — fertile land)
  → North Bihar: Muzaffarpur, Samastipur, Darbhanga, East Champaran

SPECIAL VARIETY:
  → Sathi Rice: A special quick-growing variety of Bihar
  → Katarni Rice: Famous aromatic variety of Munger/Bhagalpur area
    (Katarni rice has GI (Geographical Indication) tag!)

🎯 PYQ FACT: Rohtas = highest paddy/rice production in Bihar
🎯 PYQ FACT: Katarni rice = GI-tagged product from Bihar (Munger/Bhagalpur)
```

### WHEAT — Rabi Crop:
```
MAJOR WHEAT PRODUCING DISTRICTS:
  → ROHTAS — Highest wheat producing district (also top in rice!)
  → West Champaran, East Champaran
  → Siwan, Saran
  → Muzaffarpur, Darbhanga
  → Nalanda, Patna, Bhojpur, Buxar

SIGNIFICANCE: Bihar's Rohtas district = top producer of BOTH wheat AND rice!

🎯 PYQ FACT: Rohtas = highest wheat production in Bihar
🎯 PYQ FACT: Bihar wheat production concentrated in Gangetic plains (fertile alluvial soil)
```

### MAIZE — Kharif Crop:
```
BIHAR = LARGEST MAIZE PRODUCING STATE IN INDIA!

MAJOR DISTRICTS:
  → KOSI ZONE: Supaul, Saharsa, Madhepura, Khagaria
  → Muzaffarpur, Vaishali, Saran
  → East Champaran, West Champaran (North Bihar)

WHY NORTH BIHAR FOR MAIZE?
  → Sandy loam soil of North Bihar = ideal for maize
  → Kosi river floods deposit fresh alluvium each year = very fertile
  → Bihar produces about 10-12% of India's total maize

USE OF MAIZE IN BIHAR:
  → Cattle feed (major use)
  → Corn flour, popcorn (food)
  → Ethanol production (biofuel)
  → Starch industry

🎯 PYQ FACT: Bihar = LARGEST maize producing state in India (very important!)
🎯 PYQ FACT: Maize concentration = Kosi zone and North Bihar districts
```

### SUGARCANE — Kharif/Year-round Crop:
```
MAJOR DISTRICTS:
  → WEST CHAMPARAN — highest sugarcane production in Bihar
  → East Champaran
  → Saran, Siwan, Gopalganj
  → Muzaffarpur, Vaishali

SUGAR MILLS IN BIHAR:
  → Motihari Sugar Mill (East Champaran)
  → Sugauli Sugar Mill (East Champaran)
  → Harinagar Sugar Mill (West Champaran)
  → Gopalganj Sugar Mill

HISTORICAL NOTE:
  → Champaran region = associated with INDIGO cultivation during British era
  → Gandhi's Champaran Satyagraha (1917) was AGAINST forced indigo cultivation!
  → After independence, indigo replaced by sugarcane (more profitable)

🎯 PYQ FACT: West Champaran = highest sugarcane in Bihar
🎯 PYQ FACT: Champaran region = historically associated with indigo (British era)
```

### VEGETABLES — Bihar's Market Garden:
```
BIHAR = MAJOR VEGETABLE PRODUCING STATE IN INDIA

IMPORTANT VEGETABLE-DISTRICT LINKS:
  → POTATO: Nalanda district (Naubatpur, Ekangarsarai areas)
            Bihar's potato is exported to other states!
  → ONION: Nalanda, Patna
  → LITCHI: MUZAFFARPUR — Bihar produces 70-75% of India's litchi!
            Muzaffarpur's Shahi Litchi has GI (Geographical Indication) tag
  → MANGO: Darbhanga (Chausa, Malda, Langra varieties)
  → BANANA: Hajipur (Vaishali) — famous for banana production

MUSHROOM:
  → Bihar is a major mushroom producer
  → Samastipur district = major mushroom cultivation centre

🎯 PYQ FACT: Muzaffarpur = litchi capital of Bihar (70-75% of India's litchi production!)
🎯 PYQ FACT: Shahi Litchi of Muzaffarpur = GI-tagged product
🎯 PYQ FACT: Nalanda = potato production hub in Bihar
🎯 PYQ FACT: Hajipur/Vaishali = known for banana production
```

---

## 🔷 SECTION 3: Special Agricultural Products of Bihar

### SILK — Bhagalpur:
```
BHAGALPUR = INDIA'S SILK CITY

BHAGALPUR SILK (TUSSAR SILK):
  → Bhagalpur is famous for TUSSAR SILK (also called "Tussore" or "Kosa silk")
  → Made from silkworm cocoons of the TASSAR (Antheraea mylitta) species
  → Different from Mulberry silk (Bangalore) — Tussar is wilder, coarser
  → Bhagalpur Tussar Silk has GI (Geographical Indication) tag!

SILK SAREES:
  → Bhagalpuri sarees are famous worldwide for their texture and pattern
  → Also called "Resham" production area (Resham = silk in Hindi/Urdu)

GOVERNMENT SUPPORT:
  → Central Silk Board has offices in Bhagalpur
  → "Silk Cluster" development under central schemes

🎯 PYQ FACT: Bhagalpur = SILK city of Bihar (Tussar silk)
🎯 PYQ FACT: Bhagalpuri Tussar Silk = GI-tagged product
🎯 PYQ FACT: Bhagalpur = known as "Silk City" (Resham Nagar)
```

### MAKHANA (Fox Nuts / Lotus Seeds):
```
MAKHANA = BIHAR'S UNIQUE PRODUCT

MAKHANA = Dried seeds of the prickly water lily (Euryale ferox)
         = Also called "Fox Nuts" or "Lotus Seeds"
         
SIGNIFICANCE:
  → Bihar produces ~80-90% of India's total makhana!
  → And India produces ~90% of the WORLD's makhana!
  → Bihar = the MAKHANA capital of the world effectively!
  
MAJOR PRODUCING DISTRICT: DARBHANGA (highest)
  Other districts: Sitamarhi, Madhubani, Saharsa, Supaul, Kishanganj

CULTIVATION:
  → Grown in ponds and marshy areas of North Bihar
  → Harvested manually (farmers dive into ponds!)
  → Processed by heating seeds in hot sand/pan → "pops" like popcorn
  → Traditional cottage industry employing thousands in Mithila region

GI TAG: Mithila Makhana received GI tag in 2022!

USES:
  → Consumed as snack (roasted makhana increasingly popular)
  → Used in Indian sweets (kheer, raita)
  → High protein, low calorie — health food trend
  → Growing export market

🎯 PYQ FACT: Bihar = ~90% of India's makhana production!
🎯 PYQ FACT: Darbhanga = highest makhana producing district
🎯 PYQ FACT: Mithila Makhana = GI-tagged (2022)
🎯 PYQ FACT: Makhana = Fox Nuts / Lotus Seeds (not lotus flowers!)
```

### MITHILA PAINTING:
```
Note: While not a crop, Mithila/Madhubani Painting is a famous GI-tagged product
of Bihar worth knowing for agriculture/culture sections.

MADHUBANI PAINTING:
  → Traditional art form from Mithila region (Madhubani, Darbhanga)
  → GI-tagged product of Bihar
  → Made with natural dyes (turmeric, neem, indigo, flowers)
  → Traditionally painted by women on walls, cloth, paper
  → UNESCO Recognition: Listed as intangible cultural heritage

🎯 PYQ FACT: Madhubani Painting = from Mithila region, Bihar = GI-tagged
```

---

## 🔷 SECTION 4: Bihar GI-Tagged Products — Quick Reference

```
GI TAG = Geographical Indication tag: product is specific to a region
         (like Darjeeling Tea, Basmati Rice have GI tags)

BIHAR'S KEY GI-TAGGED PRODUCTS:
┌─────────────────────────────────┬──────────────────────────────┐
│         PRODUCT                 │         DISTRICT/REGION      │
├─────────────────────────────────┼──────────────────────────────┤
│ Shahi Litchi                    │ Muzaffarpur                  │
├─────────────────────────────────┼──────────────────────────────┤
│ Bhagalpuri Tussar Silk          │ Bhagalpur                    │
├─────────────────────────────────┼──────────────────────────────┤
│ Katarni Rice                    │ Bhagalpur/Munger             │
├─────────────────────────────────┼──────────────────────────────┤
│ Mithila Makhana                 │ Darbhanga/Mithila region     │
├─────────────────────────────────┼──────────────────────────────┤
│ Madhubani Painting              │ Madhubani/Mithila region     │
├─────────────────────────────────┼──────────────────────────────┤
│ Magahi Paan                     │ Aurangabad, Nalanda, Gaya    │
├─────────────────────────────────┼──────────────────────────────┤
│ Shahi Litchi of Muzaffarpur     │ Muzaffarpur                  │
└─────────────────────────────────┴──────────────────────────────┘

MAGAHI PAAN:
  → A special variety of betel leaf from Magahi region (Aurangabad, Gaya, Nalanda)
  → Known for its soft texture and distinctive taste
  → GI-tagged — can only be sold as "Magahi Paan" if from this region

🎯 PYQ FACT: Bihar has multiple GI-tagged products — Litchi (Muzaffarpur),
             Silk (Bhagalpur), Rice (Katarni/Bhagalpur), Makhana (Darbhanga),
             Madhubani Painting, Magahi Paan
```

---

## 🔷 SECTION 5: Bihar Agriculture — District-Crop Quick Reference

```
DISTRICT → FAMOUS CROP/PRODUCT (Most Tested):
┌───────────────────────────┬──────────────────────────────────────────────────┐
│       DISTRICT            │              FAMOUS FOR                          │
├───────────────────────────┼──────────────────────────────────────────────────┤
│ ROHTAS                    │ Highest paddy (rice) AND wheat production         │
├───────────────────────────┼──────────────────────────────────────────────────┤
│ MUZAFFARPUR               │ LITCHI (70-75% of India's litchi)! + Maize       │
├───────────────────────────┼──────────────────────────────────────────────────┤
│ BHAGALPUR                 │ SILK (Tussar silk) + Katarni Rice                │
├───────────────────────────┼──────────────────────────────────────────────────┤
│ DARBHANGA                 │ MAKHANA (highest) + Mango                        │
├───────────────────────────┼──────────────────────────────────────────────────┤
│ WEST CHAMPARAN            │ SUGARCANE (highest) + Sugar mills                │
├───────────────────────────┼──────────────────────────────────────────────────┤
│ NALANDA                   │ POTATO + Vegetables + Wheat + Rice               │
├───────────────────────────┼──────────────────────────────────────────────────┤
│ VAISHALI / HAJIPUR        │ BANANA + Vegetables                              │
├───────────────────────────┼──────────────────────────────────────────────────┤
│ KOSI ZONE (Supaul etc.)   │ MAIZE (Bihar = India's largest maize producer)  │
├───────────────────────────┼──────────────────────────────────────────────────┤
│ MADHUBANI                 │ MADHUBANI PAINTING + Makhana                    │
├───────────────────────────┼──────────────────────────────────────────────────┤
│ AURANGABAD / GAYA / NALANDA│ MAGAHI PAAN                                    │
├───────────────────────────┼──────────────────────────────────────────────────┤
│ SAMASTIPUR                │ MUSHROOM + Maize                                 │
├───────────────────────────┼──────────────────────────────────────────────────┤
│ EAST/WEST CHAMPARAN       │ SUGARCANE + Historical indigo association        │
└───────────────────────────┴──────────────────────────────────────────────────┘

🧠 MEMORY TRICKS:
  "Rohtas Rules Rice and wheat" (R = Rohtas, R = Rice, W = wheat)
  "Muzaffarpur Makes Millions from Litchi" (M = Muzaffarpur, L = Litchi)
  "Bhagalpur Builds Beautiful Silk" (B = Bhagalpur, S = Silk)
  "Darbhanga Dries Delicious Makhana" (D = Darbhanga, M = Makhana)
  "Champaran Cultivates lots of Cane" (C = Champaran, C = Cane/Sugarcane)
```

---

## 🔷 SECTION 6: Bihar Agriculture — PYQ Traps

```
🚨 TRAP 1: "Muzaffarpur is known for silk production" → FALSE!
   Muzaffarpur = LITCHI (not silk).
   Silk = BHAGALPUR (Tussar silk).

🚨 TRAP 2: "Bihar is not significant in national maize production" → FALSE!
   Bihar = LARGEST maize producing state in India!

🚨 TRAP 3: "Darbhanga is known for litchi" → FALSE!
   Litchi = MUZAFFARPUR.
   Darbhanga = MAKHANA (and also mango).

🚨 TRAP 4: "Makhana is a root vegetable grown in farms" → FALSE!
   Makhana = seeds of prickly water lily grown in PONDS and marshy areas.

🚨 TRAP 5: "Katarni rice is from Patna" → FALSE!
   Katarni Rice = from Bhagalpur/Munger area.
   Patna = known for paddy/wheat but not specifically Katarni variety.

🚨 TRAP 6: "Rohtas district is only famous for wheat" → FALSE!
   Rohtas = famous for BOTH highest paddy (rice) AND highest wheat in Bihar!

🚨 TRAP 7: "GI tag for Shahi Litchi belongs to Darbhanga" → FALSE!
   Shahi Litchi GI tag = Muzaffarpur (not Darbhanga).

🚨 TRAP 8: "Champaran is famous for cotton" → FALSE!
   Champaran = sugarcane (and historically associated with INDIGO under British).
   Cotton = more associated with Maharashtra/Gujarat, not Bihar.

🚨 TRAP 9: "Madhubani painting is from Patna" → FALSE!
   Madhubani Painting = from Madhubani/Mithila region (Darbhanga, Sitamarhi, Madhubani districts).

🚨 TRAP 10: "Bihar produces very little makhana" → FALSE!
   Bihar produces ~90% of India's makhana AND India produces ~90% of world's makhana.
   Bihar = MAKHANA CAPITAL of the world effectively!
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: Transmission Media, Network Security, Cryptography

---

**Q1.** Which transmission medium provides the HIGHEST data transmission speed and is immune to electromagnetic interference?
(A) Twisted Pair Cable (UTP)
(B) Coaxial Cable
(C) Optical Fiber
(D) More than one of the above
(E) None of the above

---

**Q2.** UTP (Unshielded Twisted Pair) cable is most susceptible to:
(A) Fire damage
(B) Electromagnetic Interference (EMI)
(C) Water damage
(D) More than one of the above
(E) None of the above

---

**Q3.** The MAIN advantage of STP (Shielded Twisted Pair) over UTP is:
(A) STP is cheaper than UTP
(B) STP provides better EMI protection due to the metal shield
(C) STP allows longer cable runs than UTP
(D) More than one of the above
(E) None of the above

---

**Q4.** Optical fiber uses which physical principle to guide light through the cable?
(A) Electromagnetic induction
(B) Total Internal Reflection (light bounces off cladding)
(C) Magnetic wave propagation
(D) More than one of the above
(E) None of the above

---

**Q5.** Which transmission medium is used in Cable TV distribution systems?
(A) Optical Fiber
(B) UTP (Twisted Pair)
(C) Coaxial Cable
(D) More than one of the above
(E) None of the above

---

**Q6.** Microwaves require which condition for successful communication?
(A) Buried underground cables for signal guidance
(B) Line-of-sight — transmitter and receiver must have clear visual alignment
(C) Water as a medium for signal propagation
(D) More than one of the above
(E) None of the above

---

**Q7.** Infrared transmission is BEST suited for:
(A) Long-distance intercontinental communication
(B) Remote controls and short-range communication (cannot penetrate walls)
(C) Broadcasting to millions of receivers simultaneously
(D) More than one of the above
(E) None of the above

---

**Q8.** Radio waves are DIFFERENT from microwaves in that radio waves:
(A) Require line-of-sight and cannot penetrate buildings
(B) Travel in only one direction (unidirectional)
(C) Are omnidirectional and can penetrate obstacles (walls, buildings)
(D) More than one of the above
(E) None of the above

---

**Q9.** Among the following, which ranks CORRECTLY from highest to lowest transmission speed?
(A) Coaxial Cable > Optical Fiber > Twisted Pair
(B) Twisted Pair > Coaxial > Optical Fiber
(C) Optical Fiber > Coaxial Cable > Twisted Pair
(D) More than one of the above
(E) None of the above

---

**Q10.** The CIA Triad in network security stands for:
(A) Central Intelligence Agency principles
(B) Confidentiality, Integrity, Availability
(C) Ciphertext, Identification, Authentication
(D) More than one of the above
(E) None of the above

---

**Q11.** A PACKET SNIFFER (network sniffer) is most effective and dangerous on which type of network?
(A) Switch-based networks (switch sends data only to intended recipient)
(B) Hub-based networks (hub broadcasts to ALL ports — sniffer sees everything)
(C) Fiber optic networks (light is easy to intercept)
(D) More than one of the above
(E) None of the above

---

**Q12.** Switching from a HUB-based network to a SWITCH-based network helps prevent/reduce:
(A) Physical cable damage
(B) IP address conflicts
(C) Packet sniffing / eavesdropping attacks
(D) More than one of the above
(E) None of the above

---

**Q13.** In SYMMETRIC KEY cryptography:
(A) Two different keys are used — one for encryption, another for decryption
(B) The same key is used for BOTH encryption and decryption
(C) The public key is used for decryption, private key for encryption
(D) More than one of the above
(E) None of the above

---

**Q14.** In ASYMMETRIC KEY cryptography, the PRIVATE KEY is:
(A) Shared publicly so anyone can encrypt messages to the owner
(B) Distributed to all network users for verification
(C) Kept SECRET by the receiver/owner — never shared
(D) More than one of the above
(E) None of the above

---

**Q15.** If Bob wants to send an encrypted message to Alice using asymmetric cryptography, Bob should encrypt the message with:
(A) Bob's own private key
(B) Alice's PUBLIC key (so only Alice with her private key can decrypt)
(C) A shared symmetric key
(D) More than one of the above
(E) None of the above

---

**Q16.** Which of the following is the correct speed comparison — SYMMETRIC vs ASYMMETRIC encryption?
(A) Asymmetric is faster than symmetric encryption
(B) Both are equally fast
(C) Symmetric is faster; Asymmetric is slower but more secure for key exchange
(D) More than one of the above
(E) None of the above

---

**Q17.** AES (Advanced Encryption Standard) is an example of:
(A) Asymmetric encryption algorithm
(B) Hashing algorithm
(C) Symmetric encryption algorithm
(D) More than one of the above
(E) None of the above

---

**Q18.** RSA is an example of:
(A) Symmetric encryption algorithm
(B) Hashing algorithm
(C) Asymmetric (public key) encryption algorithm
(D) More than one of the above
(E) None of the above

---

**Q19.** A DIGITAL SIGNATURE in cryptography is created using:
(A) The sender's PUBLIC key (anyone can verify)
(B) The sender's PRIVATE key (proves the sender's identity)
(C) A shared symmetric key
(D) More than one of the above
(E) None of the above

---

**Q20.** RANSOMWARE is a type of malware that:
(A) Secretly monitors and transmits user activity to an attacker
(B) Encrypts victim's files and demands payment for the decryption key
(C) Displays unwanted advertisements on the victim's computer
(D) More than one of the above
(E) None of the above

---

**Q21.** A WORM differs from a VIRUS in that:
(A) A worm attaches to files; a virus spreads independently
(B) A virus attaches to host files; a worm spreads independently through networks
(C) Both worm and virus are exactly the same type of malware
(D) More than one of the above
(E) None of the above

---

**Q22.** HTTPS uses which approach for encryption?
(A) Only symmetric encryption (AES) throughout the session
(B) Only asymmetric encryption (RSA) throughout the session
(C) Hybrid — asymmetric to exchange keys, then symmetric (AES) for data transfer
(D) More than one of the above
(E) None of the above

---

**Q23.** A FIREWALL primarily functions as:
(A) A device that amplifies network signals to extend cable distance
(B) A device that monitors and filters incoming/outgoing network traffic based on security rules
(C) A device that assigns IP addresses to network devices
(D) More than one of the above
(E) None of the above

---

**Q24.** BharatNet, India's rural broadband project, primarily uses which transmission medium?
(A) Coaxial cable (cable TV infrastructure)
(B) UTP twisted pair (telephone infrastructure)
(C) Optical fiber cables to gram panchayats
(D) More than one of the above
(E) None of the above

---

**Q25.** Consider these statements about transmission media and security:
I.   Optical fiber = highest speed + immune to EMI
II.  UTP = most vulnerable to EMI among wired media
III. Private key in asymmetric cryptography is shared publicly
IV.  Switch-based networks reduce the risk of packet sniffing

Which are CORRECT?
(A) I, II, and IV only
(B) I, II, III, and IV all correct
(C) I and IV only
(D) More than one of the above
(E) None of the above

---

## 📝 GENERAL STUDIES — 25 MCQs
### Topics: Bihar Agriculture — Crops, Districts, GI-tagged Products

---

**Q26.** Which district of Bihar is the HIGHEST producer of PADDY (rice)?
(A) Nalanda
(B) Muzaffarpur
(C) Rohtas
(D) More than one of the above
(E) None of the above

---

**Q27.** Bihar is the LARGEST producer of which crop in India?
(A) Wheat
(B) Rice
(C) Maize
(D) More than one of the above
(E) None of the above

---

**Q28.** Approximately what percentage of India's LITCHI production comes from Bihar (specifically Muzaffarpur)?
(A) 25–30%
(B) 40–50%
(C) 70–75%
(D) More than one of the above
(E) None of the above

---

**Q29.** Which district is famous for SILK (Tussar silk) production in Bihar?
(A) Darbhanga
(B) Muzaffarpur
(C) Bhagalpur
(D) More than one of the above
(E) None of the above

---

**Q30.** Bhagalpur is known as:
(A) The Rice Bowl of Bihar
(B) Silk City (Resham Nagar) of Bihar
(C) The Sugar City of Bihar
(D) More than one of the above
(E) None of the above

---

**Q31.** MAKHANA (Fox Nuts) production in Bihar is concentrated in which district?
(A) Rohtas
(B) Bhagalpur
(C) Darbhanga
(D) More than one of the above
(E) None of the above

---

**Q32.** Bihar accounts for approximately what share of India's total MAKHANA production?
(A) 30–40%
(B) 50–60%
(C) 80–90%
(D) More than one of the above
(E) None of the above

---

**Q33.** Which GI-tagged rice variety is associated with Bhagalpur/Munger region of Bihar?
(A) Basmati Rice
(B) Katarni Rice
(C) Sona Masuri Rice
(D) More than one of the above
(E) None of the above

---

**Q34.** The GI tag for Mithila Makhana was granted in:
(A) 2015
(B) 2019
(C) 2022
(D) More than one of the above
(E) None of the above

---

**Q35.** MAGAHI PAAN (betel leaf with GI tag) is produced in which region of Bihar?
(A) Bhojpur and Saran districts
(B) Aurangabad, Nalanda, and Gaya districts
(C) Champaran and Sitamarhi districts
(D) More than one of the above
(E) None of the above

---

**Q36.** SUGARCANE production in Bihar is highest in which district?
(A) Rohtas
(B) West Champaran
(C) Darbhanga
(D) More than one of the above
(E) None of the above

---

**Q37.** The Champaran region's historical association with which crop led to Gandhi's first Satyagraha in India (1917)?
(A) Sugarcane
(B) Paddy
(C) Indigo
(D) More than one of the above
(E) None of the above

---

**Q38.** HAJIPUR (Vaishali district) in Bihar is famous for the production of:
(A) Makhana
(B) Silk
(C) Banana
(D) More than one of the above
(E) None of the above

---

**Q39.** Nalanda district of Bihar is a major producer of:
(A) Litchi and banana
(B) Potato and vegetables
(C) Tussar silk and makhana
(D) More than one of the above
(E) None of the above

---

**Q40.** The KOSI zone of Bihar (Supaul, Saharsa, Madhepura) is known for the production of:
(A) Litchi
(B) Maize
(C) Silk
(D) More than one of the above
(E) None of the above

---

**Q41.** Madhubani Painting, a GI-tagged product of Bihar, originates from which region?
(A) Magadh region (Gaya, Nalanda)
(B) Mithila region (Madhubani, Darbhanga, Sitamarhi)
(C) Bhojpur region (Bhojpur, Rohtas)
(D) More than one of the above
(E) None of the above

---

**Q42.** The Shahi Litchi from Muzaffarpur has received which certification?
(A) ISO certification
(B) Organic India certification
(C) GI (Geographical Indication) tag
(D) More than one of the above
(E) None of the above

---

**Q43.** MAIZE is a _____ crop in Bihar (sown and harvested timing):
(A) Rabi crop (sown winter, harvested spring)
(B) Kharif crop (sown monsoon, harvested autumn)
(C) Zaid crop (grown in summer between kharif and rabi)
(D) More than one of the above
(E) None of the above

---

**Q44.** The river KOSI is called "Bihar's Sorrow" because:
(A) It has very little water and causes drought conditions
(B) It causes frequent floods, bringing devastation to North Bihar
(C) It pollutes drinking water across Bihar
(D) More than one of the above
(E) None of the above

---

**Q45.** Which of the following correctly matches a district with its famous agricultural product?
(A) Muzaffarpur → Silk; Bhagalpur → Litchi
(B) Rohtas → Maize (highest); Darbhanga → Silk
(C) Muzaffarpur → Litchi; Bhagalpur → Silk (Tussar)
(D) More than one of the above
(E) None of the above

---

**Q46.** SAMASTIPUR district of Bihar is particularly known for:
(A) Litchi cultivation
(B) Mushroom cultivation and maize
(C) Silk weaving
(D) More than one of the above
(E) None of the above

---

**Q47.** Bihar's agricultural productivity benefits primarily from which TYPE of soil?
(A) Red laterite soil (iron-rich, acidic)
(B) Black cotton soil (regur soil)
(C) Alluvial soil (highly fertile, deposited by rivers)
(D) More than one of the above
(E) None of the above

---

**Q48.** Which crop is primarily grown in North Bihar (Sandy loam soil, Kosi zone)?
(A) Sugarcane
(B) Potato
(C) Maize
(D) More than one of the above
(E) None of the above

---

**Q49.** ROHTAS district of Bihar is exceptional in agriculture because:
(A) It has the highest litchi and silk production in Bihar
(B) It is the highest producer of BOTH paddy (rice) AND wheat in Bihar
(C) It has the largest makhana ponds in Bihar
(D) More than one of the above
(E) None of the above

---

**Q50.** Consider these statements about Bihar agriculture:
I.  Bihar is the largest maize-producing state in India.
II. Muzaffarpur's Shahi Litchi has a GI tag.
III. Bhagalpur is famous for Tussar Silk production.
IV. Darbhanga is the largest litchi-producing district.

Which statements are CORRECT?
(A) I, II, and III only
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
| 1  | (C) | Fiber = highest speed + immune to EMI (uses light, not electricity) |
| 2  | (B) | UTP = most susceptible to EMI (no shielding) |
| 3  | (B) | STP = metal shield around pairs = better EMI protection |
| 4  | (B) | Fiber uses Total Internal Reflection — light bounces off cladding |
| 5  | (C) | Coaxial cable (RG-6) is standard for cable TV distribution |
| 6  | (B) | Microwaves = line-of-sight (obstacles block signal) |
| 7  | (B) | Infrared = short range, cannot penetrate walls; used in remote controls |
| 8  | (C) | Radio waves = omnidirectional, can penetrate obstacles |
| 9  | (C) | Speed: Optical Fiber > Coaxial > Twisted Pair |
| 10 | (B) | CIA = Confidentiality, Integrity, Availability (security triad) |
| 11 | (B) | Hub-based: hub broadcasts to ALL → sniffer on any port sees everything |
| 12 | (C) | Switch sends only to intended recipient → reduces sniffing risk |
| 13 | (B) | Symmetric = SAME key for encrypt + decrypt |
| 14 | (C) | Private key = NEVER shared, kept SECRET by owner/receiver |
| 15 | (B) | Encrypt with Alice's PUBLIC key → only Alice's private key can decrypt |
| 16 | (C) | Symmetric = faster; Asymmetric = slower but solves key distribution |
| 17 | (C) | AES = Advanced Encryption Standard = symmetric algorithm |
| 18 | (C) | RSA = Rivest-Shamir-Adleman = asymmetric (public key) algorithm |
| 19 | (B) | Digital signature = created with sender's PRIVATE key |
| 20 | (B) | Ransomware = encrypts files + demands ransom |
| 21 | (B) | Virus attaches to files; Worm spreads independently through network |
| 22 | (C) | HTTPS = hybrid: asymmetric for key exchange + symmetric (AES) for data |
| 23 | (B) | Firewall = monitors/filters traffic based on security rules |
| 24 | (C) | BharatNet = optical fiber to gram panchayats (rural broadband) |
| 25 | (A) | I correct (fiber=fastest+no EMI), II correct (UTP=most EMI), III WRONG (private key is NEVER shared), IV correct (switch reduces sniffing) |

---

### GS Answers (Q26–Q50):

| Q  | Ans | Key Reason |
|----|-----|-----------|
| 26 | (C) | Rohtas = highest paddy production in Bihar |
| 27 | (C) | Bihar = largest maize producing state in India |
| 28 | (C) | Muzaffarpur = 70-75% of India's litchi production |
| 29 | (C) | Bhagalpur = Silk City (Tussar silk production) |
| 30 | (B) | Bhagalpur = "Silk City" / Resham Nagar of Bihar |
| 31 | (C) | Darbhanga = highest makhana producing district |
| 32 | (C) | Bihar = 80-90% of India's makhana production |
| 33 | (B) | Katarni Rice = GI-tagged rice from Bhagalpur/Munger region |
| 34 | (C) | Mithila Makhana GI tag = granted in 2022 |
| 35 | (B) | Magahi Paan = Aurangabad, Nalanda, Gaya districts |
| 36 | (B) | West Champaran = highest sugarcane production in Bihar |
| 37 | (C) | Champaran Satyagraha (1917) = against forced INDIGO cultivation |
| 38 | (C) | Hajipur/Vaishali = famous for banana production |
| 39 | (B) | Nalanda = major potato and vegetable production hub |
| 40 | (B) | Kosi zone = maize (Bihar = India's largest maize producer) |
| 41 | (B) | Madhubani Painting = from Mithila region (Madhubani, Darbhanga) |
| 42 | (C) | Shahi Litchi = GI (Geographical Indication) tagged product |
| 43 | (B) | Maize = Kharif crop (sown monsoon, harvested autumn) |
| 44 | (B) | Kosi = "Bihar's Sorrow" for causing frequent devastating floods |
| 45 | (C) | Muzaffarpur → Litchi; Bhagalpur → Silk (Tussar) |
| 46 | (B) | Samastipur = mushroom cultivation and maize |
| 47 | (C) | Bihar's fertile agriculture = alluvial soil from river deposits |
| 48 | (C) | North Bihar / Kosi zone = maize (sandy loam soil) |
| 49 | (B) | Rohtas = highest in BOTH paddy AND wheat in Bihar |
| 50 | (A) | I correct (Bihar=largest maize), II correct (Shahi Litchi=GI), III correct (Bhagalpur=silk), IV WRONG (Litchi = Muzaffarpur, not Darbhanga) |

---

# 🔁 DAY 48 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — Transmission Media

### Guided Media Quick Reference:
```
MEDIUM          │ SPEED      │ EMI         │ DISTANCE    │ MAIN USE
────────────────┼────────────┼─────────────┼─────────────┼──────────────────
UTP (Cat5e/6)   │ 1-10 Gbps  │ HIGH risk   │ ~100m       │ Office/home LAN
STP             │ 1-10 Gbps  │ Low risk    │ ~100m       │ Industrial LAN
Coaxial         │ Few Gbps   │ Medium risk │ ~500m       │ Cable TV/internet
OPTICAL FIBER   │ Tbps!!     │ ZERO (light)│ Km-100s km  │ Backbone, FTTH

SPEED: Fiber >> Coaxial >> Twisted Pair
EMI VULNERABILITY: UTP (worst) > Coaxial > STP > Fiber (immune)
```

### Unguided Media Quick Reference:
```
Radio Waves: Omnidirectional, penetrates walls, Wi-Fi/Mobile/FM radio
Microwaves:  Line-of-sight, satellite/relay towers, long-distance
Infrared:    Short range, cannot penetrate walls, remote controls
```

### Cryptography Summary:
```
SYMMETRIC:    Same key → AES (fast, key distribution problem)
ASYMMETRIC:   Public + Private keys → RSA (slow, solves key distribution)

PRIVATE KEY:  NEVER shared → kept by RECEIVER/OWNER
PUBLIC KEY:   Shared freely → used to ENCRYPT messages TO the owner
DIGITAL SIG:  Created with PRIVATE key; verified with PUBLIC key
HTTPS:        Hybrid = asymmetric key exchange + symmetric data encryption
```

### PYQ Trap Quick List:
```
✅ Fiber = fastest + immune to EMI (NOT twisted pair!)
✅ UTP = MOST vulnerable to EMI
✅ Microwaves = LINE-OF-SIGHT (not omnidirectional like radio)
✅ Infrared = short range + no wall penetration
✅ Private key = NEVER shared (kept secret by receiver)
✅ AES = symmetric; RSA = asymmetric
✅ Hub networks = easy to sniff; Switch networks = reduces sniffing
✅ Worm = spreads independently; Virus = attaches to host files
```

---

## ⚡ RAPID FIRE — Bihar Agriculture

### Crop-District Key Pairs (Must Memorize):
```
Rohtas       → Rice (highest) + Wheat (highest) — BOTH in one district!
Muzaffarpur  → LITCHI (70-75% of India's litchi!)
Bhagalpur    → SILK (Tussar silk) + Katarni Rice (GI-tagged)
Darbhanga    → MAKHANA (highest) + Mango
W. Champaran → SUGARCANE (highest)
Nalanda      → POTATO + Vegetables
Hajipur      → BANANA
Kosi Zone    → MAIZE (Bihar = largest in India!)
Madhubani    → Madhubani Painting (GI-tagged)
Aurangabad/Gaya/Nalanda → Magahi Paan (GI-tagged)
```

### Bihar GI-Tagged Products:
```
Shahi Litchi     → Muzaffarpur
Tussar Silk      → Bhagalpur
Katarni Rice     → Bhagalpur/Munger
Mithila Makhana  → Darbhanga (GI: 2022)
Madhubani Painting → Mithila region
Magahi Paan      → Aurangabad/Gaya/Nalanda
```

### PYQ Trap Quick List:
```
✅ Bihar = LARGEST maize producer in India (not rice or wheat)
✅ Litchi = Muzaffarpur (NOT Darbhanga, NOT Bhagalpur)
✅ Silk = Bhagalpur (NOT Muzaffarpur)
✅ Makhana = Darbhanga (NOT Muzaffarpur, NOT Bhagalpur)
✅ Rohtas = both highest rice AND wheat (not just wheat)
✅ Champaran = indigo historically (not cotton; sugarcane today)
✅ Makhana = grown in PONDS (not farms/fields!)
✅ Bihar ≈ 90% of India's makhana production
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **Transmission Media**: Fiber = fastest + EMI immune (uses light); UTP = cheapest but most EMI vulnerable; Coaxial = Cable TV; Microwaves = line-of-sight; Infrared = short range + no wall penetration; Radio = omnidirectional.
2. **Cryptography**: Symmetric (same key, fast, AES) vs Asymmetric (public+private keys, slow, RSA); PRIVATE KEY = NEVER shared = kept by receiver; Digital signature = created with private, verified with public; HTTPS = hybrid approach.
3. **Network Security**: Sniffers most effective on HUB networks (broadcasts all); Switch-based networks REDUCE sniffing; CIA Triad = Confidentiality+Integrity+Availability; Ransomware = encrypts + demands ransom; Worm spreads independently; Virus attaches to files.
4. **Bihar Crop-District**: Rohtas = Rice+Wheat (highest both); Muzaffarpur = Litchi (70-75% India); Bhagalpur = Silk+Katarni Rice; Darbhanga = Makhana; W.Champaran = Sugarcane; Bihar = India's largest MAIZE producer.
5. **Bihar GI Tags**: Shahi Litchi (Muzaffarpur), Tussar Silk (Bhagalpur), Katarni Rice (Bhagalpur), Mithila Makhana 2022 (Darbhanga), Madhubani Painting (Mithila), Magahi Paan (Aurangabad/Gaya/Nalanda).

---

## 📅 DAY 49 PREVIEW — What's Coming Next:
**CS**: Computer Networks — Complete Revision: OSI Model, TCP/IP, IP Addressing, Protocols, Topologies, Devices, Security — Full Networks chapter summary + 50 mixed MCQs
**GS**: Indian Polity — Fundamental Rights (Articles 12–35): Right to Equality, Right to Freedom, Right Against Exploitation, Cultural & Educational Rights, Right to Constitutional Remedies (Article 32 — Writs)

---

*🚀 Day 48 of 170 — You're 28.2% through the journey. You've now completed the FULL Computer Networks section over Days 43-48! Transmission media and cryptography are two of the most direct fact-recall topics — the private key trap and the fiber speed fact appear in EVERY paper. For Bihar agriculture, the Muzaffarpur-Litchi and Bhagalpur-Silk pairs are the most commonly confused — burn them in today!*
