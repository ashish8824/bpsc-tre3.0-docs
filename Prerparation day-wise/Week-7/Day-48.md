# 📅 BPSC TRE 4.0 — DAY 48
## CS Topic: Transmission Media & Network Security / Cryptography
## GS Topic: Bihar GK — Agriculture (Silk, Paddy, Crops & Districts) + Indian Agriculture Basics
### 🎯 Target: 130+/150 | TOP 50 RANK

---

> **Topper Benchmark:** Transmission Media questions appear in every TRE paper — typically 2–3 questions.
> Optical Fiber superiority, asymmetric key cryptography (private key = RECEIVER), and sniffer prevention
> are the TOP 3 high-frequency CS traps in this topic.
> Bihar Agriculture GK is directly asked in BPSC — Silk (Bhagalpur), Paddy (Champaran, Rohtas),
> crop seasons (Kharif/Rabi), and Bihar's rank in production are guaranteed 3–4 GS marks.

---

## ⏰ TODAY'S STUDY SCHEDULE

| Slot | Duration | Activity |
|------|----------|----------|
| Morning | 1.5 hrs | CS: Transmission Media + Network Security + Cryptography |
| Afternoon | 1 hr | GS: Bihar Agriculture — crops, districts, silk, paddy |
| Evening | 1 hr | Solve all 50 MCQs (25 CS + 25 GS) |
| Night | 30 min | Write your 5-bullet summary for each section |

---

---

# 🖥️ PART A — COMPUTER SCIENCE
# TRANSMISSION MEDIA & NETWORK SECURITY / CRYPTOGRAPHY

---

## 🔑 WHY THIS TOPIC MATTERS FOR BPSC TRE 4.0

| Exam | Transmission Media / Security Questions |
|------|----------------------------------------|
| TRE 1.0 | 2 questions — Optical fiber, UTP interference |
| TRE 2.0 | 3 questions — Fiber speed, asymmetric key, sniffer |
| TRE 3.0 | 3 questions — Coaxial, private key receiver, integrity |
| **TRE 4.0 Expected** | **3–4 questions** |

---

## 📡 WHAT IS TRANSMISSION MEDIA?

**Transmission Media** = The physical path (channel) through which data/signals travel from sender to receiver in a network.

```
SENDER ──── [TRANSMISSION MEDIA] ──── RECEIVER
               (Physical path for
                data to travel)
```

### Two Major Categories:

```
┌─────────────────────────────────────────────────────────────┐
│              TRANSMISSION MEDIA                             │
├────────────────────────┬────────────────────────────────────┤
│   GUIDED (Wired)       │   UNGUIDED (Wireless)              │
│   Signal travels       │   Signal travels through           │
│   through a physical   │   air/space (no physical cable)    │
│   cable/conductor      │                                    │
├────────────────────────┼────────────────────────────────────┤
│ • Twisted Pair Cable   │ • Radio Waves                      │
│ • Coaxial Cable        │ • Microwaves                       │
│ • Optical Fiber Cable  │ • Infrared                         │
│                        │ • Satellite Communication          │
└────────────────────────┴────────────────────────────────────┘
```

---

## 🔵 GUIDED (WIRED) MEDIA — DETAILED

---

### 1. TWISTED PAIR CABLE

```
           TWISTED PAIR CABLE CROSS-SECTION

    ┌──────────────────────────────────────┐
    │  Outer Jacket (protective covering)  │
    │  ┌────────────────────────────────┐  │
    │  │   Wire pair twisted together   │  │
    │  │                                │  │
    │  │   ~~~wire A~~~                 │  │
    │  │      ~~~wire B~~~              │  │
    │  │   ~~~wire A~~~                 │  │
    │  │      ~~~wire B~~~              │  │
    │  │   (twisting reduces crosstalk) │  │
    │  └────────────────────────────────┘  │
    └──────────────────────────────────────┘
```

#### Two Types:

```
┌─────────────────────────────────────────────────────────────────┐
│ TYPE   │ FULL FORM                   │ KEY FEATURES             │
├─────────────────────────────────────────────────────────────────┤
│ UTP    │ Unshielded Twisted Pair     │ • NO metallic shielding  │
│        │                             │ • VULNERABLE to EM/      │
│        │                             │   electrical interference│
│        │                             │ • CHEAPEST cable         │
│        │                             │ • Most widely used       │
│        │                             │ • Used in telephone lines│
│        │                             │   and Ethernet LANs      │
│        │                             │ • Categories: Cat 3,5,6  │
├─────────────────────────────────────────────────────────────────┤
│ STP    │ Shielded Twisted Pair       │ • HAS metallic foil      │
│        │                             │   shielding              │
│        │                             │ • PROTECTED from EM      │
│        │                             │   interference           │
│        │                             │ • MORE expensive than UTP│
│        │                             │ • Heavier & bulkier      │
│        │                             │ • Used where interference│
│        │                             │   is a problem           │
└─────────────────────────────────────────────────────────────────┘
```

**🚨 KEY PYQ TRAP:** UTP is **vulnerable to electrical/electromagnetic interference** — this is the most tested fact about UTP!

**Crosstalk:** When signal from one wire bleeds into another wire. Twisting the wires reduces crosstalk.

---

### 2. COAXIAL CABLE

```
         COAXIAL CABLE CROSS-SECTION (Layers from inside out):

    ┌─────────────────────────────────────────────────┐
    │         Outer Plastic Jacket                    │
    │    ┌───────────────────────────────────┐        │
    │    │    Metallic Braid/Foil Shield      │        │
    │    │    ┌───────────────────────┐       │        │
    │    │    │   Insulating Layer    │       │        │
    │    │    │   ┌───────────┐       │       │        │
    │    │    │   │  CENTRAL  │       │       │        │
    │    │    │   │  COPPER   │       │       │        │
    │    │    │   │  CORE     │       │       │        │
    │    │    │   └───────────┘       │       │        │
    │    │    └───────────────────────┘       │        │
    │    └───────────────────────────────────┘        │
    └─────────────────────────────────────────────────┘
```

```
┌────────────────────────────────────────────────────────┐
│ Structure      │ Central conductor + insulating layer  │
│                │ + metallic braid + outer plastic      │
│ Speed          │ MODERATE (better than UTP)            │
│ Shielding      │ GOOD — metallic braid protects        │
│                │ against EM interference               │
│ Distance       │ Can cover longer distances than UTP   │
│ Used for       │ Cable TV (CATV), old Ethernet         │
│                │ (10Base2, 10Base5), Internet over     │
│                │ cable lines                           │
│ Cost           │ More expensive than UTP               │
└────────────────────────────────────────────────────────┘
```

---

### 3. ⭐ OPTICAL FIBER CABLE — THE GOLD STANDARD

```
        OPTICAL FIBER — HOW IT WORKS

    Light     ┌──────────────────────────────────┐   Light
    pulse ──> │  CLADDING (reflects light back)  │ ──> arrives
    (data)    │  ┌──────────────────────────┐    │   at receiver
              │  │  CORE (glass/plastic)    │    │
              │  │  ←── light bounces ──>   │    │
              │  │  ←── inside the core ──> │    │
              │  └──────────────────────────┘    │
              └──────────────────────────────────┘
                   TOTAL INTERNAL REFLECTION
                   (light stays inside core)
```

```
┌────────────────────────────────────────────────────────────┐
│ OPTICAL FIBER KEY FEATURES                                  │
├───────────────────────┬────────────────────────────────────┤
│ Speed                 │ HIGHEST of all transmission media  │
│                       │ (Light speed transmission)         │
│ EM Interference       │ IMMUNE / NOT affected              │
│                       │ (light doesn't react to EM fields) │
│ Bandwidth             │ HIGHEST bandwidth capacity         │
│ Distance              │ LONGEST distance without repeaters │
│ Security              │ VERY HIGH (very hard to tap)       │
│ Signal                │ Uses LIGHT (not electrical signal) │
│ Attenuation           │ VERY LOW (signal loss is minimal)  │
│ Cost                  │ EXPENSIVE (highest cost)           │
│ Installation          │ DIFFICULT (fragile, needs expert)  │
│ Weight                │ Lighter than copper cables         │
│ Cross-talk            │ NONE (uses light, not electricity) │
└───────────────────────┴────────────────────────────────────┘
```

#### Types of Optical Fiber:
```
┌───────────────────┬──────────────────────────────────────┐
│ Single-Mode Fiber │ Very thin core; one light path;      │
│ (SMF)             │ LONGER distances; used by ISPs/      │
│                   │ telecom backbone                     │
├───────────────────┼──────────────────────────────────────┤
│ Multi-Mode Fiber  │ Larger core; multiple light paths;   │
│ (MMF)             │ SHORTER distances; used in buildings │
│                   │ and campuses (LAN)                   │
└───────────────────┴──────────────────────────────────────┘
```

**🚨 TOP PYQ FACT — Memorize This:**
> **Optical Fiber = Highest Speed + Immune to Electromagnetic Interference**
> These two facts appear in EVERY BPSC TRE exam in some form!

---

### WIRED MEDIA MASTER COMPARISON TABLE

```
┌──────────────┬──────────┬──────────┬──────────┬──────────────┐
│ Feature      │ UTP      │ STP      │ Coaxial  │ Optical Fiber│
├──────────────┼──────────┼──────────┼──────────┼──────────────┤
│ Speed        │ Moderate │ Moderate │ Good     │ HIGHEST      │
│ Cost         │ LOWEST   │ Moderate │ Moderate │ HIGHEST      │
│ EM Immunity  │ LOWEST   │ Good     │ Good     │ COMPLETE     │
│ Distance     │ Short    │ Short    │ Moderate │ LONGEST      │
│ Bandwidth    │ Moderate │ Moderate │ Good     │ HIGHEST      │
│ Security     │ Low      │ Moderate │ Moderate │ HIGHEST      │
│ Installation │ Easy     │ Moderate │ Moderate │ DIFFICULT    │
│ Crosstalk    │ YES      │ Less     │ Very low │ NONE         │
│ Used for     │ LAN/Phone│ Industrial│ Cable TV │ Internet     │
│              │ networks │ areas    │ backbone │ backbone     │
└──────────────┴──────────┴──────────┴──────────┴──────────────┘
```

---

## 📻 UNGUIDED (WIRELESS) MEDIA

```
┌──────────────────────────────────────────────────────────────┐
│           WIRELESS TRANSMISSION TYPES                        │
├─────────────────┬──────────────────────────────────────────┐ │
│ TYPE            │ KEY FACTS                                │ │
├─────────────────┼──────────────────────────────────────────┤ │
│ Radio Waves     │ • Frequency: 3 kHz – 300 MHz             │ │
│                 │ • Omnidirectional (all directions)       │ │
│                 │ • Can penetrate walls                    │ │
│                 │ • Used: AM/FM radio, WiFi, Bluetooth     │ │
├─────────────────┼──────────────────────────────────────────┤ │
│ Microwaves      │ • Frequency: 300 MHz – 300 GHz           │ │
│                 │ • Line-of-sight (directional)            │ │
│                 │ • CANNOT penetrate walls/obstacles       │ │
│                 │ • Used: Mobile phones, satellite,        │ │
│                 │   radar, microwave ovens                 │ │
├─────────────────┼──────────────────────────────────────────┤ │
│ Infrared (IR)   │ • Short range (a few meters)             │ │
│                 │ • Line-of-sight required                 │ │
│                 │ • CANNOT penetrate walls                 │ │
│                 │ • Used: TV remote, IrDA port             │ │
│                 │ • Blocked by sunlight interference       │ │
├─────────────────┼──────────────────────────────────────────┤ │
│ Satellite       │ • Uses microwave frequencies             │ │
│                 │ • GEO, MEO, LEO orbits                   │ │
│                 │ • Used: GPS, weather, broadcasting       │ │
│                 │ • High propagation delay (GEO: ~270ms)  │ │
└─────────────────┴──────────────────────────────────────────┘ │
└──────────────────────────────────────────────────────────────┘
```

---

## 🔒 NETWORK SECURITY — COMPLETE GUIDE

---

### WHAT IS NETWORK SECURITY?

Network security = Protecting computer networks from **unauthorized access, attacks, data theft, or disruption**.

---

### 🕵️ SNIFFERS (PACKET SNIFFERS)

```
            SNIFFER ATTACK:
            
   PC1 ────────────── HUB ────────────── PC2
                       │
                      PC3 (ATTACKER)
                    (Sniffer running)

   In a Hub-based network: Hub broadcasts ALL data to ALL ports.
   PC3 (attacker) can capture ALL packets passing through.

   ┌────────────────────────────────────────────────┐
   │  SOLUTION: Use a SWITCHED network              │
   │                                                │
   │  PC1 ──── SWITCH ──── PC2                      │
   │             │                                  │
   │            PC3 (Attacker)                      │
   │                                                │
   │  Switch sends data ONLY to the intended device │
   │  PC3 cannot see data meant for PC1 or PC2      │
   └────────────────────────────────────────────────┘
```

**🚨 KEY PYQ FACT:** Sniffers (packet capture attacks) are prevented by using a **switched network**.
- A **Hub** network is vulnerable to sniffers (broadcasts to all)
- A **Switch** network prevents sniffing (sends only to destination)

---

### 🔐 CRYPTOGRAPHY — DETAILED

**Cryptography** = The science of protecting information by transforming it into an unreadable format (ciphertext) so that only authorized parties can read it.

```
PLAINTEXT ──[ENCRYPTION]──> CIPHERTEXT ──[DECRYPTION]──> PLAINTEXT
  (readable)                (unreadable)                  (readable)
```

#### Key Terms:
```
┌──────────────────┬─────────────────────────────────────────┐
│ Plaintext        │ Original readable message               │
│ Ciphertext       │ Encrypted (scrambled) message           │
│ Encryption       │ Converting plaintext → ciphertext       │
│ Decryption       │ Converting ciphertext → plaintext       │
│ Key              │ Secret value used for encryption/       │
│                  │ decryption                              │
│ Cipher           │ Algorithm used for encryption           │
└──────────────────┴─────────────────────────────────────────┘
```

---

### 🔑 SYMMETRIC KEY CRYPTOGRAPHY

```
┌─────────────────────────────────────────────────────────────┐
│            SYMMETRIC KEY CRYPTOGRAPHY                       │
│                                                             │
│    SENDER                              RECEIVER             │
│   ┌──────┐                            ┌──────────┐          │
│   │Plain │──[SAME KEY encrypts]──────>│Ciphertext│          │
│   │text  │                            │          │          │
│   └──────┘                            └──────┬───┘          │
│                                              │              │
│                                   [SAME KEY decrypts]       │
│                                              │              │
│                                         ┌───▼──┐            │
│                                         │Plain │            │
│                                         │text  │            │
│                                         └──────┘            │
│                                                             │
│   SAME KEY used for both encryption AND decryption          │
└─────────────────────────────────────────────────────────────┘
```

```
┌────────────────────────────────────────────────────────┐
│ SYMMETRIC KEY — KEY FEATURES                           │
├─────────────────────────────────────────────────────────┤
│ Keys used      │ SAME key for encryption & decryption  │
│ Speed          │ FASTER than asymmetric                 │
│ Key sharing    │ PROBLEM — both parties need same key   │
│                │ How to share key securely?             │
│ Security       │ Lower (if key is compromised, all      │
│                │ data is compromised)                   │
│ Examples       │ DES, 3DES, AES, Blowfish, RC4         │
│ Use case       │ Large data encryption (bulk data)      │
└────────────────────────────────────────────────────────┘
```

---

### 🗝️ ASYMMETRIC KEY CRYPTOGRAPHY (PUBLIC KEY CRYPTOGRAPHY)

```
┌─────────────────────────────────────────────────────────────┐
│         ASYMMETRIC KEY CRYPTOGRAPHY                         │
│                                                             │
│    SENDER                              RECEIVER             │
│   ┌──────┐                            ┌──────────┐          │
│   │Plain │──[Receiver's PUBLIC KEY]──>│Ciphertext│          │
│   │text  │   (used to ENCRYPT)        │          │          │
│   └──────┘                            └──────┬───┘          │
│                                              │              │
│                                  [Receiver's PRIVATE KEY]   │
│                                   (used to DECRYPT)         │
│                                              │              │
│                                         ┌───▼──┐            │
│                                         │Plain │            │
│                                         │text  │            │
│                                         └──────┘            │
│                                                             │
│   PUBLIC KEY  = shared openly (anyone can encrypt with it) │
│   PRIVATE KEY = kept SECRET by the RECEIVER only!          │
└─────────────────────────────────────────────────────────────┘
```

```
┌────────────────────────────────────────────────────────────┐
│ ASYMMETRIC KEY — KEY FEATURES                              │
├─────────────────────────────────────────────────────────────┤
│ Keys used      │ TWO different keys: Public + Private      │
│ Public key     │ Shared openly — used to ENCRYPT           │
│ Private key    │ Kept SECRET by RECEIVER — used to         │
│                │ DECRYPT                                   │
│ Speed          │ SLOWER than symmetric                     │
│ Key sharing    │ NO problem — public key can be shared     │
│                │ openly; private key never shared          │
│ Security       │ HIGHER (private key never transmitted)    │
│ Examples       │ RSA, DSA, ECC, Diffie-Hellman             │
│ Use case       │ Digital signatures, key exchange,         │
│                │ HTTPS certificates                        │
└────────────────────────────────────────────────────────────┘
```

**🚨 #1 PYQ TRAP — Memorize This Exactly:**
> **In asymmetric key cryptography, the PRIVATE KEY is kept by the RECEIVER (not the sender).**
> The sender uses the receiver's PUBLIC KEY to encrypt.
> The receiver uses their own PRIVATE KEY to decrypt.

---

### SYMMETRIC vs ASYMMETRIC — MASTER COMPARISON

```
┌───────────────────┬─────────────────────┬─────────────────────┐
│ Feature           │ Symmetric           │ Asymmetric           │
├───────────────────┼─────────────────────┼─────────────────────┤
│ Keys              │ SAME key            │ TWO different keys   │
│ Speed             │ FASTER              │ SLOWER               │
│ Key distribution  │ DIFFICULT (problem) │ EASY (public key     │
│                   │                     │ can be shared)       │
│ Security          │ Lower               │ HIGHER               │
│ Examples          │ AES, DES, RC4       │ RSA, DSA, ECC        │
│ Private key       │ N/A (same key)      │ Kept by RECEIVER     │
│ Public key        │ N/A (same key)      │ Shared openly        │
│ Used for          │ Bulk data           │ Key exchange,        │
│                   │ encryption          │ digital signatures   │
└───────────────────┴─────────────────────┴─────────────────────┘
```

---

### 🔏 DIGITAL SIGNATURE

```
┌─────────────────────────────────────────────────────────────┐
│              DIGITAL SIGNATURE PROCESS                      │
│                                                             │
│  SENDER signs with their OWN PRIVATE KEY                    │
│  RECEIVER verifies with SENDER'S PUBLIC KEY                 │
│                                                             │
│  (This is OPPOSITE to normal encryption!)                   │
│                                                             │
│  Purpose: Prove AUTHENTICITY and NON-REPUDIATION            │
│  (sender cannot deny having signed the document)           │
└─────────────────────────────────────────────────────────────┘
```

**Key Difference from normal encryption:**
- **Normal encryption:** Encrypt with receiver's PUBLIC key → Decrypt with receiver's PRIVATE key
- **Digital signature:** Sign with sender's PRIVATE key → Verify with sender's PUBLIC key

---

### 🛡️ TYPES OF NETWORK ATTACKS

```
┌──────────────────────────────────────────────────────────────┐
│ ATTACK TYPE      │ DESCRIPTION                              │
├──────────────────┼──────────────────────────────────────────┤
│ Eavesdropping    │ Passive attack; intercepting data        │
│ (Sniffing)       │ without altering it                      │
├──────────────────┼──────────────────────────────────────────┤
│ Man-in-the-      │ Attacker secretly intercepts AND relays  │
│ Middle (MITM)    │ communication between two parties        │
├──────────────────┼──────────────────────────────────────────┤
│ DoS / DDoS       │ Denial of Service — flood server with    │
│                  │ requests to make it unavailable          │
├──────────────────┼──────────────────────────────────────────┤
│ Phishing         │ Fake websites/emails to steal           │
│                  │ credentials                              │
├──────────────────┼──────────────────────────────────────────┤
│ Malware          │ Malicious software: virus, worm, trojan  │
│                  │ ransomware, spyware                      │
├──────────────────┼──────────────────────────────────────────┤
│ SQL Injection    │ Injecting malicious SQL into web forms   │
│                  │ to access/destroy database               │
├──────────────────┼──────────────────────────────────────────┤
│ Brute Force      │ Trying all possible passwords            │
├──────────────────┼──────────────────────────────────────────┤
│ Spoofing         │ Forging IP/MAC address to impersonate    │
└──────────────────┴──────────────────────────────────────────┘
```

---

### 🔥 FIREWALL

```
┌─────────────────────────────────────────────────────────────┐
│                    FIREWALL CONCEPT                         │
│                                                             │
│  INTERNET ──── [FIREWALL] ──── INTERNAL NETWORK            │
│                   │                                         │
│                   │ Firewall filters incoming/outgoing      │
│                   │ traffic based on RULES                  │
│                   │                                         │
│  ALLOWS: Legitimate traffic (approved by rules)            │
│  BLOCKS: Unauthorized/suspicious traffic                   │
│                                                             │
│  Types: Hardware Firewall, Software Firewall               │
└─────────────────────────────────────────────────────────────┘
```

---

### 🚨 SYSTEM INTEGRITY BREACH

**System Integrity** = Ensuring the system operates as intended without unauthorized modification.

**Examples of Integrity Breach (frequently asked in BPSC TRE):**
```
┌────────────────────────────────────────────────────────────┐
│ INTEGRITY BREACH EXAMPLES                                  │
├─────────────────────────────────────────────────────────────┤
│ 1. Giving FULL ACCESS RIGHTS to ALL users on a system     │
│ 2. Unauthorized modification of files/data                │
│ 3. Installing unauthorized software on a system           │
│ 4. Running unauthorized processes on a server             │
└─────────────────────────────────────────────────────────────┘
```

**🚨 KEY PYQ FACT:** "Providing full access rights to all users" = **System integrity breach** — this has appeared in TRE 3.0!

---

### 🔐 SSL / TLS

```
┌────────────────────────────────────────────────────────────┐
│ SSL  = Secure Sockets Layer (older, now deprecated)        │
│ TLS  = Transport Layer Security (modern replacement)       │
│                                                             │
│ Both are used to:                                          │
│ • Encrypt data between browser and web server             │
│ • Used in HTTPS (HTTP + SSL/TLS)                          │
│ • Certificate issued by Certificate Authority (CA)        │
│                                                             │
│ You can see: 🔒 padlock in browser = SSL/TLS active        │
└────────────────────────────────────────────────────────────┘
```

---

### 📊 SECURITY CONCEPTS SUMMARY TABLE

```
┌────────────────────┬─────────────────────────────────────────┐
│ Concept            │ Key Definition                          │
├────────────────────┼─────────────────────────────────────────┤
│ Confidentiality    │ Data only accessible by authorized users│
│ Integrity          │ Data not altered by unauthorized users  │
│ Availability       │ System accessible when needed          │
│ Authentication     │ Verifying identity of user/system      │
│ Non-repudiation    │ Sender cannot deny sending a message   │
│ Authorization      │ Granting appropriate access rights     │
└────────────────────┴─────────────────────────────────────────┘
```

*(CIA Triad = Confidentiality + Integrity + Availability)*

---

## ✅ CS CONCEPT SUMMARY — DAY 48

| # | Key Fact | Never Forget |
|---|----------|-------------|
| 1 | Optical Fiber = highest speed | Immune to electromagnetic interference |
| 2 | UTP = cheapest, most common | Vulnerable to EM/electrical interference |
| 3 | Coaxial = moderate speed | Good shielding (metallic braid) |
| 4 | Sniffers prevented by | Switched network (NOT hub-based) |
| 5 | Asymmetric crypto — private key | Kept by the RECEIVER (not sender!) |
| 6 | Asymmetric crypto — public key | Shared openly; used to ENCRYPT |
| 7 | Symmetric crypto | SAME key for both encryption & decryption |
| 8 | Full access rights to all users | = System integrity breach |
| 9 | Digital signature | Signed with sender's PRIVATE key |
| 10 | CIA Triad | Confidentiality + Integrity + Availability |

---

---

# 📚 PART B — GENERAL STUDIES (GS)
# BIHAR GK — AGRICULTURE: CROPS, DISTRICTS, SILK & PADDY

---

## 🔑 WHY THIS TOPIC MATTERS FOR BPSC TRE 4.0

Bihar Agriculture GK is a **high-frequency topic** in BPSC TRE. Questions cover:
- Which districts produce which crops
- Bihar's rank in national production
- Agricultural seasons (Kharif/Rabi/Zaid)
- Silk industry and Bhagalpur connection
- River-based agriculture and soil types in Bihar

Typically **4–5 questions** in GS from this area.

---

## 🌾 SECTION 1: AGRICULTURAL SEASONS IN INDIA

```
┌───────────────────────────────────────────────────────────────┐
│              THREE CROP SEASONS IN INDIA                      │
├─────────────┬──────────────┬────────────┬──────────────────── │
│ Season      │ Sowing Time  │ Harvest    │ Major Crops         │
├─────────────┼──────────────┼────────────┼─────────────────────┤
│ KHARIF      │ June–July    │ Sept–Oct   │ Rice (Paddy), Maize,│
│ (Autumn)    │ (Monsoon)    │            │ Cotton, Jowar,       │
│             │              │            │ Bajra, Groundnut,   │
│             │              │            │ Soybean, Jute       │
├─────────────┼──────────────┼────────────┼─────────────────────┤
│ RABI        │ Oct–Nov      │ March–Apr  │ Wheat, Barley,      │
│ (Spring)    │ (Winter)     │            │ Mustard, Gram       │
│             │              │            │ (Chickpea), Peas,   │
│             │              │            │ Linseed             │
├─────────────┼──────────────┼────────────┼─────────────────────┤
│ ZAID        │ March–April  │ June–July  │ Watermelon, Melon,  │
│ (Summer)    │ (between     │            │ Cucumber, Moong     │
│             │ Rabi & Kharif│            │ Dal (mung bean)     │
└─────────────┴──────────────┴────────────┴─────────────────────┘
```

**Memory Tricks:**
- **KHARIF** = "K" for Koyla (coal/dark) → Rainy/monsoon season → Rice, Cotton
- **RABI** = "R" for Rabi (spring) → Wheat, Mustard
- **ZAID** = Summer crops between the two main seasons

**🚨 EXAM TRAP:** Paddy (Rice) = **KHARIF** crop. Wheat = **RABI** crop. Never swap these!

---

## 🌾 SECTION 2: BIHAR'S MAJOR CROPS — DISTRICT-WISE

---

### PADDY (RICE) IN BIHAR

```
┌─────────────────────────────────────────────────────────────┐
│ PADDY — KEY FACTS FOR BIHAR                                 │
├─────────────────────────────────────────────────────────────┤
│ Season          │ KHARIF (sown June-July; harvested Oct-Nov)│
│ Bihar's rank    │ Among top paddy-producing states in India │
│ Major districts │ West Champaran, East Champaran,           │
│                 │ Rohtas, Aurangabad, Bhojpur, Patna,       │
│                 │ Gaya, Nalanda, Saran                      │
│ Soil required   │ Clay soil (high water retention)          │
│ Water requirement│ HIGH — needs flooded fields              │
│ Bihar's paddy   │ Bihar contributes significantly to India's│
│ significance    │ rice bowl through Gangetic plains         │
└─────────────────────────────────────────────────────────────┘
```

**Key Paddy Districts of Bihar:**
```
NORTH BIHAR (Champaran region):
  West Champaran ──► Heavy paddy cultivation
  East Champaran ──► Known for rice + sugarcane

CENTRAL BIHAR:
  Patna ──► Mixed cultivation including paddy
  Nalanda, Gaya ──► Paddy + Wheat

SOUTH BIHAR (Magadh region):
  Rohtas ──► LARGEST wheat AND paddy producer in Bihar
  Aurangabad ──► Paddy cultivation
  Bhojpur ──► Agricultural hub
```

---

### WHEAT IN BIHAR

```
┌─────────────────────────────────────────────────────────────┐
│ WHEAT — KEY FACTS                                           │
├─────────────────────────────────────────────────────────────┤
│ Season          │ RABI (sown Oct-Nov; harvested March-April)│
│ Leading district│ ROHTAS (largest wheat producer in Bihar)  │
│ Other districts │ Bhojpur, Buxar, Kaimur, Patna, Aurangabad│
│ Soil required   │ Alluvial loam (well-drained fertile soil) │
└─────────────────────────────────────────────────────────────┘
```

**🚨 EXAM FACT:** **Rohtas district** = largest wheat + paddy producer in Bihar!

---

### MAIZE IN BIHAR

```
┌─────────────────────────────────────────────────────────────┐
│ MAIZE — KEY FACTS                                           │
├─────────────────────────────────────────────────────────────┤
│ Season          │ KHARIF (main season); also grown in Rabi  │
│ Bihar's rank    │ Bihar = LARGEST maize producer in India   │
│ Leading district│ Kaimur, Rohtas, Bhojpur, Buxar, Gaya     │
│ Special note    │ Bihar accounts for nearly 15-20% of       │
│                 │ India's total maize production            │
└─────────────────────────────────────────────────────────────┘
```

**🚨 VERY IMPORTANT:** Bihar is the **largest maize producer** in India — frequently tested!

---

### SUGARCANE IN BIHAR

```
┌─────────────────────────────────────────────────────────────┐
│ SUGARCANE — KEY FACTS                                       │
├─────────────────────────────────────────────────────────────┤
│ Season          │ Perennial crop (takes ~12 months)         │
│ Leading districts│ West Champaran, East Champaran,          │
│                 │ Saran, Sitamarhi, Muzaffarpur             │
│ Special note    │ Champaran is called the "Sugarcane Belt"  │
│                 │ of Bihar                                  │
│ Historical note │ Gandhi's Champaran Satyagraha (1917)      │
│                 │ was to free farmers from indigo farming   │
│                 │ and shift to better crops like sugarcane  │
└─────────────────────────────────────────────────────────────┘
```

---

### MAKHANA (FOX NUT / LOTUS SEED) — BIHAR'S UNIQUE CROP

```
┌─────────────────────────────────────────────────────────────┐
│ MAKHANA — KEY FACTS                                         │
├─────────────────────────────────────────────────────────────┤
│ What is it?     │ Aquatic plant seeds (Euryale ferox)       │
│                 │ grown in wetlands/ponds                   │
│ Bihar's rank    │ Bihar produces ~90% of world's Makhana!  │
│ Leading districts│ DARBHANGA, Madhubani, Saharsa,           │
│                 │ Supaul, Sitamarhi (North Bihar)           │
│ GI Tag          │ Mithila Makhana has received GI tag       │
│ Uses            │ Nutritious food, sold as "foxnut"         │
│                 │ or "lotus seeds" globally                 │
└─────────────────────────────────────────────────────────────┘
```

**🚨 EXAM FACT:** Bihar produces ~90% of world's Makhana. Darbhanga = Makhana capital of Bihar!

---

### LITCHI IN BIHAR

```
┌─────────────────────────────────────────────────────────────┐
│ LITCHI — KEY FACTS                                          │
├─────────────────────────────────────────────────────────────┤
│ Bihar's rank    │ Bihar = Largest Litchi producer in India  │
│ Leading district│ MUZAFFARPUR — "Litchi Capital of India"  │
│ Harvest time    │ May–June                                  │
│ GI Tag          │ Shahi Litchi of Muzaffarpur has GI tag    │
│ Export          │ Bihar exports litchi internationally      │
└─────────────────────────────────────────────────────────────┘
```

**🚨 EXAM FACT:** Muzaffarpur = "Litchi Capital of India" = largest litchi producer in India!

---

## 🐛 SECTION 3: SILK INDUSTRY IN BIHAR — BHAGALPUR

```
┌─────────────────────────────────────────────────────────────┐
│              SILK — BHAGALPUR (THE SILK CITY)               │
├─────────────────────────────────────────────────────────────┤
│ District        │ Bhagalpur                                 │
│ Nickname        │ "Silk City of India"                      │
│                 │ Also: "Manchester of the East" (textiles) │
│ Famous product  │ Tussar Silk (also called Bhagalpuri Silk  │
│                 │ or Tussah Silk)                           │
│ Type of silk    │ Tussar Silk — made from TUSSAR silkworms  │
│                 │ (not the common mulberry silkworm)        │
│ GI Tag          │ Bhagalpuri Silk / Tussar Silk has         │
│                 │ Geographical Indication tag               │
│ Bihar's rank    │ Bihar is a MAJOR Tussar Silk producer     │
│ Raw material    │ Arjuna, Sal, Saja trees (host plants for  │
│                 │ Tussar silkworms)                         │
└─────────────────────────────────────────────────────────────┘
```

### Types of Silk in India:
```
┌───────────────────┬────────────────────────────────────────┐
│ Type of Silk      │ Silkworm / State                       │
├───────────────────┼────────────────────────────────────────┤
│ Mulberry Silk     │ Bombyx mori silkworm; Karnataka, AP,   │
│                   │ W. Bengal (most common; 70% of India's) │
├───────────────────┼────────────────────────────────────────┤
│ Tussar Silk       │ Antheraea mylitta; Jharkhand,          │
│ (Tussah)          │ Chhattisgarh, BIHAR (Bhagalpur)        │
├───────────────────┼────────────────────────────────────────┤
│ Eri Silk          │ Samia ricini; Assam, Meghalaya         │
│                   │ ("Ahimsa silk" — silkworm not killed)  │
├───────────────────┼────────────────────────────────────────┤
│ Muga Silk         │ Antheraea assamensis; Assam ONLY       │
│                   │ (most expensive; golden color)         │
└───────────────────┴────────────────────────────────────────┘
```

**🚨 EXAM TRAP:** Muga Silk = Assam ONLY (not Bihar). Tussar Silk = Bihar's specialty (Bhagalpur).

---

## 🌱 SECTION 4: SOIL TYPES IN BIHAR

```
┌──────────────────────────────────────────────────────────────┐
│ SOIL TYPE       │ REGION IN BIHAR       │ CROPS GROWN       │
├──────────────────────────────────────────────────────────────┤
│ Alluvial Soil   │ Entire Bihar          │ Wheat, Paddy,     │
│ (Most common)   │ (Gangetic plains)     │ Sugarcane, Maize  │
│                 │                       │                   │
│ Types:          │                       │                   │
│ • Khadar        │ Along riverbeds       │ Rabi + Kharif     │
│  (new alluvial) │ (flood plains)        │ both              │
│ • Bhangar       │ Away from rivers      │ Wheat mainly      │
│  (old alluvial) │ (elevated terraces)   │                   │
├──────────────────────────────────────────────────────────────┤
│ Sandy Soil      │ Chambal-type areas    │ Maize, Bajra      │
│                 │ of South Bihar        │                   │
├──────────────────────────────────────────────────────────────┤
│ Piedmont Soil   │ Foothills of          │ Jute, Sugarcane   │
│ (Terai)         │ Himalayas (Champaran, │                   │
│                 │ Sitamarhi)            │                   │
└──────────────────────────────────────────────────────────────┘
```

---

## 📊 SECTION 5: BIHAR AGRICULTURE — QUICK REFERENCE TABLE

```
┌──────────────────────────────────────────────────────────────────┐
│ CROP / PRODUCT  │ LEADING DISTRICT(S)        │ SPECIAL FACT     │
├──────────────────────────────────────────────────────────────────┤
│ Paddy (Rice)    │ Rohtas, W. Champaran,      │ Kharif crop      │
│                 │ E. Champaran               │                  │
├──────────────────────────────────────────────────────────────────┤
│ Wheat           │ Rohtas, Bhojpur, Buxar     │ Rabi crop;       │
│                 │                            │ Rohtas = largest │
├──────────────────────────────────────────────────────────────────┤
│ Maize           │ Kaimur, Rohtas, Bhojpur    │ Bihar = LARGEST  │
│                 │                            │ maize producer   │
│                 │                            │ IN INDIA         │
├──────────────────────────────────────────────────────────────────┤
│ Sugarcane       │ W. Champaran, E. Champaran │ Sugarcane Belt   │
│                 │ Saran, Muzaffarpur         │ of Bihar         │
├──────────────────────────────────────────────────────────────────┤
│ Makhana         │ Darbhanga, Madhubani,      │ Bihar = ~90% of  │
│                 │ Saharsa, Supaul            │ world production │
├──────────────────────────────────────────────────────────────────┤
│ Litchi          │ Muzaffarpur                │ Litchi Capital   │
│                 │                            │ of India         │
├──────────────────────────────────────────────────────────────────┤
│ Silk (Tussar)   │ Bhagalpur                  │ Silk City;       │
│                 │                            │ Tussar silk      │
├──────────────────────────────────────────────────────────────────┤
│ Jute            │ Kishanganj, Purnea,        │ Kharif crop;     │
│                 │ Katihar, Saharsa           │ "Golden Fibre"   │
├──────────────────────────────────────────────────────────────────┤
│ Vegetables      │ Nalanda, Vaishali          │ Nalanda = "Veg   │
│                 │                            │ Bowl" of Bihar   │
└──────────────────────────────────────────────────────────────────┘
```

---

## 🌿 SECTION 6: INDIA AGRICULTURE — QUICK FACTS (FOR COMPARISON)

```
┌────────────────────────────────────────────────────────────────┐
│ NATIONAL AGRICULTURE SUPERLATIVES                              │
├─────────────────────────────────────────────────────────────────┤
│ Largest rice producer in India   │ West Bengal                │
│ Largest wheat producer           │ Uttar Pradesh              │
│ Largest maize producer           │ BIHAR                      │
│ Largest sugarcane producer       │ Uttar Pradesh              │
│ Largest jute producer            │ West Bengal                │
│ Largest cotton producer          │ Gujarat                    │
│ Largest tea producer             │ Assam                      │
│ Largest coffee producer          │ Karnataka                  │
│ Largest rubber producer          │ Kerala                     │
│ Largest spices producer          │ Andhra Pradesh             │
│ Largest silk (Mulberry) producer │ Karnataka                  │
│ Largest litchi producer          │ Bihar (Muzaffarpur)        │
│ Largest Makhana producer         │ Bihar (Darbhanga)          │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🌾 SECTION 7: GREEN REVOLUTION & WHITE REVOLUTION

```
┌────────────────────────────────────────────────────────────────┐
│ REVOLUTION  │ FOCUS           │ KEY PERSONS                   │
├─────────────┼─────────────────┼───────────────────────────────┤
│ Green       │ Agriculture     │ Dr. M.S. Swaminathan (India)  │
│ Revolution  │ HYV seeds,      │ Norman Borlaug (Global)       │
│             │ fertilizers,    │ Took off in 1960s             │
│             │ irrigation      │ Punjab, Haryana main states   │
├─────────────┼─────────────────┼───────────────────────────────┤
│ White       │ Milk/Dairy      │ Dr. Verghese Kurien           │
│ Revolution  │ Operation Flood │ AMUL cooperative (Gujarat)    │
│             │ (Amul model)    │ India = world's largest milk  │
│             │                 │ producer                      │
├─────────────┼─────────────────┼───────────────────────────────┤
│ Blue        │ Fish/Aqua-      │ Hiralal Chaudhuri             │
│ Revolution  │ culture         │ India's fish production boost │
├─────────────┼─────────────────┼───────────────────────────────┤
│ Yellow      │ Oilseeds        │ Related to mustard/sunflower  │
│ Revolution  │                 │ production increase           │
└─────────────┴─────────────────┴───────────────────────────────┘
```

---

## 🚨 BPSC TOPPER TRAP CARD — GS AGRICULTURE

| Wrong Statement | Correct Answer |
|----------------|----------------|
| Wheat is a Kharif crop | ❌ WRONG — Wheat is RABI crop |
| Paddy is a Rabi crop | ❌ WRONG — Paddy is KHARIF crop |
| Muzaffarpur = Silk City | ❌ WRONG — Silk City = Bhagalpur |
| Bhagalpur produces Mulberry Silk | ❌ WRONG — Bhagalpur produces TUSSAR Silk |
| Bihar ranks lowest in Maize | ❌ WRONG — Bihar = LARGEST Maize producer in India |
| Makhana is from Bhagalpur | ❌ WRONG — Makhana is from Darbhanga/Madhubani area |
| Muga Silk is from Bihar | ❌ WRONG — Muga Silk is ONLY from Assam |
| Litchi capital = Patna | ❌ WRONG — Litchi capital = Muzaffarpur |
| Rohtas only produces wheat | ❌ WRONG — Rohtas produces BOTH wheat AND paddy |
| Father of Green Revolution (India) = Norman Borlaug | ❌ WRONG — India = M.S. Swaminathan; Borlaug = Global |

---

## ✅ GS CONCEPT SUMMARY — DAY 48

| # | Key Fact | District / Detail |
|---|----------|------------------|
| 1 | Paddy = Kharif crop | W. Champaran, Rohtas main districts |
| 2 | Wheat = Rabi crop | Rohtas = largest wheat producer Bihar |
| 3 | Maize | Bihar = LARGEST maize producer India |
| 4 | Sugarcane | W. Champaran & E. Champaran = sugarcane belt |
| 5 | Makhana | Darbhanga district; Bihar = ~90% world production |
| 6 | Litchi | Muzaffarpur = Litchi Capital of India |
| 7 | Silk | Bhagalpur = Silk City; Tussar silk (not Mulberry!) |
| 8 | Jute | Kishanganj, Purnea, Katihar (SE Bihar) |
| 9 | Green Revolution | M.S. Swaminathan (India); Borlaug (Global) |
| 10 | White Revolution | Dr. Verghese Kurien; Operation Flood; AMUL |

---

---

# 📝 PRACTICE QUESTIONS

> ⚠️ **INSTRUCTION:** Attempt ALL 50 questions BEFORE checking answers.
> The answer key is at the VERY END of this file.
> Cover the answers section with paper while solving.
> BPSC Five-Option Format: (A), (B), (C), (D) More than one of the above, (E) None of the above

---

## 🖥️ CS PRACTICE QUESTIONS (Q1–Q25)
### Topic: Transmission Media & Network Security / Cryptography

---

**Q1.** Which of the following transmission media offers the HIGHEST data transmission speed?

(A) Coaxial Cable  
(B) UTP (Unshielded Twisted Pair)  
(C) Optical Fiber Cable  
(D) More than one of the above  
(E) None of the above  

---

**Q2.** Optical Fiber Cable is immune to which type of interference that affects copper cables?

(A) Gravitational interference  
(B) Electromagnetic (EM) / Electrical interference  
(C) Sound interference  
(D) More than one of the above  
(E) None of the above  

---

**Q3.** UTP (Unshielded Twisted Pair) cable is VULNERABLE to:

(A) Optical signal distortion  
(B) Electromagnetic and electrical interference  
(C) Water damage only  
(D) More than one of the above  
(E) None of the above  

---

**Q4.** The difference between UTP and STP cable is that STP has:

(A) More twisted wire pairs than UTP  
(B) A metallic foil or braid shielding to protect against EM interference  
(C) Higher data rate due to optical components  
(D) More than one of the above  
(E) None of the above  

---

**Q5.** Coaxial cable gets its name because:

(A) It contains two coaxial conductors — inner core and outer braid  
(B) It was co-invented by two scientists  
(C) It carries signals in coaxial (parallel) direction only  
(D) More than one of the above  
(E) None of the above  

---

**Q6.** Which wireless transmission method CANNOT penetrate walls and requires line-of-sight?

(A) Radio Waves  
(B) X-rays  
(C) Infrared and Microwaves  
(D) More than one of the above  
(E) None of the above  

---

**Q7.** Packet sniffing (eavesdropping on network traffic) can be PREVENTED by:

(A) Using a HUB instead of a switch  
(B) Increasing network bandwidth  
(C) Using a switched network instead of a hub-based network  
(D) More than one of the above  
(E) None of the above  

---

**Q8.** In ASYMMETRIC KEY CRYPTOGRAPHY, which key is used to ENCRYPT a message sent to a receiver?

(A) Sender's private key  
(B) Receiver's private key  
(C) Receiver's public key  
(D) More than one of the above  
(E) None of the above  

---

**Q9.** In ASYMMETRIC KEY CRYPTOGRAPHY, the PRIVATE KEY is kept by:

(A) The sender  
(B) A trusted third party  
(C) The receiver  
(D) More than one of the above  
(E) None of the above  

---

**Q10.** In SYMMETRIC KEY CRYPTOGRAPHY:

(A) Two different keys are used — one for encryption, one for decryption  
(B) The same key is used for both encryption and decryption  
(C) No key is required  
(D) More than one of the above  
(E) None of the above  

---

**Q11.** Which of the following is an example of SYMMETRIC KEY encryption algorithm?

(A) RSA  
(B) DSA  
(C) AES (Advanced Encryption Standard)  
(D) More than one of the above  
(E) None of the above  

---

**Q12.** Which of the following is an example of ASYMMETRIC KEY cryptography?

(A) AES  
(B) DES  
(C) RSA  
(D) More than one of the above  
(E) None of the above  

---

**Q13.** A DIGITAL SIGNATURE is created using:

(A) The receiver's private key  
(B) The sender's public key  
(C) The sender's private key  
(D) More than one of the above  
(E) None of the above  

---

**Q14.** Which of the following is an example of a SYSTEM INTEGRITY BREACH?

(A) Using encrypted communication on a public network  
(B) Allowing a user to access only the files they need  
(C) Providing full access rights to ALL users on a shared system  
(D) More than one of the above  
(E) None of the above  

---

**Q15.** SSL/TLS is used to:

(A) Assign IP addresses to devices on a network  
(B) Encrypt data between a web browser and a web server (used in HTTPS)  
(C) Route packets between different networks  
(D) More than one of the above  
(E) None of the above  

---

**Q16.** Which of the following correctly describes the CIA Triad in network security?

(A) Confidentiality, Integrity, Availability  
(B) Cryptography, Internet, Antivirus  
(C) Confidentiality, Integration, Authorization  
(D) More than one of the above  
(E) None of the above  

---

**Q17.** A FIREWALL is a security device that:

(A) Physically prevents people from entering a server room  
(B) Filters network traffic based on predefined rules to block unauthorized access  
(C) Encrypts all data passing through a network  
(D) More than one of the above  
(E) None of the above  

---

**Q18.** In optical fiber, data is transmitted using:

(A) Electrical impulses through copper wires  
(B) Radio waves through the atmosphere  
(C) Light pulses through a glass or plastic core  
(D) More than one of the above  
(E) None of the above  

---

**Q19.** Which of the following CORRECTLY states the advantage of Optical Fiber over Coaxial Cable?

(A) Optical fiber is cheaper than coaxial cable  
(B) Optical fiber is easier to install than coaxial  
(C) Optical fiber has higher bandwidth and is immune to EM interference  
(D) More than one of the above  
(E) None of the above  

---

**Q20.** In a DoS (Denial of Service) attack, the attacker aims to:

(A) Steal all files from the target's computer  
(B) Flood the target server with traffic to make it unavailable to legitimate users  
(C) Decrypt encrypted messages without the key  
(D) More than one of the above  
(E) None of the above  

---

**Q21.** Which of the following transmission media is MOST suited for long-distance high-speed backbone connections between cities?

(A) UTP cable  
(B) Coaxial cable  
(C) Optical fiber  
(D) More than one of the above  
(E) None of the above  

---

**Q22.** Non-repudiation in network security means:

(A) The data cannot be read by unauthorized users  
(B) The sender of a message cannot deny having sent it  
(C) The system cannot be shut down by external attacks  
(D) More than one of the above  
(E) None of the above  

---

**Q23.** Consider the following statements about Asymmetric Key Cryptography:
1. It uses two mathematically related keys — public and private.
2. The public key is used for encryption; the private key is used for decryption.
3. The private key is kept secret by the RECEIVER.
4. It is faster than symmetric key cryptography.

Which of the above statements are CORRECT?

(A) Only 1, 2, and 3  
(B) Only 1 and 4  
(C) All four statements  
(D) More than one of the above  
(E) None of the above  

---

**Q24.** Twisted pair cables reduce crosstalk by:

(A) Adding a metallic braid shield around each wire  
(B) Twisting two wires together — the twisting cancels out electromagnetic interference  
(C) Using optical material instead of copper  
(D) More than one of the above  
(E) None of the above  

---

**Q25.** A network sniffer captures data packets that travel through the network. Which statement about sniffers and security is CORRECT?

(A) Sniffers work best in switched networks because switches encrypt all packets  
(B) Sniffers are most effective in hub-based networks because hubs broadcast data to all ports  
(C) Sniffers can only work on optical fiber networks  
(D) More than one of the above  
(E) None of the above  

---

---

## 📚 GS PRACTICE QUESTIONS (Q26–Q50)
### Topic: Bihar Agriculture — Crops, Districts, Silk, Paddy + Indian Agriculture

---

**Q26.** Paddy (Rice) belongs to which agricultural season?

(A) Rabi  
(B) Zaid  
(C) Kharif  
(D) More than one of the above  
(E) None of the above  

---

**Q27.** Wheat is primarily grown in which agricultural season in India?

(A) Kharif  
(B) Zaid  
(C) Rabi  
(D) More than one of the above  
(E) None of the above  

---

**Q28.** Which district of Bihar is known as the "Silk City of India" for its Tussar Silk production?

(A) Muzaffarpur  
(B) Darbhanga  
(C) Bhagalpur  
(D) More than one of the above  
(E) None of the above  

---

**Q29.** The silk produced in Bhagalpur is primarily which type?

(A) Mulberry Silk  
(B) Muga Silk  
(C) Tussar Silk (Bhagalpuri Silk)  
(D) More than one of the above  
(E) None of the above  

---

**Q30.** Bihar holds which position in Maize production in India?

(A) Third-largest producer  
(B) Second-largest producer  
(C) Largest producer (first rank)  
(D) More than one of the above  
(E) None of the above  

---

**Q31.** Muzaffarpur district in Bihar is especially known for production of which fruit?

(A) Mango  
(B) Banana  
(C) Litchi  
(D) More than one of the above  
(E) None of the above  

---

**Q32.** Approximately what percentage of world's Makhana (Fox Nut/Lotus Seed) production comes from Bihar?

(A) About 30%  
(B) About 50%  
(C) About 90%  
(D) More than one of the above  
(E) None of the above  

---

**Q33.** Which district of Bihar is the main hub of Makhana production?

(A) Bhagalpur  
(B) Rohtas  
(C) Darbhanga  
(D) More than one of the above  
(E) None of the above  

---

**Q34.** The "Sugarcane Belt" of Bihar primarily consists of which districts?

(A) Gaya and Bodh Gaya  
(B) West Champaran and East Champaran  
(C) Patna and Nalanda  
(D) More than one of the above  
(E) None of the above  

---

**Q35.** Rohtas district of Bihar is especially known for being the largest producer of which crop in Bihar?

(A) Litchi and Makhana  
(B) Silk and Jute  
(C) Wheat and Paddy  
(D) More than one of the above  
(E) None of the above  

---

**Q36.** Muga Silk, which is the most expensive silk variety in India with a golden color, is produced exclusively in:

(A) Bihar (Bhagalpur)  
(B) Karnataka  
(C) Assam  
(D) More than one of the above  
(E) None of the above  

---

**Q37.** Jute is grown primarily in which part of Bihar?

(A) South Bihar — Gaya, Bodh Gaya  
(B) West Bihar — Rohtas, Bhojpur  
(C) North-East Bihar — Kishanganj, Purnea, Katihar  
(D) More than one of the above  
(E) None of the above  

---

**Q38.** Which agricultural season involves crops sown in June-July (during monsoon) and harvested in September-October?

(A) Rabi season  
(B) Zaid season  
(C) Kharif season  
(D) More than one of the above  
(E) None of the above  

---

**Q39.** The Zaid season crops in India include which of the following?

(A) Wheat, Barley, Mustard  
(B) Watermelon, Cucumber, Mung Bean  
(C) Rice, Cotton, Jute, Maize  
(D) More than one of the above  
(E) None of the above  

---

**Q40.** The "Father of Green Revolution in India" is:

(A) Norman Borlaug  
(B) M.S. Swaminathan  
(C) Verghese Kurien  
(D) More than one of the above  
(E) None of the above  

---

**Q41.** The White Revolution in India is associated with which product and person?

(A) Wheat production; M.S. Swaminathan  
(B) Milk/Dairy production; Dr. Verghese Kurien  
(C) Rice production; Norman Borlaug  
(D) More than one of the above  
(E) None of the above  

---

**Q42.** Which state is the LARGEST producer of rice (paddy) in India at the national level?

(A) Bihar  
(B) Uttar Pradesh  
(C) West Bengal  
(D) More than one of the above  
(E) None of the above  

---

**Q43.** Which state is the LARGEST producer of jute in India?

(A) Bihar  
(B) Assam  
(C) West Bengal  
(D) More than one of the above  
(E) None of the above  

---

**Q44.** Nalanda district in Bihar is known as the "Vegetable Bowl" of Bihar. Which crops dominate here?

(A) Wheat and Sugarcane  
(B) Vegetables (especially onion, potato, tomato)  
(C) Litchi and Mango  
(D) More than one of the above  
(E) None of the above  

---

**Q45.** The soil type most commonly found in Bihar (the Gangetic plains) is:

(A) Black (Regur) soil  
(B) Red Laterite soil  
(C) Alluvial soil  
(D) More than one of the above  
(E) None of the above  

---

**Q46.** Bhagalpuri Silk / Tussar Silk has received which protection from the Government of India?

(A) ISO Certification  
(B) Geographical Indication (GI) Tag  
(C) National Heritage Status  
(D) More than one of the above  
(E) None of the above  

---

**Q47.** The crop Makhana (Fox Nut) grown in Bihar is an aquatic plant seed. Its cultivation requires:

(A) Dry, arid land with minimal rainfall  
(B) Wetlands, ponds, and flooded areas (aquatic environment)  
(C) High-altitude mountainous terrain  
(D) More than one of the above  
(E) None of the above  

---

**Q48.** Which of the following CORRECTLY matches crops to their category?

1. Rice — Kharif ✓
2. Wheat — Rabi ✓
3. Cotton — Rabi ✗ (actually Kharif)
4. Mustard — Rabi ✓

(A) Only 1 and 2  
(B) Only 1, 2, and 4  
(C) All four  
(D) More than one of the above  
(E) None of the above  

---

**Q49.** Bihar is India's largest producer of which crop/product — making it especially important for national food security?

(A) Wheat  
(B) Rice  
(C) Maize  
(D) More than one of the above  
(E) None of the above  

---

**Q50.** Consider these statements about Bihar's agriculture:
1. Bhagalpur is called the Silk City of Bihar for Tussar Silk production.
2. Muzaffarpur is called the Litchi Capital of India.
3. Darbhanga is the main district for Makhana production.
4. Bihar is the largest maize producer in India.

Which of the above are CORRECT?

(A) Only 1 and 2  
(B) Only 1, 2, and 3  
(C) Only 1, 2, 3, and 4 — all are correct  
(D) More than one of the above  
(E) None of the above  

---

---

# 🔑 ANSWER KEY

> ✅ Attempt ALL 50 questions BEFORE checking here!
> Scoring Guide: 45–50 = Topper Level 🏆 | 38–44 = Strong | 30–37 = Needs Revision | Below 30 = Re-study Today

---

## CS ANSWERS (Q1–Q25)

| Q | Ans | Explanation |
|---|-----|-------------|
| Q1 | **(C)** | Optical Fiber has the HIGHEST data transmission speed of all media |
| Q2 | **(B)** | Optical fiber uses light (not electricity) — completely immune to EM interference |
| Q3 | **(B)** | UTP = Unshielded = NO metallic protection = vulnerable to EM/electrical interference |
| Q4 | **(B)** | STP = Shielded Twisted Pair — metallic foil/braid reduces EM interference |
| Q5 | **(A)** | Coaxial = central copper core + outer braid sharing same axis (co-axial) |
| Q6 | **(C)** | Infrared AND Microwaves both require line-of-sight and cannot penetrate walls |
| Q7 | **(C)** | Switched network prevents sniffing; switch sends data only to the intended device |
| Q8 | **(C)** | To send a message to a receiver, sender encrypts with receiver's PUBLIC key |
| Q9 | **(C)** | Private key is kept by the RECEIVER — used for decryption |
| Q10 | **(B)** | Symmetric key = SAME key for both encryption and decryption |
| Q11 | **(C)** | AES is symmetric; RSA and DSA are asymmetric |
| Q12 | **(C)** | RSA is asymmetric (public-private key pair); AES and DES are symmetric |
| Q13 | **(C)** | Digital signature = signed with SENDER'S private key (verified with sender's public key) |
| Q14 | **(C)** | Giving full access rights to ALL users = system integrity breach |
| Q15 | **(B)** | SSL/TLS encrypts communication between browser and server — powers HTTPS |
| Q16 | **(A)** | CIA Triad = Confidentiality + Integrity + Availability |
| Q17 | **(B)** | Firewall filters traffic based on rules — blocks unauthorized access |
| Q18 | **(C)** | Optical fiber transmits data as LIGHT pulses through glass/plastic core |
| Q19 | **(C)** | Optical fiber has far higher bandwidth AND immunity to EM interference vs coaxial |
| Q20 | **(B)** | DoS attack = flooding server with requests to deny service to legitimate users |
| Q21 | **(C)** | Optical fiber — highest speed, lowest attenuation — ideal for long-distance backbone |
| Q22 | **(B)** | Non-repudiation = sender CANNOT deny sending a message |
| Q23 | **(A)** | Statements 1, 2, 3 are correct; Statement 4 is WRONG — asymmetric is SLOWER |
| Q24 | **(B)** | Twisting wires together causes signals to cancel each other's EM interference |
| Q25 | **(B)** | Sniffers are most effective on hub networks (hubs broadcast to ALL ports) |

---

## GS ANSWERS (Q26–Q50)

| Q | Ans | Explanation |
|---|-----|-------------|
| Q26 | **(C)** | Paddy/Rice = KHARIF crop (sown in monsoon June-July) |
| Q27 | **(C)** | Wheat = RABI crop (sown Oct-Nov, harvested March-April) |
| Q28 | **(C)** | Bhagalpur = "Silk City of India" for Tussar Silk |
| Q29 | **(C)** | Bhagalpur produces TUSSAR silk (not Mulberry or Muga) |
| Q30 | **(C)** | Bihar = LARGEST maize producer in India (first rank) |
| Q31 | **(C)** | Muzaffarpur = Litchi Capital of India |
| Q32 | **(C)** | Bihar produces ~90% of world's Makhana production |
| Q33 | **(C)** | Darbhanga is the main Makhana hub (North Bihar wetlands area) |
| Q34 | **(B)** | West Champaran + East Champaran = Bihar's Sugarcane Belt |
| Q35 | **(C)** | Rohtas = largest producer of both Wheat AND Paddy in Bihar |
| Q36 | **(C)** | Muga Silk = ONLY from Assam (never Bihar) — golden, most expensive |
| Q37 | **(C)** | Jute grown in NE Bihar — Kishanganj, Purnea, Katihar, Saharsa |
| Q38 | **(C)** | Kharif = sown in monsoon June-July, harvested September-October |
| Q39 | **(B)** | Zaid crops = Watermelon, Cucumber, Mung Bean (summer crops) |
| Q40 | **(B)** | M.S. Swaminathan = Father of Green Revolution in INDIA; Borlaug = Global |
| Q41 | **(B)** | White Revolution = Milk/Dairy; Dr. Verghese Kurien; Operation Flood; AMUL |
| Q42 | **(C)** | West Bengal = largest paddy producer in India at national level |
| Q43 | **(C)** | West Bengal = largest jute producer in India |
| Q44 | **(B)** | Nalanda = "Vegetable Bowl" of Bihar — known for vegetables |
| Q45 | **(C)** | Bihar's Gangetic plains = Alluvial soil (most common type) |
| Q46 | **(B)** | Bhagalpuri/Tussar Silk has received Geographical Indication (GI) Tag |
| Q47 | **(B)** | Makhana is aquatic — needs wetlands, ponds, flooded areas to grow |
| Q48 | **(B)** | Items 1, 2, 4 are correct; Cotton is Kharif (not Rabi) — so item 3 is wrong |
| Q49 | **(C)** | Bihar = India's largest MAIZE producer |
| Q50 | **(C)** | All 4 statements are correct — "More than one" applies (all 4 are right) → Answer is (D) |

> **Note for Q50:** All 4 statements are true, so the answer is **(D) More than one of the above** — all statements are correct!

---

---

# 📌 DAILY NIGHT REVISION — 5-BULLET SUMMARY

Write these from memory before sleeping tonight:

## CS — Transmission Media & Security Key Facts:
1. Optical Fiber = highest speed + immune to EM interference; uses LIGHT not electricity
2. UTP = cheapest + most common BUT vulnerable to EM interference (no shield)
3. Sniffers prevented by SWITCHED network (hub network = vulnerable to sniffing)
4. Asymmetric crypto: Encrypt with receiver's PUBLIC KEY; Decrypt with receiver's PRIVATE KEY
5. Symmetric = SAME key both ways (faster); Full access rights to all = integrity breach

## GS — Bihar Agriculture Key Facts:
1. Paddy = Kharif; Wheat = Rabi; Bihar's Rohtas = largest wheat + paddy producer
2. Bihar = LARGEST maize producer in India; Maize districts: Kaimur, Rohtas, Bhojpur
3. Bhagalpur = Silk City = TUSSAR silk (not Mulberry!); Muzaffarpur = Litchi Capital
4. Makhana = ~90% world production from Bihar; Darbhanga = Makhana hub; GI tag
5. Champaran = Sugarcane Belt of Bihar; Green Revolution = M.S. Swaminathan (India)

---

## ⚡ TOPPER'S SELF-ASSESSMENT CHECKLIST

After completing Day 48, tick these off:

- [ ] Can you name TWO key facts about Optical Fiber?
- [ ] Do you know why UTP is vulnerable but STP is not?
- [ ] Can you explain why switched networks prevent sniffing?
- [ ] Do you know who holds the private key in asymmetric cryptography?
- [ ] Can you explain what a system integrity breach is?
- [ ] Can you name the crop for each Bihar district: Bhagalpur, Muzaffarpur, Darbhanga, Rohtas?
- [ ] Do you know the difference between Tussar Silk and Muga Silk and their states?
- [ ] Can you list 3 Kharif crops and 3 Rabi crops from memory?
- [ ] Do you know Bihar's rank in maize production nationally?
- [ ] Can you name M.S. Swaminathan and his contribution?

**Score yourself:** 9–10 ✅ = Topper ready! | 7–8 = Good, quick review | Below 7 = Re-study today

---

*Day 48 Complete | Next: Day 49 — REVISION DAY: Full Computer Networks Review + GS Geography Revision*
*Phase 1 (Day 1–60) | Networks Week almost done (Day 43–49) | Keep pushing! 🎯*
*BPSC TRE 4.0 Target: 130+/150 — YOU ARE BUILDING TOWARD IT, ONE DAY AT A TIME! 💪*
