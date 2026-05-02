# 📅 BPSC TRE 4.0 — DAY 83: IoT + CLOUD COMPUTING + ENVIRONMENT & GREEN TECH
### Week 13 — AI, IoT, Emerging Tech & Theory of Computation
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): CS — IoT, Cloud Computing (IaaS/PaaS/SaaS), Blockchain
> - Afternoon (1 hr): GS — Environment (Pollution, Climate Change, Green Tech)
> - Evening (1.5 hrs): Solve all 50 Mixed MCQs (25 CS + 25 GS)
> - Night (30 min): Read the "Last 1-Hour Before Exam" revision sheet

---

# PART 1: CS RAPID REVISION
## 📘 IoT + Cloud Computing — All Concepts, One Place

---

## 🔷 TOPIC 1: IoT — Internet of Things

### What is IoT?
```
IoT = INTERNET OF THINGS

DEFINITION:
  = A network of PHYSICAL DEVICES (things) that are
    connected to the INTERNET and can COLLECT + SHARE DATA
    with each other — WITHOUT human-to-human or
    human-to-computer interaction

SIMPLE ANALOGY:
  Traditional world:   Devices work alone; need human to check
  IoT world:           Devices talk to each other + internet AUTOMATICALLY

EXAMPLE:
  Your refrigerator senses milk is low
       ↓
  Sends message to your phone automatically
       ↓
  Phone adds milk to your online grocery order
       ↓
  Delivery person brings milk (without you doing anything!)

The "Things" in IoT = ANY physical object with sensors + internet:
  → Smartwatch (monitors heart rate, sends to doctor)
  → Smart bulb (turns on/off via phone app)
  → Industrial sensor (monitors factory temperature)
  → Smart traffic light (adjusts timing based on traffic)
  → Wearable fitness tracker (Fitbit, etc.)
```

### IoT Architecture Diagram:
```
IoT SYSTEM ARCHITECTURE — How it works end-to-end
═══════════════════════════════════════════════════════════════════

LAYER 1 — PERCEPTION LAYER (Things/Devices)
  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐
  │ SENSOR 1 │  │ SENSOR 2 │  │ ACTUATOR │  │ CAMERA   │
  │(Temp     │  │(Heart    │  │(Smart    │  │(Security │
  │ Sensor)  │  │ Rate)    │  │ Door     │  │ Camera)  │
  └────┬─────┘  └────┬─────┘  └────┬─────┘  └────┬─────┘
       │              │              │              │
       └──────────────┴──────────────┴──────────────┘
                             │
                             ▼
LAYER 2 — NETWORK LAYER (Communication)
  ┌──────────────────────────────────────────────────────┐
  │          WIRELESS COMMUNICATION PROTOCOLS            │
  │  Bluetooth  │  WiFi  │  Zigbee  │  MQTT  │  LoRa    │
  │  (short     │(medium │(low      │(IoT    │(long     │
  │   range)    │ range) │ power)   │protocol│ range)   │
  └──────────────────────────────────────────────────────┘
                             │
                             ▼
LAYER 3 — PROCESSING LAYER (Data Processing)
  ┌──────────────────────────────────────────────────────┐
  │           CLOUD / EDGE COMPUTING                     │
  │     Data is stored, processed, analyzed here         │
  └──────────────────────────────────────────────────────┘
                             │
                             ▼
LAYER 4 — APPLICATION LAYER (End Users)
  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐
  │ SMART    │  │HEALTHCARE│  │INDUSTRIAL│  │ SMART    │
  │  HOME    │  │MONITORING│  │ IoT      │  │   CITY   │
  └──────────┘  └──────────┘  └──────────┘  └──────────┘
```

---

## 🔷 TOPIC 2: IoT Communication Protocols — PYQ KEY

### Most Important Protocol: MQTT
```
MQTT = MESSAGE QUEUING TELEMETRY TRANSPORT
════════════════════════════════════════════════════════

PYQ FACT: "IoT communication protocol = MQTT" ← TESTED IN BPSC TRE!
          This is the #1 most important IoT protocol to memorize.

WHY MQTT for IoT?
  → Designed for devices with LIMITED power and bandwidth
    (sensors, small devices don't have much computing power)
  → Very LIGHTWEIGHT protocol (uses very little data)
  → Works well on UNRELIABLE networks (common in IoT)
  → Uses PUBLISH-SUBSCRIBE model (not request-response)

HOW MQTT WORKS (Publish-Subscribe Model):
  ┌───────────────────────────────────────────────────────────┐
  │                    MQTT BROKER                            │
  │              (Central message hub)                        │
  │                        │                                  │
  │         ┌──────────────┼──────────────┐                  │
  │         │              │              │                   │
  │    PUBLISHER      PUBLISHER       SUBSCRIBER             │
  │    (Sensor:       (Sensor:        (Phone App:            │
  │    publishes      publishes        subscribes to         │
  │    temperature)   humidity)        "temperature"         │
  │                                    topic)                │
  └───────────────────────────────────────────────────────────┘

  PUBLISHER = device that SENDS data (e.g., temperature sensor)
  BROKER    = MIDDLE SERVER that receives and routes messages
  SUBSCRIBER= device that RECEIVES data (e.g., phone app)
  TOPIC     = category/channel for messages (e.g., "home/temperature")

  Sensor publishes temperature to BROKER under topic "home/temp"
  Your phone subscribes to "home/temp" topic
  Broker delivers temperature data to your phone automatically!

PYQ COMPARISON:
  HTTP  = request-response (used in websites) — NOT ideal for IoT
  MQTT  = publish-subscribe (used in IoT)     — IDEAL for IoT ← PYQ
  SMTP  = email protocol
  FTP   = file transfer
```

### IoT Wireless Technologies:
```
IoT WIRELESS COMMUNICATION TECHNOLOGIES
════════════════════════════════════════════════════════

TECHNOLOGY    RANGE        POWER    USE CASE              PYQ FACT
──────────────────────────────────────────────────────────────────────
Bluetooth     Short        Low      Wearables, smart      Bluetooth 5.0 = modern
(Bluetooth    (~10–100m)            home devices          IoT short-range ← PYQ!
5.0 for IoT)                        (fitness trackers,
                                     smart speakers)
──────────────────────────────────────────────────────────────────────
WiFi          Medium       Higher   Smart home, office    Common but
              (~50–100m)            IoT (cameras, smart   power-hungry
                                     TVs, robots)
──────────────────────────────────────────────────────────────────────
Zigbee        Short        Very     Home automation       Low power; used
              (~10–100m)   Low      (smart bulbs,         in smart bulbs
                                     smart locks)          and sensors
──────────────────────────────────────────────────────────────────────
LoRa          Long         Very     Agriculture IoT,      Long Range +
(Long Range)  (~2–15 km)   Low      smart city sensors,   Low Power combo
                                     remote locations
──────────────────────────────────────────────────────────────────────
NFC           Very Short   Very     Payment (Google Pay,  Used in
(Near Field   (~4 cm)      Low      contactless cards),   contactless
Communication)                      smart tags            payments
──────────────────────────────────────────────────────────────────────

PYQ FACT: "IoT short-range wireless = BLUETOOTH (Bluetooth 5.0)" ← TESTED!
          "MQTT = IoT communication protocol" ← TESTED!
```

### IoT Applications:
```
IoT APPLICATIONS — PYQ-Tested Categories
════════════════════════════════════════════════════════

CATEGORY          EXAMPLES                         KEY DEVICES
─────────────────────────────────────────────────────────────────────
Smart Home        Automatic lights, smart lock,    Smart bulb, Alexa,
                  voice-controlled appliances      Google Home, Nest
─────────────────────────────────────────────────────────────────────
Wearables         Heart rate monitor, step         Smartwatch (Apple
                  counter, sleep tracker           Watch), Fitbit
─────────────────────────────────────────────────────────────────────
Healthcare        Remote patient monitoring,       Glucose monitor,
                  connected medical devices        smart pill dispenser
─────────────────────────────────────────────────────────────────────
Industrial IoT    Factory monitoring, predictive   Temperature/pressure
(IIoT)           maintenance, quality control      sensors, robotic arms
─────────────────────────────────────────────────────────────────────
Smart City        Traffic management, smart        Smart traffic lights,
                  parking, waste management,       air quality sensors,
                  street lighting                  smart meters
─────────────────────────────────────────────────────────────────────
Agriculture       Soil moisture monitoring,        Drone sensors,
(Smart Farming)  automated irrigation, crop        weather stations,
                  health monitoring                soil sensors
─────────────────────────────────────────────────────────────────────
```

---

## 🔷 TOPIC 3: Cloud Computing — The Big Picture

### What is Cloud Computing?
```
CLOUD COMPUTING
════════════════════════════════════════════════════════

DEFINITION:
  = Delivery of computing services (servers, storage,
    databases, software, networking) OVER THE INTERNET
    ("the cloud") on a PAY-AS-YOU-GO basis

BEFORE CLOUD (Traditional):
  Company needs software →
  Buy expensive hardware servers →
  Install and maintain software →
  Hire IT team to manage it →
  Pay even when not in use!

WITH CLOUD:
  Company needs software →
  Access it via internet (rent from cloud provider) →
  Pay only for what you use →
  Provider handles all maintenance!

ADVANTAGES:
  ✅ No upfront hardware cost (CAPEX → OPEX)
  ✅ Scale up or down instantly (elasticity)
  ✅ Access from anywhere (internet needed)
  ✅ Provider handles maintenance, security, updates
  ✅ Disaster recovery built-in

MAJOR CLOUD PROVIDERS:
  AWS (Amazon Web Services) ← largest
  Microsoft Azure
  Google Cloud Platform (GCP)
  IBM Cloud

SIMPLE DIAGRAM:
  ┌─────────────────────────────────────────────────────────┐
  │                    THE CLOUD                            │
  │          (Data Centers owned by providers)              │
  │                                                         │
  │  [Servers] [Storage] [Databases] [Software] [Network]  │
  └─────────────────────────────────────────────────────────┘
         ↑                ↑               ↑
  [Your Laptop]     [Company PC]    [Mobile App]
  (access via Internet from anywhere!)
```

---

## 🔷 TOPIC 4: Cloud Service Models — IaaS, PaaS, SaaS ← PYQ CORE

### The Pizza Analogy (Best way to understand):
```
CLOUD SERVICE MODELS — PIZZA ANALOGY
════════════════════════════════════════════════════════

Imagine making pizza. How much do YOU manage vs provider?

┌────────────────────────────────────────────────────────────────────┐
│ ON-PREMISES    │ IaaS           │ PaaS           │ SaaS            │
│ (Traditional)  │                │                │                 │
├────────────────┼────────────────┼────────────────┼─────────────────┤
│ You manage     │ You manage     │ You manage     │ Provider manages│
│ EVERYTHING:    │ → Application  │ → Application  │ EVERYTHING      │
│ → Application  │ → Data         │ → Data         │                 │
│ → Data         │ → Runtime      │                │ You just USE    │
│ → Runtime      │ → Middleware   │ Provider       │ the app!        │
│ → Middleware   │ → OS           │ manages rest   │                 │
│ → OS           │                │                │                 │
│ → Virtualization│ Provider       │                │                 │
│ → Servers      │ manages:       │                │                 │
│ → Storage      │ → Virtualization│               │                 │
│ → Networking   │ → Servers      │                │                 │
│                │ → Storage      │                │                 │
│                │ → Networking   │                │                 │
├────────────────┼────────────────┼────────────────┼─────────────────┤
│ Like making    │ Like renting   │ Like ordering  │ Like ordering   │
│ pizza AT HOME  │ a kitchen to   │ pizza base     │ DELIVERED pizza │
│ (buy oven,     │ cook in        │ already made   │ (just eat it!)  │
│  ingredients,  │ (oven provided │ (add toppings  │                 │
│  cook it all)  │  you cook)     │  yourself)     │                 │
└────────────────┴────────────────┴────────────────┴─────────────────┘
```

### IaaS — Infrastructure as a Service:
```
IaaS = INFRASTRUCTURE as a Service
════════════════════════════════════════════════════════

WHAT YOU GET: Virtual machines, storage, networking
              (raw computing infrastructure)
YOU MANAGE:   Your OS, applications, runtime, data
PROVIDER MANAGES: Physical servers, storage, networking

THINK OF IT AS: Renting a VIRTUAL COMPUTER in the cloud

WHO USES IT:
  → Developers who need servers but don't want to buy hardware
  → Companies that need flexible storage
  → Start-ups that want to scale infrastructure quickly

EXAMPLES:
  AWS EC2 (Elastic Compute Cloud)  ← most famous IaaS ← PYQ!
  AWS S3 (Simple Storage Service)
  Microsoft Azure Virtual Machines
  Google Compute Engine

ANALOGY: Renting an empty apartment — you bring your own furniture,
         decorate it, cook your own food. Landlord provides the building.

PYQ FACT: "IaaS example = AWS EC2" ← tested!
          IaaS = VIRTUAL MACHINES and storage ← tested!
```

### PaaS — Platform as a Service:
```
PaaS = PLATFORM as a Service
════════════════════════════════════════════════════════

WHAT YOU GET: A PLATFORM/ENVIRONMENT to develop + deploy apps
              (OS, runtime, middleware already set up)
YOU MANAGE:   Your APPLICATION code and DATA only
PROVIDER MANAGES: Infrastructure + OS + Runtime + Middleware

THINK OF IT AS: A kitchen fully equipped — you just cook (write code)
                You don't worry about setting up the kitchen

WHO USES IT:
  → SOFTWARE DEVELOPERS who want to focus on coding,
    not server management
  → Teams building web applications rapidly

EXAMPLES:
  Google App Engine            ← PYQ! ← most tested PaaS example
  Heroku                       ← PYQ!
  Microsoft Azure App Service
  AWS Elastic Beanstalk
  Red Hat OpenShift

ANALOGY: Renting a fully equipped kitchen in a restaurant —
         you bring the recipe and ingredients; kitchen + staff provided.

PYQ FACT: "PaaS = development platform" ← tested!
          "Google App Engine, Heroku = PaaS" ← tested!
```

### SaaS — Software as a Service:
```
SaaS = SOFTWARE as a Service
════════════════════════════════════════════════════════

WHAT YOU GET: Ready-to-USE software applications via internet
YOU MANAGE:   NOTHING (just use the application!)
PROVIDER MANAGES: Everything — infrastructure, OS, software,
                  updates, security, data backups

THINK OF IT AS: You just use the app in your browser or phone
                No installation needed. Provider does everything.

WHO USES IT:
  → Everyone! Businesses, individuals
  → Anyone who uses web apps

EXAMPLES:
  Gmail / Google Workspace     ← PYQ! ← most famous SaaS
  Microsoft Office 365
  Salesforce CRM               ← PYQ!
  Zoom, Slack
  Dropbox, Google Drive
  Netflix (streaming service)
  Spotify

ANALOGY: Ordering food at a restaurant — you just sit and eat.
         Chef cooks, waiter serves, restaurant manages everything.

PYQ FACT: "SaaS = ready-to-use apps (Gmail, Salesforce, Office 365)" ← tested!
          "SaaS = user manages nothing" ← correct!
```

### Master Comparison Table:
```
IaaS vs PaaS vs SaaS — MASTER COMPARISON ← MOST IMPORTANT TABLE
═══════════════════════════════════════════════════════════════════════

SERVICE  FULL NAME           YOU MANAGE      EXAMPLES           TARGET USER
MODEL                                                           
────────────────────────────────────────────────────────────────────────────
IaaS     Infrastructure      App + Data      AWS EC2,           IT Admins,
         as a Service        + OS + Runtime  Azure VMs,         System Admins
                             (everything     Google Compute     who manage
                             except hardware Engine             servers

PaaS     Platform            App + Data      Google App         DEVELOPERS
         as a Service        ONLY            Engine, Heroku,    who build apps
                                             AWS Elastic        without managing
                                             Beanstalk          infrastructure

SaaS     Software            NOTHING         Gmail, Salesforce, END USERS
         as a Service        (just use it!)  Office 365, Zoom,  (everyone!)
                                             Netflix, Slack
────────────────────────────────────────────────────────────────────────────

MEMORY TRICK — "I Provide Software":
  IaaS → Infrastructure (raw hardware/VMs)
  PaaS → Platform (development environment)
  SaaS → Software (finished applications)

MANAGEMENT LEVEL (most to least by customer):
  IaaS > PaaS > SaaS  (IaaS = most customer management)
  (SaaS = LEAST management by customer — just use the app)

PYQ TRAP: "AWS EC2 = SaaS" → FALSE (EC2 = IaaS)
          "Gmail = PaaS" → FALSE (Gmail = SaaS)
          "Google App Engine = IaaS" → FALSE (= PaaS)
```

---

## 🔷 TOPIC 5: Cloud Deployment Models

```
CLOUD DEPLOYMENT MODELS — Types of Cloud
════════════════════════════════════════════════════════

TYPE 1: PUBLIC CLOUD
  ┌──────────────────────────────────────────────────────┐
  │            PUBLIC CLOUD PROVIDER                      │
  │    (AWS / Azure / Google Cloud)                       │
  │                                                       │
  │  Company A  │  Company B  │  Company C  │  You        │
  │  (share the SAME infrastructure — multi-tenant)       │
  └──────────────────────────────────────────────────────┘
  = Cloud resources SHARED among multiple organizations
  = Managed by cloud provider (AWS, Azure, GCP)
  = Cheapest option
  = Less control over security

TYPE 2: PRIVATE CLOUD
  ┌──────────────────────────────────────────────────────┐
  │         PRIVATE CLOUD (YOUR COMPANY ONLY)             │
  │    (Dedicated infrastructure for ONE organization)    │
  │                                                       │
  │        Only YOUR company uses this cloud              │
  └──────────────────────────────────────────────────────┘
  = Cloud resources DEDICATED to ONE organization
  = More secure and controlled
  = More expensive than public cloud
  = Used by banks, government, healthcare (sensitive data)

TYPE 3: HYBRID CLOUD
  ┌─────────────────┐     ┌─────────────────┐
  │  PRIVATE CLOUD  │◄───►│  PUBLIC CLOUD   │
  │  (sensitive     │     │  (non-sensitive │
  │   data here)    │     │   workloads)    │
  └─────────────────┘     └─────────────────┘
  = COMBINATION of public + private cloud
  = Sensitive data on private; other workloads on public
  = Best of both worlds (flexibility + security)
  = Most popular enterprise model today

TYPE 4: COMMUNITY CLOUD
  = Shared among SPECIFIC COMMUNITY with common concerns
    (e.g., government agencies, healthcare organizations)
  = Less common; between public and private

PYQ COMPARISON:
  Public  = shared, cheap, less secure
  Private = dedicated, expensive, more secure
  Hybrid  = combination of both ← most flexible
```

---

## 🔷 TOPIC 6: Blockchain Technology

```
BLOCKCHAIN
════════════════════════════════════════════════════════

DEFINITION:
  = A DISTRIBUTED LEDGER (record book) that is:
    → DECENTRALIZED (no single authority controls it)
    → IMMUTABLE (once data is written, it CANNOT be changed)
    → TRANSPARENT (everyone on the network can see records)
    → SECURE (uses cryptography to protect data)

SIMPLE ANALOGY:
  Traditional ledger:    One bank keeps record of all transactions
                         (centralized — bank can change records)
  Blockchain:            THOUSANDS of computers keep the SAME copy
                         of the record. To change data, you'd need to
                         change ALL copies simultaneously — impossible!

HOW IT WORKS — DIAGRAM:
  ┌───────────┐     ┌───────────┐     ┌───────────┐
  │  BLOCK 1  │────►│  BLOCK 2  │────►│  BLOCK 3  │
  │           │     │           │     │           │
  │ Data:     │     │ Data:     │     │ Data:     │
  │ Transaction│    │ Transaction│    │ Transaction│
  │           │     │           │     │           │
  │ Hash: A1B2│     │ Hash: C3D4│     │ Hash: E5F6│
  │ Prev: 0000│     │ Prev: A1B2│     │ Prev: C3D4│
  └───────────┘     └───────────┘     └───────────┘
       (first)           (linked          (linked to
                         to Block 1)       Block 2)

  Each BLOCK contains:
    → DATA (transaction records)
    → HASH (unique fingerprint of this block)
    → PREVIOUS HASH (fingerprint of previous block → creates CHAIN)

  If Block 2 is changed → its hash changes →
  Block 3's "previous hash" no longer matches →
  ENTIRE CHAIN becomes invalid → tampering is detected!

KEY PROPERTIES:
  Decentralized  = No single authority (not controlled by one entity)
  Distributed    = Data stored across MANY computers (nodes)
  Immutable      = Records CANNOT be altered once written ← PYQ!
  Transparent    = All participants can view the ledger

APPLICATIONS:
  → Cryptocurrency (Bitcoin, Ethereum) ← original use case
  → Supply chain tracking (food safety, medicine)
  → Smart contracts (self-executing contracts)
  → Digital voting systems
  → Healthcare record sharing
  → Land registry (Telangana used blockchain for land records)

PYQ FACT: "Blockchain = distributed ledger, decentralized" ← tested!
          "Blockchain data is immutable" = TRUE ✅
          "Blockchain is controlled by a central authority" → FALSE
```

---

## 🔷 TOPIC 7: Green Hydrogen — PYQ KEY FACT

```
GREEN HYDROGEN
════════════════════════════════════════════════════════

WHAT IS HYDROGEN AS FUEL?
  → Hydrogen (H₂) burns cleanly — only produces WATER (H₂O)
  → Zero carbon emissions when burned ← key advantage
  → Called "fuel of the future"

TYPES OF HYDROGEN (color-coded):
  ┌─────────────────────────────────────────────────────────┐
  │ GREY Hydrogen   = Made from FOSSIL FUELS (natural gas)  │
  │                  CO₂ is RELEASED → pollutes             │
  ├─────────────────────────────────────────────────────────┤
  │ BLUE Hydrogen   = Made from fossil fuels BUT CO₂ is    │
  │                  CAPTURED and stored (CCS technology)   │
  ├─────────────────────────────────────────────────────────┤
  │ GREEN Hydrogen  = Made using ELECTROLYSIS of WATER      │
  │                  Powered by RENEWABLE ENERGY (solar/    │
  │                  wind) → ZERO carbon emissions!         │
  │                  = CLEANEST form of hydrogen ← PYQ!     │
  └─────────────────────────────────────────────────────────┘

GREEN HYDROGEN PRODUCTION — ELECTROLYSIS:
  ┌────────────────────────────────────────────────────────┐
  │                    ELECTROLYZER                        │
  │                                                        │
  │  WATER (H₂O) + ELECTRICITY → H₂ + O₂                 │
  │                                                        │
  │  Renewable         ┌──────────┐                       │
  │  Energy    ───────►│ELECTROLYZER│──────► H₂ (stored)  │
  │  (Solar/           │          │                       │
  │   Wind)            │  H₂O     │──────► O₂ (released)  │
  │                    └──────────┘                       │
  └────────────────────────────────────────────────────────┘

  ELECTROLYSIS formula:
  2H₂O → 2H₂ + O₂   (water splits into hydrogen + oxygen)

  KEY: The electricity MUST come from RENEWABLE sources
       (solar or wind) for it to be "GREEN" hydrogen
       If electricity from coal → it's not green!

PYQ FACT: "Green Hydrogen is produced by ELECTROLYSIS of water"
          = TRUE ✅ ← TESTED IN BPSC TRE!
          "Green Hydrogen = zero carbon emissions" = TRUE ✅
          "First pure green hydrogen plant = Hyderabad (AP)" ← PYQ!

NATIONAL GREEN HYDROGEN MISSION (India):
  → Launched by Government of India in January 2023
  → Target: 5 million tonnes of green hydrogen per year by 2030
  → India aims to be a global hub for green hydrogen
```

---

## 📊 CS MASTER COMPARISON TABLE — Day 83

```
CONCEPT               KEY FACT                              COMMON TRAP
──────────────────────────────────────────────────────────────────────────
IoT Definition        Physical devices connected to         "IoT = only phones"
                      internet sharing data automatically   → FALSE
MQTT                  IoT COMMUNICATION PROTOCOL ← PYQ!    "HTTP = IoT protocol"
                      Publish-Subscribe model               → Not ideal for IoT
Bluetooth (5.0)       Short-range IoT wireless ← PYQ!      "WiFi = short range"
                                                            (WiFi = medium range)
IaaS                  Virtual machines + storage            "AWS EC2 = SaaS"
                      AWS EC2 = best example                → FALSE
PaaS                  Development PLATFORM                  "Google App Engine=IaaS"
                      Google App Engine, Heroku             → FALSE (= PaaS)
SaaS                  Ready-to-USE software                 "Gmail = IaaS/PaaS"
                      Gmail, Salesforce, Office 365         → FALSE (= SaaS)
Public Cloud          Shared, cheap, less secure            "Public = private"
Private Cloud         Dedicated, expensive, secure          → completely different
Hybrid Cloud          Public + Private combination          "Hybrid = only private"
Blockchain            DISTRIBUTED LEDGER; Decentralized;    "Blockchain = centralized"
                      Immutable                             → FALSE (decentralized)
Green Hydrogen        Produced by ELECTROLYSIS ← PYQ!       "Green H₂ = from gas"
                      of water using renewable energy        → FALSE (= grey H₂)
──────────────────────────────────────────────────────────────────────────
```

---
---

# PART 2: GS RAPID REVISION
## 🌿 Environment — Pollution, Climate Change & Green Technology

---

## 🔷 ENV TOPIC 1: Pollution Types & Key Facts

```
POLLUTION — TYPES AND KEY FACTS
════════════════════════════════════════════════════════

TYPE 1: AIR POLLUTION
  MAIN SOURCES:
    → Vehicle exhaust (CO, NOₓ, HC)
    → Industrial emissions (SO₂, NO₂, particulate matter)
    → Power plants burning fossil fuels
    → Agricultural burning (crop residue)
    → Brick kilns, construction dust

  KEY POLLUTANTS:
    CO (Carbon Monoxide)    = Colorless, odorless; from incomplete
                             combustion; DEADLY in enclosed spaces
    CO₂ (Carbon Dioxide)    = Main greenhouse gas; from burning fossil fuels
    SO₂ (Sulphur Dioxide)   = Acid rain precursor; from coal burning
    NO₂ (Nitrogen Dioxide)  = Brown haze; from vehicles
    PM 2.5 / PM 10          = Particulate matter; causes lung disease
                             PM 2.5 = more dangerous (finer particles)
    Ozone (O₃)              = At GROUND LEVEL = pollutant (harmful!)
                             In STRATOSPHERE = protects from UV ← PYQ!

  PYQ TRAP: "Ground-level ozone is beneficial" → FALSE (harmful!)
            "Stratospheric ozone is harmful" → FALSE (it's protective!)

TYPE 2: WATER POLLUTION
  SOURCES:
    → Industrial effluents (heavy metals: Lead, Mercury, Cadmium)
    → Agricultural runoff (fertilizers → Eutrophication)
    → Sewage and domestic waste
    → Oil spills

  EUTROPHICATION:
    = Excess nutrients (nitrogen, phosphorus from fertilizers)
      → Excessive algae growth (algal bloom)
      → Algae uses up all oxygen in water
      → Fish and aquatic life DIE (oxygen depletion)
    PYQ FACT: Eutrophication = nutrient pollution causing oxygen depletion

  MINAMATA DISEASE:
    = Caused by MERCURY (Hg) poisoning from industrial waste
    = First identified in Minamata, Japan
    PYQ FACT: Minamata disease = Mercury poisoning ← tested!

  ITAI-ITAI DISEASE:
    = Caused by CADMIUM (Cd) poisoning
    = "Ouch-ouch disease" (bone pain)
    PYQ FACT: Itai-itai disease = Cadmium poisoning ← tested!

TYPE 3: SOIL POLLUTION
  SOURCES:
    → Pesticides and insecticides (DDT, Aldrin)
    → Industrial chemicals
    → Plastic waste

  DDT:
    = Dichlorodiphenyltrichloroethane
    = Pesticide — now BANNED in many countries
    = Accumulates in food chain (Biomagnification) ← PYQ!
    = Causes thinning of bird eggshells

  BIOMAGNIFICATION:
    = Concentration of toxins INCREASES as you go UP the food chain
    = Producers (plants) → Herbivores → Carnivores → Top Predator
    = Each level has MORE concentration of toxin
    PYQ FACT: Biomagnification = toxin concentration increases in food chain

TYPE 4: NOISE POLLUTION
  Sources: Vehicles, industrial machinery, construction, firecrackers
  Safe noise level = 45 dB (decibels) for residential areas
  Hearing damage begins above 85 dB
```

---

## 🔷 ENV TOPIC 2: Greenhouse Effect & Climate Change

```
GREENHOUSE EFFECT
════════════════════════════════════════════════════════

NATURAL GREENHOUSE EFFECT (necessary for life):
  ┌─────────────────────────────────────────────────────────┐
  │                       SUN                               │
  │                        │                                │
  │               SOLAR RADIATION                           │
  │                        │                                │
  │                        ▼                                │
  │  ┌──────────────────ATMOSPHERE──────────────────────┐   │
  │  │  CO₂, H₂O, CH₄, N₂O (Greenhouse Gases/GHGs)    │   │
  │  │                                                  │   │
  │  │  Some heat escapes → → → → Space                │   │
  │  │         │                                        │   │
  │  │  Some heat TRAPPED by GHGs ← ← ← ← ← ← ←      │   │
  │  └──────────────────────────────────────────────────┘   │
  │                        │                                │
  │                        ▼                                │
  │              EARTH'S SURFACE (warms up)                 │
  └─────────────────────────────────────────────────────────┘

  WITHOUT greenhouse effect: Earth's average temp = -18°C (too cold!)
  WITH natural GHE: Earth's average temp = +15°C (just right!)

ENHANCED GREENHOUSE EFFECT (climate change):
  = Human activities ADD MORE GHGs to atmosphere
  → More heat trapped → Earth gets WARMER → GLOBAL WARMING

MAIN GREENHOUSE GASES:
  CO₂  = Carbon Dioxide   = Largest contributor; from fossil fuels
  CH₄  = Methane          = From cattle, landfills, natural gas
  N₂O  = Nitrous Oxide    = From fertilizers, agriculture
  H₂O  = Water Vapor      = Natural; amplifies warming
  O₃   = Ozone            = Stratospheric (beneficial); ground-level (harmful)
  CFCs = Chlorofluorocarbons = Ozone layer depleting; from old AC/refrigerators

GLOBAL WARMING POTENTIAL (relative to CO₂):
  CO₂ = 1 (baseline)
  CH₄ = 21 times more potent than CO₂ ← PYQ!
  N₂O = 310 times more potent than CO₂ ← PYQ!

PYQ FACT: "Methane is more potent greenhouse gas than CO₂" = TRUE ✅
          "CO₂ is the most ABUNDANT greenhouse gas (by human emission)" = TRUE
          "Methane = 21x more potent than CO₂" ← tested!
```

---

## 🔷 ENV TOPIC 3: Important International Agreements

```
INTERNATIONAL ENVIRONMENTAL AGREEMENTS — PYQ TABLE
════════════════════════════════════════════════════════

AGREEMENT            YEAR   PURPOSE                         KEY FACT
─────────────────────────────────────────────────────────────────────────
Kyoto Protocol       1997   Reduce GHG emissions from       Legally binding
                            developed nations               for developed countries
─────────────────────────────────────────────────────────────────────────
Paris Agreement      2015   Limit global warming to         All countries (NDCs)
                            BELOW 2°C above pre-industrial  India's NDC included
                            levels (aim for 1.5°C)
─────────────────────────────────────────────────────────────────────────
Montreal Protocol    1987   Phase out OZONE-DEPLETING       CFCs banned
                            substances (CFCs, HCFCs)        "Most successful treaty"
─────────────────────────────────────────────────────────────────────────
Stockholm            1972   First major UN environment      "Only One Earth"
Conference                  conference                      theme
─────────────────────────────────────────────────────────────────────────
Earth Summit         1992   Sustainable development,        Rio de Janeiro
(Rio Summit)                Agenda 21, CBD, UNFCCC          (Brazil)
─────────────────────────────────────────────────────────────────────────
Ramsar Convention    1971   Protection of WETLANDS          Wetlands of
                                                            international importance
─────────────────────────────────────────────────────────────────────────
CITES                1973   Regulate trade in               Wildlife trade
                            ENDANGERED SPECIES              protection
─────────────────────────────────────────────────────────────────────────
Biodiversity         1992   Conservation of biological      Nagoya Protocol
Convention (CBD)            diversity                       under CBD (2010)
─────────────────────────────────────────────────────────────────────────

PYQ FACTS:
  Montreal Protocol = CFC ban = ozone layer protection ← tested!
  Paris Agreement = 2015; limit to 1.5°C–2°C warming ← tested!
  Ramsar Convention = WETLANDS protection ← tested!
  Stockholm 1972 = FIRST major UN environment conference ← tested!
```

---

## 🔷 ENV TOPIC 4: Renewable Energy Types

```
RENEWABLE vs NON-RENEWABLE ENERGY
════════════════════════════════════════════════════════

NON-RENEWABLE:       Coal, Petroleum, Natural Gas, Nuclear
  → Finite; will run out eventually
  → Cause pollution (fossil fuels emit CO₂)

RENEWABLE ENERGY TYPES (never run out; cleaner):
  ┌────────────────────────────────────────────────────────┐
  │ TYPE          │ SOURCE        │ KEY FACT               │
  ├───────────────┼───────────────┼────────────────────────┤
  │ Solar Energy  │ Sunlight      │ Most abundant;         │
  │               │               │ India = 3rd largest    │
  │               │               │ solar capacity         │
  ├───────────────┼───────────────┼────────────────────────┤
  │ Wind Energy   │ Wind          │ India = 4th largest    │
  │               │               │ wind power globally    │
  ├───────────────┼───────────────┼────────────────────────┤
  │ Hydro Power   │ Flowing water │ Oldest renewable;      │
  │               │               │ most used globally     │
  ├───────────────┼───────────────┼────────────────────────┤
  │ Tidal Energy  │ Ocean tides   │ Predictable; limited   │
  │               │               │ locations              │
  ├───────────────┼───────────────┼────────────────────────┤
  │ Geothermal    │ Earth's heat  │ Stable; used in        │
  │               │               │ Iceland, NZ            │
  ├───────────────┼───────────────┼────────────────────────┤
  │ Biomass       │ Organic waste │ Can cause some         │
  │               │               │ pollution if burned    │
  └───────────────┴───────────────┴────────────────────────┘

GREEN HYDROGEN (from Day 83 CS section):
  = Hydrogen produced from water using RENEWABLE electricity
  = Electrolysis: 2H₂O → 2H₂ + O₂
  = India's National Green Hydrogen Mission (2023) ← PYQ!
  = First pure green hydrogen plant = Hyderabad (AP) ← PYQ!

PYQ FACTS:
  "Solar energy = most abundant renewable" = TRUE ✅
  "Green Hydrogen = electrolysis of water using renewable energy" ← PYQ!
  "Biogas main component = Methane (CH₄)" ← tested!
```

---

## 🔷 ENV TOPIC 5: Indian Environment — PYQ Facts

```
INDIA ENVIRONMENT — PYQ-TESTED FACTS
════════════════════════════════════════════════════════

NATIONAL PARKS / WILDLIFE (frequently tested):
  Jim Corbett NP     = Uttarakhand; FIRST national park in India (1936)
  Kaziranga NP       = Assam; ONE-HORNED RHINOCEROS ← PYQ!
  Sundarbans NP      = West Bengal; BENGAL TIGER + MANGROVES ← PYQ!
  Gir Forest NP      = Gujarat; ASIATIC LION (only place) ← PYQ!
  Periyar NP         = Kerala; ELEPHANT and TIGER reserve
  Manas NP           = Assam; Tiger + Golden Langur
  Silent Valley NP   = Kerala; rare flora/fauna; NO roads ← Day 80 PYQ!
  Namdapha NP        = Arunachal Pradesh; FOUR BIG CATS

BIOSPHERE RESERVES IN INDIA:
  Nilgiri BR = FIRST and LARGEST biosphere reserve in India ← PYQ!
  Sundarbans BR = West Bengal

PROJECT TIGER:
  = Launched in 1973 by Indira Gandhi
  = To protect BENGAL TIGERS
  = Today: 50+ tiger reserves in India
  PYQ FACT: Project Tiger launched 1973 ← tested!

PROJECT ELEPHANT:
  = Launched in 1992
  = To protect elephants and their corridors

WETLANDS IN INDIA (Ramsar Sites):
  India has 75+ Ramsar-designated wetlands (as of 2023)
  Famous: Chilika Lake (Odisha), Keoladeo NP (Rajasthan),
  Loktak Lake (Manipur), Wular Lake (J&K)

POLLUTION CONTROL BODIES:
  CPCB = Central Pollution Control Board ← PYQ!
  (controls environmental pollution in India)
  SPCB = State Pollution Control Boards

ENVIRONMENT PROTECTION ACT:
  EPA 1986 = Environmental Protection Act (enacted AFTER Bhopal gas tragedy)
  PYQ FACT: EPA enacted in 1986 following Bhopal tragedy ← tested!

BHOPAL GAS TRAGEDY:
  Year = December 1984
  Chemical = MIC (Methyl Isocyanate) leaked from Union Carbide plant
  PYQ FACT: Bhopal tragedy caused by MIC (Methyl Isocyanate) ← tested!
```

---

## 🔷 ENV TOPIC 6: Green Technology Terms

```
GREEN TECHNOLOGY — KEY TERMS
════════════════════════════════════════════════════════

GREEN TECHNOLOGY (CleanTech):
  = Technology designed to REDUCE environmental impact
  = Uses renewable resources, reduces pollution

KEY GREEN TECHNOLOGIES:
  Solar Panels       = Convert sunlight → electricity (PV effect)
  Wind Turbines      = Convert wind → electricity
  Electric Vehicles  = Run on electricity (zero direct emissions)
  Green Hydrogen     = Clean fuel from water electrolysis ← PYQ!
  CCS                = Carbon Capture and Storage (traps CO₂)
  LED Lighting       = Energy-efficient (uses 75% less energy than incandescent)

CARBON FOOTPRINT:
  = Total GHG emissions (in CO₂ equivalent) caused by
    an individual, organization, or product
  = Ways to reduce: use public transport, plant trees,
    eat less meat, use renewable energy

CARBON NEUTRAL:
  = Net ZERO carbon emissions
  = Emissions produced = Emissions removed/offset

PARIS AGREEMENT TARGETS:
  Limit warming to BELOW 2°C (aim: 1.5°C) above pre-industrial
  India's commitments:
    → 500 GW renewable energy by 2030
    → Net zero emissions by 2070
    → 50% energy from renewables by 2030

SUSTAINABLE DEVELOPMENT:
  = Development that meets needs of present WITHOUT
    compromising ability of future generations to meet their needs
  = Definition by BRUNDTLAND COMMISSION (1987) ← PYQ!
  PYQ FACT: "Sustainable development definition = Brundtland Commission 1987"

E-WASTE:
  = Electronic waste (old computers, phones, TVs)
  = Contains toxic: Lead, Mercury, Cadmium, Chromium
  = Must be disposed properly (not in regular garbage)

PYQ FACTS:
  "Sustainable development = Brundtland Commission definition 1987" ← tested!
  "Green Hydrogen = electrolysis; zero carbon" ← tested!
  "EPA 1986 = Environmental Protection Act India" ← tested!
```

---

## 📊 GS MASTER SHORTCUT TABLE — Day 83

```
TOPIC                  KEY FACT                              TRAP
──────────────────────────────────────────────────────────────────────
Ground-level ozone     HARMFUL pollutant                     "Ozone=always good"=FALSE
Stratospheric ozone    PROTECTIVE (absorbs UV rays)          Opposite of ground-level
Minamata disease       MERCURY (Hg) poisoning                "Cadmium" = WRONG
Itai-itai disease      CADMIUM (Cd) poisoning                "Mercury" = WRONG
Eutrophication         Nutrient pollution → algal bloom →    "Benefits fish" = FALSE
                       oxygen depletion
Biomagnification       Toxin concentration INCREASES up      "Decreases" = FALSE
                       food chain
Montreal Protocol      CFC ban; ozone layer protection 1987  "Kyoto = CFCs" = FALSE
Kyoto Protocol         GHG reduction; developed nations 1997 "Kyoto = 2015" = FALSE
Paris Agreement        Below 2°C target; 2015                "Paris = 1997" = FALSE
Ramsar Convention      WETLANDS protection                   "Forests" = FALSE
First NP in India      Jim Corbett (Uttarakhand) 1936        "Kaziranga" = FALSE
Gir Forest             ASIATIC LION (only location)          "Bengal Tiger" = FALSE
Kaziranga              ONE-HORNED RHINO                      "Elephant only" = FALSE
Nilgiri BR             FIRST biosphere reserve in India      "Sundarbans first" = FALSE
Project Tiger          1973 by Indira Gandhi                 "1972" or "1980" = FALSE
EPA India              1986 (after Bhopal gas tragedy)       "1984" = FALSE
Bhopal tragedy         MIC (Methyl Isocyanate); Dec 1984     Chemical = MIC not CO
Green Hydrogen         ELECTROLYSIS of water                 "Steam reforming" = grey H₂
First green H₂ plant   Hyderabad (Andhra Pradesh)            "Mumbai" = FALSE
Brundtland definition  Sustainable development (1987)        Unknown commission name
Methane potency        21x more potent than CO₂              "Less potent than CO₂"=FALSE
──────────────────────────────────────────────────────────────────────
```

---
---

# PART 3: PRACTICE QUESTIONS
## 📝 MIXED MCQs — Day 83 Topics

---

### COMPUTER SCIENCE — 25 MCQs

---

**Q1.** IoT (Internet of Things) is best defined as:
(A) A programming language for mobile applications
(B) A network of PHYSICAL DEVICES connected to the internet that collect and share data automatically
(C) A type of cloud computing service model
(D) More than one of the above
(E) None of the above

---

**Q2.** The PRIMARY communication protocol used in IoT devices is:
(A) HTTP (HyperText Transfer Protocol)
(B) FTP (File Transfer Protocol)
(C) MQTT (Message Queuing Telemetry Transport)
(D) More than one of the above
(E) None of the above

---

**Q3.** MQTT uses which communication model (unlike HTTP's request-response)?
(A) Client-Server model
(B) Peer-to-peer model
(C) PUBLISH-SUBSCRIBE model (via a broker)
(D) More than one of the above
(E) None of the above

---

**Q4.** In MQTT, the central server that RECEIVES messages from publishers and routes them to subscribers is called:
(A) Hub
(B) Switch
(C) Broker
(D) More than one of the above
(E) None of the above

---

**Q5.** The SHORT-RANGE wireless technology used in modern IoT devices (wearables, smart home) is:
(A) LoRa (Long Range)
(B) Zigbee only
(C) Bluetooth (Bluetooth 5.0 for modern IoT)
(D) More than one of the above
(E) None of the above

---

**Q6.** Cloud Computing provides computing services (servers, storage, software) over the internet on:
(A) A fixed monthly subscription only (regardless of usage)
(B) A PAY-AS-YOU-GO basis (pay for what you use)
(C) A one-time purchase model
(D) More than one of the above
(E) None of the above

---

**Q7.** IaaS (Infrastructure as a Service) provides:
(A) Ready-to-use software applications like Gmail
(B) A development platform for coders to build apps
(C) VIRTUAL MACHINES, storage, and networking (raw computing infrastructure)
(D) More than one of the above
(E) None of the above

---

**Q8.** AWS EC2 (Amazon Elastic Compute Cloud) is the best example of:
(A) SaaS (Software as a Service)
(B) PaaS (Platform as a Service)
(C) IaaS (Infrastructure as a Service)
(D) More than one of the above
(E) None of the above

---

**Q9.** PaaS (Platform as a Service) is primarily targeted at:
(A) End users who want to use finished applications (like email)
(B) DEVELOPERS who want to build and deploy apps without managing infrastructure
(C) System administrators managing physical servers
(D) More than one of the above
(E) None of the above

---

**Q10.** Which of the following are examples of PaaS (Platform as a Service)?
(A) Gmail and Office 365
(B) AWS EC2 and Azure Virtual Machines
(C) Google App Engine and Heroku
(D) More than one of the above
(E) None of the above

---

**Q11.** In SaaS (Software as a Service), the customer is responsible for managing:
(A) The operating system and runtime
(B) The application code and database
(C) NOTHING — the provider manages everything
(D) More than one of the above
(E) None of the above

---

**Q12.** Which of the following are examples of SaaS (Software as a Service)?
(A) AWS EC2 and Google Compute Engine
(B) Google App Engine and Heroku
(C) Gmail, Salesforce, and Microsoft Office 365
(D) More than one of the above
(E) None of the above

---

**Q13.** Arranging Cloud Service Models from MOST customer management to LEAST customer management:
(A) SaaS > PaaS > IaaS
(B) PaaS > IaaS > SaaS
(C) IaaS > PaaS > SaaS
(D) More than one of the above
(E) None of the above

---

**Q14.** A PRIVATE CLOUD differs from a PUBLIC CLOUD in that:
(A) Private cloud is shared among multiple organizations while public is dedicated
(B) Private cloud is DEDICATED to ONE organization while public is shared
(C) Private cloud is always less secure than public cloud
(D) More than one of the above
(E) None of the above

---

**Q15.** A HYBRID CLOUD is:
(A) A cloud that only supports hybrid programming languages
(B) A cloud operated exclusively by government organizations
(C) A COMBINATION of public and private cloud working together
(D) More than one of the above
(E) None of the above

---

**Q16.** Blockchain technology is characterized by which of the following properties?
(A) Centralized control by one authority
(B) Data can be easily modified after recording
(C) DECENTRALIZED, DISTRIBUTED, and IMMUTABLE ledger
(D) More than one of the above
(E) None of the above

---

**Q17.** In a Blockchain, once data is written to the chain, it:
(A) Can be modified by the network administrator
(B) Expires after a set period of time
(C) CANNOT be altered (immutable) — changing one block invalidates the chain
(D) More than one of the above
(E) None of the above

---

**Q18.** The component in a Blockchain that creates the CHAIN (links blocks together) is:
(A) The timestamp in each block
(B) The transaction data in each block
(C) The PREVIOUS HASH stored in each block
(D) More than one of the above
(E) None of the above

---

**Q19.** GREEN HYDROGEN is produced by:
(A) Steam reforming of natural gas (fossil fuels)
(B) Nuclear fission reactions
(C) ELECTROLYSIS of water using renewable energy (solar/wind)
(D) More than one of the above
(E) None of the above

---

**Q20.** What is the chemical process in Green Hydrogen production?
(A) 2H₂O → 2H₂ + O₂ (water splits into hydrogen and oxygen)
(B) CH₄ + H₂O → CO + 3H₂ (steam reforming)
(C) CO₂ + H₂O → CH₄ + O₂ (combustion)
(D) More than one of the above
(E) None of the above

---

**Q21.** India's FIRST pure Green Hydrogen plant was commissioned in:
(A) Mumbai, Maharashtra
(B) Jaisalmer, Rajasthan
(C) Hyderabad (Andhra Pradesh)
(D) More than one of the above
(E) None of the above

---

**Q22.** In IoT architecture, which LAYER is responsible for collecting data from the physical environment using sensors?
(A) Application Layer
(B) Processing/Cloud Layer
(C) PERCEPTION LAYER (Things/Devices Layer)
(D) More than one of the above
(E) None of the above

---

**Q23.** Which IoT wireless technology is best suited for LONG RANGE communication with very LOW POWER consumption (e.g., agriculture IoT in remote areas)?
(A) Bluetooth
(B) WiFi
(C) LoRa (Long Range)
(D) More than one of the above
(E) None of the above

---

**Q24.** GREY Hydrogen differs from GREEN Hydrogen in that:
(A) Grey hydrogen uses water electrolysis; green uses fossil fuels
(B) Grey hydrogen is made from FOSSIL FUELS releasing CO₂; green uses renewable electrolysis
(C) They are different names for the same hydrogen production process
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following CORRECTLY matches the Cloud Service Model to its example?
(A) IaaS → Gmail; PaaS → AWS EC2; SaaS → Heroku
(B) IaaS → AWS EC2; PaaS → Google App Engine; SaaS → Gmail
(C) IaaS → Heroku; PaaS → Salesforce; SaaS → AWS EC2
(D) More than one of the above
(E) None of the above

---
---

### GENERAL STUDIES — 25 MCQs
### Environment + Green Technology

---

**Q26.** Ground-level ozone is:
(A) Beneficial — it protects us from UV radiation
(B) A HARMFUL pollutant that causes respiratory problems
(C) Neutral — neither beneficial nor harmful
(D) More than one of the above
(E) None of the above

---

**Q27.** MINAMATA DISEASE is caused by poisoning from:
(A) Lead (Pb) contamination in water
(B) Cadmium (Cd) from industrial waste
(C) MERCURY (Hg) contamination — industrial effluent in water
(D) More than one of the above
(E) None of the above

---

**Q28.** ITAI-ITAI DISEASE ("ouch-ouch disease") is caused by:
(A) Mercury (Hg) poisoning
(B) Lead (Pb) poisoning
(C) CADMIUM (Cd) poisoning — causes severe bone pain
(D) More than one of the above
(E) None of the above

---

**Q29.** EUTROPHICATION in water bodies is caused by:
(A) Excess plastic waste dumped in rivers
(B) Thermal pollution from power plants
(C) EXCESS NUTRIENTS (nitrogen, phosphorus from fertilizers) causing algal bloom and oxygen depletion
(D) More than one of the above
(E) None of the above

---

**Q30.** BIOMAGNIFICATION refers to:
(A) The decrease in toxin concentration as you move up the food chain
(B) The enlargement of organisms due to genetic modification
(C) The INCREASE in concentration of toxins (like DDT) as you move UP the food chain
(D) More than one of the above
(E) None of the above

---

**Q31.** The MONTREAL PROTOCOL (1987) was specifically designed to:
(A) Reduce carbon dioxide (CO₂) emissions from developed nations
(B) Limit global warming to 2°C above pre-industrial levels
(C) PHASE OUT ozone-depleting substances like CFCs and HCFCs
(D) More than one of the above
(E) None of the above

---

**Q32.** The PARIS AGREEMENT (2015) aims to limit global temperature rise to:
(A) 0.5°C above pre-industrial levels
(B) 5°C above current levels
(C) BELOW 2°C (aiming for 1.5°C) above pre-industrial levels
(D) More than one of the above
(E) None of the above

---

**Q33.** The RAMSAR CONVENTION is related to the protection of:
(A) Endangered species of animals
(B) Tropical rainforests
(C) WETLANDS of international importance
(D) More than one of the above
(E) None of the above

---

**Q34.** The FIRST major United Nations Environment Conference was held in:
(A) Rio de Janeiro in 1992 (Earth Summit)
(B) Kyoto in 1997
(C) STOCKHOLM in 1972 (theme: "Only One Earth")
(D) More than one of the above
(E) None of the above

---

**Q35.** METHANE (CH₄) as a greenhouse gas is:
(A) Less potent than CO₂ in terms of warming potential
(B) Equally potent as CO₂
(C) ABOUT 21 TIMES MORE POTENT than CO₂ as a greenhouse gas
(D) More than one of the above
(E) None of the above

---

**Q36.** INDIA'S FIRST and LARGEST Biosphere Reserve is:
(A) Sundarbans Biosphere Reserve (West Bengal)
(B) Great Nicobar Biosphere Reserve
(C) NILGIRI Biosphere Reserve (Tamil Nadu/Kerala/Karnataka)
(D) More than one of the above
(E) None of the above

---

**Q37.** GIR FOREST NATIONAL PARK in Gujarat is famous for:
(A) Bengal Tiger (only location in India)
(B) One-horned rhinoceros (only location in India)
(C) ASIATIC LION (only natural habitat in India)
(D) More than one of the above
(E) None of the above

---

**Q38.** KAZIRANGA NATIONAL PARK in Assam is primarily known for:
(A) Asiatic Lions
(B) Bengal Tigers only
(C) ONE-HORNED RHINOCEROS (largest population in the world)
(D) More than one of the above
(E) None of the above

---

**Q39.** PROJECT TIGER was launched in India in:
(A) 1947
(B) 1984
(C) 1973 (by Prime Minister Indira Gandhi)
(D) More than one of the above
(E) None of the above

---

**Q40.** INDIA'S FIRST National Park (established 1936) is:
(A) Kaziranga National Park, Assam
(B) Bandipur National Park, Karnataka
(C) JIM CORBETT National Park, Uttarakhand
(D) More than one of the above
(E) None of the above

---

**Q41.** The BHOPAL GAS TRAGEDY (December 1984) was caused by the leakage of:
(A) Carbon monoxide (CO) from a steel plant
(B) Chlorine gas from a water treatment plant
(C) MIC (METHYL ISOCYANATE) from a Union Carbide pesticide plant
(D) More than one of the above
(E) None of the above

---

**Q42.** India's ENVIRONMENTAL PROTECTION ACT (EPA) was enacted in:
(A) 1972 (after Stockholm Conference)
(B) 1984 (same year as Bhopal tragedy)
(C) 1986 (enacted AFTER the Bhopal gas tragedy)
(D) More than one of the above
(E) None of the above

---

**Q43.** The CENTRAL POLLUTION CONTROL BOARD (CPCB) in India is responsible for:
(A) Providing loans for green energy projects
(B) Managing national parks and wildlife reserves
(C) CONTROLLING ENVIRONMENTAL POLLUTION and maintaining quality standards
(D) More than one of the above
(E) None of the above

---

**Q44.** SUSTAINABLE DEVELOPMENT was defined by the BRUNDTLAND COMMISSION in:
(A) 1972
(B) 1992
(C) 1987 — "development that meets needs of present without compromising future generations"
(D) More than one of the above
(E) None of the above

---

**Q45.** India's NATIONAL GREEN HYDROGEN MISSION was launched in:
(A) 2020
(B) 2022
(C) January 2023
(D) More than one of the above
(E) None of the above

---

**Q46.** E-WASTE (Electronic Waste) is dangerous because it contains:
(A) Only plastic which is biodegradable
(B) Radioactive materials only
(C) TOXIC substances like Lead, Mercury, Cadmium, and Chromium
(D) More than one of the above
(E) None of the above

---

**Q47.** The KYOTO PROTOCOL (1997) was primarily focused on:
(A) Protecting wetlands and biodiversity
(B) Phasing out ozone-depleting chemicals
(C) REDUCING GHG emissions from DEVELOPED (industrialized) nations
(D) More than one of the above
(E) None of the above

---

**Q48.** CARBON FOOTPRINT is:
(A) The physical area of carbon deposits underground
(B) The carbon content in the soil of a particular region
(C) TOTAL GHG emissions (in CO₂ equivalent) caused by an individual or organization
(D) More than one of the above
(E) None of the above

---

**Q49.** DDT (Dichlorodiphenyltrichloroethane) is associated with:
(A) Water purification treatment
(B) Nitrogen fixation in agriculture
(C) BIOMAGNIFICATION — accumulates in food chain; causes bird eggshell thinning; now BANNED
(D) More than one of the above
(E) None of the above

---

**Q50.** Which of the following CORRECTLY states multiple facts about Green Hydrogen?
(A) Green Hydrogen = electrolysis of water using renewable energy
(B) Green Hydrogen produces zero carbon emissions
(C) India's National Green Hydrogen Mission targets 5 million tonnes/year by 2030
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY

## ⚠️ MANDATORY: Attempt all 50 questions BEFORE checking!

---

### CS Answers (Q1–Q25):

| Q  | Answer | Reason (one-line)                                                              |
|----|--------|--------------------------------------------------------------------------------|
| 1  | (B)    | IoT = physical devices connected to internet; collect + share data auto        |
| 2  | (C)    | MQTT = primary IoT communication protocol ← PYQ!                              |
| 3  | (C)    | MQTT uses Publish-Subscribe model (not request-response like HTTP)             |
| 4  | (C)    | Broker = central server in MQTT that routes messages                           |
| 5  | (C)    | Bluetooth (5.0) = short-range IoT wireless technology ← PYQ!                  |
| 6  | (B)    | Cloud = pay-as-you-go basis                                                    |
| 7  | (C)    | IaaS = virtual machines + storage + networking (raw infrastructure)            |
| 8  | (C)    | AWS EC2 = classic IaaS example ← PYQ!                                         |
| 9  | (B)    | PaaS targeted at DEVELOPERS (build apps, not manage infrastructure)            |
| 10 | (C)    | Google App Engine + Heroku = PaaS examples ← PYQ!                             |
| 11 | (C)    | SaaS = customer manages NOTHING (provider handles everything)                  |
| 12 | (C)    | Gmail + Salesforce + Office 365 = SaaS examples ← PYQ!                        |
| 13 | (C)    | IaaS > PaaS > SaaS (most to least customer management)                         |
| 14 | (B)    | Private cloud = DEDICATED to ONE organization (public = shared)                |
| 15 | (C)    | Hybrid = combination of public + private cloud                                 |
| 16 | (C)    | Blockchain = decentralized, distributed, immutable ledger ← PYQ!              |
| 17 | (C)    | Blockchain data is IMMUTABLE — cannot be altered after writing                 |
| 18 | (C)    | Previous Hash in each block creates the chain (links blocks)                   |
| 19 | (C)    | Green Hydrogen = electrolysis of water using RENEWABLE energy ← PYQ!          |
| 20 | (A)    | 2H₂O → 2H₂ + O₂ = electrolysis reaction for green hydrogen                    |
| 21 | (C)    | First pure green H₂ plant = Hyderabad, Andhra Pradesh ← PYQ!                  |
| 22 | (C)    | Perception Layer = collects data from physical environment via sensors          |
| 23 | (C)    | LoRa = Long Range + Low Power for remote/agricultural IoT                      |
| 24 | (B)    | Grey H₂ = fossil fuels + CO₂ released; Green H₂ = renewable electrolysis      |
| 25 | (B)    | IaaS→AWS EC2 ✅; PaaS→Google App Engine ✅; SaaS→Gmail ✅ — correct match!      |

---

### GS Answers (Q26–Q50):

| Q  | Answer | Reason (one-line)                                                         |
|----|--------|---------------------------------------------------------------------------|
| 26 | (B)    | Ground-level ozone = HARMFUL pollutant (respiratory problems)             |
| 27 | (C)    | Minamata disease = MERCURY (Hg) poisoning ← PYQ!                         |
| 28 | (C)    | Itai-itai disease = CADMIUM (Cd) poisoning ← PYQ!                        |
| 29 | (C)    | Eutrophication = excess nutrients → algal bloom → oxygen depletion        |
| 30 | (C)    | Biomagnification = toxin concentration INCREASES up the food chain        |
| 31 | (C)    | Montreal Protocol 1987 = phase out CFCs/HCFCs (ozone depleting)          |
| 32 | (C)    | Paris Agreement 2015 = below 2°C (aim 1.5°C) warming limit               |
| 33 | (C)    | Ramsar Convention = WETLANDS protection ← PYQ!                           |
| 34 | (C)    | Stockholm 1972 = FIRST major UN environment conference                    |
| 35 | (C)    | Methane = 21 times MORE POTENT than CO₂ ← PYQ!                           |
| 36 | (C)    | Nilgiri = FIRST and LARGEST biosphere reserve in India ← PYQ!            |
| 37 | (C)    | Gir Forest = ASIATIC LION (only natural habitat in India) ← PYQ!         |
| 38 | (C)    | Kaziranga = ONE-HORNED RHINOCEROS (world's largest population) ← PYQ!    |
| 39 | (C)    | Project Tiger launched 1973 by Indira Gandhi ← PYQ!                      |
| 40 | (C)    | Jim Corbett NP = FIRST national park in India (1936) ← PYQ!              |
| 41 | (C)    | Bhopal gas tragedy = MIC (Methyl Isocyanate) leakage ← PYQ!              |
| 42 | (C)    | EPA India 1986 (after Bhopal tragedy) ← PYQ!                             |
| 43 | (C)    | CPCB = controls environmental pollution in India                          |
| 44 | (C)    | Brundtland Commission 1987 = defined sustainable development ← PYQ!      |
| 45 | (C)    | National Green Hydrogen Mission = January 2023                            |
| 46 | (C)    | E-waste = Lead, Mercury, Cadmium, Chromium (toxic materials)              |
| 47 | (C)    | Kyoto Protocol 1997 = GHG reduction from DEVELOPED nations                |
| 48 | (C)    | Carbon footprint = total GHG emissions in CO₂ equivalent                  |
| 49 | (C)    | DDT = biomagnification; bird eggshell thinning; now banned                |
| 50 | (D)    | ALL THREE statements about Green Hydrogen are correct → Answer (D)        |

---
---

# 🔁 FINAL REVISION NOTES
## 📌 "Last 1-Hour Before Exam" — Ultra-Crisp Format

---

### ⚡ CS — 30 MUST-KNOW FACTS (IoT + Cloud + Blockchain)

```
IoT BASICS:
1.  IoT = physical devices connected to internet; auto data sharing
2.  MQTT = PRIMARY IoT communication protocol ← PYQ! (Publish-Subscribe)
3.  Bluetooth 5.0 = short-range IoT wireless ← PYQ!
4.  LoRa = long-range, low-power IoT (for agriculture, remote areas)
5.  MQTT Broker = middle server routing messages (Publisher→Broker→Subscriber)
6.  IoT applications: Smart home, wearables, healthcare, IIoT, smart city

CLOUD SERVICE MODELS (most tested topic):
7.  IaaS = Infrastructure (Virtual Machines, Storage)
    → User manages: App + Data + OS + Runtime
    → Examples: AWS EC2 ← PYQ!, Azure VMs, Google Compute Engine
8.  PaaS = Platform (Development environment)
    → User manages: App + Data ONLY
    → Examples: Google App Engine ← PYQ!, Heroku, AWS Elastic Beanstalk
9.  SaaS = Software (Ready-to-use apps)
    → User manages: NOTHING
    → Examples: Gmail ← PYQ!, Salesforce ← PYQ!, Office 365, Zoom
10. Management order: IaaS > PaaS > SaaS (IaaS = most, SaaS = least)
11. Memory trick: I-P-S = Infrastructure → Platform → Software

CLOUD DEPLOYMENT MODELS:
12. Public Cloud = shared, cheap, less secure (AWS, Azure, GCP)
13. Private Cloud = dedicated to one org, secure, expensive
14. Hybrid Cloud = combination of public + private ← most enterprise use

BLOCKCHAIN:
15. Blockchain = Distributed Ledger; DECENTRALIZED; IMMUTABLE ← PYQ!
16. Key properties: Decentralized + Distributed + Immutable + Transparent
17. Previous Hash = links blocks together (creates the "chain")
18. Applications: Bitcoin/Cryptocurrency, supply chain, smart contracts
19. "Blockchain is centralized" → FALSE ← classic trap!

GREEN HYDROGEN:
20. Green Hydrogen = ELECTROLYSIS of water using RENEWABLE energy ← PYQ!
21. Formula: 2H₂O → 2H₂ + O₂
22. Zero carbon emissions (renewable electricity used)
23. First pure green H₂ plant = Hyderabad, AP ← PYQ!
24. India's National Green Hydrogen Mission = January 2023; target 5 MT/yr by 2030
25. Grey H₂ = fossil fuels + CO₂; Blue H₂ = fossil + CCS; Green = renewable electrolysis

EXAM TRAPS:
26. "MQTT = same as HTTP" → FALSE (MQTT = publish-subscribe; HTTP = request-response)
27. "AWS EC2 = SaaS" → FALSE (= IaaS!)
28. "Gmail = PaaS" → FALSE (= SaaS!)
29. "Google App Engine = IaaS" → FALSE (= PaaS!)
30. "Blockchain = centralized" → FALSE (= decentralized!)
```

---

### ⚡ GS — 25 MUST-KNOW ENVIRONMENT FACTS

```
POLLUTION:
1.  Ground-level ozone = HARMFUL; Stratospheric ozone = PROTECTIVE ← opposite!
2.  Minamata disease = MERCURY (Hg) poisoning ← PYQ!
3.  Itai-itai disease = CADMIUM (Cd) poisoning ← PYQ!
4.  Eutrophication = excess nutrients → algal bloom → oxygen depletion
5.  Biomagnification = toxin concentration INCREASES up food chain ← PYQ!
6.  DDT = biomagnified; causes bird eggshell thinning; BANNED

INTERNATIONAL AGREEMENTS:
7.  Montreal Protocol 1987 = CFC ban; ozone layer protection ← PYQ!
8.  Kyoto Protocol 1997 = GHG reduction; developed nations ← PYQ!
9.  Paris Agreement 2015 = below 2°C warming; all nations ← PYQ!
10. Ramsar Convention 1971 = WETLANDS protection ← PYQ!
11. Stockholm 1972 = FIRST major UN environment conference ← PYQ!
12. Earth Summit 1992 = Rio de Janeiro; Agenda 21; CBD; UNFCCC

INDIA WILDLIFE:
13. Jim Corbett NP = FIRST NP in India (1936); Uttarakhand ← PYQ!
14. Gir Forest = ASIATIC LION (only location) ← PYQ!
15. Kaziranga = ONE-HORNED RHINO ← PYQ!
16. Sundarbans = Bengal Tiger + Mangroves
17. Nilgiri = FIRST + LARGEST Biosphere Reserve in India ← PYQ!
18. Project Tiger = 1973; Indira Gandhi ← PYQ!
19. Project Elephant = 1992

INDIA ENVIRONMENT LAWS:
20. EPA India = 1986 (after Bhopal gas tragedy) ← PYQ!
21. Bhopal tragedy = MIC (Methyl Isocyanate); December 1984 ← PYQ!
22. CPCB = Central Pollution Control Board (controls pollution in India)

KEY CONCEPTS:
23. Sustainable development definition = Brundtland Commission 1987 ← PYQ!
24. Methane = 21x more potent GHG than CO₂ ← PYQ!
25. Green Hydrogen = electrolysis + renewable energy = zero carbon ← PYQ!
```

---

### ⚡ LAST-MINUTE COMPARISON TABLES

```
CLOUD MODEL  FULL NAME           YOU MANAGE        BEST EXAMPLES
─────────────────────────────────────────────────────────────────────────
IaaS         Infrastructure      App+Data+OS       AWS EC2, Azure VMs
             as a Service        +Runtime
PaaS         Platform            App+Data          Google App Engine,
             as a Service        ONLY              Heroku
SaaS         Software            NOTHING           Gmail, Salesforce,
             as a Service                          Office 365, Zoom
─────────────────────────────────────────────────────────────────────────

IoT WIRELESS   RANGE        POWER     USE CASE
─────────────────────────────────────────────────────────────────────────
Bluetooth 5.0  Short (~100m)  Low     Wearables, smart home ← PYQ
WiFi           Medium         High    Office IoT, smart TVs
Zigbee         Short          V.Low   Smart bulbs, locks
LoRa           Long (km)      V.Low   Agriculture, remote sensors
NFC            Very Short     V.Low   Contactless payments
─────────────────────────────────────────────────────────────────────────

DISEASE          CAUSED BY     MEDIUM
─────────────────────────────────────────────────────────────────────────
Minamata         Mercury (Hg)  Water contamination ← PYQ
Itai-itai        Cadmium (Cd)  Water contamination ← PYQ
─────────────────────────────────────────────────────────────────────────

AGREEMENT        YEAR   FOCUS                    KEY FACT
─────────────────────────────────────────────────────────────────────────
Montreal         1987   CFCs → Ozone layer       Most successful treaty
Kyoto            1997   GHGs → developed nations Legally binding
Paris            2015   Below 2°C warming         NDCs from all nations
Ramsar           1971   Wetlands                 International importance
Stockholm        1972   General environment       FIRST UN env conference
─────────────────────────────────────────────────────────────────────────

NATIONAL PARK    STATE              FAMOUS FOR
─────────────────────────────────────────────────────────────────────────
Jim Corbett      Uttarakhand        FIRST NP in India (1936)
Gir Forest       Gujarat            ASIATIC LION (only location)
Kaziranga        Assam              ONE-HORNED RHINO
Sundarbans       West Bengal        Bengal Tiger + Mangroves
Silent Valley    Kerala             Rare flora/fauna; no roads
Nilgiri BR       TN/Kerala/Karn.    FIRST + LARGEST biosphere reserve
─────────────────────────────────────────────────────────────────────────
```

---

## 🎯 DAY 83 COMPLETE — WHAT YOU'VE MASTERED TODAY

```
CS:   IoT — Definition, MQTT protocol (publish-subscribe, broker),
      Bluetooth 5.0 (short-range IoT), LoRa, IoT Architecture layers,
      IoT applications (smart home/healthcare/industrial/smart city) |
      Cloud Computing — IaaS (AWS EC2) / PaaS (Google App Engine, Heroku) /
      SaaS (Gmail, Salesforce, Office 365) with management level comparison |
      Cloud Deployment — Public / Private / Hybrid |
      Blockchain — decentralized, immutable, distributed ledger, previous hash |
      Green Hydrogen — electrolysis of water, zero carbon, 2H₂O→2H₂+O₂,
      first plant = Hyderabad, National Green Hydrogen Mission 2023

GS:   Environment — Minamata (Hg) / Itai-itai (Cd) diseases |
      Eutrophication, Biomagnification, DDT |
      International agreements (Montreal/Kyoto/Paris/Ramsar/Stockholm) |
      India wildlife (Jim Corbett, Gir, Kaziranga, Nilgiri BR) |
      Project Tiger 1973, EPA 1986, Bhopal tragedy MIC |
      Brundtland Commission 1987, Methane 21x CO₂ |
      Green Hydrogen Mission, Carbon footprint, E-waste

NEXT: Day 84 — Theory of Computation (Turing Machine, Halting Problem,
      Finite Automata) + Low-level Languages (Assembly vs Machine)
      GS: GS Revision
```

---

*Day 83 of 170 | Phase 2: Depth | Week 13: AI, IoT, Emerging Tech & Theory of Computation*
*BPSC TRE 4.0 Preparation | Target: TOP 50 RANK | Score: 130+/150*
