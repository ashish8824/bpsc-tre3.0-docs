# 📅 BPSC TRE 4.0 — DAY 52 COMPLETE STUDY MODULE
### OOP Quick Revision (CS) + Ancient Indian History — Indus Valley, Vedic, Mauryas, Guptas (GS)
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): OOP + C++ — rapid-fire revision of every PYQ-tested fact
> - Afternoon (1 hr): Ancient Indian History — Indus Valley to Guptas — story + facts
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5-bullet revision notes in your notebook

---

# PART 1: COMPUTER SCIENCE
## 📘 OOP + C++ — Complete Quick Revision for Day 52

> **Day 52 Context:** OOP + C++ is the **#1 highest-weight CS topic** — ~20% of the paper (~16 questions). You covered it deeply on Days 1–14. Today: every single PYQ-tested fact in rapid-fire format. This is the topic that wins or loses the exam. Treat each block as a checklist — tick it only if you can recall it without reading.

---

## 🔷 BLOCK 1: The 4 Pillars of OOP

```
THE 4 PILLARS — ALL FOUR REQUIRED for "pure OOP":
  1. ENCAPSULATION  — wrapping data + methods together; data hiding
  2. ABSTRACTION    — hiding implementation, showing only interface
  3. INHERITANCE    — child class acquires properties of parent class
  4. POLYMORPHISM   — "many forms"; same entity behaves differently in different contexts

⚠️ PYQ TRAP: "Which is NOT a feature of pure OOP?"
              If any of the 4 pillars is listed as "not required" = WRONG statement
              A pure OOP language MUST support ALL 4 pillars

CLASS vs OBJECT:
  Class  = blueprint/template (e.g., "Car" design)
  Object = instance of class (e.g., "my Honda City" = one specific car)

Instance variable = belongs to OBJECT (different value per object)
Class variable    = belongs to CLASS (shared by ALL objects)
```

---

## 🔷 BLOCK 2: Access Specifiers

```
THREE ACCESS SPECIFIERS:
  public    → accessible from ANYWHERE (inside class, outside class, derived class)
  private   → accessible ONLY inside the class (default for class)
  protected → accessible inside class AND derived classes; NOT from outside

struct vs class in C++ — THE ONLY DIFFERENCE:
  struct → default access = PUBLIC   ← PYQ tested
  class  → default access = PRIVATE  ← PYQ tested
  (In all other ways, struct and class are identical in C++)

⚠️ PYQ TRAP: "Modularity in OOP means ___?"
              Answer: dividing program into small independent modules
              NOT "hiding parts of the program" (that's Encapsulation/Abstraction)
```

### 🚨 PYQ TRAP #1:
> `struct` default = **PUBLIC** | `class` default = **PRIVATE**.
> This single distinction is the only difference between struct and class in C++.
> Modularity = **dividing into modules** (NOT hiding).

---

## 🔷 BLOCK 3: Inheritance — Types & Syntax

```
TYPES OF INHERITANCE:
  Single       → one child, one parent         (A → B)
  Multiple     → one child, multiple parents   (A + B → C)
  Multilevel   → chain of inheritance          (A → B → C)
  Hierarchical → one parent, multiple children (A → B, A → C)
  Hybrid       → combination of above

C++ SYNTAX:
  class Derived : access_specifier Base { };
  Example: class Dog : public Animal { };
  ← Uses COLON (:), NOT "extends"

Java SYNTAX:
  class Derived extends Base { }
  ← Uses "extends" keyword

⚠️ TRAP: C++ uses colon (:) | Java uses "extends"
          They CANNOT be swapped!

WHAT IS INHERITED:
  ✅ public members of base
  ✅ protected members of base
  ❌ private members of base (NOT inherited — only accessible via public methods)
  ❌ Constructors and Destructors (NOT inherited)
  ❌ Friend functions (NOT inherited)

Protected members:
  → CAN be inherited by derived class
  → CANNOT be accessed from outside the class hierarchy ← PYQ exact phrasing
```

---

## 🔷 BLOCK 4: Virtual Inheritance & Diamond Problem

```
DIAMOND PROBLEM:
  Occurs in MULTIPLE INHERITANCE when two parent classes share a common grandparent
  Result: Grandparent's data gets duplicated in the final derived class

      A
     / \
    B   C
     \ /
      D     ← D gets TWO copies of A's data → AMBIGUITY

SOLUTION: VIRTUAL INHERITANCE
  class B : virtual public A { };
  class C : virtual public A { };
  class D : public B, public C { };
  Now D gets only ONE copy of A's data ← virtual keyword ensures this

VIRTUAL FUNCTION:
  → Function declared with "virtual" keyword in base class
  → Can be overridden in derived class
  → Enables RUNTIME POLYMORPHISM

PURE VIRTUAL FUNCTION:
  → Syntax: virtual void funcName() = 0;
  → Has NO implementation in base class
  → Derived class MUST implement it
  → Making a class have even ONE pure virtual function = ABSTRACT CLASS

ABSTRACT CLASS:
  → Has at least ONE pure virtual function ← PYQ definition
  → CANNOT be instantiated (no objects can be created from it)
  → Can have mix of virtual, pure virtual, and normal functions
```

### 🚨 PYQ TRAP #2:
> Abstract class = at least **one pure virtual function**.
> Pure virtual function syntax = `virtual void func() = 0;`
> A class with **ALL** pure virtual functions = **interface** (concept from Java but tested conceptually).

---

## 🔷 BLOCK 5: Polymorphism

```
POLYMORPHISM = "many forms"

TWO TYPES:

1. COMPILE-TIME POLYMORPHISM (Static / Early Binding):
   → Resolved at COMPILE TIME
   → Types:
     a. Method Overloading  — same function name, different parameters
     b. Operator Overloading — redefining operators (+, -, *, etc.)
     c. Templates           — function/class templates in C++
   → HOW TO IMPLEMENT compile-time polymorphism: use TEMPLATE ← TRE 2.0 PYQ

2. RUNTIME POLYMORPHISM (Dynamic / Late Binding):
   → Resolved at RUN TIME
   → Achieved through: METHOD OVERRIDING with virtual functions
   → vtable (virtual function table) and vptr (virtual pointer) used internally

OVERLOADING vs OVERRIDING:
  Overloading → SAME class, SAME name, DIFFERENT parameters (compile-time)
  Overriding  → DIFFERENT classes (parent-child), SAME name, SAME parameters (runtime)
```

### 🚨 PYQ TRAP #3:
> **Templates** implement compile-time polymorphism (TRE 2.0 exact question).
> Runtime polymorphism **requires virtual functions**.
> Overloading = same class | Overriding = parent-child classes.

---

## 🔷 BLOCK 6: Constructors & Destructors

```
CONSTRUCTOR RULES:
  → Same name as class
  → No return type (not even void)
  → Called AUTOMATICALLY when object is created
  → Can be overloaded (multiple constructors allowed)

TYPES OF CONSTRUCTORS:
  Default     → no parameters; compiler provides if none defined ← PYQ
  Parameterized → takes arguments
  Copy        → takes reference to same class object; used for deep/shallow copy

DESTRUCTOR RULES:
  → Name = ~ClassName()
  → No parameters, no return type
  → Only ONE destructor per class (CANNOT be overloaded)
  → Called automatically when object goes out of scope
  → Used for cleanup (freeing memory, closing files)

ORDER IN INHERITANCE:
  Creation: Base constructor → Derived constructor
  Destruction: Derived destructor → Base destructor (REVERSE order)

COMPILER-PROVIDED DEFAULT CONSTRUCTOR:
  → If programmer writes NO constructor, compiler automatically provides default
  → As soon as programmer writes ANY constructor, compiler stops providing default

UNNAMED CLASS:
  → In C++, a class can exist without a name
  → Unnamed class has NO constructor and NO destructor ← PYQ exact fact

DEEP COPY vs SHALLOW COPY:
  Shallow copy → copies pointer addresses (both objects point to SAME memory)
  Deep copy    → creates new memory and copies actual data (independent copies)
  Copy constructor should do DEEP COPY to avoid dangling pointer issues
```

### 🚨 PYQ TRAP #4:
> Compiler provides DEFAULT constructor **only if programmer defines NO constructor**.
> Unnamed class = **no constructor, no destructor**.
> Only **ONE destructor** per class — cannot be overloaded.

---

## 🔷 BLOCK 7: C++ Specifics — The Exam Mines

```
VARIABLE NAMING RULES:
  ✅ Valid: myVar, _count, var123, MyClass
  ❌ Invalid: 123Variable (starts with digit), my var (space), my-var (hyphen)
  → Cannot start with digit ← most tested invalid rule
  → No spaces, no special characters except underscore (_)

SIZEOF():
  → Does NOT evaluate the expression inside ← PYQ key fact
  → sizeof(x++) → x is NOT incremented; sizeof just checks type size

RESERVED KEYWORD "new":
  → "new" is a RESERVED KEYWORD in C++
  → Using "new" as a variable name in C++ → COMPILE ERROR
  → Using "new" as a variable name in C → WORKS FINE (not reserved in C)

HEADER FILES:
  → User-defined header files use .h extension ← PYQ
  → Standard headers: <iostream>, <cstdlib>, etc. (no .h in modern C++)

FILE HANDLING MODES:
  ios::in     → open for reading
  ios::out    → open for writing
  ios::trunc  → TRUNCATE file to ZERO length on open ← PYQ tested
  ios::app    → append to end of file
  ios::binary → binary mode
  Modes CAN be combined with | operator (e.g., ios::in | ios::out) ← PYQ

TURBO C++ SHORTCUTS:
  Ctrl+F9  → COMPILE AND RUN ← PYQ tested
  Alt+F9   → COMPILE ONLY

ARRAYS:
  → Correct declaration: int array[10];  ← PYQ
  → is_array() → checks if variable is of array type
  → rank()     → returns DIMENSION of the array ← PYQ tested
  → Two types in C++: Single-dimensional + Multi-dimensional
  → String concatenation with char arrays using + → COMPILE ERROR ← PYQ
  → Example: char s1[]="Hello"; s1 + " world" → ERROR (cannot use + with char arrays)

EXCEPTION HANDLING:
  → Code with RISK OF ABNORMAL TERMINATION → must go in TRY block ← PYQ
  → try { risky code } catch(type) { handler } throw expression;
  → catch(...) → catches ALL exception types
  → Code throws exception → nearest matching catch block handles it

INLINE FUNCTIONS:
  → inline keyword → function body inserted at call site
  → Purpose: eliminate function call overhead (no return call)
  → Used for SMALL, SIMPLE functions
  → NOT used for large/complex functions ← "Inline is used for large functions" = WRONG STATEMENT
  → Compiler may IGNORE inline request for complex functions
```

### 🚨 PYQ TRAP #5:
> `ios::trunc` **truncates** file to zero (not appends, not closes).
> `rank()` returns the **dimension** (not size, not length) of an array.
> `sizeof()` does **NOT evaluate** the expression — just checks data type.
> "Inline functions are used for large/complex functions" = **INCORRECT statement**.

---

## 🔷 BLOCK 8: Friend Functions & Operator Overloading

```
FRIEND FUNCTION:
  → NOT a member of the class
  → Declared inside class with "friend" keyword
  → Defined OUTSIDE the class (no class scope)
  → Can access PRIVATE and PROTECTED members of the class
  → NOT inherited by derived classes ← PYQ trap
  → NOT called using dot (.) operator (it's not a member)

OPERATOR OVERLOADING:
  → Redefining the meaning of operators for user-defined types
  → Example: overloading + for complex number addition
  → Syntax: return_type operator symbol (parameters) { }
  → NOT all operators can be overloaded:
    Cannot overload: ::  .  .*  ?:  sizeof
    These 5 operators CANNOT be overloaded in C++ ← PYQ
```

---

## 📊 OOP RAPID FIRE — 1-LINE RECALL TABLE

| Concept | Key Fact |
|---------|----------|
| 4 pillars | Encapsulation, Abstraction, Inheritance, Polymorphism |
| struct default | PUBLIC |
| class default | PRIVATE |
| Abstract class | At least ONE pure virtual function |
| Pure virtual syntax | `virtual void f() = 0;` |
| Compile-time poly | Overloading, Templates, Operator overloading |
| Runtime poly | Overriding with virtual functions |
| Templates implement | Compile-time polymorphism |
| Overloading vs Overriding | Same class vs Parent-child class |
| C++ inheritance syntax | `class D : public B { }` (colon) |
| Java inheritance syntax | `class D extends B { }` (extends) |
| Diamond problem solution | Virtual inheritance |
| Default constructor | Compiler provides IF no constructor defined |
| Destructor count | Only ONE per class |
| Unnamed class | No constructor, no destructor |
| `sizeof()` | Does NOT evaluate expression |
| `new` in C++ | Reserved keyword — can't use as variable |
| `ios::trunc` | Truncates file to zero |
| Ctrl+F9 (Turbo C++) | Compile AND run |
| `rank()` | Returns DIMENSION of array |
| String + with char[] | COMPILE ERROR |
| TRY block contains | Code at risk of abnormal termination |
| Inline functions | Small/simple, NOT large/complex |
| Friend function | Accesses private members; NOT inherited |
| Modularity | Dividing into modules (NOT hiding) |

---
---

# PART 2: GENERAL STUDIES
## 🏛️ Ancient Indian History — Complete PYQ-Focused Deep Dive

> **Why Day 52?** Ancient History appeared in TRE 3.0 and is expected to continue in TRE 4.0. The exam tests specific, factual recall — not essays. Every section below is built around what a BPSC TRE question would actually ask.

---

## 🔷 SECTION 1: INDUS VALLEY CIVILISATION (IVC)

### Dates & Overview:
```
Period:  ~2500–1500 BCE (also called 3300–1300 BCE in broader estimates)
         For BPSC: remember 2500–1500 BCE
Also called: Harappan Civilisation (after the FIRST discovered site — Harappa)
Location: Indus River valley — present-day Pakistan + northwest India
Type:     URBAN civilisation (the first urban civilisation of the Indian subcontinent)
```

### Major Sites — The Most Tested Table:

```
SITE                  | LOCATION (Modern)        | FAMOUS FOR
──────────────────────┼──────────────────────────┼───────────────────────────────
Harappa               | Punjab, Pakistan          | FIRST discovered site (1921)
                      |                           | Discovered by: Daya Ram Sahni
Mohenjo-daro          | Sindh, Pakistan           | "Mound of the Dead"; GREAT BATH
                      |                           | Discovered by: R.D. Banerji (1922)
Lothal                | Gujarat, India            | DOCKYARD (ancient seaport) ← PYQ
                      |                           | Trade with Mesopotamia
Dholavira             | Gujarat (Rann of Kutch)   | Water conservation; unique signboard
Kalibangan            | Rajasthan, India          | Fire altars; pre-Harappan ploughed field
Rakhigarhi            | Haryana, India            | Largest Harappan site (IN INDIA)
Surkotada             | Gujarat, India            | Horse bones found
Banawali              | Haryana, India            | Barley cultivation evidence
```

### Key Features of IVC:
```
TOWN PLANNING (the most distinctive feature):
  → GRID PATTERN streets (roads at right angles to each other)
  → Two-storied brick houses
  → Houses had WELLS and BATHROOMS
  → Advanced DRAINAGE SYSTEM (covered drains running along streets)
  → Granaries for storing grain (found at Harappa and Mohenjo-daro)

GREAT BATH (Mohenjo-daro):
  → Large public bathing structure
  → Made of baked bricks with bitumen waterproofing
  → Purpose: possibly religious/ritual purification
  → Surrounded by a colonnade of rooms

SCRIPT:
  → Indus Valley script EXISTS but is UNDECIPHERED ← PYQ key fact
  → Written right to left (and sometimes boustrophedon — alternating directions)
  → No bilingual inscription found yet (reason it remains undeciphered)

TRADE AND ECONOMY:
  → TRADE-BASED economy (NOT agriculture-based primarily) ← PYQ angle
  → Evidence of trade with Mesopotamia (present-day Iraq)
  → Lothal's dockyard = evidence of sea trade
  → Standardised weights and measures (cube-shaped stone weights)

MATERIALS AND TECHNOLOGY:
  → Used BRONZE (not iron) — this was the Bronze Age civilisation
  → NO IRON WEAPONS found ← PYQ key fact (Iron Age came later)
  → Pottery: red/black ware with geometric designs
  → Cotton cultivation evidence (Mohenjo-daro)
  → Famous bronze figurine: "Dancing Girl" (Mohenjo-daro)
  → Terracotta toys and figurines found

RELIGION:
  → No grand temples found (unlike later civilisations)
  → Evidence of MOTHER GODDESS worship (terracotta female figurines)
  → Proto-Shiva figure (Pashupati seal) — man surrounded by animals
  → Tree worship and animal worship evidence

DECLINE (debated causes):
  → Flood theory (Indus floods)
  → Aryan invasion theory (now largely rejected)
  → Climate change / drought
  → Tectonic activity
```

### 🚨 PYQ TRAP #6:
> IVC had **NO IRON WEAPONS** — it was a Bronze Age civilisation.
> Lothal = **dockyard** (not granary, not bath). The dockyard is Lothal's unique marker.
> IVC script = **undeciphered** (important exam negative).

---

## 🔷 SECTION 2: VEDIC AGE

### Early Vedic Period (1500–1000 BCE):
```
People:    Aryans (Indo-European people who migrated into India)
Economy:   PASTORAL (cattle-herding) + NOMADIC ← key feature
           Cattle = primary wealth
Text:      RIGVEDA — the oldest of the four Vedas ← PYQ
           Collection of hymns to gods (Agni, Indra, Varuna, Soma)
Society:   Tribal; relatively simple social structure
           Women had somewhat better status (could attend sabhas, study Vedas)
Polity:    Jana (tribe) → Janapada (territory of a tribe) — transition
```

### Later Vedic Period (1000–600 BCE):
```
Economy:   SETTLED AGRICULTURE (shift from nomadic pastoralism)
           Iron tools used for agriculture and clearing forests
Society:   CASTE SYSTEM becomes more rigid ← PYQ
           Varna system: Brahmin, Kshatriya, Vaishya, Shudra
           Women's status declined (excluded from education, rituals)
Polity:    Large kingdoms (mahajanapadas) emerging
Texts:     Samaveda (music), Yajurveda (rituals), Atharvaveda (medicine/magic)
           Upanishads: philosophical texts questioning rituals; "Brahman-Atman" concept
           Aranyakas: "forest texts" — philosophical
```

### Four Vedas — Quick Recall:
```
1. RIGVEDA   → Hymns; OLDEST; most important for historians ← PYQ
2. SAMAVEDA  → Melodies and chants (musical Veda)
3. YAJURVEDA → Rituals and sacrificial formulas
4. ATHARVAVEDA → Spells, charms, medicine

Epics (NOT Vedas, but tested):
  Ramayana → Valmiki
  Mahabharata → Ved Vyasa (also contains Bhagavad Gita)
```

---

## 🔷 SECTION 3: MAURYAN EMPIRE (321–185 BCE)

### Founding of the Empire:
```
Founded by: CHANDRAGUPTA MAURYA (321 BCE)
Adviser:    CHANAKYA (also called Kautilya or Vishnugupta) ← same person, three names
            Chanakya's role: strategic adviser who helped Chandragupta overthrow
                             the Nanda dynasty and establish the Mauryan Empire

Chanakya's famous work: ARTHASHASTRA ← PYQ key fact
  → A treatise on statecraft, economic policy, and military strategy
  → Written in Sanskrit
  → Deals with: governance, taxation, diplomacy, war, espionage
  → Often compared to Machiavelli's "The Prince"

Capital: PATALIPUTRA (modern Patna, Bihar) ← Bihar connection!
         Pataliputra was the capital of the Mauryan Empire
```

### Chandragupta Maurya:
```
Reign: ~321–297 BCE
Achievements:
  → First emperor to unify most of the Indian subcontinent
  → Defeated Seleucus Nicator (Greek general) — signed a treaty
  → Seleucus gave four provinces to Chandragupta + gave his daughter in marriage
  → Ambassador Megasthenes sent to Pataliputra by Seleucus
  → Megasthenes wrote "INDICA" — a detailed account of Mauryan India ← PYQ
End of life: Chandragupta converted to JAINISM (Digambara sect)
             Fasted to death at Shravanabelagola (Karnataka) — Sallekhana
```

### Ashoka — The Greatest Mauryan Emperor:
```
Reign: ~268–232 BCE (grandson of Chandragupta Maurya)
Full name: Ashoka Maurya (also known as "Devanampiya Piyadasi" — Beloved of Gods)

THE KALINGA WAR (261 BCE) — The Turning Point: ← PYQ key event
  → Kalinga = present-day Odisha
  → Ashoka attacked Kalinga to expand the empire
  → Result: 100,000 soldiers killed; 150,000 deported; many more died
  → Ashoka saw the massive suffering and was overcome with remorse
  → Converted to BUDDHISM ← PYQ: Ashoka converted after Kalinga War
  → Abandoned further military conquest
  → Adopted DHAMMA (his own moral code)

DHAMMA (Ashoka's Code):
  → Not the same as Buddhism (a broader personal code)
  → Principles: non-violence, truth, respect for elders, compassion for animals
  → Spread through Rock Edicts and Pillar Edicts across the empire

ASHOKA'S CONTRIBUTIONS:
  → Spread Buddhism across Asia (sent missionaries to Sri Lanka, Central Asia, Egypt)
  → Built hospitals for humans and animals
  → Planted trees along roads; dug wells
  → Built stupas (Buddhist monuments) including Sanchi Stupa
  → Lion Capital (at Sarnath) = India's national emblem ← PYQ
  → Ashoka Chakra (on Indian flag) = from Ashoka's pillar ← PYQ

ROCK EDICTS AND PILLAR EDICTS:
  → Used Brahmi script (in India) and Kharosthi + Greek (in northwest)
  → Girnar (Gujarat) — Major Rock Edict
  → Topra (Delhi) — Pillar Edict (moved to Delhi by Firuz Shah Tughlaq)
  → Lumbini Pillar Edict — records Buddha's birthplace

DECLINE OF MAURYAN EMPIRE:
  → Brihadratha (last Mauryan emperor) was killed by his general Pushyamitra Shunga (185 BCE)
  → Shunga dynasty replaced the Mauryans
```

### 🚨 PYQ TRAP #7:
> Chanakya = Kautilya = Vishnugupta → **all the same person**; wrote **Arthashastra**.
> Ashoka converted to Buddhism after **Kalinga War (261 BCE)**.
> **Lion Capital** of Sarnath = India's national emblem.
> Capital of Mauryan Empire = **Pataliputra** (modern Patna).

---

## 🔷 SECTION 4: POST-MAURYAN PERIOD

### Shunga Dynasty (185–73 BCE):
```
Founded by: Pushyamitra Shunga (killed last Mauryan emperor)
Religion:   Brahmanical revival (reversed Ashoka's Buddhist policies to some extent)
Famous for: Sanchi Stupa's gateways (toranas) built during Shunga period
```

### Kushana Dynasty (1st–3rd century CE):
```
Famous king: KANISHKA ← PYQ key name
             → Promoted BUDDHISM extensively
             → Held the 4th Buddhist Council (in Kashmir)
             → Extended empire into Central Asia
             → Capital: Purushapura (modern Peshawar, Pakistan)
             → Era: Kanishka era (78 CE onwards)

Gandhara Art:
  → Developed under Kushanas
  → Blend of Greek and Indian styles (Hellenistic influence)
  → Buddha first depicted in HUMAN FORM (earlier only symbols used)
```

### Satavahana Dynasty (230 BCE – 220 CE):
```
Location: DECCAN REGION (mainly present-day Maharashtra, Telangana)
Religion: Hindu (patronized Brahmanism + tolerated Buddhism)
Famous king: Gautamiputra Satakarni
Achievement: Stopped Shaka (Saka) invasions; consolidated Deccan
```

---

## 🔷 SECTION 5: GUPTA EMPIRE — THE GOLDEN AGE

### Overview:
```
Period: 319–550 CE approximately
Why "Golden Age"?
  → Peak of art, literature, science, mathematics in ancient India
  → Political stability + economic prosperity + cultural flowering

Founders and Key Rulers:
  Chandragupta I      (319–335 CE) → FOUNDED Gupta Empire
  Samudragupta        (335–375 CE) → "Napoleon of India" — military conqueror
  Chandragupta II     (375–415 CE) → "VIKRAMADITYA" — PEAK of Gupta Empire ← PYQ
  Kumaragupta I       (415–455 CE) → Founded Nalanda University
  Skandagupta         (455–467 CE) → Last great Gupta emperor; fought Hunas
```

### Chandragupta II (Vikramaditya) — The Golden Peak:
```
Title:      VIKRAMADITYA ← Most tested Gupta emperor
Period:     375–415 CE
Capital:    PATALIPUTRA (later also Ujjain)
Achievements:
  → Defeated the Shakas (western Kshatrapas) — annexed Malwa, Gujarat
  → Extended empire to its maximum extent
  → Era of maximum peace and prosperity
  → NAVARATNAS (Nine gems) at his court:

The 9 Gems of Chandragupta II's Court:
  1. KALIDASA       → Greatest Sanskrit poet and dramatist
                      Works: Meghaduta, Abhijnanasakuntalam, Raghuvamsha, Kumarasambhava
  2. ARYABHATA      → Mathematician-astronomer
                      Calculated value of pi; discovered Earth rotates on axis
                      Wrote Aryabhatiya
  3. VARAHAMIHIRA   → Astronomer; Brihatsamhita
  4. VARARUCHI      → Grammarian
  5. Brahmagupta    → Mathematician (later period)
  ... (not all 9 are equally PYQ-tested; focus on Kalidasa + Aryabhata)
```

### Gupta Period Achievements:
```
LITERATURE:
  → Kalidasa's works — greatest Sanskrit literature ever produced
  → Panchatantra (fables) — compiled in Gupta period
  → Ramayana and Mahabharata got final form during this period

SCIENCE AND MATHEMATICS:
  → ARYABHATA: ← PYQ key person
    - Calculated PI (π) ≈ 3.1416
    - Proposed HELIOCENTRIC theory (Earth revolves around Sun) — for ancient India
    - Explained solar and lunar eclipses scientifically
    - Wrote ARYABHATIYA ← his key text
  → Place value system and concept of ZERO developed (credited to this period)
  → Decimal system refined

MEDICINE:
  → Dhanvantari — physician (Gupta court)
  → Sushruta Samhita (earlier, but used extensively in Gupta period) — surgery

ARCHITECTURE AND ART:
  → IRON PILLAR at DELHI (Mehrauli) ← PYQ key fact
    - Built during Chandragupta II's reign
    - Made of rust-free iron — remarkable metallurgical achievement
    - Stands even today without rusting (1600+ years)
    - Located near Qutb Minar complex
  → Cave temples: Ajanta (Buddhist) and Ellora (multi-religious) — developed in this period
  → Temple architecture: Dashavatara Temple (Deogarh), etc.

NALANDA UNIVERSITY:
  → Founded by KUMARAGUPTA I (Gupta emperor) ← PYQ
  → Located in Bihar (modern Nalanda district, Bihar)
  → Became one of the greatest centres of learning in the ancient world
  → Students came from China, Korea, Japan, Tibet, Central Asia
  → Famous Chinese traveller: XUANZANG (Hiuen Tsang) visited during Harsha's reign
```

### Decline of Gupta Empire:
```
Causes:
  → HUNA invasions (Central Asian nomads) — weakened the empire
  → Skandagupta repelled them but it drained resources
  → Internal rebellions by feudal lords
  → Fragmentation into smaller kingdoms after 500 CE
```

### 🚨 PYQ TRAP #8:
> **Gupta period = Golden Age of Ancient India** (not Mauryan, not Vedic).
> **Chandragupta II = Vikramaditya** (not Chandragupta I who just founded the empire).
> **Iron Pillar at Delhi** = Gupta period, not Medieval, not British.
> **Nalanda University** = founded by **Kumaragupta I** (Gupta emperor), located in **Bihar**.
> **Aryabhata** = Gupta period mathematician/astronomer.

---

## 🔷 SECTION 6: MASTER COMPARISON TABLE — All Ancient Empires

| Empire | Period | Key Ruler | Capital | Famous For |
|--------|--------|-----------|---------|------------|
| IVC | 2500–1500 BCE | (no single ruler) | Mohenjo-daro / Harappa | Great Bath, grid towns, undeciphered script |
| Vedic | 1500–600 BCE | (tribal/Aryan) | — | Rigveda, caste system |
| Mauryan | 321–185 BCE | Ashoka | Pataliputra (Patna) | Arthashastra, Dhamma, Kalinga War, Lion Capital |
| Shunga | 185–73 BCE | Pushyamitra Shunga | Pataliputra | Brahmanical revival |
| Kushana | 1st–3rd CE | **Kanishka** | Purushapura | Buddhism, Gandhara art |
| Satavahana | 230 BCE–220 CE | Gautamiputra Satakarni | Pratishthana | Deccan region, Brahmanical |
| **Gupta** | **319–550 CE** | **Chandragupta II (Vikramaditya)** | **Pataliputra** | **Golden Age, Kalidasa, Aryabhata, Iron Pillar** |

---

## 🔷 SECTION 7: MEMORY TRICKS

```
IVC SITES TRICK — "HML + DR":
  H = Harappa (Punjab, Pakistan) — FIRST discovered
  M = Mohenjo-daro (Sindh) — GREAT BATH
  L = Lothal (Gujarat) — DOCKYARD
  D = Dholavira (Gujarat) — water conservation
  R = Rakhigarhi (Haryana) — LARGEST site in India

MAURYAN MEMORY:
  "Chandragupta with CHANakya defeated NANDA, made PATALIPUTRA capital"
  CHA = CHAndragupta + CHAnakya together
  ARTHASHASTRA = ARTHA (money/policy) + SHASTRA (science) → Chanakya's book on governance

ASHOKA'S FORMULA:
  KALINGA WAR (261 BCE) → BUDDHISM → DHAMMA → EDICTS → LION CAPITAL
  "War caused sorrow → sought peace in Buddha → spread Dhamma → carved it in stone"

GUPTA GOLDEN AGE:
  "CHANDRAGUPTA II was VIKRAMADITYA — KALIDASA wrote for him, ARYABHATA calculated under him,
   IRON PILLAR stands for him, NALANDA educated beyond him"

ARYABHATA vs ARYABHATTA:
  Common spelling in exams: ARYABHATA (one 't') — though both spellings appear
  Remember: He was from PATALIPUTRA (Bihar) — local pride!

FOUR VEDAS in order:
  "Real Saints Yell Aloud"
  R = Rigveda (oldest)
  S = Samaveda
  Y = Yajurveda
  A = Atharvaveda
```

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topic: OOP + C++ — All Concepts

---

**Q1.** Which of the following is TRUE about the FOUR PILLARS of Object-Oriented Programming?
(A) A pure OOP language requires only Inheritance and Polymorphism
(B) Abstraction and Encapsulation are the same concept
(C) A pure OOP language must support all four pillars: Encapsulation, Abstraction, Inheritance, Polymorphism
(D) More than one of the above
(E) None of the above

---

**Q2.** What is the DEFAULT access specifier for members of a `struct` in C++?
(A) private
(B) protected
(C) public
(D) More than one of the above
(E) None of the above

---

**Q3.** An abstract class in C++ is defined as a class that:
(A) Has no data members, only methods
(B) Has at least ONE pure virtual function
(C) Cannot inherit from any other class
(D) More than one of the above
(E) None of the above

---

**Q4.** The syntax for a pure virtual function in C++ is:
(A) `virtual void func();`
(B) `void func() = 0;`
(C) `virtual void func() = 0;`
(D) More than one of the above
(E) None of the above

---

**Q5.** Compile-time polymorphism in C++ can be implemented using:
(A) Virtual functions
(B) Method overriding
(C) Templates
(D) More than one of the above
(E) None of the above

---

**Q6.** What is the difference between method OVERLOADING and method OVERRIDING?
(A) Overloading = same class, different parameters; Overriding = parent-child, same signature
(B) Overloading = parent-child classes; Overriding = same class
(C) Both are the same concept with different names
(D) More than one of the above
(E) None of the above

---

**Q7.** C++ uses which keyword/syntax for inheritance?
(A) `class Derived extends Base { }`
(B) `class Derived : public Base { }`
(C) `class Derived implements Base { }`
(D) More than one of the above
(E) None of the above

---

**Q8.** Virtual inheritance in C++ is used to solve:
(A) The dangling pointer problem
(B) The diamond problem in multiple inheritance
(C) Memory leaks in destructors
(D) More than one of the above
(E) None of the above

---

**Q9.** Which of the following is TRUE about constructors?
(A) A constructor must have a return type of void
(B) A class can have only one constructor
(C) If no constructor is defined by the programmer, the compiler provides a default constructor
(D) More than one of the above
(E) None of the above

---

**Q10.** Which of the following is TRUE about destructors in C++?
(A) A class can have multiple destructors (destructor overloading is allowed)
(B) A destructor has the same name as the class preceded by ~
(C) Destructors can take parameters
(D) More than one of the above
(E) None of the above

---

**Q11.** An UNNAMED class in C++ has:
(A) A system-generated default constructor
(B) No constructor and no destructor
(C) Only a destructor, no constructor
(D) More than one of the above
(E) None of the above

---

**Q12.** `sizeof()` operator in C++:
(A) Evaluates the expression inside before returning the size
(B) Returns the number of elements in an array
(C) Does NOT evaluate the expression — it only checks the data type for size
(D) More than one of the above
(E) None of the above

---

**Q13.** Using `new` as a variable name in C++:
(A) Is allowed since it's just a keyword suggestion
(B) Causes a compile error because `new` is a reserved keyword in C++
(C) Works fine because C++ is case-sensitive and New is different from new
(D) More than one of the above
(E) None of the above

---

**Q14.** The file mode `ios::trunc` in C++ file handling:
(A) Appends new data to the end of an existing file
(B) Opens a file for both reading and writing simultaneously
(C) Truncates the file to ZERO length when opened
(D) More than one of the above
(E) None of the above

---

**Q15.** In Turbo C++, which shortcut key is used to COMPILE AND RUN a program?
(A) Alt+F9
(B) Ctrl+F5
(C) Ctrl+F9
(D) More than one of the above
(E) None of the above

---

**Q16.** The `rank()` function in C++ returns:
(A) The number of elements in an array
(B) The size of each element in bytes
(C) The DIMENSION (number of dimensions) of an array
(D) More than one of the above
(E) None of the above

---

**Q17.** What is the result of executing: `char s1[] = "Hello"; char s2[] = "World"; char s3[] = s1 + s2;`
(A) s3 = "HelloWorld"
(B) s3 = "Hello World"
(C) Compile error — cannot use + operator with char arrays directly
(D) More than one of the above
(E) None of the above

---

**Q18.** Code that is at risk of causing ABNORMAL TERMINATION must be placed in which block?
(A) catch block
(B) throw block
(C) try block
(D) More than one of the above
(E) None of the above

---

**Q19.** Which of the following is an INCORRECT statement about inline functions?
(A) Inline functions save the overhead of a function call
(B) Inline functions are best suited for small, simple functions
(C) Inline functions are recommended for large and complex functions
(D) More than one of the above
(E) None of the above

---

**Q20.** A FRIEND function in C++:
(A) Is a member function of the class
(B) Can access private and protected members of the class but is NOT a member
(C) Is inherited by derived classes automatically
(D) More than one of the above
(E) None of the above

---

**Q21.** Which of the following variable names is INVALID in C++?
(A) `_myVariable`
(B) `MyVar123`
(C) `123Variable`
(D) More than one of the above
(E) None of the above

---

**Q22.** Protected members of a class:
(A) Are accessible from anywhere in the program
(B) Are accessible inside the class and in derived classes, but NOT from outside
(C) Are the same as private members and cannot be inherited
(D) More than one of the above
(E) None of the above

---

**Q23.** The order of constructor and destructor calls in inheritance (Base + Derived) is:
(A) Derived constructor → Base constructor; Base destructor → Derived destructor
(B) Base constructor → Derived constructor; Derived destructor → Base destructor
(C) Both constructors called simultaneously; both destructors called simultaneously
(D) More than one of the above
(E) None of the above

---

**Q24.** What does "Modularity" mean in OOP?
(A) Hiding the internal implementation from the user
(B) Dividing a program into small, independent, manageable modules
(C) Allowing multiple classes to share a single interface
(D) More than one of the above
(E) None of the above

---

**Q25.** User-defined header files in C++ use which extension?
(A) `.cpp`
(B) `.obj`
(C) `.h`
(D) More than one of the above
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 MCQs
### Ancient Indian History — IVC, Vedic, Mauryas, Guptas

---

**Q26.** The Indus Valley Civilisation is also known as:
(A) Vedic Civilisation
(B) Harappan Civilisation
(C) Gangetic Civilisation
(D) More than one of the above
(E) None of the above

---

**Q27.** Which Indus Valley Civilisation site is famous for its DOCKYARD?
(A) Harappa (Punjab)
(B) Mohenjo-daro (Sindh)
(C) Lothal (Gujarat)
(D) More than one of the above
(E) None of the above

---

**Q28.** The GREAT BATH is associated with which IVC site?
(A) Harappa
(B) Lothal
(C) Mohenjo-daro
(D) More than one of the above
(E) None of the above

---

**Q29.** The script of the Indus Valley Civilisation is:
(A) Written in Sanskrit
(B) Deciphered by scholars in the 20th century
(C) Still undeciphered
(D) More than one of the above
(E) None of the above

---

**Q30.** Which of the following is TRUE about weapons found in IVC archaeological sites?
(A) Iron weapons were the primary military tools
(B) Steel swords were found at Mohenjo-daro
(C) No iron weapons were found — IVC used bronze
(D) More than one of the above
(E) None of the above

---

**Q31.** The RIGVEDA is significant because it is:
(A) A text on military strategy written by Chanakya
(B) The oldest of the four Vedas — a collection of hymns
(C) A collection of stories about the Mauryan emperors
(D) More than one of the above
(E) None of the above

---

**Q32.** The Mauryan Empire was founded by:
(A) Ashoka Maurya
(B) Chandragupta Maurya
(C) Samudragupta
(D) More than one of the above
(E) None of the above

---

**Q33.** Chanakya (Kautilya) is famous for writing:
(A) Arthashastra — a treatise on statecraft and governance
(B) Rigveda — the collection of hymns
(C) Indica — an account of Mauryan India
(D) More than one of the above
(E) None of the above

---

**Q34.** The capital of the Mauryan Empire was:
(A) Ujjain
(B) Taxila
(C) Pataliputra (modern Patna, Bihar)
(D) More than one of the above
(E) None of the above

---

**Q35.** Ashoka converted to Buddhism after which event?
(A) His coronation ceremony in 268 BCE
(B) A meeting with Buddhist monks in Pataliputra
(C) The Kalinga War (261 BCE) and witnessing its immense suffering
(D) More than one of the above
(E) None of the above

---

**Q36.** DHAMMA, as propagated by Ashoka, referred to:
(A) A new form of Buddhism he invented
(B) His personal moral code based on non-violence, truth, and compassion
(C) A military doctrine for his generals
(D) More than one of the above
(E) None of the above

---

**Q37.** India's national emblem (the Lion Capital) was originally erected by:
(A) Chandragupta Maurya
(B) Chandragupta II (Vikramaditya)
(C) Ashoka (at Sarnath)
(D) More than one of the above
(E) None of the above

---

**Q38.** Kanishka, who promoted Buddhism and held the 4th Buddhist Council, was a king of which dynasty?
(A) Mauryan dynasty
(B) Gupta dynasty
(C) Kushana dynasty
(D) More than one of the above
(E) None of the above

---

**Q39.** The Gupta period is called the "Golden Age" of ancient India because:
(A) India had the world's largest gold reserves during this period
(B) It witnessed exceptional achievements in art, literature, science, and mathematics
(C) All rulers of the Gupta empire had "golden" in their name
(D) More than one of the above
(E) None of the above

---

**Q40.** Who founded the Gupta Empire?
(A) Samudragupta
(B) Chandragupta II
(C) Chandragupta I
(D) More than one of the above
(E) None of the above

---

**Q41.** Chandragupta II of the Gupta empire is also known as:
(A) Ashoka
(B) Vikramaditya
(C) Samudragupta
(D) More than one of the above
(E) None of the above

---

**Q42.** KALIDASA, the greatest Sanskrit poet and dramatist, was a gem at the court of:
(A) Ashoka (Mauryan emperor)
(B) Chandragupta II (Gupta emperor)
(C) Kanishka (Kushana king)
(D) More than one of the above
(E) None of the above

---

**Q43.** ARYABHATA was a Gupta period scholar famous for contributions to:
(A) Architecture and sculpture
(B) Mathematics and astronomy
(C) Military strategy and warfare
(D) More than one of the above
(E) None of the above

---

**Q44.** The famous IRON PILLAR at Delhi (Mehrauli), which has not rusted after 1600+ years, was built during:
(A) The Mauryan period
(B) The Delhi Sultanate period
(C) The Gupta period (during Chandragupta II's reign)
(D) More than one of the above
(E) None of the above

---

**Q45.** NALANDA UNIVERSITY was founded by which Gupta ruler?
(A) Chandragupta I
(B) Samudragupta
(C) Kumaragupta I
(D) More than one of the above
(E) None of the above

---

**Q46.** Nalanda University is located in which present-day Indian state?
(A) Uttar Pradesh
(B) West Bengal
(C) Bihar
(D) More than one of the above
(E) None of the above

---

**Q47.** The ARTHASHASTRA deals with:
(A) Religious philosophy and Buddhist principles
(B) Statecraft, economic policy, governance, and military strategy
(C) Mathematical calculations and astronomical observations
(D) More than one of the above
(E) None of the above

---

**Q48.** "INDICA" — an account of Mauryan India — was written by:
(A) Chanakya (Kautilya)
(B) Megasthenes (Greek ambassador)
(C) Ashoka himself
(D) More than one of the above
(E) None of the above

---

**Q49.** The Satavahana dynasty ruled over which region of India?
(A) Northwestern India (Punjab and Sindh)
(B) The Deccan region (Maharashtra, Telangana)
(C) Eastern India (Bengal and Odisha)
(D) More than one of the above
(E) None of the above

---

**Q50.** Which of the following CORRECTLY matches ancient personalities with their works or associations?
(A) Chanakya → Arthashastra | Kalidasa → Meghaduta | Aryabhata → Aryabhatiya
(B) Chanakya → Rigveda | Kalidasa → Arthashastra | Ashoka → Indica
(C) Megasthenes → Arthashastra | Aryabhata → Panchatantra
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
| 1 | (C) | Pure OOP requires ALL 4 pillars |
| 2 | (C) | struct default = PUBLIC |
| 3 | (B) | Abstract class = at least ONE pure virtual function |
| 4 | (C) | Pure virtual syntax: `virtual void func() = 0;` |
| 5 | (C) | Templates = compile-time polymorphism (TRE 2.0 PYQ) |
| 6 | (A) | Overloading=same class+diff params; Overriding=parent-child |
| 7 | (B) | C++ uses colon: `class D : public B {}` |
| 8 | (B) | Virtual inheritance solves the diamond problem |
| 9 | (C) | Compiler provides default constructor if none defined |
| 10 | (B) | Destructor = ~ClassName(); only ONE allowed |
| 11 | (B) | Unnamed class = no constructor, no destructor |
| 12 | (C) | sizeof() does NOT evaluate the expression |
| 13 | (B) | `new` is reserved in C++ — compile error if used as variable |
| 14 | (C) | ios::trunc = truncates file to zero |
| 15 | (C) | Ctrl+F9 = compile AND run in Turbo C++ |
| 16 | (C) | rank() = returns DIMENSION of array |
| 17 | (C) | Compile error — cannot use + with char arrays |
| 18 | (C) | Risk of abnormal termination → try block |
| 19 | (C) | "Inline for large/complex functions" = INCORRECT statement |
| 20 | (B) | Friend = accesses private, but NOT a member, NOT inherited |
| 21 | (C) | 123Variable is INVALID (starts with digit) |
| 22 | (B) | Protected = inside class + derived; NOT outside |
| 23 | (B) | Base constr→Derived constr; Derived destr→Base destr |
| 24 | (B) | Modularity = dividing into modules (not hiding) |
| 25 | (C) | User-defined headers use .h extension |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | IVC = Harappan Civilisation (after Harappa, first site found) |
| 27 | (C) | Lothal = dockyard (ancient seaport, Gujarat) |
| 28 | (C) | Great Bath = Mohenjo-daro |
| 29 | (C) | IVC script = still undeciphered |
| 30 | (C) | IVC = Bronze Age; NO iron weapons found |
| 31 | (B) | Rigveda = oldest Veda; collection of hymns |
| 32 | (B) | Mauryan Empire founded by Chandragupta Maurya |
| 33 | (A) | Chanakya wrote Arthashastra (statecraft) |
| 34 | (C) | Mauryan capital = Pataliputra (modern Patna, Bihar) |
| 35 | (C) | Ashoka converted to Buddhism after Kalinga War (261 BCE) |
| 36 | (B) | Dhamma = Ashoka's personal moral code |
| 37 | (C) | Lion Capital = Ashoka at Sarnath = India's national emblem |
| 38 | (C) | Kanishka = Kushana dynasty |
| 39 | (B) | Golden Age = exceptional art, literature, science |
| 40 | (C) | Gupta Empire FOUNDED by Chandragupta I |
| 41 | (B) | Chandragupta II = VIKRAMADITYA |
| 42 | (B) | Kalidasa = at court of Chandragupta II (Gupta) |
| 43 | (B) | Aryabhata = mathematics and astronomy |
| 44 | (C) | Iron Pillar Delhi = Gupta period (Chandragupta II) |
| 45 | (C) | Nalanda = founded by Kumaragupta I |
| 46 | (C) | Nalanda University = Bihar |
| 47 | (B) | Arthashastra = statecraft, economics, governance |
| 48 | (B) | Indica = written by Megasthenes (Greek ambassador) |
| 49 | (B) | Satavahana = Deccan region |
| 50 | (A) | Chanakya→Arthashastra; Kalidasa→Meghaduta; Aryabhata→Aryabhatiya — ALL CORRECT |

---
---

# 🔁 DAY 52 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — OOP + C++

```
4 PILLARS: Encapsulation, Abstraction, Inheritance, Polymorphism (ALL 4 required for pure OOP)
struct default = PUBLIC | class default = PRIVATE (only difference)
Abstract class = at least ONE pure virtual function: virtual void f() = 0;
Templates = compile-time polymorphism (TRE 2.0 PYQ)
Overloading = same class | Overriding = parent-child (with virtual)
C++ inheritance = colon (:) | Java = extends
Diamond problem → Virtual inheritance fixes it
Default constructor → compiler provides IF programmer writes NO constructor
Destructor → only ONE per class; cannot overload
Unnamed class → NO constructor, NO destructor
sizeof() → does NOT evaluate expression inside
new → RESERVED keyword in C++; cannot use as variable name (C++ only)
ios::trunc → truncates file to ZERO
Ctrl+F9 (Turbo C++) → compile AND run
rank() → returns DIMENSION of array (not size)
char[] + char[] → COMPILE ERROR
TRY block → code at risk of abnormal termination
Inline → small/simple; "for large/complex" = INCORRECT statement
Friend function → NOT a member; NOT inherited; accesses private members
Modularity → dividing into modules (NOT hiding)
User-defined headers → .h extension
```

---

## ⚡ RAPID FIRE — Ancient Indian History

```
IVC SITES:
  Harappa (Punjab) = FIRST discovered (1921) by Daya Ram Sahni
  Mohenjo-daro (Sindh) = GREAT BATH
  Lothal (Gujarat) = DOCKYARD ← most PYQ-tested IVC fact
  Rakhigarhi (Haryana) = largest IVC site in India
IVC = Bronze Age → NO IRON WEAPONS
IVC script = UNDECIPHERED
IVC economy = TRADE-BASED

VEDAS IN ORDER: Rigveda (oldest) → Samaveda → Yajurveda → Atharvaveda

MAURYAN:
  Founded by: CHANDRAGUPTA MAURYA (321 BCE)
  Adviser: CHANAKYA = KAUTILYA = VISHNUGUPTA (same person)
  Chanakya's book: ARTHASHASTRA (statecraft)
  Capital: PATALIPUTRA (Patna, Bihar)
  Greek ambassador: MEGASTHENES wrote INDICA
  Ashoka: converted after KALINGA WAR (261 BCE) → spread DHAMMA
  Lion Capital (Sarnath) = India's national emblem = Ashoka

POST-MAURYAN:
  KANISHKA (Kushana) → promoted Buddhism + 4th Buddhist Council

GUPTA GOLDEN AGE:
  Founded by: CHANDRAGUPTA I (319 CE)
  Peak: CHANDRAGUPTA II = VIKRAMADITYA (375–415 CE)
  Court gems: KALIDASA (poet) + ARYABHATA (mathematician)
  IRON PILLAR Delhi = Gupta period (Chandragupta II)
  NALANDA UNIVERSITY = founded by KUMARAGUPTA I, located in BIHAR
  ARYABHATA = calculated pi + heliocentric theory + wrote ARYABHATIYA
```

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. **Lothal** = dockyard (IVC, Gujarat); **Mohenjo-daro** = Great Bath; IVC script = undeciphered; NO iron weapons
2. **Ashoka** converted to Buddhism after **Kalinga War (261 BCE)**; Chanakya wrote **Arthashastra**; capital = **Pataliputra (Patna)**
3. **Gupta period = Golden Age**; **Chandragupta II = Vikramaditya**; Iron Pillar Delhi = Gupta period
4. **Nalanda University** = founded by Kumaragupta I = located in **Bihar** — always answer Bihar for Nalanda
5. OOP: Templates = **compile-time polymorphism**; struct = **PUBLIC** default; class = **PRIVATE** default

---

*Next: Day 53 — Medieval Indian History (Delhi Sultanate, Mughals, Bhakti, Sufism) + SQL Quick Revision*
