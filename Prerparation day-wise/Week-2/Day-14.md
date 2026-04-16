# 📅 BPSC TRE 4.0 — DAY 14: COMPLETE REVISION + PYQ PRACTICE
### Week 2 Master Revision — Day 8 to Day 13 (CS + GS)
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): CS Revision — all 6 topics, crisp format
> - Afternoon (1 hr): GS Revision — all 5 history topics, timeline-based
> - Evening (1.5 hrs): Solve all 50 Mixed PYQ MCQs
> - Night (30 min): Read the "Last 1-Hour Before Exam" revision sheet

---

# PART 1: CS RAPID REVISION
## 📘 Day 8–13 Complete — All Topics, One Place

---

## 🔷 TOPIC 1: C++ Variables, Data Types & sizeof()
*(Day 8)*

### Variable Naming Rules — Master Checklist:
```
✅ Can start with: letter (a-z, A-Z) or underscore (_)
❌ Cannot start with: digit (0-9)
✅ Can contain: letters, digits, underscore
❌ Cannot contain: spaces, special chars (-, @, #, ...)
✅ Case-sensitive: score ≠ Score ≠ SCORE
❌ Cannot use: reserved keywords (int, float, class, ...)
✅ _123 → VALID    ❌ 123_ → INVALID
✅ myVar → VALID   ❌ my-var → INVALID
```

### Data Types Size Cheat Sheet:
```
TYPE        SIZE    NOTES
─────────────────────────────────────────────
char        1 byte  stores ASCII value
bool        1 byte  NOT 1 bit! ← PYQ TRAP
short       2 bytes
int         4 bytes
float       4 bytes 6-7 digits precision
double      8 bytes 15-16 digits precision
long long   8 bytes very large integers
void        0 bytes cannot declare void variable!
any pointer 4 bytes (32-bit) / 8 bytes (64-bit)
```

### sizeof() — The #1 PYQ Trap:
```
sizeof() = compile-time OPERATOR (NOT a function!)
sizeof(x++) → returns 4 (int size), x is NOT incremented
sizeof(int arr[5]) = 20 bytes (5×4)
sizeof(arr)/sizeof(int) = 5 (number of elements)
Inside function: sizeof(arr param) = pointer size (4/8) ← TRAP!
```

### PYQ Traps Summary:
```
TRAP 1: bool = 1 BYTE, not 1 bit
TRAP 2: void x = 5; → COMPILE ERROR (but void* ptr → VALID)
TRAP 3: sizeof(x++) does NOT change x
TRAP 4: sizeof(arr) inside function = pointer size, NOT array size
TRAP 5: User-defined headers: "myfile.h" | Standard: <iostream>
TRAP 6: Ctrl + F9 = Compile AND Run (Turbo C++)
```

---

## 🔷 TOPIC 2: C++ Pointers
*(Day 9)*

### Core Facts — One-Liners:
```
Pointer    = variable storing the MEMORY ADDRESS of another variable
&x         = address-of x (gives the address)
*p         = value at address stored in p (dereference)
int* p, q  = p is pointer, q is plain int ← TRAP!
int *p, *q = both are pointers ← CORRECT way for two pointers
```

### NULL vs nullptr:
```
NULL     = integer constant 0 (C-style, old)
nullptr  = type-safe null pointer (C++11, modern)
delete NULL  → SAFE, no crash, no error ← #1 PYQ TRAP
delete ptr; p=nullptr; → correct cleanup pattern
```

### new vs malloc:
```
FEATURE        new              malloc()
─────────────────────────────────────────────
Constructor?   YES (calls it)   NO (raw memory only)
Returns        typed pointer    void* (needs cast)
On failure     throws bad_alloc returns NULL
Header         none (keyword)   <cstdlib>
Pair with      delete           free()
─────────────────────────────────────────────
NEVER mix: new + free() or malloc + delete → UNDEFINED BEHAVIOR
```

### Pointer Types:
```
Dangling pointer = points to FREED or out-of-scope memory
Wild pointer     = UNINITIALIZED pointer (declared, never assigned)
void* pointer    = generic pointer, cannot dereference without cast
double pointer** = pointer to pointer

Fix dangling pointer: delete p; p = nullptr;  ← always do this!
```

### Pointer Arithmetic:
```
p + 1 → moves by sizeof(type) bytes (NOT 1 byte!)
p1 + p2 → INVALID (cannot add two pointers)
p1 - p2 → valid (number of elements between)
sizeof(any pointer) = same (4 or 8 bytes, not type-dependent)
```

---

## 🔷 TOPIC 3: C++ Arrays
*(Day 10)*

### Array Fundamentals:
```
Correct syntax: int arr[10];  ← NOT int arr(10) or int[10] arr
Index range:    0 to n-1      ← arr[n] is OUT OF BOUNDS
Last index:     n-1           ← ALWAYS n-1, never n
arr == &arr[0] = base address  ← array name IS base address
arr[i] == *(arr+i)             ← completely equivalent
arr cannot be incremented (arr++) ← constant pointer!
```

### sizeof() with Arrays:
```
int arr[5]:
  sizeof(arr)              = 20 bytes (5×4)
  sizeof(arr)/sizeof(int)  = 5 (element count)
  sizeof(arr)/sizeof(arr[0])= 5 (same, more robust)

Inside function:
  sizeof(arr param)        = 4 or 8 (pointer size!) ← TRAP
  Array DECAYS to pointer when passed to function
  Modifications to array inside function AFFECT original
```

### 2D Arrays:
```
int mat[3][4]:
  First bracket = ROWS, Second = COLUMNS
  Total elements = 3 × 4 = 12
  Storage: ROW-MAJOR ORDER (row by row in memory)
  Address of mat[i][j] = base + (i×cols + j) × sizeof(type)
```

### String as Char Array:
```
char str[] = "BPSC":  5 bytes (4 chars + '\0' null terminator)
'\0' ASCII = 0        marks end of C-style string
char s1[] + char s2[] → COMPILE ERROR (pointer + pointer = invalid!)
Use strcat(s1, s2) for concatenation
strcmp(s1, s2): 0=equal, <0 if s1<s2, >0 if s1>s2
```

### is_array() and rank():
```
Header: <type_traits>
is_array<int[5]>::value  = 1 (true)
is_array<int*>::value    = 0 (pointer ≠ array)
rank<int[3][4]>::value   = 2 (2D array)
rank<int>::value         = 0 (not an array)
```

---

## 🔷 TOPIC 4: File Handling
*(Day 11)*

### Stream Classes:
```
ifstream  = INPUT from file (READ)     default: ios::in
ofstream  = OUTPUT to file (WRITE)     default: ios::out | ios::trunc
fstream   = BOTH read and write        must specify mode
Header: #include <fstream>
```

### File Modes — THE Exam Topic:
```
MODE         MEANING                    REMEMBER AS
────────────────────────────────────────────────────────
ios::in      open for reading           IN = input
ios::out     open for writing           OUT = output
ios::app     APPEND (preserve old)      APP = add at end ← SAFE
ios::trunc   TRUNCATE (DELETE old!)     TRUNC = tear/erase ← DANGER
ios::binary  binary mode (raw bytes)    BINARY = not text
ios::ate     open, go to end            ATE = at end

KEY TRAP: ofstream default = ios::out | ios::trunc
          = AUTOMATICALLY DELETES old content when opened!
          To PRESERVE: use ios::app explicitly
```

### ios::trunc vs ios::app:
```
ios::trunc → DELETES ALL existing content → starts fresh
ios::app   → PRESERVES existing content  → adds at end
```

### File Operations:
```
open()      → opens the file
close()     → flushes buffer + releases OS resource
>>          → reads word/value
<<          → writes value
getline()   → reads entire line (including spaces)
eof()       → true AFTER failed read (use while(fin>>x) instead)
read()      → reads binary data
write()     → writes binary data: fout.write((char*)&n, sizeof(n))
```

### Text vs Binary:
```
Text:   ASCII chars | human readable | int 65 = "65" (2 bytes)
Binary: raw bytes   | not readable   | int 65 = 0x41 (1 byte)
Binary mode flag: ios::binary
```

### Turbo C++ Shortcuts:
```
Ctrl + F9 = Compile AND Run  ← most tested!
Alt  + F9 = Compile ONLY
```

---

## 🔷 TOPIC 5: Exception Handling & Inline Functions
*(Day 12)*

### Exception Handling — Core:
```
try    = "watch this code — it might throw"
throw  = "signal/raise an exception"
catch  = "handle the thrown exception"

Flow: try { ... throw X ... } → catch(TypeX e) { handle }
      → No match → terminate() called → crash!
```

### catch Block Ordering Rules:
```
RULE 1: Most SPECIFIC (derived) catch block FIRST
RULE 2: Most GENERAL (base class) catch block LATER
RULE 3: catch(...) [catch-all] MUST be LAST — ALWAYS
RULE 4: catch(...) catches ALL types

WRONG: catch(exception) first → catch(runtime_error) after → never reached!
RIGHT: catch(runtime_error) first → catch(exception) later
```

### Rethrowing:
```
throw;   = rethrow SAME exception (no copy) ← CORRECT for rethrow
throw e; = rethrow COPY of e (may cause slicing in polymorphism)
```

### Standard Exceptions:
```
std::exception     = base of ALL standard exceptions
std::bad_alloc     = thrown by new on memory failure ← PYQ TRAP
std::runtime_error = runtime problems
std::logic_error   = logic problems
e.what()           = returns error message string
```

### Inline Functions — Key Facts:
```
inline = REQUEST to compiler (not guaranteed)
Effect = code substituted at call site (no function call overhead)
Trade-off: FASTER execution ↔ LARGER code size (code bloat)

Compiler HONORS inline for: short, simple, non-recursive functions
Compiler IGNORES inline for:
  ❌ Recursive functions ← KEY PYQ TRAP
  ❌ Functions with loops (for/while/do-while)
  ❌ Functions with static variables
  ❌ Large functions (many lines)

AUTO-INLINE: Member functions defined INSIDE class body
             = automatically inline (no keyword needed!)
```

---

## 🔷 TOPIC 6: Output Prediction, Bitwise, struct/class
*(Day 13)*

### Pre/Post Increment Rules:
```
i=5: cout<<i++  → prints 5, THEN i=6  (post: use THEN increment)
i=5: cout<<++i  → i=6, prints 6       (pre: increment THEN use)
b = a++         → b gets old a, then a increments
c = ++a         → a increments first, c gets new a
while(i++ < 3): checks old value (0,1,2), prints new (1,2,3)
```

### Bitwise Complete Reference:
```
Operator  a=5(0101) b=3(0011)  Result  Decimal
─────────────────────────────────────────────────
a & b     0101 & 0011 = 0001    AND       1
a | b     0101 | 0011 = 0111    OR        7
a ^ b     0101 ^ 0011 = 0110    XOR       6
~a        flip all bits          NOT      -6   ← ~n = -(n+1)
a << 1    0101 → 1010            ×2       10
a >> 1    0101 → 0010            ÷2        2

KEY FORMULAS:
  ~n    = -(n+1)     →  ~5=-6,  ~0=-1,  ~(-5)=4
  n & 1 = odd/even   →  1=odd,  0=even
  n ^ n = 0          →  any number XOR itself = 0
  n<<k  = n × 2^k    →  5<<2 = 20
  n>>k  = n ÷ 2^k    →  20>>2 = 5
```

### struct vs class:
```
THE ONLY DIFFERENCE: Default access specifier
  struct → PUBLIC by default
  class  → PRIVATE by default
Both support: methods, constructors, inheritance, all access specifiers
Inheritance default: struct → public | class → private
```

### Friend Function Quick Rules:
```
→ NOT a member function (called like regular function)
→ Can access PRIVATE and PROTECTED members
→ Declared INSIDE class with 'friend' keyword
→ Defined OUTSIDE class (no ClassName:: prefix needed)
→ Friendship NOT inherited (derived class doesn't get it)
→ Friendship NOT symmetric (A friend of B ≠ B friend of A)
```

### Scope Resolution `::` Uses:
```
::x                → access GLOBAL x (when local x shadows it)
ClassName::method  → define method outside class
ClassName::static  → access static member
Namespace::item    → access namespace member
```

---

## 📊 CS MASTER COMPARISON TABLE

```
TOPIC              KEY FACT                           COMMON TRAP
───────────────────────────────────────────────────────────────────
bool size          1 byte (NOT 1 bit)                bool ≠ 1 bit
sizeof(x++)        returns type size, x unchanged     doesn't evaluate
delete NULL        safe no-op, no crash               students think it crashes
new vs malloc      new=constructor; malloc=no constr  never mix new+free
char "Hello"       6 bytes (5 + '\0')                forgetting null terminator
s1 + s2 (char[])   COMPILE ERROR                      use strcat() instead
ofstream default   ios::out | ios::trunc = DELETES    use ios::app to preserve
catch(...)         MUST be LAST catch block            placing it first = rest unreachable
inline + recursion compiler IGNORES inline            recursive inline = regular func
class default      PRIVATE                            struct = PUBLIC
~5                 -6 (not 5 or -5)                  ~n = -(n+1) formula
friend function    NOT a member, NOT inherited        called like: func(obj) not obj.func()
```

---
---

# PART 2: GS RAPID REVISION
## 🏛️ Day 8–13: Modern Indian History — Complete Timeline

---

## 🔷 MASTER TIMELINE — FREEDOM STRUGGLE (1498–1947)

```
COMPLETE FREEDOM STRUGGLE TIMELINE
════════════════════════════════════════════════════════════════

1498    Vasco da Gama reaches India (Calicut) ← Portuguese FIRST
1600    British East India Company formed
1612    First British factory at Surat
1757    Battle of Plassey (Clive vs Siraj; Mir Jafar betrays)
        → Foundation of British rule in Bengal
1764    Battle of Buxar (Hector Munro vs 3 rulers)
        → CONFIRMED British supremacy
1773    Regulating Act → first parliamentary oversight
1784    Pitt's India Act → dual control (Company + Parliament)
1857    Revolt of 1857 (Sepoy Mutiny / First War of Independence)
        → Bihar: KUNWAR SINGH (Jagdishpur, Bhojpur)
        → Delhi: Bahadur Shah Zafar; Jhansi: Rani Laxmibai
1858    Company rule ended → Crown took over
        → Governor-General becomes VICEROY
        → First Viceroy: Lord Canning
1885    INC founded by A.O. HUME (British!) at Bombay
        → First president: W.C. BANERJEE
1905    Partition of Bengal by Lord CURZON
        → Swadeshi Movement begins
        → Annulled 1911
1906    Muslim League founded (Dhaka)
1909    Morley-Minto Reforms → communal electorate begins
1915    Gandhi returns to India
1916    Lucknow Congress: Gandhi meets Rajendra Prasad
        Lucknow Pact: INC + Muslim League together
        Home Rule: Tilak (April) + Annie Besant (September)
1917    CHAMPARAN SATYAGRAHA ← BIHAR ← BPSC HIGH PROBABILITY
        → Gandhi arrives Motihari April 15, 1917
        → Raj Kumar Shukla brought Gandhi
        → Tinkathia system (3/20 land = forced indigo)
        → Gandhi's FIRST SATYAGRAHA IN INDIA
        → Rajendra Prasad received Gandhi in Patna
1918    Champaran Agrarian Act → Tinkathia ABOLISHED, 25% refund
        Kheda Satyagraha (Gujarat farmers, crop failure)
        Ahmedabad Mill Strike (Gandhi's first hunger strike)
1919    Rowlatt Act ("No Daleel No Vakeel No Appeal" = Black Act)
        April 13: JALLIANWALA BAGH MASSACRE
        → General Dyer ordered firing; 379+ killed
        → Tagore returned KNIGHTHOOD
        → Udham Singh killed O'Dwyer in London, 1940
1920    Sept: Calcutta Special Session (Lala Lajpat Rai presides)
        → NCM proposed
        Dec: Nagpur Session → NCM FORMALLY ADOPTED
        Khilafat + NCM merged (Ali Brothers + Gandhi)
1921    Bihar Vidyapeeth founded by RAJENDRA PRASAD ← BIHAR
1922    Feb 5: CHAURI CHAURA → 22 policemen burned (UP, Gorakhpur)
        → Gandhi SUSPENDS NCM
        March: Gandhi arrested, 6 years
1923    Swaraj Party: C.R. DAS + MOTILAL NEHRU
1927    Simon Commission (7 all-British members, "Simon Go Back")
1928    Oct: Lala Lajpat Rai beaten at Lahore (Simon protests)
        Nov 17: Lala dies → "Punjab Kesari"
        Bhagat Singh kills Saunders (to avenge Lala)
        Nehru Report by MOTILAL NEHRU (demands DOMINION STATUS)
1929    Dec 31: LAHORE SESSION (Jawaharlal Nehru presides)
        → PURNA SWARAJ declared at midnight
        → Jan 26, 1930 = first Independence Day celebration
1930    Mar 2: Gandhi writes to Lord Irwin (11 demands, advance warning)
        Mar 12: DANDI MARCH BEGINS (Sabarmati Ashram, 78 volunteers)
        Apr 6: GANDHI MAKES SALT → CDM OFFICIALLY LAUNCHED
        May: Gandhi arrested; Sarojini Naidu leads Dharasana raid
        Dec: RTC 1 (Gandhi ABSENT — in jail)
1931    Mar 5: GANDHI-IRWIN PACT (Delhi Pact) → CDM SUSPENDED
        Mar 23: Bhagat Singh, Rajguru, Sukhdev HANGED
        Sept: RTC 2 (Gandhi PRESENT) → fails
1932    Jan: CDM RE-LAUNCHED; Gandhi arrested again
        Poona Pact (Gandhi + Ambedkar)
1934    CDM formally WITHDRAWN
1942    Mar–Apr: CRIPPS MISSION FAILS
        → Gandhi: "post-dated cheque on a crashing bank"
        Jul 14: WARDHA RESOLUTION (Congress Working Committee)
        Aug 8: AICC at GOWALIA TANK MAIDAN, BOMBAY
        → QUIT INDIA RESOLUTION + Gandhi's "DO OR DIE" speech
        Aug 9: Gandhi arrested (Aga Khan Palace, Pune)
        → = "AUGUST KRANTI DIWAS"
        → Aruna Asaf Ali hoists flag at Gowalia Tank
        Nov 9: JP escapes HAZARIBAGH JAIL ← BIHAR ← HIGH PROBABILITY
1944    Feb 22: Kasturba Gandhi dies (Aga Khan Palace, Pune)
        May 6: Gandhi released
1946    Dec 9: CONSTITUENT ASSEMBLY first meets
        → Rajendra Prasad elected PRESIDENT of CA
1947    Aug 15: INDIA INDEPENDENT
        First PM: Nehru | First President: Rajendra Prasad
        First GG: Lord Mountbatten
        First Indian GG: C. Rajagopalachari

════════════════════════════════════════════════════════════════
```

---

## 🔷 BIHAR-SPECIFIC FACTS — HIGH BPSC PROBABILITY

```
BIHAR FACTS — NEVER FORGET THESE
══════════════════════════════════════════════════

1857 Revolt:
→ KUNWAR SINGH led Bihar's revolt (Jagdishpur, BHOJPUR district)
→ He was 80 years old — folk hero of Bihar

Champaran Satyagraha (1917):
→ MOTIHARI = East Champaran = where Gandhi was summoned to court
→ RAJ KUMAR SHUKLA = Champaran indigo farmer who brought Gandhi
→ Gandhi arrived: April 15, 1917
→ RAJENDRA PRASAD received Gandhi in Patna
→ Champaran Agrarian Act 1918 = Tinkathia abolished + 25% refund

Rajendra Prasad:
→ Born: December 3, 1884 at ZERADEI, SIWAN, BIHAR
→ Founded BIHAR VIDYAPEETH, 1921 (during NCM)
→ Imprisoned at BANKIPUR JAIL, PATNA (Quit India 1942)
→ Elected President of Constituent Assembly: December 9, 1946
→ FIRST PRESIDENT OF INDIA: January 26, 1950
→ LONGEST SERVING: 2 terms, 12 years (1950–1962)
→ BHARAT RATNA: 1962 (while still President!)
→ Died: February 28, 1963, SADAQAT ASHRAM, PATNA
→ Book: India Divided (1946) — against partition

NCM Bihar:
→ BIHAR VIDYAPEETH (1921) = alternative national university
→ Rajendra Prasad organized NCM in Bihar

Quit India Movement:
→ JP (Jayaprakash Narayan) = FROM SITABDIARA, SARAN, BIHAR
→ JP led underground movement
→ JP ESCAPED HAZARIBAGH CENTRAL JAIL — November 9, 1942
→ Hazaribagh now in Jharkhand (was Bihar during independence)
→ Bihar had MOST INTENSE QIM participation of all provinces

══════════════════════════════════════════════════
```

---

## 🔷 MOVEMENT COMPARISON TABLE — MASTER

```
FEATURE         NCM (1920-22)    CDM (1930-34)    QUIT INDIA (1942)
──────────────────────────────────────────────────────────────────────
Launch site     Calcutta/Nagpur  Sabarmati/Dandi  Gowalia Tank, Bombay
Launched by     Gandhi           Gandhi           Gandhi
Method          Boycott          Break laws(salt) "Do or Die" rebellion
Key slogan      —                Salt = freedom   "Karo ya Maro"
Ended by        Chauri Chaura    Gandhi-Irwin Pact WWII end + 1947
Gandhi arrested 1922 (March)     1930 (May)       1942 (Aug 9)
Gandhi prison   —                Yerwada(Pune)    Aga Khan Palace(Pune)
Bihar event     Bihar Vidyapeeth Rajendra Prasad  JP jail escape
                founded (1921)   arrested         (Hazaribagh, Nov 9)
Key institution Bihar Vidyapeeth —                Parallel govts.
Underground     None (early end) Aruna(partial)   JP + Aruna + Lohia
Khilafat link   YES (1919-1924)  No               No
Women's role    Limited          Large (Sarojini) Very large (Aruna)
Result          Swaraj Party(23) CDM relaunch(32) Independence path
──────────────────────────────────────────────────────────────────────
```

---

## 🔷 PEOPLE & THEIR SINGLE MOST IMPORTANT FACT

```
PERSON                    MOST IMPORTANT FACT FOR EXAM
──────────────────────────────────────────────────────────────────
A.O. Hume                 Founded INC 1885 (was BRITISH!)
W.C. Banerjee             First President of INC
Bal Gangadhar Tilak       "Swaraj is my birthright" | Lal-Bal-Pal
Lala Lajpat Rai           Died after Simon Commission lathi charge
                          "Punjab Kesari"
Kunwar Singh              Led 1857 revolt in Bihar (Jagdishpur, Bhojpur)
Raj Kumar Shukla          Brought Gandhi to Champaran (indigo farmer)
Rajendra Prasad           Bihar's son; First President; Bihar Vidyapeeth
                          Zeradei, Siwan; 12 years as President
Ali Brothers              Khilafat Movement (Muhammad Ali + Shaukat Ali)
C.R. Das                  Co-founded Swaraj Party (with Motilal Nehru)
Motilal Nehru             Authored Nehru Report 1928; Swaraj Party
Sarojini Naidu            Led Dharasana raid; "Nightingale of India" (poet)
Aruna Asaf Ali            Hoisted flag at Gowalia Tank on Aug 9, 1942
JP (Jayaprakash)          Led QIM underground; Hazaribagh escape; FROM SARAN, BIHAR
Ram Manohar Lohia         Ran "Congress Radio" during QIM underground
Nana Patil                Led Satara Parallel Government (Prati Sarkar)
Bhagat Singh              Killed Saunders (avenging Lala); hanged Mar 23, 1931
Udham Singh               Killed Michael O'Dwyer (avenging JWB) in London, 1940
Rabindranath Tagore       Returned KNIGHTHOOD after Jallianwala Bagh
General Dyer              Ordered JWB firing
Lord Curzon               Partitioned Bengal 1905
Lord Irwin                Signed Gandhi-Irwin Pact (March 5, 1931)
Stafford Cripps           Led Cripps Mission 1942 (Labour Party leader)
Sucheta Kripalani         QIM underground; first female CM (UP, 1963)
──────────────────────────────────────────────────────────────────
```

---

## 🔷 KEY DATES FLASH CARDS

```
DATE              EVENT
────────────────────────────────────────────────
1498              Vasco da Gama arrives (Calicut)
1757              Battle of Plassey
1764              Battle of Buxar
1857 (May 10)     Revolt begins at Meerut
1885              INC founded (Bombay, A.O. Hume)
1905              Partition of Bengal (Lord Curzon)
1906              Muslim League founded (Dhaka)
1915              Gandhi returns to India
1916              Lucknow Congress + Lucknow Pact
1917 (Apr 15)     Gandhi arrives Motihari, Champaran
1918              Champaran Agrarian Act
1919 (Apr 13)     Jallianwala Bagh Massacre
1919 (Sept–Dec)   Non-Cooperation proposed + adopted
1921              Bihar Vidyapeeth founded (Rajendra Prasad)
1922 (Feb 5)      Chauri Chaura → NCM suspended
1923              Swaraj Party (C.R. Das + Motilal Nehru)
1927              Simon Commission formed
1928 (Nov 17)     Lala Lajpat Rai dies
1929 (Dec 31)     Lahore Session — Purna Swaraj
1930 (Mar 12)     Dandi March begins
1930 (Apr 6)      Gandhi makes salt → CDM launched
1931 (Mar 5)      Gandhi-Irwin Pact → CDM suspended
1931 (Mar 23)     Bhagat Singh hanged
1934              CDM formally withdrawn
1942 (Apr)        Cripps Mission fails
1942 (Aug 8)      QIM Resolution — Gowalia Tank, Bombay
1942 (Aug 9)      Gandhi arrested → August Kranti Diwas
1942 (Nov 9)      JP escapes Hazaribagh jail
1944 (Feb 22)     Kasturba Gandhi dies (Aga Khan Palace)
1946 (Dec 9)      Constituent Assembly first meets
1947 (Aug 15)     India Independence
1949 (Nov 26)     Constitution signed (Constitution Day)
1950 (Jan 26)     India becomes Republic; Rajendra Prasad 1st President
1962              Rajendra Prasad gets Bharat Ratna
1963 (Feb 28)     Rajendra Prasad dies (Sadaqat Ashram, Patna)
────────────────────────────────────────────────
```

---
---

# PART 3: PRACTICE QUESTIONS
## 📝 MIXED PYQ + CONCEPT MCQs — Day 8–13 All Topics

---

### COMPUTER SCIENCE — 25 MIXED MCQs

---

**Q1.** What is the output of:
```cpp
int a = 5;
int b = a++;
int c = ++a;
cout << a << " " << b << " " << c;
```
(A) 7 5 7
(B) 6 5 6
(C) 7 6 7
(D) More than one of the above
(E) None of the above

---

**Q2.** What is `12 & 10` in C++?
(A) 14
(B) 10
(C) 8
(D) More than one of the above
(E) None of the above

---

**Q3.** What is `~7` in C++?
(A) -7
(B) -8
(C) 7
(D) More than one of the above
(E) None of the above

---

**Q4.** Which of the following is TRUE about the default mode of `ofstream`?
(A) It opens the file in append mode — old content is preserved
(B) It opens with ios::out | ios::trunc — old content is DELETED
(C) It opens in read-only mode
(D) More than one of the above
(E) None of the above

---

**Q5.** What will happen if you execute `delete ptr;` where `ptr = NULL`?
(A) Runtime error
(B) Segmentation fault
(C) Safe no-operation — nothing happens
(D) More than one of the above
(E) None of the above

---

**Q6.** What is the size of `bool` in C++?
(A) 1 bit
(B) 1 byte
(C) 4 bytes
(D) More than one of the above
(E) None of the above

---

**Q7.** What does `rank<int[2][3][4]>::value` return?
(A) 24
(B) 2
(C) 3
(D) More than one of the above
(E) None of the above

---

**Q8.** A friend function in C++ is:
(A) A member function with special privileges
(B) A non-member function that can access private and protected members
(C) A function that must be defined inside the class
(D) More than one of the above
(E) None of the above

---

**Q9.** Which catch block MUST always be placed LAST?
(A) `catch(int e)`
(B) `catch(std::exception& e)`
(C) `catch(...)`
(D) More than one of the above
(E) None of the above

---

**Q10.** Which of the following causes the compiler to IGNORE the inline keyword?
(A) A function with a single return statement
(B) A recursive function
(C) A function defined inside a class body
(D) More than one of the above
(E) None of the above

---

**Q11.** What is the output of:
```cpp
int i = 0;
while (i++ < 3) cout << i << " ";
```
(A) 0 1 2
(B) 1 2 3
(C) 0 1 2 3
(D) More than one of the above
(E) None of the above

---

**Q12.** For `char str[] = "India"`, what is `sizeof(str)`?
(A) 5
(B) 6
(C) 4
(D) More than one of the above
(E) None of the above

---

**Q13.** What is the key difference between `new` and `malloc()`?
(A) `new` calls the constructor; `malloc` does not
(B) `new` returns `void*`; `malloc` returns a typed pointer
(C) `malloc` is available in C++ only; `new` in C only
(D) More than one of the above
(E) None of the above

---

**Q14.** Which of the following is the Compile AND Run shortcut in Turbo C++?
(A) Alt + F9
(B) Ctrl + F5
(C) Ctrl + F9
(D) More than one of the above
(E) None of the above

---

**Q15.** What is `6 ^ 6` in C++?
(A) 12
(B) 36
(C) 0
(D) More than one of the above
(E) None of the above

---

**Q16.** What is the default access specifier in a C++ `struct`?
(A) private
(B) protected
(C) public
(D) More than one of the above
(E) None of the above

---

**Q17.** Consider: `int arr[5] = {1, 2};` — what is `arr[4]`?
(A) Garbage value
(B) 2
(C) 0
(D) More than one of the above
(E) None of the above

---

**Q18.** What does `ios::trunc` do when opening a file?
(A) Opens the file at the end (go to last position)
(B) Appends new data after existing content
(C) Deletes all existing content in the file
(D) More than one of the above
(E) None of the above

---

**Q19.** What happens when `throw` is executed outside a `try` block with no matching catch?
(A) Exception is silently ignored
(B) Program resumes from next line
(C) `terminate()` is called — program crashes
(D) More than one of the above
(E) None of the above

---

**Q20.** What is `5 << 3` in C++?
(A) 15
(B) 40
(C) 20
(D) More than one of the above
(E) None of the above

---

**Q21.** Which of the following is FALSE about inline functions?
(A) They eliminate function call overhead
(B) They always reduce code size
(C) Member functions defined inside a class are automatically inline
(D) More than one of the above
(E) None of the above

---

**Q22.** What is a dangling pointer?
(A) A pointer that is not initialized (never assigned)
(B) A pointer that points to memory that has already been freed
(C) A pointer with value NULL
(D) More than one of the above
(E) None of the above

---

**Q23.** Which of the following correctly reads an entire line including spaces from a file?
(A) `fin >> line;`
(B) `getline(fin, line);`
(C) `fin.read(line);`
(D) More than one of the above
(E) None of the above

---

**Q24.** What is `~0` in C++?
(A) 0
(B) 1
(C) -1
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following is TRUE about passing an array to a function in C++?
(A) A complete copy of the array is made
(B) The array decays to a pointer — modifications affect the original
(C) `sizeof(arr)` inside the function gives original array size
(D) More than one of the above
(E) None of the above

---
---

### GENERAL STUDIES — 25 MIXED MCQs
### Modern Indian History — Day 8–13 All Topics

---

**Q26.** The Champaran Satyagraha of 1917 was Gandhi's:
(A) First Satyagraha in South Africa
(B) First Satyagraha in India
(C) First hunger strike
(D) More than one of the above
(E) None of the above

---

**Q27.** The Chauri Chaura incident (1922) is located in which state?
(A) Bihar
(B) Punjab
(C) Uttar Pradesh (Gorakhpur district)
(D) More than one of the above
(E) None of the above

---

**Q28.** Which of the following CORRECTLY pairs the leader with their role?
(A) Raj Kumar Shukla — led 1857 revolt in Bihar
(B) Kunwar Singh — brought Gandhi to Champaran
(C) Rajendra Prasad — received Gandhi in Patna for Champaran
(D) More than one of the above
(E) None of the above

---

**Q29.** The Dandi March started from which location on March 12, 1930?
(A) Wardha Ashram, Maharashtra
(B) Sabarmati Ashram, Ahmedabad, Gujarat
(C) Sevagram Ashram
(D) More than one of the above
(E) None of the above

---

**Q30.** JP (Jayaprakash Narayan) escaped from jail during the Quit India Movement. From which jail?
(A) Bankipur Jail, Patna
(B) Hazaribagh Central Jail
(C) Yerwada Prison, Pune
(D) More than one of the above
(E) None of the above

---

**Q31.** Who was the first President of the Indian National Congress (1885)?
(A) A.O. Hume
(B) Dadabhai Naoroji
(C) W.C. Banerjee
(D) More than one of the above
(E) None of the above

---

**Q32.** The Tinkathia system in Champaran required farmers to grow indigo on what portion of their land?
(A) 1/4 of land
(B) 3/20 of land (3 katha per bigha)
(C) 1/2 of land
(D) More than one of the above
(E) None of the above

---

**Q33.** Arrange in CORRECT CHRONOLOGICAL ORDER:
1. Quit India Movement
2. Champaran Satyagraha
3. Civil Disobedience Movement
4. Non-Cooperation Movement

(A) 2 → 4 → 3 → 1
(B) 4 → 2 → 3 → 1
(C) 2 → 3 → 4 → 1
(D) More than one of the above
(E) None of the above

---

**Q34.** The Gandhi-Irwin Pact (March 5, 1931) resulted in:
(A) Permanent end of the Civil Disobedience Movement
(B) Suspension of CDM; Gandhi to attend RTC 2
(C) India getting Dominion Status
(D) More than one of the above
(E) None of the above

---

**Q35.** Rajendra Prasad founded Bihar Vidyapeeth in which year and during which movement?
(A) 1917, Champaran Satyagraha
(B) 1921, Non-Cooperation Movement
(C) 1930, Civil Disobedience Movement
(D) More than one of the above
(E) None of the above

---

**Q36.** Who described the Cripps Mission offer as "a post-dated cheque on a crashing bank"?
(A) Jawaharlal Nehru
(B) Subhas Chandra Bose
(C) Mahatma Gandhi
(D) More than one of the above
(E) None of the above

---

**Q37.** The Lahore Session of INC (December 1929) declared:
(A) Dominion Status as the goal
(B) Purna Swaraj (Complete Independence)
(C) Quit India as the immediate demand
(D) More than one of the above
(E) None of the above

---

**Q38.** Who hoisted the Congress flag at Gowalia Tank Maidan after leaders were arrested on August 9, 1942?
(A) Kasturba Gandhi
(B) Sarojini Naidu
(C) Aruna Asaf Ali
(D) More than one of the above
(E) None of the above

---

**Q39.** Rajendra Prasad was born in which district of Bihar?
(A) Patna
(B) Siwan
(C) Champaran
(D) More than one of the above
(E) None of the above

---

**Q40.** The Non-Cooperation Movement was FORMALLY ADOPTED (not just proposed) at which Congress session?
(A) Calcutta Special Session, September 1920
(B) Nagpur Session, December 1920
(C) Lahore Session, December 1929
(D) More than one of the above
(E) None of the above

---

**Q41.** Rajendra Prasad served as President of India for how many years — making him the longest serving?
(A) 7 years
(B) 10 years
(C) 12 years (1950–1962)
(D) More than one of the above
(E) None of the above

---

**Q42.** MATCH THE FOLLOWING — Movements and their key events:
```
Movement              Key Event
1. NCM (1920–22)      A. Gandhi makes salt at Dandi coast
2. CDM (1930)         B. 22 policemen burned — movement suspended
3. Quit India (1942)  C. JP escapes Hazaribagh jail
```
(A) 1-B, 2-A, 3-C
(B) 1-A, 2-B, 3-C
(C) 1-C, 2-A, 3-B
(D) More than one of the above
(E) None of the above

---

**Q43.** The Nehru Report (1928) was authored by which leader and demanded what?
(A) Jawaharlal Nehru; demanded Purna Swaraj
(B) Motilal Nehru; demanded Dominion Status
(C) Gandhi; demanded withdrawal of all British acts
(D) More than one of the above
(E) None of the above

---

**Q44.** Which of the following statements about the Battle of Buxar (1764) is CORRECT?
(A) It was fought between Clive and Siraj-ud-Daula
(B) It was more significant than Plassey — confirmed British supremacy
(C) It was led by Robert Clive on the British side
(D) More than one of the above
(E) None of the above

---

**Q45.** Rabindranath Tagore returned his Knighthood to protest:
(A) Partition of Bengal
(B) Simon Commission
(C) Jallianwala Bagh Massacre
(D) More than one of the above
(E) None of the above

---

**Q46.** Dr. Rajendra Prasad signed the Constitution of India on which date (now celebrated as Constitution Day)?
(A) January 26, 1950
(B) August 15, 1949
(C) November 26, 1949
(D) More than one of the above
(E) None of the above

---

**Q47.** What was the role of Ram Manohar Lohia during the Quit India Movement?
(A) He led the Dharasana Salt Works raid
(B) He hoisted the Congress flag at Gowalia Tank
(C) He ran "Congress Radio" underground in Bombay
(D) More than one of the above
(E) None of the above

---

**Q48.** August 9, 1942, is celebrated as:
(A) Republic Day
(B) Independence Day
(C) August Kranti Diwas (August Revolution Day)
(D) More than one of the above
(E) None of the above

---

**Q49.** Which of the following CORRECTLY describes JP (Jayaprakash Narayan)?
(A) He was from Sitabdiara village, Saran district, Bihar
(B) He escaped from Hazaribagh Central Jail on November 9, 1942
(C) He led the underground Quit India movement
(D) More than one of the above
(E) None of the above

---

**Q50.** MATCH THE FOLLOWING — Person and their most important contribution:
```
Person              Contribution
1. Kunwar Singh     A. Led underground QIM; Hazaribagh escape
2. Rajendra Prasad  B. Led 1857 revolt in Bihar (Jagdishpur, Bhojpur)
3. JP               C. Founded Bihar Vidyapeeth; First President of India
4. Raj Kumar Shukla D. Brought Gandhi to Champaran Satyagraha
```
(A) 1-B, 2-C, 3-A, 4-D
(B) 1-A, 2-B, 3-D, 4-C
(C) 1-C, 2-D, 3-A, 4-B
(D) More than one of the above
(E) None of the above

---
---

# ANSWER KEY

## ⚠️ MANDATORY: Attempt all 50 questions BEFORE checking!

---

### CS Answers (Q1–Q25):

| Q | Answer | Reason (one-line) |
|---|--------|------------------|
| 1 | (A) | b=a++(b=5,a→6); c=++a(a→7,c=7); a=7,b=5,c=7 |
| 2 | (C) | 12=1100, 10=1010, AND=1000=8 |
| 3 | (B) | ~n=-(n+1); ~7=-8 |
| 4 | (B) | ofstream default = ios::out\|ios::trunc = DELETES content |
| 5 | (C) | delete NULL = safe no-op in C++ |
| 6 | (B) | bool = 1 byte (not 1 bit!) |
| 7 | (C) | 3D array → rank = 3 |
| 8 | (B) | Non-member function with access to private/protected |
| 9 | (C) | catch(...) = catch-all = MUST be last |
| 10 | (B) | Recursive function → compiler ignores inline |
| 11 | (B) | while(i++ < 3) checks 0,1,2 < 3 (true); prints i=1,2,3 |
| 12 | (B) | "India" = 5 chars + '\0' = 6 bytes |
| 13 | (A) | new calls constructor; malloc does not |
| 14 | (C) | Ctrl+F9 = Compile AND Run in Turbo C++ |
| 15 | (C) | n^n = 0 always; 6^6=0 |
| 16 | (C) | struct default = public |
| 17 | (C) | Partial init: rest = 0 (not garbage!) |
| 18 | (C) | ios::trunc = deletes all existing content |
| 19 | (C) | No matching catch → terminate() called → crash |
| 20 | (B) | 5<<3 = 5×2³ = 5×8 = 40 |
| 21 | (B) | FALSE: inline INCREASES code size (code bloat) |
| 22 | (B) | Dangling = points to freed/destroyed memory |
| 23 | (B) | getline(fin, line) reads full line with spaces |
| 24 | (C) | ~0 = -(0+1) = -1 |
| 25 | (B) | Array decays to pointer; modifications affect original |

---

### GS Answers (Q26–Q50):

| Q | Answer | Reason (one-line) |
|---|--------|------------------|
| 26 | (B) | First Satyagraha IN India (had done in South Africa earlier) |
| 27 | (C) | Chauri Chaura = Gorakhpur district, UP |
| 28 | (C) | Rajendra Prasad received Gandhi in Patna (correct pairing) |
| 29 | (B) | Sabarmati Ashram, Ahmedabad, Gujarat |
| 30 | (B) | Hazaribagh Central Jail, November 9, 1942 |
| 31 | (C) | W.C. Banerjee = first INC President (Hume = founder) |
| 32 | (B) | 3 katha per bigha = 3/20 of land |
| 33 | (A) | 1917 Champaran → 1920 NCM → 1930 CDM → 1942 QIM |
| 34 | (B) | Pact suspended CDM; Gandhi attended RTC 2 |
| 35 | (B) | 1921, during Non-Cooperation Movement |
| 36 | (C) | Gandhi's famous quote about Cripps Mission |
| 37 | (B) | Purna Swaraj = Complete Independence (not Dominion Status) |
| 38 | (C) | Aruna Asaf Ali hoisted flag after arrests |
| 39 | (B) | Siwan district (Zeradei village) |
| 40 | (B) | Nagpur Session Dec 1920 = FORMAL adoption (Calcutta = proposed) |
| 41 | (C) | 12 years (1950–1962) = longest serving President |
| 42 | (A) | NCM=Chauri Chaura, CDM=Dandi salt, QIM=JP escape |
| 43 | (B) | Motilal Nehru authored it; demanded Dominion Status |
| 44 | (B) | Buxar more significant; confirmed British supremacy |
| 45 | (C) | Tagore returned Knighthood after Jallianwala Bagh |
| 46 | (C) | November 26, 1949 = Constitution Day |
| 47 | (C) | Lohia ran Congress Radio underground in Bombay |
| 48 | (C) | August Kranti Diwas = August Revolution Day |
| 49 | (D) | ALL three facts about JP are correct |
| 50 | (A) | Kunwar Singh-B, Rajendra Prasad-C, JP-A, Shukla-D |

---
---

# 🔁 FINAL REVISION NOTES
## 📌 "Last 1-Hour Before Exam" — Ultra-Crisp Format

---

### ⚡ CS — 30 MUST-KNOW FACTS

```
VARIABLES & DATA TYPES:
1.  bool = 1 BYTE (not 1 bit)
2.  void x; → compile error | void* ptr → valid
3.  sizeof(x++) → does NOT increment x (compile-time operator)
4.  User-defined header: "file.h" | Standard: <iostream>
5.  Ctrl+F9 = Compile + Run | Alt+F9 = Compile only

POINTERS:
6.  &x = address of x | *p = value at address in p
7.  int* p, q → p=pointer, q=int (TRAP!) | int *p, *q → both pointers
8.  delete NULL → SAFE, no crash, no error
9.  new → calls constructor | malloc → does NOT
10. new pair: delete | new[] pair: delete[] | NEVER mix!
11. Dangling = freed memory still pointed to | Wild = never initialized
12. ~n = -(n+1) → ~5=-6 | sizeof(pointer) = 4/8 (NOT type-dependent)

ARRAYS:
13. arr[i] == *(arr+i) — always equivalent
14. arr++ → INVALID (array name = constant pointer)
15. char "Bihar" = 6 bytes (5 + '\0')
16. char s1[] + s2[] → COMPILE ERROR; use strcat()
17. Partial init: int arr[5]={1,2} → arr[2..4] = 0 (not garbage!)
18. is_array<int[5]>::value=1 | rank<int[3][4]>::value=2

FILE HANDLING:
19. ios::trunc = DELETES content | ios::app = PRESERVES + adds at end
20. ofstream default = ios::out | ios::trunc → DESTROYS old content!
21. close() = flushes buffer to disk (data loss if skipped)
22. Binary write: fout.write((char*)&n, sizeof(n))

EXCEPTION HANDLING:
23. catch(...) = catch-all → MUST be LAST block always!
24. Specific catch BEFORE general catch (derived before base)
25. throw; = rethrow original | throw e; = rethrow copy
26. new fails → std::bad_alloc thrown (not NULL like malloc)

INLINE FUNCTIONS:
27. inline = request (not guaranteed) | code substituted at call site
28. Trade-off: FASTER execution but LARGER code size
29. Inline IGNORED for: recursion, loops, static vars, large body
30. Member functions INSIDE class = automatically inline (no keyword!)

OUTPUT PREDICTION:
31. i=5: i++ prints 5 then i=6 | ++i makes i=6 then prints 6
32. while(i++ < 3) → checks 0,1,2 (old) → prints 1,2,3 (new)
33. 5&3=1 | 5|3=7 | 5^3=6 | ~5=-6 | 5<<1=10 | 20>>2=5
34. n^n = 0 (always!) | n&1: 1=odd, 0=even
35. struct = PUBLIC default | class = PRIVATE default
36. Friend: NOT member, can access private, NOT inherited
37. :: = scope resolution (::x for global, ClassName::method for outside def)
```

---

### ⚡ GS — 30 MUST-KNOW FACTS

```
TIMELINE ANCHORS:
1.  1757 = Plassey (Mir Jafar betrays) | 1764 = Buxar (Hector Munro)
2.  1885 = INC founded by A.O. HUME | First president = W.C. Banerjee
3.  1905 = Partition of Bengal (Lord Curzon) → Swadeshi Movement
4.  1906 = Muslim League founded (Dhaka)

CHAMPARAN 1917 (BIHAR HIGH PRIORITY):
5.  Raj Kumar Shukla brought Gandhi | Gandhi arrived April 15, 1917 (Motihari)
6.  Tinkathia = 3/20 land for forced indigo cultivation
7.  FIRST Satyagraha in India | Rajendra Prasad received Gandhi in Patna
8.  1918 = Champaran Agrarian Act; Tinkathia abolished; 25% refund

JALLIANWALA BAGH 1919:
9.  April 13, 1919 (Baisakhi Day) | General Dyer ordered firing
10. Tagore returned KNIGHTHOOD (not Nobel Prize!)
11. Udham Singh killed O'Dwyer in London, 1940 (avenge JWB)

NON-COOPERATION MOVEMENT:
12. Proposed: Calcutta Sept 1920 (Lala Lajpat Rai presides)
13. Formally adopted: Nagpur Dec 1920
14. Feb 5, 1922 = Chauri Chaura (UP, Gorakhpur) = 22 policemen killed
15. Bihar Vidyapeeth founded 1921 by RAJENDRA PRASAD (during NCM)
16. Swaraj Party 1923 = C.R. Das + Motilal Nehru (opposed suspension)

CIVIL DISOBEDIENCE MOVEMENT:
17. Nehru Report 1928 = MOTILAL Nehru = demanded DOMINION STATUS (not Purna Swaraj)
18. Lahore 1929 (J. Nehru presides) = PURNA SWARAJ declared (midnight, Dec 31)
19. Dandi March: March 12 → April 6, 1930 | 241 miles | 78 volunteers
20. Gandhi makes salt = April 6, 1930 = CDM launched
21. Gandhi-Irwin PACT = March 5, 1931 = CDM SUSPENDED (not ended)
22. Bhagat Singh hanged = March 23, 1931

QUIT INDIA MOVEMENT:
23. Cripps = "post-dated cheque on crashing bank" = fails April 1942
24. Aug 8 = QIM Resolution (Gowalia Tank, Bombay) | Aug 9 = arrests = August Kranti Diwas
25. Gandhi to Aga Khan Palace, Pune | Aruna Asaf Ali hoists flag
26. JP = Sitabdiara, Saran, BIHAR | escaped HAZARIBAGH jail = November 9, 1942
27. Ram Manohar Lohia = Congress Radio underground
28. Kasturba dies = February 22, 1944 (Aga Khan Palace, Pune)

RAJENDRA PRASAD (BIHAR SPECIAL):
29. Born Dec 3, 1884 | Zeradei, Siwan, Bihar
30. Bihar Vidyapeeth 1921 | CA President Dec 9, 1946
    Constitution signed Nov 26, 1949 | 1st President Jan 26, 1950
    Two terms | 12 years | Bharat Ratna 1962 | Died Feb 28, 1963
```

---

### ⚡ LAST-MINUTE COMPARISON TABLES

```
MOVEMENT    LAUNCHED          ENDED             GANDHI ARRESTED
NCM         Sept/Dec 1920     Feb 1922 (CC)     March 1922
CDM         April 6, 1930     March 5, 1931*    May 1930
QIM         August 9, 1942    1945+             August 9, 1942
*CDM relaunched 1932, withdrawn 1934

BATTLE      YEAR   BRITISH COMMANDER   OPPONENT         SIGNIFICANCE
Plassey     1757   Robert Clive        Siraj-ud-Daula   Foundation of British rule
Buxar       1764   Hector Munro        Mir Qasim+2      CONFIRMATION of supremacy

RTC         YEAR   GANDHI
RTC 1       1930   ABSENT (in jail)
RTC 2       1931   PRESENT (after pact)
RTC 3       1932   ABSENT (in jail again)
```

---

## 🎯 WEEK 2 COMPLETE — WHAT YOU'VE MASTERED

```
Day 8:  C++ Variables, Data Types, sizeof() + Modern Indian History
Day 9:  C++ Pointers (new/delete, NULL, dangling) + Champaran 1917
Day 10: C++ Arrays (1D, 2D, strings, is_array/rank) + NCM 1920-22
Day 11: C++ File Handling (modes, streams, trunc/app) + CDM 1930
Day 12: Exception Handling (try/catch/throw) + Inline + Quit India 1942
Day 13: Output Prediction (bitwise, increment) + Rajendra Prasad
Day 14: COMPLETE REVISION + 50 Mixed PYQ Practice Questions ← TODAY

NEXT: Day 15 begins Week 3 → DBMS Basics + Indian Constitution
```

---

*Tomorrow: Day 15 — Introduction to DBMS + Indian Constitution (Preamble & Fundamental Rights)*
