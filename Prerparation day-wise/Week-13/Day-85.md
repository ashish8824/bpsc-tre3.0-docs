# 📅 BPSC TRE 4.0 — DAY 85: WEB TECHNOLOGIES + CYBERSECURITY + AWARDS & RECOGNITIONS
### Week 13 — AI, IoT, Emerging Tech & Theory of Computation
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): CS — HTML/CSS/JS, Server-side scripting, WWW, Cybersecurity
> - Afternoon (1 hr): GS — Awards & Recognitions (Bharat Ratna, Nobel, Padma, Sports)
> - Evening (1.5 hrs): Solve all 50 Mixed MCQs (25 CS + 25 GS)
> - Night (30 min): Read the "Last 1-Hour Before Exam" revision sheet

---

# PART 1: CS RAPID REVISION
## 📘 Web Technologies + Cybersecurity — All Concepts, One Place

---

## 🔷 TOPIC 1: The World Wide Web (WWW) — Origins & Basics

```
WORLD WIDE WEB (WWW) — FOUNDATIONAL FACTS
════════════════════════════════════════════════════════

INVENTOR:       TIM BERNERS-LEE ← PYQ! ← #1 fact to memorize
YEAR INVENTED:  1989 (proposed) / 1991 (publicly launched) ← PYQ!
INSTITUTION:    CERN (European particle physics lab, Geneva)

WHAT TIM BERNERS-LEE CREATED:
  → HTML (HyperText Markup Language)
  → HTTP (HyperText Transfer Protocol)
  → URL (Uniform Resource Locator)
  → First web browser AND first web server

WWW vs INTERNET — KEY DIFFERENCE:
  ┌───────────────────────────────────────────────────────┐
  │ INTERNET = The physical NETWORK (cables, routers,    │
  │            servers connected globally)               │
  │            → Infrastructure (like roads)             │
  │                                                      │
  │ WWW = A SERVICE that RUNS ON the Internet            │
  │       → Collection of web pages accessed via HTTP   │
  │       → One of many services on the Internet        │
  │       → Like cars that USE the roads                │
  └───────────────────────────────────────────────────────┘
  PYQ TRAP: "WWW = Internet" → FALSE (WWW uses the Internet)
            "Internet was invented by Tim Berners-Lee" → FALSE
            (He invented WWW, NOT the Internet itself)

HOW BROWSER DISPLAYS WWW:
  Browser uses HTML (not machine code, not C++) ← PYQ!
  to display web information.

  URL → HTTP request → Web Server → HTML response → Browser renders it

  ┌──────────┐  HTTP request  ┌──────────────┐
  │ BROWSER  │ ─────────────► │  WEB SERVER  │
  │(Chrome/  │                │  (Apache,    │
  │ Firefox) │ ◄───────────── │   Nginx)     │
  └──────────┘  HTML response └──────────────┘
        │
        ▼
  Renders HTML → shows webpage to user
```

---

## 🔷 TOPIC 2: HTML — Structure of Web Pages ← PYQ CORE

```
HTML = HyperText Markup Language
════════════════════════════════════════════════════════

PURPOSE OF HTML: DEFINE THE STRUCTURE of web pages ← PYQ #1!
  → NOT for styling (that's CSS)
  → NOT for behavior/interactivity (that's JavaScript)
  → ONLY for structure and content

THINK OF IT AS: HTML = SKELETON of a webpage
                (bones give structure; clothes = CSS; actions = JS)

HTML WORKS WITH TAGS:
  <html>    = root element
  <head>    = metadata (title, links to CSS/JS)
  <body>    = visible content
  <h1>-<h6> = headings
  <p>       = paragraph
  <a href>  = hyperlink (anchor tag)
  <img>     = image
  <table>   = table
  <form>    = input form
  <div>     = division/container
  <ul><li>  = unordered list

EXAMPLE HTML STRUCTURE:
  <!DOCTYPE html>
  <html>
    <head>
      <title>My Page</title>        ← Not visible on page
      <link rel="stylesheet" href="style.css">  ← Links to CSS
    </head>
    <body>
      <h1>Welcome!</h1>             ← Heading (structure)
      <p>This is a paragraph.</p>   ← Content (structure)
      <a href="page2.html">Click</a> ← Link (structure)
    </body>
  </html>

KEY HTML FACTS:
  → HTML is NOT a programming language — it is a MARKUP language
  → HTML defines STRUCTURE (headings, paragraphs, links, images)
  → HTML file saved as .html or .htm
  → HTML = CLIENT-SIDE technology (runs in browser)

PYQ FACT: "HTML = defines STRUCTURE of web pages" ← TESTED!
          "HTML is used for styling web pages" → FALSE (CSS does styling)
          "Browser uses HTML to display WWW information" ← TESTED!
```

---

## 🔷 TOPIC 3: CSS and JavaScript — Role Separation ← PYQ

```
THE THREE LAYERS OF WEB DEVELOPMENT
════════════════════════════════════════════════════════

  ┌──────────────────────────────────────────────────────────┐
  │                   WEB PAGE                               │
  │                                                          │
  │  ┌────────────────────────────────────────────────────┐  │
  │  │  HTML — STRUCTURE (skeleton)                       │  │
  │  │  "What is on the page"                             │  │
  │  │  headings, paragraphs, lists, images, links        │  │
  │  └────────────────────────────────────────────────────┘  │
  │                        +                                 │
  │  ┌────────────────────────────────────────────────────┐  │
  │  │  CSS — STYLING (appearance)                        │  │
  │  │  "How it looks"                                    │  │
  │  │  colors, fonts, sizes, layout, animations         │  │
  │  └────────────────────────────────────────────────────┘  │
  │                        +                                 │
  │  ┌────────────────────────────────────────────────────┐  │
  │  │  JAVASCRIPT — BEHAVIOR (interactivity)             │  │
  │  │  "What it does"                                    │  │
  │  │  button clicks, form validation, dynamic updates,  │  │
  │  │  animations, API calls                             │  │
  │  └────────────────────────────────────────────────────┘  │
  └──────────────────────────────────────────────────────────┘

CSS = Cascading Style Sheets
  PURPOSE: STYLING web pages (colors, fonts, layout) ← PYQ!
  Example: h1 { color: red; font-size: 24px; }
  → Makes heading red and 24px tall
  → CLIENT-SIDE (runs in browser)
  → File saved as .css

JAVASCRIPT (JS):
  PURPOSE: BEHAVIOR and INTERACTIVITY of web pages ← PYQ!
  Example: When button clicked → show alert, validate form,
           fetch new data without refreshing page
  → CLIENT-SIDE (runs in browser) ← PYQ!
  → NOT a compiled language (interpreted in browser)
  → File saved as .js

IMPORTANT: ALL THREE (HTML, CSS, JavaScript) are CLIENT-SIDE technologies
  = They run in the USER'S BROWSER, not on the server ← PYQ!

PYQ COMPARISON TABLE:
  Technology  │ Purpose        │ Side    │ Example
  ────────────┼────────────────┼─────────┼──────────────────────
  HTML        │ STRUCTURE      │ Client  │ <h1>, <p>, <a>, <img>
  CSS         │ STYLING        │ Client  │ color:red, font-size
  JavaScript  │ BEHAVIOR       │ Client  │ onClick, form check

PYQ TRAPS:
  "CSS defines structure of web page" → FALSE (HTML defines structure)
  "JavaScript is server-side" → FALSE (client-side!)
  "HTML is used for styling" → FALSE (CSS is for styling)
```

---

## 🔷 TOPIC 4: Server-Side vs Client-Side Technologies ← PYQ

```
SERVER-SIDE vs CLIENT-SIDE SCRIPTING
════════════════════════════════════════════════════════

DIAGRAM — Request-Response Cycle:

  ┌─────────────────┐                    ┌─────────────────┐
  │   USER'S        │   HTTP Request     │    WEB SERVER   │
  │   BROWSER       │ ─────────────────► │                 │
  │                 │                    │  Server-side    │
  │  CLIENT-SIDE    │                    │  code runs HERE │
  │  CODE RUNS HERE │ ◄───────────────── │  (PHP, Python,  │
  │  (HTML, CSS, JS)│   HTML Response    │   Node.js, etc) │
  └─────────────────┘                    └─────────────────┘

CLIENT-SIDE (runs in USER'S BROWSER):
  ✅ HTML       → structure
  ✅ CSS        → styling
  ✅ JavaScript → behavior/interactivity
  These are downloaded from server and run in browser

SERVER-SIDE (runs on WEB SERVER — not in browser):
  ✅ PHP             ← PYQ! ← most common server-side language
  ✅ Python          (with Flask or Django framework) ← PYQ!
  ✅ Node.js         (JavaScript runtime on server) ← PYQ!
  ✅ ASP.NET         (Microsoft's server-side technology) ← PYQ!
  ✅ JSP/Java        (Java Server Pages)
  ✅ Ruby on Rails   (Ruby framework)

NOT SERVER-SIDE (common trap):
  ❌ HTML       = client-side only
  ❌ CSS        = client-side only
  ❌ JavaScript = primarily client-side (Node.js = exception where JS
                  BECOMES server-side — important nuance!)

KEY USES OF SERVER-SIDE:
  → Database queries (fetch user data from DB)
  → Authentication (check username/password)
  → Generate dynamic HTML based on database
  → File uploads and processing
  → E-commerce transactions

PHP SPECIFICALLY:
  = Hypertext Preprocessor
  = Most widely used server-side scripting language ← PYQ!
  = Originally "Personal Home Page" tools
  = File extension: .php
  = Used by: WordPress (75% of websites use PHP)
  = Runs on server → generates HTML → sends to browser

PYQ FACTS:
  "Server-side scripting: PHP, Python, Node.js, ASP.NET" ← TESTED!
  "HTML, CSS, JavaScript = NOT server-side" ← TESTED!
  "PHP = server-side; HTML = client-side" ← TESTED!
```

---

## 🔷 TOPIC 5: Cybersecurity — Types of Malware ← PYQ CORE

```
CYBERSECURITY — MALWARE TYPES
════════════════════════════════════════════════════════

MALWARE = MALicious softWARE
= Software designed to HARM, DISRUPT, or gain unauthorized
  access to computer systems

TYPE 1: VIRUS ← PYQ!
  ┌──────────────────────────────────────────────────────┐
  │ DEFINITION: Malicious code that ATTACHES ITSELF to  │
  │             a HOST FILE and REPLICATES when the     │
  │             file is executed                        │
  │                                                     │
  │ KEY FEATURES:                                       │
  │  → NEEDS A HOST FILE to spread (like biological    │
  │    virus needs a host organism)                    │
  │  → Spreads when infected file is RUN/OPENED         │
  │  → Can corrupt or delete files                     │
  │  → Does NOT spread by itself over network          │
  │    (needs human action — copy, run infected file)  │
  │                                                     │
  │ EXAMPLE: ILOVEYOU virus, Melissa virus             │
  │ ANALOGY: A parasite (needs a host to survive)      │
  └──────────────────────────────────────────────────────┘

TYPE 2: WORM ← PYQ!
  ┌──────────────────────────────────────────────────────┐
  │ DEFINITION: Self-replicating malware that spreads   │
  │             OVER NETWORKS WITHOUT needing a host    │
  │             file or human action                    │
  │                                                     │
  │ KEY FEATURES:                                       │
  │  → SELF-REPLICATING (spreads on its own)           │
  │  → NO HOST FILE needed ← key difference from Virus │
  │  → Spreads via NETWORK (email, internet)           │
  │  → Consumes NETWORK BANDWIDTH (major impact)       │
  │  → Can carry a payload (dangerous code)            │
  │                                                     │
  │ EXAMPLE: WannaCry worm, Conficker worm             │
  │ ANALOGY: An organism that multiplies on its own    │
  └──────────────────────────────────────────────────────┘

TYPE 3: TROJAN HORSE ← PYQ!
  ┌──────────────────────────────────────────────────────┐
  │ DEFINITION: Malware DISGUISED as legitimate/useful  │
  │             software to trick users into installing │
  │                                                     │
  │ KEY FEATURES:                                       │
  │  → DISGUISED as legitimate software ← key feature │
  │  → User voluntarily installs it (tricked!)        │
  │  → Does NOT replicate itself (different from virus)│
  │  → Once inside, opens BACKDOOR for attacker       │
  │  → Can steal data, install more malware           │
  │                                                     │
  │ EXAMPLE: "Free game download" that is actually     │
  │          a keylogger stealing passwords            │
  │ ANALOGY: Trojan Horse from Greek mythology —      │
  │          enemy hidden inside a "gift"              │
  └──────────────────────────────────────────────────────┘

TYPE 4: RANSOMWARE ← PYQ!
  ┌──────────────────────────────────────────────────────┐
  │ DEFINITION: Malware that ENCRYPTS victim's data    │
  │             and DEMANDS PAYMENT (ransom) to        │
  │             restore access                         │
  │                                                     │
  │ KEY FEATURES:                                       │
  │  → ENCRYPTS files (victim cannot access own data) │
  │  → DEMANDS RANSOM (usually in cryptocurrency)     │
  │  → Most financially damaging malware type        │
  │  → Spreads via phishing emails or vulnerabilities │
  │                                                     │
  │ FAMOUS EXAMPLES:                                   │
  │  → WannaCry (2017) — affected 200,000+ computers  │
  │  → Petya/NotPetya, CryptoLocker                   │
  │                                                     │
  │ ANALOGY: Kidnapper locks your data and demands     │
  │          money for the key                        │
  └──────────────────────────────────────────────────────┘

TYPE 5: SPYWARE
  = Secretly MONITORS user activity (keystrokes, browsing)
  = Sends data to attacker WITHOUT user's knowledge
  = Different from Trojan (Trojan = disguised delivery mechanism;
    Spyware = surveillance tool)

TYPE 6: ADWARE
  = Shows UNWANTED ADVERTISEMENTS
  = Less dangerous than others; annoying

MALWARE COMPARISON TABLE:
  ┌────────────────────────────────────────────────────────────────┐
  │ Type      │ Key Feature        │ Spreads How?  │ Main Damage  │
  ├───────────┼────────────────────┼───────────────┼──────────────┤
  │ Virus     │ NEEDS HOST FILE    │ Infected file │ Corrupts     │
  │           │ Attaches to files  │ execution     │ files        │
  ├───────────┼────────────────────┼───────────────┼──────────────┤
  │ Worm      │ SELF-REPLICATING   │ NETWORK       │ Bandwidth    │
  │           │ No host needed     │ (auto-spread) │ consumption  │
  ├───────────┼────────────────────┼───────────────┼──────────────┤
  │ Trojan    │ DISGUISED as       │ User installs │ Backdoor     │
  │           │ legitimate app     │ willingly     │ access       │
  ├───────────┼────────────────────┼───────────────┼──────────────┤
  │ Ransomware│ ENCRYPTS data,     │ Phishing/     │ Data locked; │
  │           │ demands ransom     │ network       │ financial    │
  └───────────┴────────────────────┴───────────────┴──────────────┘

PYQ TRAPS:
  "Virus spreads over network without host" → FALSE (that's WORM)
  "Worm needs a host file" → FALSE (Virus needs host file)
  "Trojan is self-replicating" → FALSE (Trojan does NOT replicate)
  "Ransomware = encrypts data + demands ransom" → TRUE ✅
```

---

## 🔷 TOPIC 6: Other Cybersecurity Threats ← PYQ

```
PHISHING
════════════════════════════════════════════════════════
= Fraudulent EMAILS/MESSAGES that appear to be from
  legitimate sources (banks, Google, Amazon) to TRICK
  users into revealing SENSITIVE INFORMATION
  (passwords, credit card numbers, OTPs)

HOW PHISHING WORKS:
  Attacker sends email:
  "Your bank account is at risk! Click here to verify:
   www.fake-bank-login.com"

  Victim clicks → goes to FAKE website (looks real)
  Victim enters username + password
  Attacker STEALS credentials!

TYPES OF PHISHING:
  Spear Phishing = TARGETED phishing (specific person/org)
  Whaling        = Phishing targeting HIGH-LEVEL executives (CEO/CFO)
  Vishing        = Voice phishing (phone calls)
  Smishing       = SMS phishing (text messages)

PYQ FACT: Phishing = fraudulent emails to steal credentials ← TESTED!
══════════════════════════════════════════════════════

FIREWALL
════════════════════════════════════════════════════════
= A NETWORK SECURITY DEVICE (hardware or software) that
  MONITORS and FILTERS incoming/outgoing network traffic
  based on predefined security RULES

DIAGRAM — Firewall Position:

  INTERNET          FIREWALL             INTERNAL NETWORK
  (Untrusted)   ┌──────────────┐         (Trusted)
       ─────────►│   FIREWALL   │────────► Company PCs
  All traffic  │  ALLOW/BLOCK  │  Only allowed
               │  based on     │  traffic passes
               │  rules        │
               └──────────────┘
                    Blocks:
                    → Suspicious IPs
                    → Blocked ports
                    → Malicious packets

TYPES OF FIREWALLS:
  Packet Filter Firewall = checks packet headers (IP/port)
  Stateful Firewall      = tracks connection state
  Application Firewall   = inspects application-level traffic
  Next-Gen Firewall (NGFW) = combines all + deep inspection

PYQ FACT: Firewall = monitors + filters network traffic ← TESTED!
══════════════════════════════════════════════════════

SNIFFERS (Packet Sniffers)
════════════════════════════════════════════════════════
= Tools that CAPTURE and analyze network packets
  (can intercept data traveling on network)

PREVENTION: SWITCHED NETWORKS ← PYQ!
  (Switched networks send packets only to intended recipient;
   HUB-based networks broadcast to everyone — easier to sniff)

PYQ FACT: "Sniffers are prevented by SWITCHED NETWORKS" ← TESTED!
══════════════════════════════════════════════════════

SYSTEM INTEGRITY BREACH
════════════════════════════════════════════════════════
= When FULL ACCESS RIGHTS are given to ALL USERS ← PYQ!
= Violates the principle of "least privilege"
  (users should only have access to what they need)

PYQ FACT: "System integrity breach = full access rights for all users"
          ← TESTED in BPSC TRE!
══════════════════════════════════════════════════════

OTHER KEY SECURITY CONCEPTS:
  ┌──────────────────────────────────────────────────────────┐
  │ ENCRYPTION: Converting data into unreadable format     │
  │   → Symmetric encryption: SAME key for encrypt/decrypt │
  │     (AES = Advanced Encryption Standard) ← PYQ!       │
  │   → Asymmetric: Different keys (public/private key)   │
  │     (RSA algorithm) ← PYQ!                            │
  ├──────────────────────────────────────────────────────────┤
  │ PUBLIC KEY CRYPTOGRAPHY (Asymmetric):                  │
  │   → PUBLIC key = used to ENCRYPT (share openly)       │
  │   → PRIVATE key = used to DECRYPT (keep SECRET)       │
  │   → RECEIVER uses private key to decrypt ← PYQ!       │
  │   PYQ TRAP: "Sender uses private key" → FALSE         │
  │             "Receiver uses private key" → TRUE ✅      │
  ├──────────────────────────────────────────────────────────┤
  │ SSL/TLS: Secure Sockets Layer / Transport Layer Security│
  │   → Encrypts data between browser and server          │
  │   → HTTPS = HTTP + SSL/TLS encryption ← PYQ!         │
  │   → Padlock icon in browser = SSL active              │
  ├──────────────────────────────────────────────────────────┤
  │ DOS / DDOS Attack:                                     │
  │   DoS  = Denial of Service (single attacker floods    │
  │          server with requests → crashes it)           │
  │   DDoS = DISTRIBUTED DoS (many computers attack       │
  │          simultaneously — harder to block)            │
  └──────────────────────────────────────────────────────────┘
```

---

## 🔷 TOPIC 7: Web Security — Additional PYQ Facts

```
WEB SECURITY ADDITIONAL FACTS
════════════════════════════════════════════════════════

SQL INJECTION:
  = Attacker inserts MALICIOUS SQL CODE into input fields
  = Example: Login field with: ' OR '1'='1
  = Tricks database into giving unauthorized access
  = Prevention: Input validation, parameterized queries

CROSS-SITE SCRIPTING (XSS):
  = Attacker injects MALICIOUS JAVASCRIPT into web pages
    that other users then view
  = Steals cookies, session tokens, redirects users

PING COMMAND:
  = Checks IP-LEVEL connectivity (not port-level) ← PYQ!
  = Tests if a host is reachable on network
  = Uses ICMP (Internet Control Message Protocol)
  PYQ FACT: "Ping checks IP-level, NOT port-level connectivity" ← TESTED!

COOKIES:
  = Small data files stored by BROWSER on user's computer
  = Used for: Session management, user preferences, tracking
  = Sent with every HTTP request to same domain

HTTP vs HTTPS:
  HTTP  = Hypertext Transfer Protocol (port 80) — NOT encrypted
  HTTPS = HTTP Secure (port 443) — ENCRYPTED with SSL/TLS ← PYQ!

HTTPS shows PADLOCK in browser address bar.
  PYQ FACT: "HTTPS = HTTP + SSL/TLS encryption" ← TESTED!

COMMON PORT NUMBERS:
  ┌───────────────────────────────────────────────────┐
  │ Protocol  │ Port  │ Purpose                       │
  ├───────────┼───────┼───────────────────────────────┤
  │ HTTP      │  80   │ Web traffic (unencrypted)     │
  │ HTTPS     │  443  │ Secure web traffic            │
  │ FTP       │  21   │ File Transfer Protocol        │
  │ SSH       │  22   │ Secure Shell (remote login)   │
  │ SMTP      │  25   │ Email sending                 │
  │ DNS       │  53   │ Domain name resolution        │
  │ POP3      │  110  │ Email receiving               │
  │ IMAP      │  143  │ Email access (keep on server) │
  └───────────┴───────┴───────────────────────────────┘
  PYQ MOST TESTED: HTTP=80, HTTPS=443, FTP=21, SSH=22, SMTP=25
```

---

## 🔷 TOPIC 8: E-Commerce Security + Digital Concepts

```
E-COMMERCE AND DIGITAL CONCEPTS — PYQ FACTS
════════════════════════════════════════════════════════

DIGITAL SIGNATURE:
  = Electronic equivalent of a HANDWRITTEN SIGNATURE
  = Uses ASYMMETRIC CRYPTOGRAPHY (private key of SENDER)
  = Provides: Authentication + Non-repudiation + Integrity
  
  HOW IT WORKS:
    Sender SIGNS with their PRIVATE KEY
    Receiver VERIFIES with sender's PUBLIC KEY
  
  NOTE: Opposite of encryption!
    Encryption: PUBLIC key encrypts; PRIVATE key decrypts
    Digital Signature: PRIVATE key signs; PUBLIC key verifies
  
  PYQ TRAP: "Digital signature uses receiver's private key" → FALSE
            Digital sig = SENDER's private key ← tested!

DIGITAL CERTIFICATE:
  = Electronic document that PROVES IDENTITY of a website/person
  = Issued by a trusted CA (Certificate Authority)
  = Contains: Public key + Identity info + CA's signature
  = Used in HTTPS connections

CYBER LAWS IN INDIA:
  IT Act 2000 = Information Technology Act ← PYQ!
  = Main law governing cybercrime in India
  = Provides legal framework for electronic transactions
  = Amended in 2008 to include cybercrime provisions
  
  Key sections:
  Section 66 = Hacking ← PYQ!
  Section 66A = Offensive messages (struck down 2015)
  Section 67 = Obscene electronic content
  Section 43 = Unauthorized computer access (civil)

PYQ FACT: "IT Act 2000 = governs cybercrime in India" ← TESTED!
          "Section 66 of IT Act = Hacking" ← TESTED!
```

---

## 📊 CS MASTER COMPARISON TABLE — Day 85

```
CONCEPT               KEY FACT                              COMMON TRAP
──────────────────────────────────────────────────────────────────────────
WWW Inventor          TIM BERNERS-LEE (1989) ← PYQ!        "Al Gore invented
                                                            internet" ≠ WWW
HTML purpose          STRUCTURE of web pages ← PYQ!        "HTML = styling"=FALSE
CSS purpose           STYLING (colors, fonts, layout)       "CSS = structure"=FALSE
JavaScript purpose    BEHAVIOR/INTERACTIVITY                "JS = server-side"=FALSE
                                                            (mostly client-side)
All three (HTML/CSS/JS) CLIENT-SIDE technologies ← PYQ!    "JS = server-side"=FALSE
Server-side languages  PHP, Python, Node.js, ASP.NET ← PYQ "HTML = server-side"=FALSE
Browser uses           HTML to display WWW info ← PYQ!     "Machine code"=FALSE
Virus                 Needs HOST FILE; replicates when      "Virus self-spreads
                      file executed                         on network"=FALSE(=Worm)
Worm                  SELF-REPLICATING; no host file;       "Worm needs host"=FALSE
                      spreads via network
Trojan                DISGUISED as legitimate software       "Trojan replicates"=FALSE
Ransomware            ENCRYPTS data + demands RANSOM         "Ransomware=virus"=imprecise
Phishing              Fraudulent emails to steal creds       "Phishing=hacking"=incomplete
Firewall              Monitors + FILTERS network traffic     "Firewall=antivirus"=FALSE
Sniffers              Prevented by SWITCHED NETWORKS ← PYQ! "Hub prevents sniff"=FALSE
System integrity      FULL ACCESS RIGHTS for all users       "No access=integrity
breach                = integrity breach ← PYQ!             breach"=FALSE
Private key           RECEIVER uses to DECRYPT ← PYQ!      "Sender uses private"=FALSE
Digital Signature     SENDER uses PRIVATE KEY to sign        "Receiver's key signs"=FALSE
HTTPS                 HTTP + SSL/TLS encryption (port 443)   "HTTP = secure"=FALSE
IT Act 2000           Governs cybercrime in India ← PYQ!    "IT Act 1999"=FALSE
Ping                  Checks IP-level; NOT port-level ← PYQ "Ping checks ports"=FALSE
──────────────────────────────────────────────────────────────────────────
```

---
---

# PART 2: GS RAPID REVISION
## 🏆 Awards & Recognitions — India's Highest Honours

---

## 🔷 AWARDS TOPIC 1: Bharat Ratna — India's Highest Civilian Award

```
BHARAT RATNA — INDIA'S HIGHEST CIVILIAN HONOUR
════════════════════════════════════════════════════════

ESTABLISHED:  1954
AWARDED FOR:  Exceptional service toward advancement of Art,
              Literature, Science, OR Public Service
SHAPE:        Peepal leaf design (not a medal — it's a decoration)
GIVEN BY:     President of India

FIRST RECIPIENTS (1954):
  C. Rajagopalachari (Rajaji)  ← PYQ!
  Dr. S. Radhakrishnan          ← PYQ!
  Dr. C.V. Raman                ← PYQ!

SELECTED BHARAT RATNA RECIPIENTS (PYQ-tested):
  ┌────────────────────────────────────────────────────────────┐
  │ Year  │ Recipient                  │ Known For             │
  ├───────┼────────────────────────────┼───────────────────────┤
  │ 1955  │ Dr. M. Visvesvaraya        │ Engineer; Mysore Dam  │
  │ 1955  │ Jawaharlal Nehru           │ First PM of India     │
  │ 1971  │ Indira Gandhi              │ First female PM       │
  │ 1975  │ V.V. Giri                  │ 4th President of India│
  │ 1976  │ K. Kamaraj                 │ "Kingmaker" of India  │
  │ 1980  │ Mother Teresa              │ Humanitarian service  │
  │ 1983  │ Vinoba Bhave               │ Bhoodan Movement      │
  │ 1987  │ A.G.K. Khan Abdul          │ Freedom fighter       │
  │       │ Ghaffar Khan ("Frontier   │ (first non-Indian!)   │
  │       │  Gandhi")                  │                       │
  │ 1988  │ M.G. Ramachandran (MGR)   │ Actor + TN CM         │
  │ 1990  │ Dr. B.R. Ambedkar          │ Constitution framer   │
  │       │ (posthumous)              │ ← PYQ!                │
  │ 1990  │ Nelson Mandela             │ Anti-apartheid (2nd   │
  │       │                            │ non-Indian!)          │
  │ 1991  │ Rajiv Gandhi (posthumous) │ PM of India           │
  │ 1991  │ Sardar Vallabhbhai Patel  │ Iron Man of India ←PYQ│
  │ 1992  │ J.R.D. Tata                │ Industrialist         │
  │ 1997  │ Gulzarilal Nanda           │ Acting PM (twice)     │
  │ 1997  │ Aruna Asaf Ali (posthumous)│ Quit India heroine    │
  │ 1997  │ A.P.J. Abdul Kalam        │ Missile Man ← PYQ!   │
  │ 1998  │ M.S. Subbulakshmi          │ Carnatic vocalist     │
  │ 1998  │ Chidambaram Subramaniam   │ Green Revolution       │
  │ 1999  │ Amartya Sen                │ Nobel (Economics) ←PYQ│
  │ 1999  │ Ravi Shankar               │ Sitar maestro         │
  │ 2001  │ Lata Mangeshkar            │ Singer ← PYQ!         │
  │ 2001  │ Bismillah Khan             │ Shehnai maestro       │
  │ 2014  │ Sachin Tendulkar           │ Cricket ← PYQ!        │
  │       │ (youngest ever at 40)     │ (first sportsperson!) │
  │ 2014  │ C.N.R. Rao                 │ Scientist             │
  │ 2019  │ Pranab Mukherjee           │ 13th President ← PYQ! │
  │ 2019  │ Nanaji Deshmukh (posthum) │ Social activist        │
  │ 2019  │ Bhupen Hazarika (posthum) │ Assamese singer        │
  │ 2024  │ Karpoori Thakur (posthum) │ Bihar CM ← Bihar PYQ! │
  │ 2024  │ Chaudhary Charan Singh     │ Former PM              │
  │ 2024  │ P.V. Narasimha Rao         │ Former PM (economic   │
  │       │                            │  reforms)             │
  │ 2024  │ M.S. Swaminathan           │ Green Revolution      │
  │       │ (posthumous)              │ Father                │
  │ 2024  │ Lal Krishna Advani         │ BJP leader            │
  └────────────────────────────────────────────────────────────┘

PYQ KEY FACTS:
  FIRST non-Indian: Khan Abdul Ghaffar Khan (1987) ← PYQ!
  FIRST sportsperson: Sachin Tendulkar (2014) ← PYQ!
  FIRST posthumous: to multiple recipients
  Bihar-related: Karpoori Thakur 2024 ← Bihar PYQ!
  Sachin = youngest ever recipient (at age 40) ← PYQ!
```

---

## 🔷 AWARDS TOPIC 2: Padma Awards

```
PADMA AWARDS — INDIA'S CIVILIAN HONOURS
════════════════════════════════════════════════════════

THREE LEVELS (in order of precedence):
  ┌──────────────────────────────────────────────────────┐
  │ 1. PADMA VIBHUSHAN  = Exceptional and distinguished  │
  │                      service (2nd highest civilian)  │
  │ 2. PADMA BHUSHAN    = Distinguished service of high  │
  │                      order                          │
  │ 3. PADMA SHRI       = Distinguished service in any  │
  │                      field (most common)            │
  └──────────────────────────────────────────────────────┘

ESTABLISHED: 1954 (same year as Bharat Ratna)
ANNOUNCED:   Republic Day (January 26) every year
GIVEN BY:    President of India

FIELDS: Art, Literature, Science, Sports, Medicine, Social Work,
        Public Affairs, Civil Service

IMPORTANT NOTES:
  → Government servants in active service generally
    NOT eligible for Padma Awards ← PYQ!
  → Announced on Republic Day (Jan 26) ← PYQ!
  → Highest → Padma Vibhushan; Lowest → Padma Shri

PYQ TRAP: "Padma Shri = highest Padma award" → FALSE
          (Padma Vibhushan = highest Padma award)
```

---

## 🔷 AWARDS TOPIC 3: Nobel Prizes — Indian Winners

```
NOBEL PRIZE WINNERS OF INDIAN ORIGIN ← PYQ TABLE
════════════════════════════════════════════════════════

  ┌────────────────────────────────────────────────────────────┐
  │ Name              │ Year │ Field        │ Achievement      │
  ├───────────────────┼──────┼──────────────┼──────────────────┤
  │ Rabindranath      │ 1913 │ Literature   │ Gitanjali ← PYQ! │
  │ Tagore            │      │              │ FIRST Asian Nobel│
  ├───────────────────┼──────┼──────────────┼──────────────────┤
  │ C.V. Raman        │ 1930 │ Physics      │ Raman Effect     │
  │                   │      │              │ ← PYQ!           │
  ├───────────────────┼──────┼──────────────┼──────────────────┤
  │ Har Gobind        │ 1968 │ Medicine     │ Genetic code     │
  │ Khorana           │      │              │ research         │
  ├───────────────────┼──────┼──────────────┼──────────────────┤
  │ Mother Teresa     │ 1979 │ Peace        │ Humanitarian     │
  │                   │      │              │ ← PYQ!           │
  ├───────────────────┼──────┼──────────────┼──────────────────┤
  │ S. Chandrasekhar  │ 1983 │ Physics      │ Chandrasekhar    │
  │                   │      │              │ limit (stars)    │
  ├───────────────────┼──────┼──────────────┼──────────────────┤
  │ Amartya Sen       │ 1998 │ Economics    │ Welfare economics│
  │                   │      │              │ ← PYQ!           │
  ├───────────────────┼──────┼──────────────┼──────────────────┤
  │ V.S. Naipaul      │ 2001 │ Literature   │ Indo-Trinidadian │
  ├───────────────────┼──────┼──────────────┼──────────────────┤
  │ Venkatraman       │ 2009 │ Chemistry    │ Ribosome         │
  │ Ramakrishnan      │      │              │ structure        │
  ├───────────────────┼──────┼──────────────┼──────────────────┤
  │ Kailash           │ 2014 │ Peace        │ Child rights ←PYQ│
  │ Satyarthi         │      │              │ BACPAN BACHAO    │
  └────────────────────────────────────────────────────────────┘

PYQ KEY FACTS:
  FIRST Nobel (India) = RABINDRANATH TAGORE (Literature, 1913) ← PYQ!
  FIRST Physics Nobel (India) = C.V. RAMAN (1930) ← PYQ!
  FIRST Asian Nobel = Rabindranath Tagore ← PYQ!
  "Raman Effect" = C.V. Raman's discovery ← PYQ!
  Kailash Satyarthi = Peace Nobel 2014 (Bacpan Bachao Andolan)
```

---

## 🔷 AWARDS TOPIC 4: Sports Awards (India)

```
NATIONAL SPORTS AWARDS — INDIA
════════════════════════════════════════════════════════

MAJOR ARJUNA AWARD:
  = Awarded for OUTSTANDING PERFORMANCE in sports
  = Established: 1961
  = Given by: Ministry of Youth Affairs and Sports
  = For: Athletes who showed consistency over 4 years

RAJIV GANDHI KHEL RATNA AWARD:
  (Now renamed: MAJOR DHYAN CHAND KHEL RATNA AWARD — 2021)
  = HIGHEST sports honour in India ← PYQ!
  = Named after Major Dhyan Chand (Hockey legend) in 2021
  = Previously named after Rajiv Gandhi
  = Annual award for most spectacular achievement

DRONACHARYA AWARD:
  = Awarded to SPORTS COACHES ← PYQ!
  = For producing medal-winning athletes

DHYAN CHAND AWARD:
  = For LIFETIME ACHIEVEMENT in sports ← PYQ!

KEY PYQ FACTS:
  "Highest sports award India = Major Dhyan Chand Khel Ratna" ← PYQ!
  "Dronacharya Award = for COACHES" ← PYQ!
  "Arjuna Award = for athletes (established 1961)" ← PYQ!
  "Dhyan Chand Award = lifetime achievement" ← PYQ!

FAMOUS DHYAN CHAND FACTS:
  = "Wizard of Hockey" ← PYQ!
  = Birth date: 29 August = NATIONAL SPORTS DAY ← PYQ!
  = Played in three Olympics (1928, 1932, 1936) — all GOLD medals
  = Scored 570 goals in international hockey

CRICKET AWARDS:
  ICC Cricketer of Year: Wisden Trophy + ICC awards
  Sachin Tendulkar = FIRST sportsperson to receive BHARAT RATNA (2014)
```

---

## 🔷 AWARDS TOPIC 5: Bihar-Specific Awards & Recognitions

```
BIHAR — AWARDS AND PERSONALITIES ← HIGH PYQ PRIORITY
════════════════════════════════════════════════════════

KARPOORI THAKUR:
  = Former Chief Minister of Bihar (twice: 1970-71, 1977-79)
  = Known as "Jan Nayak" (People's Leader) ← PYQ!
  = Awarded BHARAT RATNA (posthumously) in 2024 ← PYQ!
  = Pioneer of reservation for backward classes in Bihar
  = Karpoori Thakur formula = OBC reservation in Bihar

JAYAPRAKASH NARAYAN (JP):
  = "Loknayak" (People's Leader) ← PYQ!
  = Led the TOTAL REVOLUTION movement (1974) against Indira Gandhi
  = Bihar's most famous freedom fighter + social reformer
  = Co-founded Bihar Socialist Party ← Day 84 PYQ!
  = Magsaysay Award winner (1965) ← PYQ!
  = NEVER became PM despite huge popularity

RAJENDRA PRASAD:
  = FIRST PRESIDENT of India (1950-1962) ← PYQ!
  = From Bihar (Zeradei, Siwan district) ← PYQ!
  = President of Constituent Assembly (framed Constitution)
  = Bharat Ratna recipient ← PYQ!

ANUGRAH NARAYAN SINHA:
  = First Finance Minister of Bihar ← PYQ!
  = "Bihar Vibhushan"
  = Bihari leader of freedom struggle

BABU VEER KUNWAR SINGH:
  = Hero of 1857 revolt from Bihar (Jagdishpur, Bhojpur) ← PYQ!
  = Led revolt against British at age 80+
  = Symbol of Bihar's contribution to 1857 revolt

DR. RAJENDRA PRASAD AWARD (Bihar):
  = State award of Bihar named after first President

PYQ FACT: "Karpoori Thakur = Jan Nayak; Bihar CM; Bharat Ratna 2024" ← Bihar PYQ!
          "JP = Loknayak; Total Revolution; Magsaysay Award" ← PYQ!
          "Rajendra Prasad = First President of India; from Bihar" ← PYQ!
```

---

## 📊 GS MASTER SHORTCUT TABLE — Day 85

```
TOPIC                  KEY FACT                              TRAP
──────────────────────────────────────────────────────────────────────
Bharat Ratna started   1954                                   "1947" = FALSE
First Bharat Ratna     C. Rajagopalachari, S. Radhakrishnan,  Only one name = incomplete
(1954)                 C.V. Raman (THREE in 1954)
First non-Indian BR    Khan Abdul Ghaffar Khan 1987           "Nelson Mandela first"=FALSE
First sportsperson BR  Sachin Tendulkar 2014                  "Dhyan Chand"=FALSE
Karpoori Thakur        Bharat Ratna 2024; Jan Nayak; Bihar CM "Bharat Ratna 2020"=FALSE
Rajendra Prasad        FIRST PRESIDENT of India; from Bihar   "First PM"=FALSE
JP Narayan             Loknayak; Magsaysay 1965; Bihar        "Bharat Ratna"=FALSE (died
                                                              before receiving it)
1913 Nobel             TAGORE (Literature); First Asian Nobel  "1912" = FALSE
1930 Nobel             C.V. RAMAN (Physics); Raman Effect     "CV Raman=Chemistry"=FALSE
1998 Nobel             AMARTYA SEN (Economics)                "Literature"=FALSE
2014 Nobel Peace       KAILASH SATYARTHI (child rights)       "2013" = FALSE
Highest sports award   Major Dhyan Chand Khel Ratna Award     "Arjuna Award"=FALSE
                       (renamed from Rajiv Gandhi in 2021)
Dronacharya Award      For COACHES ← PYQ!                     "For athletes"=FALSE
Dhyan Chand Award      LIFETIME ACHIEVEMENT in sports         "Best player"=imprecise
National Sports Day    29 August (Dhyan Chand's birthday)     "15 August"=FALSE
Dhyan Chand nickname   "Wizard of Hockey"                     "Wizard of Cricket"=FALSE
Padma Vibhushan        HIGHEST of three Padma awards          "Padma Shri=highest"=FALSE
IT Act India           IT Act 2000; Section 66 = Hacking      "1999" = FALSE
──────────────────────────────────────────────────────────────────────
```

---
---

# PART 3: PRACTICE QUESTIONS
## 📝 MIXED MCQs — Day 85 Topics

---

### COMPUTER SCIENCE — 25 MCQs

---

**Q1.** The WORLD WIDE WEB (WWW) was invented by:
(A) Bill Gates
(B) Vint Cerf
(C) TIM BERNERS-LEE (1989, at CERN)
(D) More than one of the above
(E) None of the above

---

**Q2.** The PRIMARY PURPOSE of HTML in web development is to:
(A) Add styling and visual design to web pages (colors, fonts, layout)
(B) Provide interactivity and behavior (button clicks, form validation)
(C) DEFINE THE STRUCTURE of web pages (headings, paragraphs, links)
(D) More than one of the above
(E) None of the above

---

**Q3.** A web BROWSER uses which technology to DISPLAY information from the World Wide Web?
(A) Machine code (binary instructions)
(B) C++ compiled programs
(C) HTML (HyperText Markup Language)
(D) More than one of the above
(E) None of the above

---

**Q4.** CSS (Cascading Style Sheets) is used for:
(A) Defining the logical structure of web pages (headings, content)
(B) Adding interactivity (button clicks, form validation)
(C) STYLING web pages (colors, fonts, sizes, layout)
(D) More than one of the above
(E) None of the above

---

**Q5.** JavaScript in web development is primarily responsible for:
(A) Defining structure of web pages
(B) Applying visual design (colors and fonts)
(C) BEHAVIOR and INTERACTIVITY (dynamic effects, user interactions)
(D) More than one of the above
(E) None of the above

---

**Q6.** Which of the following are CLIENT-SIDE web technologies (run in the user's browser)?
```
1. HTML
2. CSS
3. JavaScript
```
(A) Only 1 (HTML)
(B) Only 1 and 3
(C) All three — HTML, CSS, and JavaScript
(D) More than one of the above
(E) None of the above

---

**Q7.** Which of the following are SERVER-SIDE scripting technologies?
(A) HTML, CSS, JavaScript
(B) HTML and PHP
(C) PHP, Python (Flask/Django), Node.js, ASP.NET
(D) More than one of the above
(E) None of the above

---

**Q8.** PHP is best classified as:
(A) A client-side markup language like HTML
(B) A database management system
(C) A SERVER-SIDE scripting language
(D) More than one of the above
(E) None of the above

---

**Q9.** The key difference between INTERNET and WWW is:
(A) They are identical — different names for the same thing
(B) WWW is a physical network; Internet is a collection of web pages
(C) INTERNET = physical network infrastructure; WWW = a SERVICE running on the Internet
(D) More than one of the above
(E) None of the above

---

**Q10.** A COMPUTER VIRUS differs from a WORM in that:
(A) A virus self-replicates over networks without human action; a worm needs a host file
(B) A virus is harmless; a worm causes damage
(C) A virus NEEDS A HOST FILE to spread; a worm is SELF-REPLICATING without a host
(D) More than one of the above
(E) None of the above

---

**Q11.** A COMPUTER WORM is characterized by:
(A) Attaching itself to host files and spreading when files are opened
(B) Disguising itself as legitimate software
(C) SELF-REPLICATION over networks WITHOUT needing a host file
(D) More than one of the above
(E) None of the above

---

**Q12.** A TROJAN HORSE in cybersecurity:
(A) Replicates rapidly and spreads through network connections
(B) Encrypts all files on a computer and demands ransom
(C) Is DISGUISED AS LEGITIMATE SOFTWARE to trick users into installing it
(D) More than one of the above
(E) None of the above

---

**Q13.** RANSOMWARE attacks are characterized by:
(A) Monitoring user activity and sending data to attackers
(B) Spreading through networks by self-replication
(C) ENCRYPTING victim's data and DEMANDING PAYMENT to restore access
(D) More than one of the above
(E) None of the above

---

**Q14.** PHISHING attacks primarily involve:
(A) Physically breaking into server rooms to steal data
(B) Flooding servers with requests to crash them
(C) Sending FRAUDULENT EMAILS/MESSAGES posing as legitimate sources to steal credentials
(D) More than one of the above
(E) None of the above

---

**Q15.** A FIREWALL in network security:
(A) Removes malware from infected computers
(B) Speeds up internet connection
(C) MONITORS and FILTERS network traffic based on predefined security rules
(D) More than one of the above
(E) None of the above

---

**Q16.** PACKET SNIFFERS on a network are best prevented by using:
(A) Antivirus software on all computers
(B) A stronger firewall
(C) SWITCHED NETWORKS (which send packets only to intended recipients)
(D) More than one of the above
(E) None of the above

---

**Q17.** A SYSTEM INTEGRITY BREACH occurs when:
(A) A computer runs out of storage space
(B) A software program crashes unexpectedly
(C) FULL ACCESS RIGHTS are given to ALL USERS (violating least-privilege principle)
(D) More than one of the above
(E) None of the above

---

**Q18.** In ASYMMETRIC (Public Key) CRYPTOGRAPHY, the PRIVATE KEY is used by the:
(A) SENDER to encrypt messages before sending
(B) Certificate Authority to issue digital certificates
(C) RECEIVER to DECRYPT messages (also: sender uses private key to sign digitally)
(D) More than one of the above
(E) None of the above

---

**Q19.** HTTPS (Hypertext Transfer Protocol Secure) differs from HTTP in that:
(A) HTTPS is faster than HTTP
(B) HTTPS only works on mobile devices
(C) HTTPS uses SSL/TLS ENCRYPTION (shown by padlock in browser)
(D) More than one of the above
(E) None of the above

---

**Q20.** The PING command in networking:
(A) Tests which ports are open on a remote server
(B) Checks the speed of internet download
(C) Checks IP-LEVEL CONNECTIVITY (whether a host is reachable — NOT port-level)
(D) More than one of the above
(E) None of the above

---

**Q21.** A DIGITAL SIGNATURE uses which key of the SENDER?
(A) The receiver's public key
(B) A shared symmetric key
(C) The SENDER'S PRIVATE KEY (receiver verifies with sender's public key)
(D) More than one of the above
(E) None of the above

---

**Q22.** The IT Act (Information Technology Act) in India was enacted in:
(A) 1995
(B) 2008
(C) 2000
(D) More than one of the above
(E) None of the above

---

**Q23.** Which of the following correctly describes the ROLE SEPARATION in web development?
(A) HTML = styling; CSS = structure; JavaScript = behavior
(B) HTML = behavior; JavaScript = structure; CSS = styling
(C) HTML = structure; CSS = styling; JavaScript = behavior
(D) More than one of the above
(E) None of the above

---

**Q24.** What is the standard PORT NUMBER for HTTPS (Secure HTTP)?
(A) Port 80
(B) Port 21
(C) Port 443
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following statements about malware types are ALL CORRECT?
(A) Virus = needs host file; Worm = self-replicates on network; Trojan = disguised software
(B) Ransomware = encrypts data + demands ransom; Phishing = fraudulent emails
(C) Both (A) and (B) above
(D) More than one of the above
(E) None of the above

---
---

### GENERAL STUDIES — 25 MCQs
### Awards & Recognitions

---

**Q26.** The BHARAT RATNA award was established in:
(A) 1947 (at Independence)
(B) 1950 (when Constitution came into effect)
(C) 1954
(D) More than one of the above
(E) None of the above

---

**Q27.** Who were the FIRST RECIPIENTS of the Bharat Ratna in 1954?
(A) Jawaharlal Nehru, Indira Gandhi, Rajiv Gandhi
(B) Mahatma Gandhi, Nehru, Ambedkar
(C) C. Rajagopalachari, Dr. S. Radhakrishnan, Dr. C.V. Raman
(D) More than one of the above
(E) None of the above

---

**Q28.** The FIRST NON-INDIAN to receive the Bharat Ratna was:
(A) Nelson Mandela (1990)
(B) Mother Teresa (1980)
(C) KHAN ABDUL GHAFFAR KHAN — "Frontier Gandhi" (1987)
(D) More than one of the above
(E) None of the above

---

**Q29.** Sachin Tendulkar received the Bharat Ratna in 2014. He was significant because:
(A) He was the oldest person to receive it
(B) He was the first Prime Minister to receive it
(C) He was the FIRST SPORTSPERSON to receive the Bharat Ratna
(D) More than one of the above
(E) None of the above

---

**Q30.** KARPOORI THAKUR, who received the Bharat Ratna in 2024, was:
(A) A famous scientist from Bihar known for agricultural research
(B) The first Chief Justice of Bihar High Court
(C) Former Chief Minister of Bihar; known as "JAN NAYAK" (People's Leader)
(D) More than one of the above
(E) None of the above

---

**Q31.** JAYAPRAKASH NARAYAN (JP) is known by which title?
(A) Mahamanav (Great Man)
(B) Deshratna (Jewel of Nation)
(C) LOKNAYAK (People's Leader)
(D) More than one of the above
(E) None of the above

---

**Q32.** DR. RAJENDRA PRASAD was:
(A) The first Chief Justice of India
(B) The first Finance Minister of India
(C) The FIRST PRESIDENT OF INDIA (1950–1962); from Bihar
(D) More than one of the above
(E) None of the above

---

**Q33.** RABINDRANATH TAGORE received the Nobel Prize in:
(A) 1911 — for Physics
(B) 1915 — for Peace
(C) 1913 — for LITERATURE (for Gitanjali) — FIRST Asian Nobel Prize winner
(D) More than one of the above
(E) None of the above

---

**Q34.** C.V. RAMAN received the Nobel Prize (1930) for:
(A) Chemistry — for discovering the structure of proteins
(B) Peace — for work in nuclear disarmament
(C) PHYSICS — for the RAMAN EFFECT (scattering of light)
(D) More than one of the above
(E) None of the above

---

**Q35.** AMARTYA SEN received the Nobel Prize in 1998 for:
(A) Literature — for his novels on poverty
(B) Peace — for work in food distribution
(C) ECONOMICS — for welfare economics and poverty analysis
(D) More than one of the above
(E) None of the above

---

**Q36.** KAILASH SATYARTHI received the Nobel Peace Prize in 2014 for:
(A) Environmental activism and climate change work
(B) Conflict resolution in South Asia
(C) Work for CHILDREN'S RIGHTS (Bacpan Bachao Andolan — Save Childhood)
(D) More than one of the above
(E) None of the above

---

**Q37.** The HIGHEST national sports award in India is currently named:
(A) Arjuna Award
(B) Rajiv Gandhi Khel Ratna Award (original name)
(C) MAJOR DHYAN CHAND KHEL RATNA AWARD (renamed in 2021)
(D) More than one of the above
(E) None of the above

---

**Q38.** The DRONACHARYA AWARD in India is given to:
(A) Athletes who win medals at the Olympics
(B) Sports journalists who promote Indian sports
(C) SPORTS COACHES who produce outstanding athletes
(D) More than one of the above
(E) None of the above

---

**Q39.** NATIONAL SPORTS DAY in India is celebrated on 29 August because:
(A) India won its first Olympic gold medal on this day
(B) The National Sports Authority was established on this day
(C) It is the BIRTHDAY of Major DHYAN CHAND — "Wizard of Hockey"
(D) More than one of the above
(E) None of the above

---

**Q40.** Among the three Padma Awards, which is the HIGHEST?
(A) Padma Shri
(B) Padma Bhushan
(C) PADMA VIBHUSHAN
(D) More than one of the above
(E) None of the above

---

**Q41.** The Padma Awards are announced every year on:
(A) Independence Day (15 August)
(B) Gandhi Jayanti (2 October)
(C) REPUBLIC DAY (26 January)
(D) More than one of the above
(E) None of the above

---

**Q42.** BABU VEER KUNWAR SINGH from Bihar is known for:
(A) Leading Bihar's peasant movement in the 1940s
(B) Founding the Bihar Provincial Congress Committee
(C) Leading the REVOLT OF 1857 against British from Jagdishpur, Bhojpur district
(D) More than one of the above
(E) None of the above

---

**Q43.** The MAGSAYSAY AWARD (Asia's Nobel Prize equivalent) was won by Jayaprakash Narayan in:
(A) 1970
(B) 1958
(C) 1965
(D) More than one of the above
(E) None of the above

---

**Q44.** DR. B.R. AMBEDKAR received the Bharat Ratna in:
(A) 1956 (same year he converted to Buddhism)
(B) 1980 (by Indira Gandhi's government)
(C) 1990 (POSTHUMOUSLY — awarded after his death in 1956)
(D) More than one of the above
(E) None of the above

---

**Q45.** SARDAR VALLABHBHAI PATEL received the Bharat Ratna in 1991. He is also known as:
(A) "Father of the Nation"
(B) "Pandit" for his scholarship
(C) "IRON MAN OF INDIA" (for integrating 562 princely states)
(D) More than one of the above
(E) None of the above

---

**Q46.** Which of the following is TRUE about the BHARAT RATNA award?
(A) It is given in the shape of a circular gold medal
(B) It is given only to scientists and politicians
(C) It is given for exceptional service in Art, Literature, Science, or Public Service; shaped like a Peepal leaf
(D) More than one of the above
(E) None of the above

---

**Q47.** A.P.J. ABDUL KALAM received the Bharat Ratna in 1997. He is best known as:
(A) The first Muslim President of India
(B) The architect of India's banking reforms
(C) THE "MISSILE MAN OF INDIA" — key role in ISRO and DRDO missile programs
(D) More than one of the above
(E) None of the above

---

**Q48.** Which of the following Bihar personalities and their descriptions are CORRECTLY matched?
(A) Rajendra Prasad = First President; Karpoori Thakur = Jan Nayak; JP = Loknayak
(B) Rajendra Prasad = First PM; Karpoori Thakur = Loknayak; JP = Jan Nayak
(C) Rajendra Prasad = First President; Karpoori Thakur = Loknayak; JP = Jan Nayak
(D) More than one of the above
(E) None of the above

---

**Q49.** The DHYAN CHAND AWARD (distinct from Khel Ratna) is given for:
(A) Best performance in a single Olympic Games
(B) Outstanding coaching achievement of the year
(C) LIFETIME ACHIEVEMENT in sports and contribution to sports after retirement
(D) More than one of the above
(E) None of the above

---

**Q50.** Which of the following statements about India's Nobel Prize winners are ALL CORRECT?
(A) Tagore = Literature 1913 (first Asian Nobel); C.V. Raman = Physics 1930 (Raman Effect)
(B) Amartya Sen = Economics 1998; Kailash Satyarthi = Peace 2014
(C) Both (A) and (B) above are correct
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY

## ⚠️ MANDATORY: Attempt all 50 questions BEFORE checking!

---

### CS Answers (Q1–Q25):

| Q  | Answer | Reason (one-line)                                                                |
|----|--------|----------------------------------------------------------------------------------|
| 1  | (C)    | WWW invented by TIM BERNERS-LEE (1989) at CERN ← PYQ!                           |
| 2  | (C)    | HTML = STRUCTURE of web pages ← #1 PYQ fact!                                    |
| 3  | (C)    | Browser uses HTML to display WWW information ← PYQ!                             |
| 4  | (C)    | CSS = STYLING (colors, fonts, layout) ← PYQ!                                    |
| 5  | (C)    | JavaScript = BEHAVIOR and INTERACTIVITY ← PYQ!                                  |
| 6  | (C)    | HTML + CSS + JavaScript = ALL client-side ← PYQ!                                |
| 7  | (C)    | Server-side = PHP, Python, Node.js, ASP.NET ← PYQ!                              |
| 8  | (C)    | PHP = SERVER-SIDE scripting language ← PYQ!                                     |
| 9  | (C)    | Internet = infrastructure; WWW = service running on Internet ← PYQ!             |
| 10 | (C)    | Virus = needs host file; Worm = self-replicating without host ← PYQ!            |
| 11 | (C)    | Worm = SELF-REPLICATING over network WITHOUT host file ← PYQ!                   |
| 12 | (C)    | Trojan = DISGUISED as legitimate software ← PYQ!                                |
| 13 | (C)    | Ransomware = ENCRYPTS data + DEMANDS ransom ← PYQ!                              |
| 14 | (C)    | Phishing = FRAUDULENT EMAILS posing as legitimate to steal credentials ← PYQ!   |
| 15 | (C)    | Firewall = MONITORS + FILTERS network traffic ← PYQ!                            |
| 16 | (C)    | Sniffers prevented by SWITCHED NETWORKS ← PYQ!                                  |
| 17 | (C)    | System integrity breach = FULL ACCESS RIGHTS for all users ← PYQ!              |
| 18 | (C)    | RECEIVER uses PRIVATE KEY to DECRYPT (sender uses public key of receiver)        |
| 19 | (C)    | HTTPS = HTTP + SSL/TLS encryption (padlock in browser) ← PYQ!                  |
| 20 | (C)    | PING = IP-level connectivity check; NOT port-level ← PYQ!                       |
| 21 | (C)    | Digital signature = SENDER'S PRIVATE KEY (receiver verifies with public key)    |
| 22 | (C)    | IT Act = 2000 ← PYQ!                                                             |
| 23 | (C)    | HTML=structure; CSS=styling; JavaScript=behavior ← classic PYQ!                 |
| 24 | (C)    | HTTPS = Port 443 ← PYQ! (HTTP = port 80)                                        |
| 25 | (D)    | BOTH (A) and (B) are correct → Answer = (D) ← classic BPSC TRE answer pattern! |

---

### GS Answers (Q26–Q50):

| Q  | Answer | Reason (one-line)                                                              |
|----|--------|--------------------------------------------------------------------------------|
| 26 | (C)    | Bharat Ratna established 1954 ← PYQ!                                           |
| 27 | (C)    | First BR (1954) = C. Rajagopalachari + S. Radhakrishnan + C.V. Raman ← PYQ!   |
| 28 | (C)    | First non-Indian BR = Khan Abdul Ghaffar Khan 1987 ← PYQ!                     |
| 29 | (C)    | Sachin Tendulkar = FIRST SPORTSPERSON to receive Bharat Ratna (2014) ← PYQ!   |
| 30 | (C)    | Karpoori Thakur = former Bihar CM; Jan Nayak; Bharat Ratna 2024 ← Bihar PYQ!  |
| 31 | (C)    | JP Narayan = LOKNAYAK ← PYQ!                                                   |
| 32 | (C)    | Rajendra Prasad = FIRST PRESIDENT of India; from Bihar ← PYQ!                 |
| 33 | (C)    | Tagore = Nobel Literature 1913; Gitanjali; First Asian Nobel ← PYQ!           |
| 34 | (C)    | C.V. Raman = Nobel Physics 1930; Raman Effect ← PYQ!                          |
| 35 | (C)    | Amartya Sen = Nobel Economics 1998 ← PYQ!                                      |
| 36 | (C)    | Kailash Satyarthi = Nobel Peace 2014; Bacpan Bachao Andolan ← PYQ!            |
| 37 | (C)    | Highest sports award = Major Dhyan Chand Khel Ratna (renamed 2021) ← PYQ!    |
| 38 | (C)    | Dronacharya Award = for COACHES ← PYQ!                                         |
| 39 | (C)    | National Sports Day = 29 Aug = Dhyan Chand's birthday ← PYQ!                  |
| 40 | (C)    | Padma Vibhushan = highest of three Padma awards ← PYQ!                        |
| 41 | (C)    | Padma Awards announced on REPUBLIC DAY (Jan 26) ← PYQ!                        |
| 42 | (C)    | Veer Kunwar Singh = led 1857 revolt from Jagdishpur, Bhojpur ← Bihar PYQ!     |
| 43 | (C)    | JP Narayan received Magsaysay Award in 1965 ← PYQ!                            |
| 44 | (C)    | Ambedkar received Bharat Ratna 1990 POSTHUMOUSLY ← PYQ!                       |
| 45 | (C)    | Sardar Patel = IRON MAN OF INDIA (integrated 562 princely states) ← PYQ!      |
| 46 | (C)    | Bharat Ratna = exceptional service; Peepal leaf shape ← PYQ!                  |
| 47 | (C)    | APJ Abdul Kalam = MISSILE MAN OF INDIA ← PYQ!                                 |
| 48 | (A)    | Rajendra Prasad=1st President ✅; Karpoori=Jan Nayak ✅; JP=Loknayak ✅         |
| 49 | (C)    | Dhyan Chand Award = LIFETIME ACHIEVEMENT in sports ← PYQ!                     |
| 50 | (D)    | BOTH (A) and (B) correct → Answer = (D) ← classic BPSC TRE pattern!          |

---
---

# 🔁 FINAL REVISION NOTES
## 📌 "Last 1-Hour Before Exam" — Ultra-Crisp Format

---

### ⚡ CS — 30 MUST-KNOW FACTS (Web Tech + Cybersecurity)

```
WWW AND WEB BASICS:
1.  WWW inventor = TIM BERNERS-LEE (1989, CERN) ← PYQ!
2.  Internet ≠ WWW: Internet=infrastructure; WWW=service on Internet ← PYQ!
3.  Browser uses HTML (not machine code) to display WWW info ← PYQ!

THREE LAYERS OF WEB:
4.  HTML        = STRUCTURE ("what is on the page") ← PYQ!
5.  CSS         = STYLING ("how it looks") ← PYQ!
6.  JavaScript  = BEHAVIOR ("what it does") ← PYQ!
7.  ALL THREE = CLIENT-SIDE technologies ← PYQ!

SERVER-SIDE vs CLIENT-SIDE:
8.  SERVER-SIDE = PHP, Python, Node.js, ASP.NET, JSP ← PYQ!
9.  CLIENT-SIDE = HTML, CSS, JavaScript ← PYQ!
10. PHP = most widely used server-side language
    "HTML = server-side" → FALSE! ← trap!

MALWARE TYPES (KEY DIFFERENCES):
11. VIRUS     = needs HOST FILE; spreads when file is executed ← PYQ!
12. WORM      = SELF-REPLICATING; NO host file; spreads via NETWORK ← PYQ!
13. TROJAN    = DISGUISED as legitimate software ← PYQ!
14. RANSOMWARE= ENCRYPTS data + demands RANSOM ← PYQ!
    KEY DIFFERENCE: Virus=host needed; Worm=self-replicates
    Most common trap: "Worm needs host file" → FALSE (Virus does!)

SECURITY TOOLS:
15. FIREWALL  = monitors + FILTERS network traffic ← PYQ!
16. Sniffers prevented by SWITCHED NETWORKS ← PYQ!
17. System integrity breach = FULL ACCESS RIGHTS for all users ← PYQ!
18. PHISHING  = fraudulent emails to steal credentials ← PYQ!
19. Ping = checks IP-level; NOT port-level ← PYQ!

CRYPTOGRAPHY:
20. Asymmetric: PUBLIC key=encrypt; PRIVATE key=decrypt ← PYQ!
21. PRIVATE key = used by RECEIVER to decrypt ← PYQ!
22. Digital Signature = SENDER'S PRIVATE KEY signs ← PYQ!
23. HTTPS = HTTP + SSL/TLS (port 443); HTTP = port 80 ← PYQ!
24. IT Act 2000 = governs cybercrime India; Section 66 = Hacking ← PYQ!

PORT NUMBERS (memorize top 5):
25. HTTP=80, HTTPS=443, FTP=21, SSH=22, SMTP=25 ← PYQ!

EXAM TRAPS:
26. "CSS = structure" → FALSE (HTML=structure)
27. "JS = server-side" → FALSE (client-side, mostly)
28. "Worm = needs host file" → FALSE (Virus does!)
29. "Trojan = self-replicates" → FALSE (doesn't replicate)
30. "Sender uses private key to encrypt" → FALSE (receiver decrypts with private)
```

---

### ⚡ GS — 25 MUST-KNOW AWARDS FACTS

```
BHARAT RATNA:
1.  Established 1954; for exceptional service (Art/Lit/Science/Public service)
2.  First recipients (1954) = Rajagopalachari + Radhakrishnan + C.V. Raman ← PYQ!
3.  First NON-INDIAN = Khan Abdul Ghaffar Khan 1987 ← PYQ!
4.  First SPORTSPERSON = Sachin Tendulkar 2014 ← PYQ!
5.  Bihar's: Karpoori Thakur 2024 (Jan Nayak; former Bihar CM) ← Bihar PYQ!
6.  Ambedkar = 1990 POSTHUMOUSLY ← PYQ!
7.  Sardar Patel = Iron Man of India; BR 1991 ← PYQ!
8.  APJ Abdul Kalam = Missile Man; BR 1997 ← PYQ!

BIHAR PERSONALITIES:
9.  Rajendra Prasad = FIRST PRESIDENT of India; from Bihar ← PYQ!
10. JP Narayan = LOKNAYAK; Total Revolution; Magsaysay 1965 ← PYQ!
11. Karpoori Thakur = JAN NAYAK; Bihar CM; BR 2024 ← PYQ!
12. Veer Kunwar Singh = 1857 revolt; Jagdishpur, Bhojpur ← PYQ!

NOBEL PRIZES (Indian):
13. Tagore = Literature 1913; Gitanjali; FIRST Asian Nobel ← PYQ!
14. C.V. Raman = Physics 1930; RAMAN EFFECT ← PYQ!
15. Amartya Sen = Economics 1998 ← PYQ!
16. Kailash Satyarthi = Peace 2014; Bacpan Bachao Andolan ← PYQ!

SPORTS AWARDS:
17. Highest sports award = Major Dhyan Chand Khel Ratna ← PYQ!
    (renamed from Rajiv Gandhi Khel Ratna in 2021)
18. Dronacharya Award = for COACHES ← PYQ!
19. Dhyan Chand Award = LIFETIME ACHIEVEMENT ← PYQ!
20. Arjuna Award = established 1961; for outstanding performance ← PYQ!
21. National Sports Day = 29 August (Dhyan Chand's birthday) ← PYQ!
22. Dhyan Chand = "Wizard of Hockey" ← PYQ!

PADMA AWARDS:
23. Padma Vibhushan > Padma Bhushan > Padma Shri (high to low) ← PYQ!
24. Announced on REPUBLIC DAY (January 26) ← PYQ!
25. Padma Vibhushan = HIGHEST of three Padma awards ← PYQ!
```

---

### ⚡ LAST-MINUTE COMPARISON TABLES

```
WEB TECHNOLOGY  PURPOSE         SIDE      EXAMPLE
─────────────────────────────────────────────────────────────────────
HTML            STRUCTURE       Client    <h1>, <p>, <a href>
CSS             STYLING         Client    color:red; font-size:14px
JavaScript      BEHAVIOR        Client    onClick, form validation
PHP             Server logic    Server    Database queries, auth
Python (Flask)  Server logic    Server    API endpoints
Node.js         Server logic    Server    Backend JS applications
─────────────────────────────────────────────────────────────────────

MALWARE    KEY FEATURE           SPREADS VIA        DOES NOT
─────────────────────────────────────────────────────────────────────
Virus      Needs HOST FILE       Infected files     Self-spread network
Worm       SELF-REPLICATING      NETWORK (auto)     Need host file
Trojan     DISGUISED as legit    User installs       Replicate itself
Ransomware ENCRYPTS + ransom     Phishing/network    Spy silently
─────────────────────────────────────────────────────────────────────

AWARD              TYPE            CRITERIA           ANNOUNCED
─────────────────────────────────────────────────────────────────────
Bharat Ratna       Civilian        Exceptional service President gives
Padma Vibhushan    Civilian        Highest Padma       Republic Day
Padma Bhushan      Civilian        Middle Padma        Republic Day
Padma Shri         Civilian        Lowest Padma        Republic Day
Khel Ratna         Sports          Highest sports award Ministry gives
Dronacharya        Sports COACHES  Producing champions Ministry gives
Arjuna Award       Sports players  Outstanding perform Ministry gives
─────────────────────────────────────────────────────────────────────

PERSON             TITLE/NICK      KNOWN FOR
─────────────────────────────────────────────────────────────────────
Rajendra Prasad    —               FIRST PRESIDENT; from Bihar
JP Narayan         LOKNAYAK        Total Revolution; Magsaysay 1965
Karpoori Thakur    JAN NAYAK       Bihar CM; Bharat Ratna 2024
Sardar Patel       IRON MAN        Integrated 562 princely states
APJ Abdul Kalam    MISSILE MAN     ISRO + DRDO; BR 1997
Dhyan Chand        WIZARD of Hockey 29 Aug = National Sports Day
─────────────────────────────────────────────────────────────────────
```

---

## 🎯 DAY 85 COMPLETE — WHAT YOU'VE MASTERED TODAY

```
CS:   Web Technologies — Tim Berners-Lee invented WWW (1989) |
      HTML=structure / CSS=styling / JavaScript=behavior ← all PYQ |
      All three = CLIENT-SIDE; Server-side = PHP/Python/Node.js/ASP.NET |
      Browser uses HTML (not machine code) to display WWW ← PYQ |
      Cybersecurity — Virus (host file) / Worm (self-replicates network) /
      Trojan (disguised) / Ransomware (encrypts + ransom) ← all PYQ |
      Phishing=fraudulent emails; Firewall=filters traffic;
      Sniffers→SWITCHED NETWORKS prevent; Integrity breach=full access rights |
      Asymmetric crypto: private key=receiver decrypts; Digital sig=sender's pvt key |
      HTTPS=port 443; HTTP=port 80; IT Act 2000; Ping=IP-level only |

GS:   Bharat Ratna — 1954; first 3 recipients; first non-Indian (Ghaffar Khan);
      first sportsperson (Sachin 2014); Karpoori Thakur 2024 (Bihar) |
      Bihar personalities — Rajendra Prasad (1st President), JP (Loknayak),
      Karpoori Thakur (Jan Nayak), Veer Kunwar Singh (1857) |
      Nobel — Tagore (1913 Lit); C.V. Raman (1930 Physics-Raman Effect);
      Amartya Sen (1998 Econ); Kailash Satyarthi (2014 Peace) |
      Sports awards — Khel Ratna (highest); Dronacharya (coaches);
      Dhyan Chand (lifetime); Arjuna (athletes); 29 Aug=National Sports Day

NEXT: Day 86 — TRE 3.0 FULL PYQ PAPER PRACTICE
      (80 CS questions from TRE 3.0 paper — heaviest on Digital Electronics + OS)
```

---

*Day 85 of 170 | Phase 2: Depth | Week 13: AI, IoT, Emerging Tech & Theory of Computation*
*BPSC TRE 4.0 Preparation | Target: TOP 50 RANK | Score: 130+/150*
