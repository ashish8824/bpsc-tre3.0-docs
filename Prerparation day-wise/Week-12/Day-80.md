# 📅 BPSC TRE 4.0 — DAY 80: SOFTWARE ENGINEERING (SDLC MODELS) + SCIENCE SHORTCUTS
### Week 12 — Computer Architecture + Software Engineering
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): CS — SDLC Models, Requirements, Verification vs Validation
> - Afternoon (1 hr): GS — Science Shortcuts (Physics + Biology PYQ facts)
> - Evening (1.5 hrs): Solve all 50 Mixed MCQs (25 CS + 25 GS)
> - Night (30 min): Read the "Last 1-Hour Before Exam" revision sheet

---

# PART 1: CS RAPID REVISION
## 📘 Software Engineering — All Concepts, One Place

---

## 🔷 TOPIC 1: What is Software Engineering?

```
SOFTWARE ENGINEERING = Application of engineering principles to
                       the design, development, testing, and
                       maintenance of software

PRIMARY GOAL of Software Engineering:
  → Produce software that meets USER REQUIREMENTS
    within BUDGET AND SCHEDULE ← #1 PYQ FACT

  (NOT just "write working code" — must meet budget + timeline too)

KEY ACTIVITIES:
  Requirements → Design → Implementation → Testing → Maintenance

SOFTWARE = Programs + Documentation + Data
         (NOT just the executable code alone)
```

---

## 🔷 TOPIC 2: SDLC — Software Development Life Cycle

### What is SDLC?
```
SDLC = Software Development Life Cycle

= The STRUCTURED PROCESS followed to develop software
= A framework that defines activities at each stage of development
= Ensures quality, organized development

PHASES in a typical SDLC (all models share these phases, in different order/style):
  1. Requirements Gathering
  2. System Design
  3. Implementation (Coding)
  4. Testing
  5. Deployment
  6. Maintenance
```

---

## 🔷 TOPIC 3: WATERFALL MODEL — Sequential & Rigid

### Diagram:
```
WATERFALL MODEL — One-way flow like a waterfall
════════════════════════════════════════════════

  ┌─────────────────────────────┐
  │   1. REQUIREMENTS           │
  │   (gather all requirements) │
  └──────────────┬──────────────┘
                 │ (only moves DOWN)
                 ▼
  ┌─────────────────────────────┐
  │   2. SYSTEM DESIGN          │
  │   (architecture, modules)   │
  └──────────────┬──────────────┘
                 │
                 ▼
  ┌─────────────────────────────┐
  │   3. IMPLEMENTATION         │
  │   (actual coding)           │
  └──────────────┬──────────────┘
                 │
                 ▼
  ┌─────────────────────────────┐
  │   4. TESTING                │
  │   (find and fix bugs)       │
  └──────────────┬──────────────┘
                 │
                 ▼
  ┌─────────────────────────────┐
  │   5. DEPLOYMENT             │
  │   (release to users)        │
  └──────────────┬──────────────┘
                 │
                 ▼
  ┌─────────────────────────────┐
  │   6. MAINTENANCE            │
  │   (updates and fixes)       │
  └─────────────────────────────┘

  KEY PROPERTY: EACH PHASE MUST BE FULLY COMPLETED
                BEFORE THE NEXT PHASE BEGINS
                (no going back easily — like a waterfall,
                 water only flows DOWN, not up)
```

### Waterfall Key Facts:
```
WATERFALL MODEL — KEY FACTS
────────────────────────────────────────────────────────────
Type        : Sequential (one phase at a time)
Flexibility : RIGID (hard to go back to previous phase)
Best for    : Projects with WELL-DEFINED, STABLE requirements
              (requirements known from beginning, unlikely to change)
Drawback    : If requirements change mid-way → very costly to revise
              Testing comes LATE → bugs found late
              Customer sees product only at the END
Example use : Government/defense projects (fixed specs)

PYQ TRAP: "Waterfall is flexible" → FALSE (it is RIGID)
          "Waterfall allows easy changes" → FALSE
          "Waterfall is best when requirements are unclear" → FALSE
          (Prototype model is better for unclear requirements)
```

---

## 🔷 TOPIC 4: PROTOTYPE MODEL — Build to Clarify

### Diagram:
```
PROTOTYPE MODEL — Build Quick Model First
════════════════════════════════════════════════

       START
         │
         ▼
  ┌──────────────────┐
  │ Requirements     │
  │ (initial, may be │
  │  incomplete/     │
  │  unclear)        │
  └────────┬─────────┘
           │
           ▼
  ┌──────────────────┐
  │  QUICK PROTOTYPE │◄─────────────┐
  │  (rough working  │              │
  │   model built    │              │
  │   fast)          │              │
  └────────┬─────────┘              │
           │                        │
           ▼                        │
  ┌──────────────────┐              │
  │ Customer REVIEWS │              │
  │ the prototype    │              │
  │ and gives        │              │
  │ FEEDBACK         │              │
  └────────┬─────────┘              │
           │                        │
    ┌──────┴──────┐                 │
    │             │                 │
    ▼             ▼                 │
 Happy?      Not Happy?             │
    │         (changes needed)──────┘
    │         (REFINE prototype)
    ▼
  ┌──────────────────┐
  │  FINAL SYSTEM    │
  │  DEVELOPMENT     │
  │  (build the real │
  │   full product)  │
  └──────────────────┘

  KEY PROPERTY: Builds a QUICK working model (prototype) FIRST
                to clarify and refine requirements through
                customer feedback BEFORE building the final system
```

### Prototype Key Facts:
```
PROTOTYPE MODEL — KEY FACTS
────────────────────────────────────────────────────────────
Type        : Iterative (keep refining the prototype)
Flexibility : HIGH (easy to incorporate changes)
Best for    : Projects where requirements are UNCLEAR or INCOMPLETE
              Customer doesn't fully know what they want
Purpose     : CLARIFY requirements through working model feedback
              SPEED UP development process ← PYQ FACT
              (speeds up because requirements are nailed early)
Drawback    : Customer may get attached to prototype
              Prototype may be poor quality code (rushed)

PYQ FACT: "Software prototype is built to SPEED UP development" = TRUE ✅
          "Prototype is best when requirements are well-defined" → FALSE
          (Waterfall is best for well-defined requirements)
```

---

## 🔷 TOPIC 5: AGILE MODEL — Iterative Sprints

### Diagram:
```
AGILE MODEL — Iterative Development in Short Sprints
════════════════════════════════════════════════════════

  REQUIREMENTS (high-level, can change)
         │
         ▼
  ┌────────────────────────────────────────────────┐
  │                SPRINT 1 (1–4 weeks)            │
  │  Plan → Design → Code → Test → Review          │
  │  ↓ Delivers WORKING SOFTWARE increment         │
  └────────────────────────────────────────────────┘
         │
         ▼  (Feedback from customer after each sprint)
  ┌────────────────────────────────────────────────┐
  │                SPRINT 2 (1–4 weeks)            │
  │  Plan → Design → Code → Test → Review          │
  │  ↓ Delivers next WORKING SOFTWARE increment    │
  └────────────────────────────────────────────────┘
         │
         ▼
  ┌────────────────────────────────────────────────┐
  │                SPRINT 3 (1–4 weeks)            │
  │  Plan → Design → Code → Test → Review          │
  │  ↓ Each sprint ADDS to previous increment      │
  └────────────────────────────────────────────────┘
         │
         ▼
    FINAL PRODUCT
    (built incrementally through all sprints)

  KEY INSIGHT: After every sprint, a working product is available
               Customer sees real working software early and often
               Requirements CAN CHANGE between sprints (flexible!)
```

### Agile Key Facts:
```
AGILE MODEL — KEY FACTS
────────────────────────────────────────────────────────────
Type        : Iterative + Incremental
Flexibility : MOST FLEXIBLE (requirements can change anytime)
Best for    : Projects where requirements CHANGE FREQUENTLY
              Modern web/app development
Structure   : SPRINTS = short development cycles (1–4 weeks each)
              Each sprint = plan, design, code, test, review
              Each sprint delivers working software
Teams       : Small, self-organizing, cross-functional teams
Customer    : INVOLVED throughout (not just at start/end)
Drawbacks   : Hard to predict final cost/time upfront
              Documentation is less emphasized

AGILE FRAMEWORKS: Scrum (most popular), Kanban, XP (Extreme Programming)

PYQ TRAP: "Agile is rigid and sequential" → FALSE
          "In Agile, customer is involved only at the beginning" → FALSE
```

---

## 🔷 TOPIC 6: SPIRAL MODEL — Risk-Driven

### Diagram:
```
SPIRAL MODEL — Risk-Driven, Combines Waterfall + Prototype
════════════════════════════════════════════════════════════

The spiral is divided into 4 QUADRANTS, repeated each loop:

                    PLANNING
                      ↑
         ┌────────────┼────────────┐
         │            │            │
         │    ╔═══════╪═══════╗    │
  RISK   │    ║  3rd  │  2nd  ║    │  ENGINEERING
  ANALYSIS←  ║ Loop  │ Loop  ║   →(Design/Code/Test)
         │    ║       │       ║    │
         │    ║  ─────┼─────  ║    │
         │    ║  1st  │  1st  ║    │
         │    ║ Loop  │ Loop  ║    │
         │    ╚═══════╪═══════╝    │
         │            │            │
         └────────────┼────────────┘
                      ↓
               CUSTOMER EVALUATION

EACH LOOP (spiral rotation) has 4 phases:
  ┌─────────────────────────────────────────────────────────┐
  │ QUADRANT 1 — PLANNING                                   │
  │   Determine objectives, alternatives, constraints       │
  ├─────────────────────────────────────────────────────────┤
  │ QUADRANT 2 — RISK ANALYSIS                              │
  │   Identify and resolve RISKS ← KEY feature of Spiral   │
  │   Build prototype if needed to reduce risk              │
  ├─────────────────────────────────────────────────────────┤
  │ QUADRANT 3 — ENGINEERING                                │
  │   Develop and test the product (like Waterfall phases)  │
  ├─────────────────────────────────────────────────────────┤
  │ QUADRANT 4 — CUSTOMER EVALUATION                        │
  │   Customer reviews; plan next spiral loop               │
  └─────────────────────────────────────────────────────────┘

  As spirals progress: product becomes more complete,
  cost/risk reduces with each loop
```

### Spiral Key Facts:
```
SPIRAL MODEL — KEY FACTS
────────────────────────────────────────────────────────────
Type        : RISK-DRIVEN iterative model
Flexibility : High (iterative loops)
Best for    : LARGE, COMPLEX, HIGH-RISK projects
              Projects where risks must be identified early
Combines    : Waterfall's systematic phases + Prototype's iterative nature
Key feature : RISK ANALYSIS done at every loop ← distinguishes Spiral
Drawback    : Expensive (requires risk expertise)
              Complex to manage
              Not suitable for small/simple projects

PYQ FACT: "Spiral model is risk-driven" = TRUE ✅
          "Spiral combines Waterfall and Prototyping" = TRUE ✅
          "Spiral is best for small projects" → FALSE
```

---

## 🔷 TOPIC 7: All Four SDLC Models — Master Comparison

```
MODEL       TYPE            FLEXIBILITY   BEST FOR                KEY FEATURE
──────────────────────────────────────────────────────────────────────────────
Waterfall   Sequential      RIGID         Well-defined, stable    Sequential phases;
                                          requirements            no going back
Prototype   Iterative       HIGH          Unclear/incomplete      Quick prototype
                                          requirements            built first
Agile       Iterative+      MOST          Frequently changing     Short SPRINTS;
            Incremental     FLEXIBLE      requirements            working software
                                                                  each sprint
Spiral      Risk-driven     HIGH          Large, complex,         RISK ANALYSIS
            Iterative                     high-risk projects      every loop
──────────────────────────────────────────────────────────────────────────────

PYQ MEGA-TRAP:
  "Which of the following are SDLC models?"
  → Waterfall ← valid
  → Agile     ← valid
  → Spiral    ← valid
  → Prototype ← valid
  ANSWER = (D) "More than one of the above" ← ALL FOUR are valid SDLC models!
```

### Visual Timeline Comparison:
```
HOW EACH MODEL HANDLES REQUIREMENTS vs DELIVERY:

WATERFALL:
  Req ──────────────────────────────────────► Delivery
  [All requirements first]                  [Product at end only]

PROTOTYPE:
  Req → [Proto 1] → Feedback → [Proto 2] → Feedback → [Final Product]
  [Requirements refined through prototypes]

AGILE:
  Req → [Sprint1]→ [Sprint2]→ [Sprint3]→ [Sprint4]→ ... → [Full Product]
          ↑Working   ↑Working   ↑Working   ↑Working
          software   software   software   software
  [Working software delivered AFTER EVERY SPRINT]

SPIRAL:
       Loop1    Loop2    Loop3    Loop4
  Req →[Plan+  →[Plan+  →[Plan+  →[Plan+  → Full Product
        Risk+   Risk+   Risk+   Risk+
        Dev+    Dev+    Dev+    Dev+
        Eval]   Eval]   Eval]   Eval]
  [Risk assessed at every loop]
```

---

## 🔷 TOPIC 8: Requirements Types

```
TYPES OF SOFTWARE REQUIREMENTS

TYPE 1 — FUNCTIONAL REQUIREMENTS:
  = What the SYSTEM DOES
  = Features and functions the software must provide
  = Describes BEHAVIOR of the system

  Examples:
    "The system shall allow users to LOGIN with email+password"
    "The system shall send email notifications on order placement"
    "The system shall display student marks after entering roll number"

TYPE 2 — NON-FUNCTIONAL REQUIREMENTS:
  = HOW WELL the system does it
  = Quality attributes / constraints on the system

  Examples:
    Performance   : "System shall respond within 2 seconds"
    Security      : "All data shall be encrypted using AES-256"
    Scalability   : "System shall handle 10,000 simultaneous users"
    Reliability   : "System uptime shall be 99.9%"
    Usability     : "System shall be operable by untrained users"
    Maintainability: "Code shall have 80%+ test coverage"

  CATEGORIES of non-functional requirements:
    → Performance, Security, Reliability, Scalability,
      Maintainability, Portability, Usability

NOT A VALID REQUIREMENT TYPE:
  ❌ "Physical requirements" → NOT a standard type ← PYQ TRAP!
     (Functional and Non-functional are the two main types)
  ❌ "Domain requirements" — sometimes used but NOT a main standard type

PYQ TRAP: "Physical requirements are a type of software requirement"
          → FALSE — the two types are FUNCTIONAL and NON-FUNCTIONAL
```

---

## 🔷 TOPIC 9: Verification vs Validation

```
VERIFICATION vs VALIDATION — The #1 Exam Confusion

VERIFICATION = "Are we building the product RIGHT?"
  → Checks PROCESS (is the development process correct?)
  → Internal quality check (done by developers)
  → Static testing — reviews, walkthroughs, inspections
  → Does not involve running the actual software
  → Example: Code review, design document review
  → Question asked: "Does the software meet the DESIGN SPECIFICATIONS?"

VALIDATION = "Are we building the RIGHT product?"
  → Checks PRODUCT (does it meet user needs?)
  → External quality check (done with customer/user)
  → Dynamic testing — running the actual software
  → Involves actual execution and user testing
  → Example: User acceptance testing (UAT)
  → Question asked: "Does the software meet the USER REQUIREMENTS?"

MEMORY TRICK:
  Verification = V = right pRocess (checking Process)
  Validation   = V = right product (checking Product for user)

  OR even simpler:
  VERification = VERifying our PROCESS is correct
  VALidation   = VALidating the product for the customer
```

### Diagram:
```
VERIFICATION vs VALIDATION — Side by Side

  VERIFICATION                    VALIDATION
  ─────────────────────────────────────────────────────────
  "Building product RIGHT?"       "Building RIGHT product?"
         ↑                                ↑
  Process check                   Product check
  (internal)                      (external / user)
         │                                │
  ┌──────┴──────┐               ┌────────┴────────┐
  │ Does code   │               │ Does software   │
  │ match the   │               │ meet USER       │
  │ DESIGN      │               │ REQUIREMENTS    │
  │ SPEC?       │               │ and NEEDS?      │
  └─────────────┘               └─────────────────┘
  Static activities:             Dynamic activities:
  → Code review                  → User acceptance test
  → Inspection                   → Functional testing
  → Walkthrough                  → System testing
  → Design review                → Beta testing

  Catches: Wrong implementation  Catches: Wrong product built
  (built it wrong)               (built the wrong thing)

EXAM ANSWER PATTERN:
  Q: "Are we building the product right?" → VERIFICATION
  Q: "Are we building the right product?" → VALIDATION
```

---

## 🔷 TOPIC 10: Software Engineering — Additional Key Facts

### Software Complexity & Metrics:
```
COHESION = degree to which elements of a module BELONG TOGETHER
           HIGH cohesion = good design ← aim for this
           (module does ONE specific thing well)

COUPLING  = degree of INTERDEPENDENCE between modules
            LOW coupling = good design ← aim for this
            (modules are independent; change in one doesn't break others)

DESIGN GOAL: HIGH COHESION + LOW COUPLING ← exam fact

SOFTWARE QUALITY ATTRIBUTES (Non-functional):
  Reliability      = works correctly under specified conditions
  Maintainability  = ease of modifying after delivery
  Portability      = can run on different platforms
  Efficiency       = uses resources (CPU, memory) optimally
  Usability        = easy to use for intended users
```

### SDLC Phases Explained:
```
PHASE                  WHAT HAPPENS                  OUTPUT
──────────────────────────────────────────────────────────────
Requirements           Gather what client needs      SRS document
                                                    (Software Req. Spec.)
System Design          Plan architecture, DB,        HLD + LLD documents
                       UI, modules                  (High/Low Level Design)
Implementation         Write actual code             Source code
Testing                Find and fix bugs             Test reports
Deployment             Release to production         Running software
Maintenance            Fix bugs, add features        Updated software
──────────────────────────────────────────────────────────────
SRS = Software Requirements Specification ← important document name
HLD = High Level Design | LLD = Low Level Design
```

---

## 📊 CS MASTER COMPARISON TABLE — Day 80

```
CONCEPT               KEY FACT                              COMMON TRAP
──────────────────────────────────────────────────────────────────────
SE Primary Goal       Meet requirements in BUDGET+SCHEDULE  NOT just "working code"
Waterfall             Sequential, RIGID, stable requirements "Waterfall is flexible" = FALSE
Prototype             Quick model; clarify requirements;     "Prototype = final product" = NO
                      speeds up development
Agile                 SPRINTS; most flexible; working        "Agile = sequential" = FALSE
                      software after every sprint
Spiral                RISK-DRIVEN; combines W+P; large       "Spiral = simple projects" = FALSE
                      complex projects
All 4 SDLC models     ALL are valid → answer = (D)           Don't pick just one!
Functional req.       What the system DOES                   "Physical req." = NOT a type
Non-functional req.   HOW WELL it does it (perf/security)
Verification          "Building product RIGHT?" (process)    Confused with Validation
Validation            "Building RIGHT product?" (product)    Confused with Verification
High Cohesion         GOOD design (module does one thing)    "Low cohesion = good" = FALSE
Low Coupling          GOOD design (modules independent)      "High coupling = good" = FALSE
──────────────────────────────────────────────────────────────────────
```

---
---

# PART 2: GS RAPID REVISION
## ⚗️ Science Shortcuts — Physics + Biology PYQ Coverage

---

## 🔷 PHYSICS — PYQ-Tested Facts

### Bernoulli's Principle:
```
BERNOULLI'S PRINCIPLE:
  "In a flowing fluid, where velocity is HIGH,
   pressure is LOW — and vice versa"

  High velocity → Low pressure
  Low velocity  → High pressure

APPLICATION — Spray bottle / Atomizer / Perfume bottle:
  → Air blown fast over a tube opening
  → Creates LOW PRESSURE above the tube
  → Atmospheric pressure (higher) PUSHES liquid UP the tube
  → Liquid is sprayed as a mist

DIAGRAM:
         AIR BLOWN →→→→→→→→→→→→→→
                    ↓ fast air
                  [LOW PRESSURE here]
                       │ liquid
                 ──────┤    rises
                  tube │    up
                  with ┤
                 liquid└──────── bottle

OTHER APPLICATIONS:
  → Aeroplane lift (wings — faster air on top = lower pressure)
  → Venturi meter
  → Bunsen burner

PYQ TRAP: "Bernoulli applies only to liquids" → FALSE (applies to all fluids)
```

### Stefan's Law (Blackbody Radiation):
```
STEFAN'S LAW:
  E ∝ T⁴   (Energy radiated is proportional to Temperature to the 4th power)

  Full formula: E = σT⁴
  where σ = Stefan-Boltzmann constant = 5.67 × 10⁻⁸ W/m²K⁴

PYQ APPLICATION:
  If temperature is reduced to T/3:
  New E = σ(T/3)⁴ = σ × T⁴/81 = E/81

  So: "Temperature reduced to T/3 → energy radiated becomes E/81" ← PYQ tested!

PYQ TRAP: "Stefan's law: E ∝ T²" → FALSE (it's T⁴ not T²)
```

### Electrical Power:
```
ELECTRICAL POWER FORMULAS:
  P = VI        (Power = Voltage × Current)
  P = I²R       (Power = Current² × Resistance) ← PYQ tested!
  P = V²/R      (Power = Voltage² / Resistance)

  Where: P = Power (Watts), V = Voltage (Volts),
         I = Current (Amperes), R = Resistance (Ohms)

PYQ FACT: P = I²R ← this specific form is tested most often
          "Electrical power equals current squared times resistance" = TRUE

RESISTANCE IN PARALLEL:
  1/R_total = 1/R₁ + 1/R₂ + 1/R₃ ...
  Two equal resistors R in parallel = R/2
```

### Speed of Electron in Hydrogen Orbit:
```
SPEED OF ELECTRON IN HYDROGEN ATOM:
  In the FIRST (n=1) orbit of hydrogen:
  v = c/137   where c = speed of light

  137 = Fine Structure Constant (dimensionless) ← memorize this number

PYQ TRAP: "Speed of electron = c (speed of light)" → FALSE
          "Speed = c/100" → FALSE (it's c/137)
```

### Convex Lens in Water:
```
CONVEX LENS IN WATER:
  → Remains CONVEX (does NOT become concave)
  → FOCAL LENGTH INCREASES (lens becomes less powerful/converging)
  → Because refractive index difference between lens and water
    is less than between lens and air

PYQ FACT: "Convex lens submerged in water: remains convex, focal length increases"
          = TRUE ✅
PYQ TRAP: "Convex lens becomes concave in water" → FALSE
```

### Light and Medium:
```
WHEN LIGHT CHANGES MEDIUM (e.g., air to water):
  → FREQUENCY remains UNCHANGED ← PYQ tested!
  → Speed CHANGES (decreases when entering denser medium)
  → Wavelength CHANGES (decreases with speed)
  → Color (and frequency) stay the same

REASON: Frequency = intrinsic property of light source
        Speed and wavelength adjust to the new medium

PYQ TRAP: "Wavelength stays same when light changes medium" → FALSE
          "Frequency changes when light enters water" → FALSE
          (FREQUENCY stays same!)
```

### Isotropic Light Source:
```
ISOTROPIC LIGHT SOURCE = emits light EQUALLY in ALL directions

  Luminous intensity unit: CANDELA (cd)
  Luminous flux unit: LUMEN (lm)

  For isotropic source: Flux (lumens) = 4π × Intensity (candela)
  (4π = total solid angle of a sphere)

  1 candela of isotropic source = 4π ≈ 12.57 lumens
```

---

## 🔷 BIOLOGY — Additional PYQ-Tested Facts

### Quick Reference Card:
```
BIOLOGY FACT                                PYQ SOURCE
──────────────────────────────────────────────────────────────
Photoperiodism = Garner & Allard (1920)    TRE 2.0 tested
Ginger = underground stem (rhizome)        TRE tested
  → has nodes and internodes (proof of stem)
Yeast = asexual reproduction by BUDDING    TRE tested
Anther contains POLLEN GRAINS              TRE tested
Diaphragm FLATTENS during inhalation       TRE tested
Lymphocytes = most important for immunity  TRE tested
Silent Valley = KERALA (rare flora/fauna)  TRE tested
Antacid = neutralizes stomach acid (HCl)   TRE tested
Vas deferens = MALE reproductive system    TRE tested
Stomata = gas exchange + transpiration     NCERT Class 10
Chlorophyll reflects GREEN (absorbs R+B)   NCERT Class 10
Ethylene = only GASEOUS plant hormone      NCERT Class 11
ABA (Abscisic Acid) = closes stomata       NCERT Class 11
──────────────────────────────────────────────────────────────
```

---

## 🔷 SCIENCE SHORTCUT MASTER SHEET

```
TOPIC                      SHORTCUT / KEY FORMULA           PYQ TRAP
──────────────────────────────────────────────────────────────────────
Bernoulli                  High velocity → Low pressure      Spray bottle works
Stefan's Law               E ∝ T⁴; T→T/3 means E→E/81       NOT T², NOT T³
Electrical Power           P = I²R (most tested form)        Not P = IR²
Speed of e⁻ in H orbit     c/137                             NOT c/100 or c
Convex lens in water        Remains convex; f INCREASES       NOT becomes concave
Light in new medium         FREQUENCY unchanged               NOT wavelength
Photosynthesis              6CO₂+6H₂O → C₆H₁₂O₆+6O₂         In CHLOROPLASTS
Resistance in parallel      1/R_total = 1/R₁ + 1/R₂          Less than smallest R
Ginger                      Underground STEM (not root)       Has nodes+internodes
Yeast                       BUDDING                           NOT binary fission
Diaphragm (inhale)          CONTRACTS and FLATTENS            NOT relaxes
Lymphocytes                 MOST important for immunity       NOT platelets
──────────────────────────────────────────────────────────────────────
```

---
---

# PART 3: PRACTICE QUESTIONS
## 📝 MIXED MCQs — Day 80 Topics

---

### COMPUTER SCIENCE — 25 MCQs

---

**Q1.** The PRIMARY GOAL of Software Engineering is to:
(A) Write code that is error-free at all times
(B) Develop software meeting user requirements within BUDGET AND SCHEDULE
(C) Use the most modern programming languages and tools
(D) More than one of the above
(E) None of the above

---

**Q2.** In the Waterfall model, each phase:
(A) Runs simultaneously with other phases
(B) Can be revisited at any time without restriction
(C) Must be FULLY COMPLETED before the next phase begins
(D) More than one of the above
(E) None of the above

---

**Q3.** The Waterfall model is BEST suited for projects with:
(A) Frequently changing requirements
(B) Short development timelines (< 1 week)
(C) Well-defined and STABLE requirements that are unlikely to change
(D) More than one of the above
(E) None of the above

---

**Q4.** Which SDLC model builds a QUICK WORKING MODEL first to clarify requirements through customer feedback?
(A) Waterfall model
(B) Agile model
(C) Prototype model
(D) More than one of the above
(E) None of the above

---

**Q5.** A software prototype is primarily built to:
(A) Replace the final system directly
(B) Speed up the development process and clarify requirements
(C) Perform security testing of the final software
(D) More than one of the above
(E) None of the above

---

**Q6.** In the Agile model, a SPRINT is:
(A) A long-term development phase lasting 6–12 months
(B) A short development iteration (1–4 weeks) delivering working software
(C) A risk analysis phase at the beginning of the project
(D) More than one of the above
(E) None of the above

---

**Q7.** Which of the following is TRUE about the Agile model?
(A) Customer is involved only at the beginning and end
(B) Requirements cannot change once development starts
(C) Working software is delivered after every sprint
(D) More than one of the above
(E) None of the above

---

**Q8.** The Spiral model is PRIMARILY characterized by:
(A) Sequential one-time phases like Waterfall
(B) Short sprints like Agile
(C) RISK ANALYSIS at every loop/iteration
(D) More than one of the above
(E) None of the above

---

**Q9.** Which SDLC model COMBINES features of both Waterfall and Prototype models?
(A) Agile
(B) V-Model
(C) Spiral
(D) More than one of the above
(E) None of the above

---

**Q10.** The Spiral model is BEST for:
(A) Small, simple projects with clear requirements
(B) Short-term projects with low budget
(C) LARGE, COMPLEX, HIGH-RISK projects
(D) More than one of the above
(E) None of the above

---

**Q11.** Which of the following are valid SDLC models?
```
1. Waterfall
2. Agile
3. Spiral
4. Prototype
```
(A) Only 1 and 2
(B) Only 1, 2, and 3
(C) All four are valid SDLC models
(D) More than one of the above
(E) None of the above

---

**Q12.** FUNCTIONAL requirements describe:
(A) How WELL the system performs (performance, security, scalability)
(B) What the SYSTEM DOES (features, functions, behavior)
(C) Physical hardware specifications of the system
(D) More than one of the above
(E) None of the above

---

**Q13.** NON-FUNCTIONAL requirements describe:
(A) What features the system provides (login, search, payment)
(B) How WELL the system does it (performance, security, reliability)
(C) The physical location where servers will be hosted
(D) More than one of the above
(E) None of the above

---

**Q14.** Which of the following is NOT a standard type of software requirement?
(A) Functional requirements
(B) Non-functional requirements
(C) Physical requirements
(D) More than one of the above
(E) None of the above

---

**Q15.** "Are we building the product RIGHT?" refers to:
(A) Validation
(B) Testing
(C) Verification
(D) More than one of the above
(E) None of the above

---

**Q16.** "Are we building the RIGHT product?" refers to:
(A) Verification
(B) Testing
(C) Validation
(D) More than one of the above
(E) None of the above

---

**Q17.** Verification involves:
(A) Running the actual software and testing it with users
(B) Checking the process — code reviews, design walkthroughs, inspections
(C) Deploying the software to production
(D) More than one of the above
(E) None of the above

---

**Q18.** Validation involves:
(A) Reviewing design documents without executing the software
(B) Code inspection and walkthroughs
(C) Running the actual software and testing with USERS (acceptance testing)
(D) More than one of the above
(E) None of the above

---

**Q19.** High COHESION in software design means:
(A) Modules are highly interdependent and closely linked
(B) A module performs ONE specific, well-defined function
(C) The software has very few modules
(D) More than one of the above
(E) None of the above

---

**Q20.** The DESIGN GOAL in software engineering for module interaction is:
(A) High cohesion + High coupling
(B) Low cohesion + Low coupling
(C) HIGH cohesion + LOW coupling
(D) More than one of the above
(E) None of the above

---

**Q21.** The SRS document in SDLC stands for:
(A) Software Runtime Specification
(B) Software Requirements Specification
(C) System Review Standard
(D) More than one of the above
(E) None of the above

---

**Q22.** Which SDLC model is MOST FLEXIBLE and best handles frequently changing requirements?
(A) Waterfall
(B) Spiral
(C) Agile
(D) More than one of the above
(E) None of the above

---

**Q23.** In which SDLC model does the customer see working software ONLY at the very END?
(A) Agile
(B) Prototype
(C) Waterfall
(D) More than one of the above
(E) None of the above

---

**Q24.** "System shall respond within 2 seconds to any user query" is an example of:
(A) Functional requirement
(B) Physical requirement
(C) Non-functional requirement (performance)
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following is a correct match?
(A) Verification = checking if product meets USER NEEDS (dynamic testing)
(B) Validation = checking if product is built per DESIGN SPEC (static testing)
(C) Verification = process check; Validation = product check for user needs
(D) More than one of the above
(E) None of the above

---
---

### GENERAL STUDIES — 25 MCQs
### Science Shortcuts — Physics + Biology

---

**Q26.** Bernoulli's principle states that in a flowing fluid:
(A) High velocity regions have HIGH pressure
(B) High velocity regions have LOW pressure
(C) Pressure is always equal regardless of velocity
(D) More than one of the above
(E) None of the above

---

**Q27.** Bernoulli's principle explains the working of:
(A) Thermometer
(B) Barometer
(C) Spray bottle (atomizer/perfume bottle)
(D) More than one of the above
(E) None of the above

---

**Q28.** According to Stefan's Law of blackbody radiation, energy radiated (E) is proportional to:
(A) T (temperature)
(B) T² (temperature squared)
(C) T⁴ (temperature to the 4th power)
(D) More than one of the above
(E) None of the above

---

**Q29.** If the temperature of a blackbody is reduced to T/3, the energy radiated becomes:
(A) E/3
(B) E/9
(C) E/81
(D) More than one of the above
(E) None of the above

---

**Q30.** The formula P = I²R represents:
(A) Ohm's Law
(B) Electrical POWER dissipated in a resistor
(C) Kinetic energy of a moving charge
(D) More than one of the above
(E) None of the above

---

**Q31.** The speed of an electron in the first orbit of a hydrogen atom is approximately:
(A) c (equal to speed of light)
(B) c/137
(C) c/10
(D) More than one of the above
(E) None of the above

---

**Q32.** A convex lens submerged in water:
(A) Becomes a concave lens due to higher refractive index of water
(B) Remains convex but its focal length INCREASES
(C) Remains unchanged (same focal length as in air)
(D) More than one of the above
(E) None of the above

---

**Q33.** When light travels from air into water (denser medium), which property remains UNCHANGED?
(A) Speed
(B) Wavelength
(C) Frequency
(D) More than one of the above
(E) None of the above

---

**Q34.** For an isotropic light source of 1 candela, the luminous flux emitted is approximately:
(A) 1 lumen
(B) 4π lumens (≈ 12.57 lumens)
(C) 2π lumens (≈ 6.28 lumens)
(D) More than one of the above
(E) None of the above

---

**Q35.** Two resistors of 4Ω each are connected in PARALLEL. What is the total resistance?
(A) 8Ω
(B) 4Ω
(C) 2Ω
(D) More than one of the above
(E) None of the above

---

**Q36.** If a 10Ω resistor carries a current of 3A, the power dissipated is:
(A) 30 W
(B) 90 W
(C) 900 W
(D) More than one of the above
(E) None of the above

---

**Q37.** Photoperiodism in plants is a response to:
(A) Duration of light (day/night length)
(B) Prolonged cold temperature
(C) Water availability
(D) More than one of the above
(E) None of the above

---

**Q38.** Ginger is botanically a:
(A) Root (taproot modified for storage)
(B) Underground stem (rhizome)
(C) Modified leaf for storage
(D) More than one of the above
(E) None of the above

---

**Q39.** What PROVES that ginger is a stem and not a root?
(A) It grows underground
(B) It contains stored food (starch)
(C) It has NODES and INTERNODES
(D) More than one of the above
(E) None of the above

---

**Q40.** Yeast reproduces asexually by:
(A) Binary fission (dividing into two equal halves)
(B) Spore formation
(C) Budding
(D) More than one of the above
(E) None of the above

---

**Q41.** The part of a flower's stamen that CONTAINS POLLEN GRAINS is:
(A) Filament
(B) Style
(C) Anther
(D) More than one of the above
(E) None of the above

---

**Q42.** During INHALATION (normal breathing), the diaphragm:
(A) Relaxes and moves upward (becomes dome-shaped)
(B) Contracts and FLATTENS
(C) Stays in the same position; only ribs move
(D) More than one of the above
(E) None of the above

---

**Q43.** Which cells are MOST IMPORTANT for providing immunity?
(A) Red Blood Cells (RBCs)
(B) Platelets (thrombocytes)
(C) Lymphocytes
(D) More than one of the above
(E) None of the above

---

**Q44.** Silent Valley National Park (famous for rare flora and fauna) is located in:
(A) Karnataka
(B) Tamil Nadu
(C) Kerala
(D) More than one of the above
(E) None of the above

---

**Q45.** Antacid medicines are used to treat:
(A) Fever (high body temperature)
(B) Allergic reactions
(C) INDIGESTION (by neutralizing excess stomach acid)
(D) More than one of the above
(E) None of the above

---

**Q46.** Vas deferens is a part of the:
(A) Female reproductive system
(B) Digestive system
(C) Male reproductive system
(D) More than one of the above
(E) None of the above

---

**Q47.** In photosynthesis, chlorophyll:
(A) Absorbs green light and reflects red and blue light
(B) Absorbs red and blue light; REFLECTS GREEN light (making leaves appear green)
(C) Absorbs all wavelengths equally
(D) More than one of the above
(E) None of the above

---

**Q48.** The ONLY gaseous plant hormone that promotes fruit ripening is:
(A) Auxin
(B) Abscisic Acid (ABA)
(C) Ethylene
(D) More than one of the above
(E) None of the above

---

**Q49.** Stomata in plant leaves are primarily responsible for:
(A) Absorbing water from soil
(B) Producing chlorophyll for photosynthesis
(C) GAS EXCHANGE (CO₂ in, O₂ out) and TRANSPIRATION (water vapor loss)
(D) More than one of the above
(E) None of the above

---

**Q50.** Which of the following CORRECTLY matches the science fact and its key detail?
(A) Bernoulli's principle — high velocity = LOW pressure
(B) Stefan's Law — E ∝ T⁴ (energy proportional to temperature to the 4th)
(C) Speed of electron in H orbit — c/137
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY

## ⚠️ MANDATORY: Attempt all 50 questions BEFORE checking!

---

### CS Answers (Q1–Q25):

| Q  | Answer | Reason (one-line)                                                           |
|----|--------|-----------------------------------------------------------------------------|
| 1  | (B)    | SE primary goal = meet user requirements within BUDGET AND SCHEDULE         |
| 2  | (C)    | Waterfall: each phase FULLY COMPLETED before the next begins                |
| 3  | (C)    | Waterfall best for WELL-DEFINED, STABLE requirements                        |
| 4  | (C)    | Prototype model = builds quick working model to clarify requirements        |
| 5  | (B)    | Prototype purpose = speed up development + clarify requirements             |
| 6  | (B)    | Sprint = short iteration (1–4 weeks) delivering working software            |
| 7  | (C)    | Agile: working software delivered after EVERY sprint                        |
| 8  | (C)    | Spiral = characterized by RISK ANALYSIS at every loop                      |
| 9  | (C)    | Spiral combines Waterfall's phases + Prototype's iterative nature           |
| 10 | (C)    | Spiral best for LARGE, COMPLEX, HIGH-RISK projects                         |
| 11 | (C)    | ALL FOUR are valid SDLC models → answer is (C) (all four) = also (D)       |
| 12 | (B)    | Functional = what the SYSTEM DOES (features, behavior)                     |
| 13 | (B)    | Non-functional = HOW WELL it does it (performance, security, reliability)  |
| 14 | (C)    | "Physical requirements" = NOT a standard type ← PYQ trap                  |
| 15 | (C)    | "Building product RIGHT?" = VERIFICATION (process check)                   |
| 16 | (C)    | "Building RIGHT product?" = VALIDATION (product check for user needs)      |
| 17 | (B)    | Verification = code reviews, inspections, walkthroughs (static, no run)    |
| 18 | (C)    | Validation = running software + user acceptance testing (dynamic)          |
| 19 | (B)    | High cohesion = module does ONE specific well-defined function              |
| 20 | (C)    | Good design goal = HIGH cohesion + LOW coupling                            |
| 21 | (B)    | SRS = Software Requirements Specification                                  |
| 22 | (C)    | Agile = most flexible; handles frequently changing requirements best       |
| 23 | (C)    | Waterfall = customer sees product only at the VERY END                     |
| 24 | (C)    | "Respond within 2 seconds" = performance = NON-FUNCTIONAL requirement      |
| 25 | (C)    | Verification=process check; Validation=product check for user needs        |

---

### GS Answers (Q26–Q50):

| Q  | Answer | Reason (one-line)                                                      |
|----|--------|------------------------------------------------------------------------|
| 26 | (B)    | Bernoulli: high velocity regions = LOW pressure                        |
| 27 | (C)    | Bernoulli explains spray bottle / atomizer / perfume bottle            |
| 28 | (C)    | Stefan's Law: E ∝ T⁴ (4th power, NOT T² or T³)                        |
| 29 | (C)    | T→T/3: E→(T/3)⁴=T⁴/81 → E becomes E/81                               |
| 30 | (B)    | P = I²R = electrical POWER dissipated in a resistor                    |
| 31 | (B)    | Speed of electron in H atom first orbit = c/137                        |
| 32 | (B)    | Convex lens in water: remains convex; focal length INCREASES           |
| 33 | (C)    | FREQUENCY remains unchanged when light changes medium                  |
| 34 | (B)    | Isotropic 1 candela = 4π ≈ 12.57 lumens total flux                    |
| 35 | (C)    | Two 4Ω in parallel: 1/R=1/4+1/4=2/4; R=2Ω                            |
| 36 | (B)    | P = I²R = 3² × 10 = 9 × 10 = 90 W                                     |
| 37 | (A)    | Photoperiodism = response to DURATION OF LIGHT (day/night length)      |
| 38 | (B)    | Ginger = underground stem (rhizome) — NOT a root                       |
| 39 | (C)    | Nodes and internodes = proof of STEM (roots don't have these)          |
| 40 | (C)    | Yeast = BUDDING (bacteria = binary fission)                            |
| 41 | (C)    | ANTHER contains pollen grains (filament = stalk; style = female part)  |
| 42 | (B)    | Inhalation → diaphragm CONTRACTS and FLATTENS                         |
| 43 | (C)    | LYMPHOCYTES = most important for immunity                              |
| 44 | (C)    | Silent Valley = KERALA                                                 |
| 45 | (C)    | Antacid = neutralizes excess HCl = treats INDIGESTION                 |
| 46 | (C)    | Vas deferens = MALE reproductive system                                |
| 47 | (B)    | Chlorophyll absorbs red+blue; REFLECTS GREEN → leaves appear green     |
| 48 | (C)    | ETHYLENE = only gaseous hormone; promotes fruit ripening + leaf fall   |
| 49 | (C)    | Stomata = gas exchange (CO₂/O₂) AND transpiration (water vapor)        |
| 50 | (D)    | ALL THREE facts — Bernoulli, Stefan, electron speed — are correct      |

---
---

# 🔁 FINAL REVISION NOTES
## 📌 "Last 1-Hour Before Exam" — Ultra-Crisp Format

---

### ⚡ CS — 30 MUST-KNOW FACTS (Software Engineering)

```
SOFTWARE ENGINEERING BASICS:
1.  SE primary goal = meet requirements within BUDGET AND SCHEDULE ← PYQ
2.  Software = Programs + Documentation + Data (NOT just executable)
3.  SRS = Software Requirements Specification document

SDLC MODELS (memorize all 4 — any of them can appear as "valid SDLC model"):
4.  WATERFALL  = sequential, RIGID, stable requirements
                 Customer sees product only at END
                 Each phase fully done before next begins
5.  PROTOTYPE  = quick model first; clarifies requirements; SPEEDS UP dev ← PYQ
                 Best when requirements are UNCLEAR
6.  AGILE      = SPRINTS (1–4 weeks); working software after EVERY sprint
                 MOST FLEXIBLE; requirements can change; customer involved always
7.  SPIRAL     = RISK-DRIVEN; combines Waterfall+Prototype; LARGE complex projects
                 Risk analysis at every loop ← distinguishes Spiral
8.  ALL FOUR are valid SDLC models → answer = (D) when asked "which are valid?" ← PYQ!

REQUIREMENTS:
9.  Functional     = WHAT system DOES (features, behavior, functions)
10. Non-functional = HOW WELL it does it (performance, security, reliability)
11. "Physical requirements" = NOT a standard type ← PYQ trap!
12. Performance "respond in 2 sec" = NON-FUNCTIONAL requirement

VERIFICATION vs VALIDATION:
13. VERIFICATION = "Building product RIGHT?" = PROCESS check = static (no execution)
    Activities: code review, inspection, walkthrough, design review
14. VALIDATION   = "Building RIGHT product?" = PRODUCT check = dynamic (execution)
    Activities: user acceptance test, system test, beta test
15. TRAP: Students often swap these — use memory trick:
    VERification = VERify our Process is right
    VALidation   = VALidate product for the customer

DESIGN PRINCIPLES:
16. HIGH COHESION = GOOD (module does one specific thing)
17. LOW COUPLING  = GOOD (modules are independent of each other)
18. GOAL: HIGH cohesion + LOW coupling

WATERFALL PHASES (in order):
19. Requirements → Design → Implementation → Testing → Deployment → Maintenance

EXAM TRAPS:
20. "Waterfall is flexible" → WRONG (RIGID)
21. "Prototype = final product" → WRONG (it's a quick working model)
22. "Agile is sequential" → WRONG (ITERATIVE)
23. "Spiral = small simple projects" → WRONG (LARGE complex high-risk)
24. "Physical requirements" = NOT a type → WRONG answer if chosen
25. "Verification = user testing" → WRONG (Validation = user testing)
```

---

### ⚡ GS — 25 MUST-KNOW SCIENCE FACTS

```
PHYSICS:
1.  Bernoulli: High velocity → LOW pressure (spray bottle works on this)
2.  Stefan's Law: E ∝ T⁴; T→T/3 means E→E/81
3.  P = I²R (electrical power, most tested form)
4.  Speed of e⁻ in H atom first orbit = c/137 (NOT c, NOT c/100)
5.  Convex lens in water: stays convex; FOCAL LENGTH INCREASES
6.  Light changes medium: FREQUENCY stays same; speed+wavelength change
7.  Isotropic source: 1 candela = 4π lumens (≈12.57 lumens)
8.  Parallel resistance: always LESS than smallest individual resistor

BIOLOGY:
9.  Photoperiodism = discovered by GARNER and ALLARD (1920)
    = response to LIGHT DURATION for flowering
10. Ginger = UNDERGROUND STEM (rhizome); proof = nodes+internodes
11. Potato = stem TUBER (also underground stem; has nodes=eyes)
12. Yeast = BUDDING | Bacteria = BINARY FISSION
13. Anther = contains POLLEN GRAINS
14. Diaphragm FLATTENS during INHALATION (contracts)
    Diaphragm DOMES UP during EXHALATION (relaxes)
15. Lymphocytes = MOST IMPORTANT for immunity
16. Silent Valley = KERALA (rare flora and fauna)
17. Antacid = neutralizes excess HCl (stomach acid; treats indigestion)
18. Vas deferens = MALE reproductive system
19. Chlorophyll absorbs RED+BLUE; REFLECTS GREEN → leaves look green
20. Ethylene = ONLY GASEOUS hormone; fruit ripening + leaf fall
21. ABA (Abscisic Acid) = CLOSES stomata during drought (stress hormone)
22. Stomata = gas exchange (CO₂/O₂) + transpiration (water loss)
23. Photosynthesis in CHLOROPLASTS: 6CO₂+6H₂O → C₆H₁₂O₆+6O₂
24. Vernalization = response to COLD (different from photoperiodism)
25. Auxin = phototropism (bending toward light; unequal distribution)
```

---

### ⚡ LAST-MINUTE COMPARISON TABLES

```
SDLC MODEL  TYPE           FLEXIBILITY  BEST FOR            KEY IDENTIFIER
────────────────────────────────────────────────────────────────────────────
Waterfall   Sequential     RIGID        Stable requirements  One-way; no going back
Prototype   Iterative      HIGH         Unclear requirements Quick model first
Agile       Iter+Increm    MOST FLEX    Changing requirements SPRINTS
Spiral      Risk-driven    HIGH         Large/complex/risky  RISK ANALYSIS every loop
────────────────────────────────────────────────────────────────────────────

REQUIREMENT  WHAT IT MEANS                    EXAMPLE
────────────────────────────────────────────────────────────────────────────
Functional   What system DOES                 "User can log in with email"
Non-funct.   HOW WELL it does it              "Response time < 2 seconds"
Physical     NOT a standard type ← TRAP!
────────────────────────────────────────────────────────────────────────────

CONCEPT       QUESTION ASKED             ACTIVITY TYPE
────────────────────────────────────────────────────────────────────────────
Verification  "Building product RIGHT?"  Code review, inspection (static)
Validation    "Building RIGHT product?"  User testing, UAT (dynamic)
────────────────────────────────────────────────────────────────────────────

SCIENCE       FACT                           TRAP
────────────────────────────────────────────────────────────────────────────
Bernoulli     High velocity → LOW pressure   "High velocity = HIGH pressure"
Stefan        E ∝ T⁴; T/3 → E/81            "E ∝ T²"
Electron H    c/137                          "c/100" or "equal to c"
Lens in water Stays convex; f increases      "Becomes concave"
Light medium  FREQUENCY unchanged            "Wavelength unchanged"
Ginger        Underground STEM               "It is a root"
Yeast         BUDDING                        "Binary fission"
Diaphragm     FLATTENS on inhalation         "Relaxes on inhalation"
────────────────────────────────────────────────────────────────────────────
```

---

## 🎯 DAY 80 COMPLETE — WHAT YOU'VE MASTERED TODAY

```
CS:   Software Engineering — SDLC models (Waterfall/Prototype/Agile/Spiral)
      with full diagrams | Functional vs Non-functional requirements |
      Verification vs Validation | Cohesion vs Coupling |
      All 4 SDLC models = valid → answer is (D)

GS:   Science Shortcuts — Bernoulli's Principle, Stefan's Law (T⁴),
      P=I²R, electron speed c/137, convex lens in water,
      frequency unchanged in medium + All biology PYQ facts reviewed

NEXT: Day 81 — Software Testing Types (Unit/Integration/System/Acceptance)
      + Black-box vs White-box testing + Java OOP Inheritance
      GS: Current Affairs Update
```

---

*Day 80 of 170 | Phase 2: Depth | Week 12: Computer Architecture + Software Engineering*
*BPSC TRE 4.0 Preparation | Target: TOP 50 RANK | Score: 130+/150*
