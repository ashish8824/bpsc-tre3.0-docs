# 📅 BPSC TRE 4.0 — DAY 56: MEGA REVISION DAY
### Phase 1 Complete Summary (Days 1–55) + Full 75-Question Mock Test
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1 hr): Read Phase 1 Master Summary — every topic, one line each
> - Afternoon (1 hr): Identify your 5 weakest topics (mark while reading summary)
> - Evening (2.5 hrs): Attempt Full Mock Test — 75 questions under timed conditions
> - Night (30 min): Score yourself → check answer key → write tomorrow's weak-topic list

---

> **How to use today:**
> Step 1 — Read the Master Summary below WITHOUT skipping. Mark any line you feel shaky on with a ✗.
> Step 2 — Count your ✗ marks by topic. Your 5 topics with most ✗ = your Phase 2 priority list.
> Step 3 — Attempt the mock test with a timer. 75 questions = 75 minutes target (1 min/question).
> Step 4 — Score: 65+ = Excellent | 55–64 = Good | 45–54 = Needs work | Below 45 = Phase 2 intensive needed.

---

# PART 1: PHASE 1 MASTER SUMMARY
## Everything You Learned in Days 1–55 — One Line Per Fact

---

## 🔷 CS UNIT 1: OOP + C++ (Days 1–14)

```
4 PILLARS: Encapsulation | Abstraction | Inheritance | Polymorphism (ALL required for pure OOP)
struct default = PUBLIC | class default = PRIVATE ← only difference between them
Abstract class = at least ONE pure virtual function: virtual void f() = 0;
Templates = compile-time polymorphism ← TRE 2.0 PYQ
Overloading = same class + different params | Overriding = parent-child + same signature
C++ inheritance = colon (:) | Java inheritance = extends
Diamond problem → solution = Virtual inheritance
Default constructor = compiler provides ONLY IF programmer writes NO constructor
Destructor = ~ClassName(); only ONE per class; CANNOT be overloaded
Unnamed class = NO constructor, NO destructor
sizeof() = does NOT evaluate the expression inside
new = RESERVED keyword in C++ (cannot use as variable name)
ios::trunc = truncates file to ZERO
Ctrl+F9 (Turbo C++) = compile AND run | Alt+F9 = compile only
rank() = returns DIMENSION of array (not size, not length)
char[] + char[] with + operator = COMPILE ERROR
TRY block = code at risk of abnormal termination
Inline functions = small/simple; NOT for large/complex
Friend function = NOT a member; NOT inherited; can access private members
Modularity = dividing into modules (NOT hiding)
User-defined headers = .h extension
delete ptr where ptr=NULL = SAFE (no crash; no-op) ← #1 exam trap
new int[5] pairs with delete[] | new int pairs with delete (NEVER mix)
Dangling pointer = points to freed memory | Wild pointer = uninitialized
p+1 advances by sizeof(type) bytes (NOT 1 byte)
sizeof(any pointer) = 4 bytes (32-bit) or 8 bytes (64-bit)
p1 + p2 = INVALID (cannot add two pointers)
void* cannot be dereferenced without casting
new throws std::bad_alloc on failure | malloc returns NULL on failure
```

---

## 🔷 CS UNIT 2: Data Structures + Algorithms (Days 15–30)

```
Stack = LIFO (Last In First Out)
Queue = FIFO (First In First Out)
Stack operations: PUSH (insert) | POP (remove) | PEEK (view top)
Stack overflow = PUSH on a FULL stack ← most tested
Stack underflow = POP from an EMPTY stack ← most tested
Queue overflow = ENQUEUE on full | Queue underflow = DEQUEUE from empty
Check overflow BEFORE push | Check underflow BEFORE pop/dequeue

CIRCULAR QUEUE:
  Empty condition: front == rear ← PYQ
  Also called: RING BUFFER ← PYQ
  Advantage: Reuses empty spaces; no "false full" issue

RECURSION uses STACK data structure internally ← PYQ

LINKED LIST:
  Node = data + pointer to next node
  Last node pointer = NULL
  No random access (must traverse from head)
  Insertion/deletion = O(1) if pointer available

ARRAYS:
  Correct declaration: int array[10]; ← PYQ
  is_array() = checks if variable is array type
  Random access = O(1) | Insertion/deletion = O(n)

BINARY SEARCH TREE (BST):
  Left subtree < root < Right subtree ← PYQ rule
  Inorder traversal of BST = SORTED (ascending) order ← PYQ
  Traversals: Preorder (Root-Left-Right), Inorder (Left-Root-Right), Postorder (Left-Right-Root)
  Search/Insert = O(log n) average | O(n) worst case (skewed tree)

BIG-O NOTATION:
  O(1) = constant | O(log n) = logarithmic | O(n) = linear
  O(n log n) = linearithmic | O(n²) = quadratic
  Big-O = UPPER BOUND (worst-case complexity) ← PYQ

SORTING:
  Merge Sort = Divide and Conquer ← PYQ | O(n log n) always
  Quick Sort = Divide and Conquer | O(n log n) avg, O(n²) worst
  Bubble Sort = O(n²) | Selection Sort = O(n²) | Insertion Sort = O(n²)

SEARCHING:
  Linear Search = O(n) | Binary Search = O(log n) (requires sorted array)

NUMBER SYSTEMS:
  Binary (base 2) | Octal (base 8) | Decimal (base 10) | Hexadecimal (base 16)
  10 (decimal) = 1010 (binary) = 12 (octal) = A (hex)
  FF (hex) = 255 (decimal) = 11111111 (binary)
```

---

## 🔷 CS UNIT 3: Digital Electronics (Days 31–37)

```
NOT gate: output = complement of input (1→0, 0→1)
AND gate: output 1 only when ALL inputs = 1
OR gate: output 1 when ANY input = 1
NAND = NOT + AND = UNIVERSAL GATE ← PYQ (can build ANY gate from NAND)
NOR = NOT + OR = UNIVERSAL GATE ← PYQ (can build ANY gate from NOR)
XOR: output 1 when inputs are DIFFERENT | XNOR: output 1 when inputs are SAME

DE MORGAN'S THEOREMS: ← PYQ tested both
  Theorem 1: NOT(A AND B) = (NOT A) OR (NOT B)  → NAND = NOT-A OR NOT-B
  Theorem 2: NOT(A OR B) = (NOT A) AND (NOT B)  → NOR = NOT-A AND NOT-B

BOOLEAN ALGEBRA LAWS: ← PYQ
  A + 0 = A | A · 1 = A (Identity)
  A + A = A | A · A = A (Idempotent)
  A + 1 = 1 | A · 0 = 0 (Domination)
  A + A' = 1 | A · A' = 0 (Complement)
  (A')' = A (Double Negation)

FLIP-FLOPS:
  SR flip-flop: S=1,R=0 → SET (Q=1) | S=0,R=1 → RESET (Q=0) | S=R=1 → FORBIDDEN
  D flip-flop: output Q = input D (on clock edge) — simplest
  JK flip-flop: J=K=1 → TOGGLES (no forbidden state) ← improvement over SR

LOGIC CIRCUIT simplification: K-Map (Karnaugh Map) for 2–4 variables

NUMBER CONVERSIONS:
  2's complement: invert all bits, add 1 → used for negative numbers in computers
```

---

## 🔷 CS UNIT 4: DBMS + SQL (Days 38–42, Day 50, Day 53)

```
DBMS = interface between DATABASE APPLICATION and DATABASE (NOT user-hardware)
Google = NOT a DBMS (search engine)
Decentralized = NOT a database type; correct = Distributed
Metadata = information ABOUT data

KEY TYPES:
  Superkey = ANY set uniquely identifying a record (broadest)
  Candidate key = MINIMAL superkey
  Primary key = UNIQUE + NOT NULL + only ONE per table
  Foreign key = references primary key; CAN be NULL; enforces REFERENTIAL INTEGRITY
  Unique key = like primary key but CAN have ONE NULL

NORMALIZATION:
  1NF = atomic values (no multi-valued attributes)
  2NF = no partial dependencies (composite key scenario)
  3NF = no transitive dependencies → ADEQUATE for normal RDBMS design ← PYQ
  BCNF = stricter than 3NF

ER DIAGRAM:
  Weak entity = DOUBLE RECTANGLE | Multivalued attribute = DOUBLE ELLIPSE
  Derived attribute = DASHED ELLIPSE

SQL COMMAND TYPES:
  DDL: CREATE, ALTER, DROP, TRUNCATE
  DML: INSERT, UPDATE, DELETE
  DCL: GRANT, REVOKE
  TCL: COMMIT, ROLLBACK, SAVEPOINT
  COMMIT = permanent save | ROLLBACK = undo | TRUNCATE = no rollback

SQL CLAUSE ORDER: SELECT → FROM → WHERE → GROUP BY → HAVING → ORDER BY
  WHERE = filters ROWS | HAVING = filters GROUPS (after GROUP BY)
  ORDER BY default = ASC

ROUND(65.726, -1) = 70 ← PYQ most tested SQL calculation
COMPUTE = NOT a valid aggregate function ← PYQ trap
UNION = NOT a SQL constraint (it's a set operation) ← PYQ trap
VIEW = virtual table (not stored physically; recomputed each query)
WITH clause = creates temporary relation (CTE)
Natural JOIN = basic approach; joins on common column names
DELETE FROM teaches; = correct syntax to remove all rows ← PYQ
db_accessadmin = adds/removes user IDs
SQL hierarchy: Environments → Catalogs → Schemas → Tables
RAW data type = stores unstructured data
Filing cabinet by customer = Hierarchical DBMS ← PYQ analogy
Data in two places → wasted space AND data inconsistency
```

---

## 🔷 CS UNIT 5: Computer Networks (Days 43–49, Day 51)

```
OSI = 7 layers | TCP/IP = 4 layers
Layer order (OSI top→bottom): Application, Presentation, Session, Transport, Network, Data Link, Physical
Host-to-Host (TCP/IP) = Transport layer (OSI Layer 4)
MAC sublayer = medium-dependent functions ← PYQ
IPv4 = 32 bits | IPv6 = 128 bits ← PYQ trap (always 128)
TCP = connection-oriented + 3-way handshake (SYN→SYN-ACK→ACK)
UDP = connectionless (faster; used for DNS, streaming, VoIP)
SMTP client = mail server SENDING to another server ← PYQ
PING = packet loss + round-trip delay (NOT "Packet Internet Generator")
MQTT = IoT protocol ← PYQ
Socket = endpoint of inter-process communication
Peer-to-peer = NOT a topology (it's a network type) ← PYQ trap
Optical fiber = highest speed + immune to EM interference ← PYQ
UTP = vulnerable to EM interference
Switched networks prevent sniffers (not hubs) ← PYQ
Private key in asymmetric crypto = kept by RECEIVER ← PYQ trap
Computer ↔ Keyboard = SIMPLEX (one direction only) ← PYQ
TDM: time slots → FRAMES ← PYQ
Memory-mapped I/O = I/O + memory share SAME address space ← PYQ
I/O-mapped I/O = SEPARATE address spaces
Polling = program-controlled I/O (CPU checks status flags) ← PYQ
WWW = collection of hyperlinked documents (≠ Internet)
Switch = Data Link layer | Router = Network layer
Hub = broadcasts to ALL ports | Switch = sends to SPECIFIC port
```

---

## 🔷 CS UNIT 6: Operating Systems (Days 43–49)

```
CPU = brain of computer ← PYQ
Control unit generates = control signals ← PYQ
Page = fixed-size block of virtual memory
4KB page → page offset = 12 bits (2¹² = 4096) ← PYQ
TLB = organised as associative cache ← PYQ
Thrashing = caused by excessive paging activity ← PYQ
FCFS disk scheduling = service requests in arrival order; calculate head movement by adding absolute differences
Thread shares with same-process threads = code section + data section ← PYQ
Interrupt types: Hardware, Software, Trap (NOT "Memory interrupt") ← PYQ
Types of OS: Real-time, Embedded, Network, Batch, Time-sharing
Secondary memory = long-term storage = logical organisation
ASCII = keystrokes to bits standard ← PYQ
Immediate addressing = operand is in the instruction itself (most common) ← PYQ
ADD X Y format = Absolute addressing ← PYQ
Buffer registers = overcome difference in data transfer speed ← PYQ
```

---

## 🔷 CS UNIT 7: Compiler Theory + Languages (Day 55)

```
Compiler: input = source program | output = object code | NOT involved in execution
TRE 1.0 Q44: all 3 compiler statements correct → Answer D
Interpreter = line by line; no separate object file; stops at first error
Assembler = assembly language → machine code
Linker = object files → executable | Loader = executable → memory
Assembly language = LOW-LEVEL language ← PYQ
PASCAL = structured code ← PYQ | FORTRAN = scientific
COBOL = business data processing | BASIC = beginners
Open source = view + modify + redistribute (all three) ← PYQ
Time sharing = beginning of computer communications ← PYQ
Turing machine wrong component = "output tape" (does NOT exist) ← PYQ
Halting problem = undecidable / NOT computable ← PYQ
```

---

## 🔷 CS UNIT 8: E-Commerce + Multimedia + Generations (Day 54)

```
B2C = Amazon, Flipkart, Snapdeal ← TRE 3.0 PYQ
B2B = Alibaba, IndiaMART | C2C = OLX, eBay | B2G = GeM
Multimedia = Text + Audio + Video + Animation + Graphics (all 5)
PowerPoint = presentation tool, NOT authoring tool ← PYQ trap
Authoring tools = Director, Flash/Animate, Authorware, ToolBook
Graphics package = libraries providing 2D graphics functions ← PYQ
Gen 1 = vacuum tubes | Gen 2 = transistors (IBM 7094) | Gen 3 = ICs + Multiprogramming
Gen 4 = VLSI/microprocessors + C++/Java | Gen 5 = AI + NLP + OOP ← PYQ
SDLC: Waterfall, Agile, Spiral are valid; "Physical model" is NOT ← PYQ
Verification = "building RIGHT?" | Validation = "RIGHT product?"
Decision Tree = supervised learning | K-Means = unsupervised
Green Hydrogen = produced by ELECTROLYSIS ← PYQ
```

---

## 🔷 GS: MODERN HISTORY (Days 1–15, 50–51)

```
Champaran 1917: Raj Kumar Shukla brought Gandhi | April 15, 1917 arrival
  Tinkathia system abolished | Champaran Agrarian Act 1918 | 25% refund
  First civil disobedience in India | Rajendra Prasad helped
Non-Cooperation Movement 1920: Gandhi; stopped after Chauri Chaura (Feb 1922)
Civil Disobedience 1930: Salt March; Dandi (April 6, 1930)
Quit India 1942: "Do or Die" | August 8, 1942
INA: Mohan Singh FOUNDED (1942, Singapore); Bose REORGANISED (1943)
  Azad Hind Government = Singapore, Oct 21, 1943
  INA Trials = Red Fort, Delhi | Bose: "Give me blood"; "Jai Hind"; "Delhi Chalo"
Anandamath = Bankim Chandra → describes SANNYASI REVOLT (NOT 1857) ← PYQ
1857 "First War of Independence" = V.D. SAVARKAR (wrote this) ← PYQ
Abhinav Bharat (London) = V.D. SAVARKAR | Ghadar Party = USA, 1913 (Lala Har Dayal)
Bihar Socialist Party = Phulan Prasad Varma + JP Narayan (1931)
Bihar Provincial Congress = 1908, Patna
Anushilan Samiti Patna = Sachindra Nath Sanyal (1913)
Birsa Munda: Ulgulan (1899-1900); Munda tribe; C-in-C = Gaya Munda; died Ranchi Jail (June 9, 1900)
Santhal Rebellion = 1855-56; Sidhu + Kanhu Murmu; Rajmahal Hills
Tana Bhagat = 1914; Oraon tribe; Jatra Bhagat; NON-VIOLENT; TRIBAL (not peasant) ← PYQ trap
Swadeshi + Boycott FIRST used = Bengal Partition (1905) ← NOT NCM 1920
First INC President = W.C. Bonnerjee (1885, Bombay)
INC Gaya Session 1922 = Chittaranjan Das ← PYQ
"Congress tottering" = Lord Curzon ← PYQ
"Prophet of New India" = Raja Ram Mohan Roy ← PYQ
Hindu College Calcutta (1817) = David Hare (founder); Derozio = teacher ← PYQ
```

---

## 🔷 GS: ANCIENT HISTORY (Day 52)

```
IVC = Harappan Civilisation | 2500–1500 BCE | Bronze Age (NO iron weapons) ← PYQ
  Harappa (Punjab) = FIRST discovered (Daya Ram Sahni)
  Mohenjo-daro (Sindh) = GREAT BATH
  Lothal (Gujarat) = DOCKYARD ← #1 PYQ IVC fact
  Rakhigarhi (Haryana) = largest IVC site IN INDIA
  IVC script = UNDECIPHERED ← PYQ
Rigveda = OLDEST Veda; 4 Vedas: Rigveda → Samaveda → Yajurveda → Atharvaveda
Mauryan Empire: Founded by CHANDRAGUPTA MAURYA (321 BCE)
  Capital = PATALIPUTRA (Patna, Bihar)
  Chanakya = Kautilya = Vishnugupta (SAME person); wrote ARTHASHASTRA
  Megasthenes (Greek ambassador) wrote INDICA
  Ashoka: converted after KALINGA WAR (261 BCE) → spread DHAMMA
  Lion Capital (Sarnath) = India's national emblem ← PYQ
Kanishka = Kushana dynasty; promoted Buddhism; 4th Buddhist Council
GUPTA GOLDEN AGE: founded by Chandragupta I (319 CE)
  Chandragupta II = VIKRAMADITYA (peak; 375-415 CE) ← PYQ
  Kalidasa = Meghaduta, Abhijnanasakuntalam ← Gupta court
  Aryabhata = calculated pi; heliocentric theory; wrote ARYABHATIYA
  Iron Pillar Delhi = Gupta period (Chandragupta II) ← PYQ
  Nalanda University = founded by KUMARAGUPTA I; located in BIHAR ← PYQ
```

---

## 🔷 GS: MEDIEVAL HISTORY (Day 53)

```
Delhi Sultanate: "Some Kings Take Special Leave" = Slave→Khilji→Tughlaq→Sayyid→Lodi (1206–1526)
Qutb Minar: STARTED by Aibak; COMPLETED by Iltutmish ← PYQ
Iltutmish: introduced silver tanka + copper jital coins ← PYQ
Razia Sultana = FIRST FEMALE SULTAN ← PYQ
Alauddin Khilji = market reforms + Diwan-i-Riyasat + Malik Kafur (S.India)
Muhammad bin Tughlaq = moved capital to DAULATABAD + token currency + Ibn Battuta (Rihla) ← PYQ
SHER SHAH SURI = Grand Trunk Road + Rupee (NOT Akbar/Babur) ← PYQ trap
1st Battle Panipat (1526): Babur vs Ibrahim Lodi → Mughal Empire begins
2nd Battle Panipat (1556): Akbar (via Bairam Khan) vs Hemu
Baburnama = Babur's autobiography (first in India) | Gunpowder/artillery = introduced by Babur
Akbar: Din-i-Ilahi (1582) + abolished Jaziya (1564) + Todar Mal (revenue) + Tansen (music)
  Birbal accepted Din-i-Ilahi; Abul Fazl wrote Akbarnama
Jahangir: Nur Jahan (co-ruled) + Chain of Justice + Sir Thomas Roe (British ambassador)
Shah Jahan: Taj Mahal (Mumtaz Mahal) + Ustad Ahmad Lahauri (architect) ← PYQ
  Peacock Throne = taken by Nadir Shah (1739)
Aurangzeb: reimposed Jaziya (1679); 27-year Deccan campaigns
CHISHTI = MOST POPULAR Sufi order in India ← PYQ
  Moinuddin Chishti → Ajmer | Nizamuddin Auliya → Delhi (Amir Khusrau = disciple)
  Mujaddid Alf Sani = Sheikh Ahmad Sirhindi (Naqshbandi) ← PYQ
Tulsidas = Ramcharitmanas (Ram, Awadhi) ← PYQ; Surdas = blind; Sursagar (Krishna)
Ramdas = Shivaji's spiritual guru ← PYQ
Vijayanagara: Harihara + Bukka (1336); Krishnadevaraya = greatest; contemporary of Babur
```

---

## 🔷 GS: TRIBAL MOVEMENTS (Day 51)

```
CHRONOLOGICAL ORDER: Santhal (1855) → Birsa Munda (1899) → Tana Bhagat (1914)
Santhal Rebellion (1855-56): Sidhu + Kanhu Murmu; Rajmahal Hills; against zamindars + moneylenders
  → Santhal Parganas Tenancy Act (1876)
Birsa Munda (1899-1900): Munda tribe; Chota Nagpur; C-in-C = Gaya Munda
  Birsa = "Dharti Aba" (avatar); died Ranchi Jail June 9, 1900
  → Chota Nagpur Tenancy Act (1908)
TANA BHAGAT (1914): ORAON tribe; JATRA BHAGAT; NON-VIOLENT; TRIBAL movement ← #1 PYQ trap
```

---

## 🔷 GS: SCIENCE — PHYSICS + BIOLOGY (Day 54)

```
Spray bottle = BERNOULLI'S PRINCIPLE ← PYQ
Stefan's Law: E ∝ T⁴ | T→T/3 makes E = E/81 ← PYQ calculation
Convex lens in water = still convex; focal length INCREASES ← PYQ
Frequency of light = UNCHANGED when medium changes ← PYQ
P = I²R = V²/R = VI (all three valid → answer D in BPSC)
Photoperiodism = GARNER AND ALLARD ← PYQ
Silent Valley = KERALA; rare flora and fauna ← PYQ
Diaphragm during inhalation = FLATTENS (contracts) ← PYQ
Lymphocytes = most important in immunity ← PYQ
Ginger = underground stem (NODES + INTERNODES) ← PYQ
Yeast = reproduces by budding ← PYQ
Pollen grains = in ANTHER ← PYQ
Antacid = medicine for INDIGESTION ← PYQ
Vas deferens = MALE reproductive system ← PYQ
Mitochondria = powerhouse (ATP production)
Universal donor = O | Universal recipient = AB
Vitamin K = blood clotting | Vitamin C = scurvy | Vitamin D = rickets
Malaria = Anopheles mosquito | Dengue = Aedes mosquito
```

---

## 🔷 GS: GEOGRAPHY — INDIA + BIHAR (Day 55)

```
Bihar population % of India = 8.58% ← PYQ
Max paddy in Bihar = ROHTAS | Max silk = BHAGALPUR (Silk City; Tussar)
Sorrow of Bihar = KOSHI river | Litchi = MUZAFFARPUR
Eastern Ghats highest = MAHENDRAGIRI (Odisha) ← PYQ
Western Ghats highest = ANAMUDI (Kerala)
South Peninsular Upland = GONDWANA LAND ← PYQ
Malnad = KARNATAKA (Western Ghats region) ← PYQ
Black soil = KARNATAKA + GUJARAT → Answer D ← PYQ
SW monsoon withdrawal Hyderabad = OCTOBER 1 ← PYQ
Trewartha India climate = SUBTROPICAL MONSOON ← PYQ
Stalactites/Stalagmites = UNDERGROUND WATER ← PYQ
East-West Corridor = SILCHAR (Assam) ↔ PORBANDAR (Gujarat) ← PYQ
Topographic maps = SURVEY OF INDIA (Dehradun) ← PYQ
Max urbanisation state = GOA ← PYQ
Largest state (area) = RAJASTHAN | Smallest = GOA
Chilika Lake = Odisha (largest saltwater) | Wular = J&K (largest freshwater)
Majuli = Assam, Brahmaputra (world's largest river island)
Alluvial soil = ~40% of India | Khadar = new alluvial | Bangar = old alluvial
Longest land border = BANGLADESH | Sundarbans = Ganga + Brahmaputra
```

---

# PART 2: WEAK-TOPIC IDENTIFICATION TABLE

**Instructions:** After reading the summary, fill this in honestly:

| # | Topic | Confidence (1–5) | Action Needed |
|---|-------|-----------------|---------------|
| 1 | OOP + C++ (pointers, constructors, inheritance) | ___ | ___ |
| 2 | DSA (Stack/Queue, BST, Big-O) | ___ | ___ |
| 3 | Digital Electronics (gates, De Morgan's) | ___ | ___ |
| 4 | DBMS + SQL (normalization, SQL queries) | ___ | ___ |
| 5 | Computer Networks (OSI, protocols, IPv6) | ___ | ___ |
| 6 | OS (paging, TLB, scheduling) | ___ | ___ |
| 7 | Compiler Theory + Language types | ___ | ___ |
| 8 | E-Commerce + Multimedia + Generations | ___ | ___ |
| 9 | Modern Indian History | ___ | ___ |
| 10 | Ancient + Medieval History | ___ | ___ |
| 11 | Tribal Movements | ___ | ___ |
| 12 | Science GK | ___ | ___ |
| 13 | Geography (India + Bihar) | ___ | ___ |

**Your bottom 5 topics (score 1–2) = Phase 2 intensive focus areas.**

---

---

# PART 3: FULL MOCK TEST — 75 QUESTIONS
## Phase 1 Comprehensive Assessment

> **Rules:** ⏱ 75 minutes target | No peeking at notes | Mark difficult questions for review
> **Scoring:** +1 for correct | 0 for skipped | −¼ if TRE 4.0 has negative marking (attempt with 70%+ confidence)

---

## SECTION A: COMPUTER SCIENCE — 40 Questions

### OOP + C++ (Q1–10)

**Q1.** What is the ONLY difference between `struct` and `class` in C++?
(A) struct cannot have member functions; class can
(B) struct supports inheritance; class does not
(C) struct default access = public; class default access = private
(D) More than one of the above
(E) None of the above

---

**Q2.** A class with at least ONE pure virtual function is called:
(A) A virtual class
(B) A friend class
(C) An abstract class
(D) More than one of the above
(E) None of the above

---

**Q3.** Which of the following implements COMPILE-TIME polymorphism in C++?
(A) Virtual function overriding
(B) Runtime method dispatch via vtable
(C) Templates
(D) More than one of the above
(E) None of the above

---

**Q4.** Consider: `int* p = NULL; delete p;` — what happens?
(A) Runtime segmentation fault
(B) Compile error — cannot delete NULL
(C) Nothing — deleting NULL is safe and does nothing
(D) More than one of the above
(E) None of the above

---

**Q5.** `int* p, q;` — which statement is TRUE?
(A) Both p and q are pointers to int
(B) Neither p nor q is a pointer
(C) p is a pointer to int; q is a plain integer
(D) More than one of the above
(E) None of the above

---

**Q6.** In C++ inheritance, which members of the base class are NOT inherited by the derived class?
(A) public members
(B) protected members
(C) Constructors, destructors, and friend functions
(D) More than one of the above
(E) None of the above

---

**Q7.** The DIAMOND PROBLEM in multiple inheritance is solved by:
(A) Using private inheritance
(B) Avoiding all multiple inheritance
(C) Virtual inheritance
(D) More than one of the above
(E) None of the above

---

**Q8.** `sizeof(x++)` where x is an int variable — what happens to x?
(A) x is incremented by 1
(B) x is incremented by sizeof(int)
(C) x is NOT incremented — sizeof does not evaluate its operand
(D) More than one of the above
(E) None of the above

---

**Q9.** An UNNAMED class in C++ has:
(A) A compiler-generated default constructor
(B) A virtual destructor
(C) No constructor and no destructor
(D) More than one of the above
(E) None of the above

---

**Q10.** `ios::trunc` in C++ file handling:
(A) Appends data to the end of an existing file
(B) Opens the file in read-only mode
(C) Truncates the file to zero length when opened
(D) More than one of the above
(E) None of the above

---

### Data Structures + Algorithms (Q11–18)

**Q11.** A STACK OVERFLOW occurs when:
(A) You try to POP from an empty stack
(B) The stack is used in recursion
(C) You try to PUSH onto a full stack
(D) More than one of the above
(E) None of the above

---

**Q12.** A CIRCULAR QUEUE in its EMPTY state satisfies:
(A) front == -1
(B) rear == -1
(C) front == rear
(D) More than one of the above
(E) None of the above

---

**Q13.** Which data structure does RECURSION use internally?
(A) Queue
(B) Array
(C) Stack
(D) More than one of the above
(E) None of the above

---

**Q14.** The INORDER traversal of a Binary Search Tree produces:
(A) A reverse-sorted sequence
(B) A random sequence depending on tree shape
(C) A sorted (ascending) sequence
(D) More than one of the above
(E) None of the above

---

**Q15.** Big-O notation represents:
(A) Average-case complexity
(B) Best-case complexity
(C) Upper bound (worst-case complexity)
(D) More than one of the above
(E) None of the above

---

**Q16.** MERGE SORT belongs to which algorithm design paradigm?
(A) Greedy
(B) Dynamic Programming
(C) Divide and Conquer
(D) More than one of the above
(E) None of the above

---

**Q17.** What is the decimal value of hexadecimal FF?
(A) 128
(B) 200
(C) 255
(D) More than one of the above
(E) None of the above

---

**Q18.** Before performing a DELETION (dequeue) on a queue, you should check for:
(A) Overflow condition
(B) Stack pointer value
(C) Underflow condition
(D) More than one of the above
(E) None of the above

---

### Digital Electronics (Q19–22)

**Q19.** Which gate is called the UNIVERSAL GATE because any logic circuit can be built from it alone?
(A) AND gate
(B) OR gate
(C) NAND gate
(D) More than one of the above
(E) None of the above

---

**Q20.** De Morgan's Theorem states: NOT(A AND B) equals:
(A) (NOT A) AND (NOT B)
(B) A OR B
(C) (NOT A) OR (NOT B)
(D) More than one of the above
(E) None of the above

---

**Q21.** A JK flip-flop with J=1 and K=1:
(A) Sets the output to 1 (Q=1)
(B) Resets the output to 0 (Q=0)
(C) Toggles the output (Q changes to its complement)
(D) More than one of the above
(E) None of the above

---

**Q22.** Boolean expression: A + 1 = ?
(A) A
(B) 0
(C) 1
(D) More than one of the above
(E) None of the above

---

### DBMS + SQL (Q23–30)

**Q23.** Which of the following is TRUE about a PRIMARY KEY?
(A) It can contain NULL values if the table is small
(B) A table can have two primary keys if needed
(C) It is UNIQUE, NOT NULL, and only ONE per table
(D) More than one of the above
(E) None of the above

---

**Q24.** The HAVING clause is used to filter:
(A) Individual rows before grouping
(B) Columns returned by SELECT
(C) Groups after a GROUP BY operation
(D) More than one of the above
(E) None of the above

---

**Q25.** `ROUND(65.726, -1)` evaluates to:
(A) 65.7
(B) 66
(C) 70
(D) More than one of the above
(E) None of the above

---

**Q26.** Which of the following is NOT a valid SQL aggregate function?
(A) COUNT
(B) AVG
(C) COMPUTE
(D) More than one of the above
(E) None of the above

---

**Q27.** Third Normal Form (3NF) is significant because:
(A) It is the strictest form of normalization
(B) It eliminates partial dependencies
(C) It is considered adequate for normal relational database design
(D) More than one of the above
(E) None of the above

---

**Q28.** A SQL VIEW is:
(A) A physical copy of a table stored separately for backup
(B) A stored procedure for batch operations
(C) A virtual table computed dynamically on every query
(D) More than one of the above
(E) None of the above

---

**Q29.** REFERENTIAL INTEGRITY in a relational database is enforced by:
(A) Primary key constraints
(B) NOT NULL constraints
(C) Foreign key constraints
(D) More than one of the above
(E) None of the above

---

**Q30.** `TRUNCATE` differs from `DELETE` in that:
(A) TRUNCATE removes only specific rows; DELETE removes all rows
(B) TRUNCATE is slower than DELETE
(C) TRUNCATE cannot be rolled back; DELETE can be rolled back
(D) More than one of the above
(E) None of the above

---

### Computer Networks + OS (Q31–40)

**Q31.** IPv6 addresses are:
(A) 32 bits
(B) 64 bits
(C) 128 bits
(D) More than one of the above
(E) None of the above

---

**Q32.** TCP uses which mechanism to establish a connection?
(A) Two-way handshake (SYN → ACK)
(B) Four-way handshake
(C) Three-way handshake (SYN → SYN-ACK → ACK)
(D) More than one of the above
(E) None of the above

---

**Q33.** The MAC sublayer of the Data Link layer performs:
(A) Session management between applications
(B) Routing packets between networks
(C) Functions that depend on the type of medium used
(D) More than one of the above
(E) None of the above

---

**Q34.** Which transmission medium offers the HIGHEST speed and is immune to electromagnetic interference?
(A) UTP (Unshielded Twisted Pair)
(B) Coaxial cable
(C) Optical fiber
(D) More than one of the above
(E) None of the above

---

**Q35.** In asymmetric key cryptography, the PRIVATE key is:
(A) Shared openly with everyone
(B) Used by the sender to decrypt messages
(C) Kept secret by the RECEIVER
(D) More than one of the above
(E) None of the above

---

**Q36.** Communication between a computer and its keyboard is:
(A) Full-duplex (simultaneous both ways)
(B) Half-duplex (both ways, not simultaneous)
(C) Simplex (one direction only)
(D) More than one of the above
(E) None of the above

---

**Q37.** THRASHING in an operating system is caused by:
(A) A corrupted disk sector
(B) Running too many GUI applications
(C) Excessive paging activity due to insufficient RAM
(D) More than one of the above
(E) None of the above

---

**Q38.** For a page size of 4KB, the number of bits required for the page offset is:
(A) 8 bits
(B) 10 bits
(C) 12 bits
(D) More than one of the above
(E) None of the above

---

**Q39.** PASCAL programming language is best suited for:
(A) Scientific and engineering computations
(B) Business data processing
(C) Writing structured code
(D) More than one of the above
(E) None of the above

---

**Q40.** A COMPILER (choose the most complete answer):
(A) Translates source program to object code and executes it directly
(B) Translates line by line and executes immediately
(C) Takes source program as input, produces object code as output, and is not involved in execution
(D) More than one of the above
(E) None of the above

---

## SECTION B: GENERAL STUDIES — 35 Questions

### Modern Indian History (Q41–50)

**Q41.** The TANA BHAGAT MOVEMENT (1914) is correctly categorised as:
(A) A peasant movement for land rights
(B) A Dalit rights movement
(C) A tribal movement (Oraon tribe) with non-violent character
(D) More than one of the above
(E) None of the above

---

**Q42.** The INDIAN NATIONAL ARMY (INA) was FOUNDED by:
(A) Subhash Chandra Bose
(B) Rash Bihari Bose
(C) Mohan Singh
(D) More than one of the above
(E) None of the above

---

**Q43.** The FIRST PRESIDENT of the Indian National Congress (1885, Bombay) was:
(A) A.O. Hume
(B) Bal Gangadhar Tilak
(C) W.C. Bonnerjee (Womesh Chandra Bonnerjee)
(D) More than one of the above
(E) None of the above

---

**Q44.** Swadeshi and Boycott as methods of political protest were FIRST formally adopted during:
(A) Non-Cooperation Movement (1920)
(B) Partition of Bengal (1905)
(C) Quit India Movement (1942)
(D) More than one of the above
(E) None of the above

---

**Q45.** "Anandamath" by Bankim Chandra Chattopadhyay describes which revolt?
(A) Sepoy Mutiny of 1857
(B) Santhal Rebellion
(C) Sannyasi Revolt
(D) More than one of the above
(E) None of the above

---

**Q46.** The correct CHRONOLOGICAL ORDER of three tribal movements is:
(A) Birsa Munda → Santhal Rebellion → Tana Bhagat
(B) Tana Bhagat → Birsa Munda → Santhal Rebellion
(C) Santhal Rebellion (1855) → Birsa Munda (1899) → Tana Bhagat (1914)
(D) More than one of the above
(E) None of the above

---

**Q47.** Who was Bihar's FIRST PEASANT LEADER in the Non-Cooperation Movement?
(A) Rajendra Prasad
(B) Swami Vidyanand
(C) Jayaprakash Narayan
(D) More than one of the above
(E) None of the above

---

**Q48.** "The Congress is tottering to its fall" — this statement was made by:
(A) Lord Irwin
(B) Lord Dalhousie
(C) Lord Curzon
(D) More than one of the above
(E) None of the above

---

**Q49.** The SHER SHAH SURI (non-Mughal interlude) is remembered for introducing:
(A) Din-i-Ilahi religion
(B) Mansabdari system
(C) Grand Trunk Road and the Rupee
(D) More than one of the above
(E) None of the above

---

**Q50.** Which of the following matches is CORRECT?
(A) Tulsidas → Ramcharitmanas | Surdas → Sursagar | Ramdas → Shivaji's guru
(B) Tulsidas → Sursagar | Surdas → Ramcharitmanas | Ramdas → Taj Mahal architect
(C) Tulsidas → Arthashastra | Surdas → Baburnama | Ramdas → Akbarnama
(D) More than one of the above
(E) None of the above

---

### Ancient + Medieval History (Q51–56)

**Q51.** The Indus Valley Civilisation site famous for its DOCKYARD is:
(A) Harappa
(B) Mohenjo-daro
(C) Lothal
(D) More than one of the above
(E) None of the above

---

**Q52.** Ashoka converted to Buddhism after the:
(A) Battle of Khanwa
(B) Coronation ceremony at Pataliputra
(C) Kalinga War (261 BCE)
(D) More than one of the above
(E) None of the above

---

**Q53.** The GUPTA period is called the "Golden Age" of ancient India. Its peak was under:
(A) Chandragupta I (founder)
(B) Samudragupta (military conqueror)
(C) Chandragupta II (Vikramaditya)
(D) More than one of the above
(E) None of the above

---

**Q54.** Nalanda University was founded by which Gupta ruler and is located in:
(A) Samudragupta; located in Uttar Pradesh
(B) Chandragupta II; located in West Bengal
(C) Kumaragupta I; located in Bihar
(D) More than one of the above
(E) None of the above

---

**Q55.** The MOST POPULAR Sufi order in India is:
(A) Naqshbandi order
(B) Suhrawardi order
(C) Chishti order
(D) More than one of the above
(E) None of the above

---

**Q56.** The TAJ MAHAL was built by Shah Jahan in memory of his wife Mumtaz Mahal. Its architect was:
(A) Todar Mal
(B) Abul Fazl
(C) Ustad Ahmad Lahauri
(D) More than one of the above
(E) None of the above

---

### Science GK (Q57–63)

**Q57.** According to Stefan's Law (E ∝ T⁴), if a body's temperature is reduced to T/3, its radiated energy becomes:
(A) E/3
(B) E/9
(C) E/81
(D) More than one of the above
(E) None of the above

---

**Q58.** PHOTOPERIODISM was discovered by:
(A) Mendel and Darwin
(B) Watson and Crick
(C) Garner and Allard
(D) More than one of the above
(E) None of the above

---

**Q59.** GINGER is classified as which plant part?
(A) A root, because it grows underground
(B) A fruit, because it has nutrients
(C) An underground stem (rhizome) — it has nodes and internodes
(D) More than one of the above
(E) None of the above

---

**Q60.** Electrical power can be expressed as: P = I²R, P = V²/R, and P = VI.
(A) Only P = I²R is correct
(B) Only P = VI is the correct formula
(C) All three expressions are correct equivalents
(D) More than one of the above
(E) None of the above

---

**Q61.** The UNIVERSAL BLOOD DONOR (can donate to all blood groups) is:
(A) Blood group AB
(B) Blood group A
(C) Blood group O
(D) More than one of the above
(E) None of the above

---

**Q62.** MALARIA is caused by Plasmodium parasite, transmitted by which mosquito?
(A) Aedes mosquito
(B) Culex mosquito
(C) Anopheles mosquito
(D) More than one of the above
(E) None of the above

---

**Q63.** A spray bottle (atomiser) works on which principle?
(A) Pascal's Law
(B) Archimedes' Principle
(C) Bernoulli's Principle
(D) More than one of the above
(E) None of the above

---

### Geography — India + Bihar (Q64–75)

**Q64.** Bihar's maximum SILK production is concentrated in:
(A) Rohtas district
(B) Patna district
(C) Bhagalpur district
(D) More than one of the above
(E) None of the above

---

**Q65.** Bihar's maximum PADDY (rice) production is in:
(A) Gaya district
(B) Muzaffarpur district
(C) Rohtas district
(D) More than one of the above
(E) None of the above

---

**Q66.** The HIGHEST PEAK of the EASTERN GHATS is:
(A) Anamudi
(B) Doddabetta
(C) Mahendragiri
(D) More than one of the above
(E) None of the above

---

**Q67.** BLACK SOIL (Regur) is found in which of the following?
(A) Karnataka only
(B) Gujarat only
(C) Both Karnataka and Gujarat
(D) More than one of the above
(E) None of the above

---

**Q68.** STALACTITES and STALAGMITES in caves are formed by:
(A) Wind erosion over millions of years
(B) Glacial deposits melting underground
(C) Underground water (chemical weathering of limestone)
(D) More than one of the above
(E) None of the above

---

**Q69.** The EAST-WEST CORRIDOR of India connects:
(A) Srinagar (J&K) and Kanyakumari (Tamil Nadu)
(B) Delhi and Mumbai
(C) Silchar (Assam) and Porbandar (Gujarat)
(D) More than one of the above
(E) None of the above

---

**Q70.** TOPOGRAPHICAL MAPS of India are published by:
(A) Geological Survey of India
(B) Census of India
(C) Survey of India (headquartered at Dehradun)
(D) More than one of the above
(E) None of the above

---

**Q71.** The South Peninsular Upland is considered part of:
(A) Himalayan fold mountains
(B) Tethys Sea sedimentary deposits
(C) Gondwana Land (ancient supercontinent)
(D) More than one of the above
(E) None of the above

---

**Q72.** The SOUTHWEST MONSOON withdraws from Hyderabad around:
(A) September 1
(B) October 1
(C) November 1
(D) More than one of the above
(E) None of the above

---

**Q73.** According to Trewartha's climate classification, India's climate is:
(A) Tropical wet and dry
(B) Mediterranean
(C) Subtropical monsoon
(D) More than one of the above
(E) None of the above

---

**Q74.** Bihar's share of India's total population is approximately:
(A) 5.8%
(B) 8.58%
(C) 12.5%
(D) More than one of the above
(E) None of the above

---

**Q75.** The MALNAD region (Western Ghats hilly zone) belongs to:
(A) Kerala
(B) Maharashtra
(C) Karnataka
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY — FULL MOCK TEST

## ⚠️ Score yourself ONLY after attempting all 75!

---

### Section A — Computer Science (Q1–Q40):

| Q | Ans | Topic | Key Reason |
|---|-----|-------|-----------|
| 1 | (C) | OOP | struct=public default; class=private default |
| 2 | (C) | OOP | Abstract class = at least one pure virtual function |
| 3 | (C) | OOP | Templates = compile-time polymorphism |
| 4 | (C) | Pointers | delete NULL = safe no-op |
| 5 | (C) | Pointers | `int* p, q` → only p is pointer; q is plain int |
| 6 | (C) | Inheritance | Constructors, destructors, friend functions NOT inherited |
| 7 | (C) | Inheritance | Diamond problem → virtual inheritance |
| 8 | (C) | C++ | sizeof() does NOT evaluate its operand |
| 9 | (C) | C++ | Unnamed class = no constructor, no destructor |
| 10 | (C) | C++ | ios::trunc = truncates file to zero |
| 11 | (C) | DSA | Stack overflow = PUSH on full stack |
| 12 | (C) | DSA | Circular queue empty = front == rear |
| 13 | (C) | DSA | Recursion uses Stack internally |
| 14 | (C) | DSA | BST inorder = sorted ascending sequence |
| 15 | (C) | DSA | Big-O = upper bound (worst-case) |
| 16 | (C) | DSA | Merge sort = Divide and Conquer |
| 17 | (C) | Numbers | FF (hex) = 255 (decimal) |
| 18 | (C) | DSA | Check underflow before dequeue |
| 19 | (C) | Digital | NAND = universal gate (also NOR → answer D valid) |
| 20 | (C) | Digital | De Morgan: NOT(A AND B) = NOT-A OR NOT-B |
| 21 | (C) | Digital | JK flip-flop J=K=1 → toggles |
| 22 | (C) | Digital | Boolean: A + 1 = 1 (domination law) |
| 23 | (C) | DBMS | Primary key = unique + NOT NULL + only ONE per table |
| 24 | (C) | SQL | HAVING = filters groups (after GROUP BY) |
| 25 | (C) | SQL | ROUND(65.726, -1) = 70 |
| 26 | (C) | SQL | COMPUTE = NOT valid aggregate function |
| 27 | (C) | DBMS | 3NF = adequate for normal RDBMS design |
| 28 | (C) | SQL | VIEW = virtual table, recomputed each query |
| 29 | (C) | DBMS | Referential integrity = enforced by foreign key |
| 30 | (C) | SQL | TRUNCATE = cannot rollback; DELETE can rollback |
| 31 | (C) | Networks | IPv6 = 128 bits |
| 32 | (C) | Networks | TCP = 3-way handshake (SYN→SYN-ACK→ACK) |
| 33 | (C) | Networks | MAC = medium-dependent functions |
| 34 | (C) | Networks | Optical fiber = highest speed + EM immune |
| 35 | (C) | Networks | Private key = kept by RECEIVER |
| 36 | (C) | Networks | Computer↔Keyboard = SIMPLEX |
| 37 | (C) | OS | Thrashing = excessive paging activity |
| 38 | (C) | OS | 4KB = 2¹² → 12-bit page offset |
| 39 | (C) | Languages | PASCAL = structured code |
| 40 | (C) | Compiler | Compiler: source→object code; not involved in execution |

---

### Section B — General Studies (Q41–Q75):

| Q | Ans | Topic | Key Reason |
|---|-----|-------|-----------|
| 41 | (C) | History | Tana Bhagat = TRIBAL, non-violent, Oraon tribe |
| 42 | (C) | History | INA FOUNDED by Mohan Singh (not Bose) |
| 43 | (C) | History | First INC President = W.C. Bonnerjee (1885) |
| 44 | (B) | History | Swadeshi + Boycott first = Bengal Partition (1905) |
| 45 | (C) | History | Anandamath = Sannyasi Revolt (not 1857) |
| 46 | (C) | History | Santhal(1855)→Birsa(1899)→Tana Bhagat(1914) |
| 47 | (B) | History | Bihar NCM peasants = Swami Vidyanand |
| 48 | (C) | History | "Congress tottering" = Lord Curzon |
| 49 | (C) | History | Sher Shah Suri = GT Road + Rupee |
| 50 | (A) | History | Tulsidas→Ramcharitmanas; Surdas→Sursagar; Ramdas→Shivaji's guru |
| 51 | (C) | Anc.Hist | Lothal = DOCKYARD (IVC, Gujarat) |
| 52 | (C) | Anc.Hist | Ashoka converted after KALINGA WAR (261 BCE) |
| 53 | (C) | Anc.Hist | Gupta peak = Chandragupta II (Vikramaditya) |
| 54 | (C) | Anc.Hist | Nalanda = Kumaragupta I; located in BIHAR |
| 55 | (C) | Med.Hist | CHISHTI = most popular Sufi order in India |
| 56 | (C) | Med.Hist | Taj Mahal architect = Ustad Ahmad Lahauri |
| 57 | (C) | Physics | T→T/3: E→E/3⁴=E/81 (Stefan's Law) |
| 58 | (C) | Biology | Photoperiodism = Garner and Allard |
| 59 | (C) | Biology | Ginger = underground stem (nodes+internodes) |
| 60 | (C) | Physics | P=I²R=V²/R=VI — all three correct → Answer C |
| 61 | (C) | Biology | Universal donor = blood group O |
| 62 | (C) | Biology | Malaria = Anopheles mosquito |
| 63 | (C) | Physics | Spray bottle = Bernoulli's Principle |
| 64 | (C) | Geography | Bhagalpur = max silk in Bihar |
| 65 | (C) | Geography | Rohtas = max paddy in Bihar |
| 66 | (C) | Geography | Mahendragiri = highest peak Eastern Ghats |
| 67 | (D) | Geography | Black soil = Karnataka AND Gujarat (both) → D |
| 68 | (C) | Geography | Stalactites/Stalagmites = underground water |
| 69 | (C) | Geography | E-W Corridor = Silchar to Porbandar |
| 70 | (C) | Geography | Topographic maps = Survey of India (Dehradun) |
| 71 | (C) | Geography | South Peninsular Upland = Gondwana Land |
| 72 | (B) | Geography | SW Monsoon withdrawal Hyderabad = October 1 |
| 73 | (C) | Geography | Trewartha: India = Subtropical monsoon |
| 74 | (B) | Geography | Bihar = 8.58% of India's population |
| 75 | (C) | Geography | Malnad = Karnataka |

---

# SCORE ANALYSIS

## Calculate Your Score:
```
Total correct answers: _____ / 75

Percentage: (correct / 75) × 100 = _____%

GRADE:
  68–75 correct (90%+)  → OUTSTANDING — You are topper material
  60–67 correct (80%+)  → EXCELLENT — Minor gaps; focused revision needed
  53–59 correct (70%+)  → GOOD — Some topics need deeper work
  45–52 correct (60%+)  → AVERAGE — Systematic Phase 2 revision essential
  Below 45 (< 60%)      → NEEDS WORK — Return to raw content; more practice

BY SECTION:
  CS score: _____ / 40  (target: 32+)
  GS score: _____ / 35  (target: 30+)
```

## Topic-Wise Performance:
```
Count your WRONG answers per block:

OOP + C++ (Q1–10):         Wrong: ___
DSA + Algorithms (Q11–18): Wrong: ___
Digital Electronics (Q19–22): Wrong: ___
DBMS + SQL (Q23–30):       Wrong: ___
Networks + OS (Q31–40):    Wrong: ___
Modern History (Q41–50):   Wrong: ___
Ancient + Medieval (Q51–56): Wrong: ___
Science GK (Q57–63):       Wrong: ___
Geography (Q64–75):        Wrong: ___

YOUR 3 WEAKEST BLOCKS (most wrong answers):
  1. _______________________
  2. _______________________
  3. _______________________

These become your DAY 57–70 intensive focus areas in Phase 2.
```

---

# PHASE 2 PLANNING TABLE

## Based on your weak topics, here is the Phase 2 roadmap already scheduled:

| Day | CS Topic | GS Topic |
|-----|----------|----------|
| 57 | SQL Advanced: Views, Joins, Subqueries | Polity — State Legislature |
| 58 | SQL Transactions + ACID | Current Affairs — Space |
| 59 | Networks Advanced: TDM, Subnetting, I/O | History — Salt Satyagraha |
| 60 | Full Mock Test 1 (150 Q, 2.5 hrs) | All sections |
| 61–67 | Digital Electronics: Logic Gates + Boolean Algebra | Geography + Economy |
| 68–77 | Algorithms: Sorting, Searching, Trees | Indian Constitution |
| 78–84 | OS: Memory Management + Process Scheduling | Science GK Part 2 |

---

# 🔁 DAY 56 — EVENING RECAP

## Key Reminders Before Phase 2:

```
MOST COMMON MISTAKES TO NEVER REPEAT:
  ❌ "Tana Bhagat = peasant movement" → ✅ TRIBAL movement
  ❌ "INA founded by Bose" → ✅ FOUNDED by Mohan Singh
  ❌ "delete NULL crashes" → ✅ SAFE — no-op
  ❌ "UNION is a SQL constraint" → ✅ UNION is a SET OPERATION
  ❌ "COMPUTE is aggregate function" → ✅ COMPUTE is INVALID
  ❌ "IPv6 = 64 bits" → ✅ IPv6 = 128 BITS
  ❌ "Private key = sender's" → ✅ Private key = RECEIVER keeps it
  ❌ "Peer-to-peer is a topology" → ✅ NOT a topology
  ❌ "Multiprogramming = 4th gen" → ✅ MULTIPROGRAMMING = 3rd generation
  ❌ "PASCAL = scientific" → ✅ PASCAL = STRUCTURED code
  ❌ "Lothal = Great Bath" → ✅ LOTHAL = DOCKYARD; Mohenjo-daro = Great Bath
  ❌ "GT Road = Akbar" → ✅ GT ROAD = SHER SHAH SURI
  ❌ "Black soil only in Karnataka" → ✅ Karnataka AND Gujarat (Answer D)

ANSWER PATTERN REMINDER:
  ~20–25% of BPSC TRE answers = Option D (More than one)
  ~5–8% of answers = Option E (None of the above)
  Never eliminate D or E automatically!
```

---

## 🎯 Tonight's Action Items:
1. **Score your mock test** → identify your 3 weakest blocks
2. **Write Phase 2 priority list** in your notebook: which 3 CS topics need re-study
3. **Write a one-line fact** for each question you got wrong (the correct answer)
4. Tomorrow (Day 57): Start SQL Advanced — it's one of the highest-weight topics

---

*Phase 2 begins: Day 57 — SQL Advanced: Views, Joins, Subqueries + State Legislature*
