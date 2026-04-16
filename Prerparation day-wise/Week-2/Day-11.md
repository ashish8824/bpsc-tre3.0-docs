# 📅 BPSC TRE 4.0 — DAY 11 COMPLETE STUDY MODULE
### C++ File Handling (File I/O) + Civil Disobedience Movement 1930
**Target: TOP 50 RANK | Score: 130+/150**

---

> ⏰ **Today's Schedule**
> - Morning (1.5 hrs): C++ File Handling — streams, modes, operations, binary vs text
> - Afternoon (1 hr): Civil Disobedience Movement — story-based deep understanding
> - Evening (1 hr): Solve all 50 MCQs (25 CS + 25 GS)
> - Night (30 min): Write 5-bullet revision notes in your notebook

---

# PART 1: COMPUTER SCIENCE
## 📘 C++ File Handling — Complete Deep Dive

---

## 🔷 SECTION 1: What is File Handling? (The Foundation)

### Real-Life Analogy — The Office Filing Cabinet:
```
Imagine an office with a FILING CABINET (= hard disk storage).
You need to:
  → OPEN a drawer (file) to start working
  → READ documents from the drawer
  → WRITE new documents into it
  → CLOSE the drawer when done

Without filing cabinet:
  → All data lives only in RAM (lost when program ends)
  → Like writing on a whiteboard — erased when power off

With file handling:
  → Data persists on disk PERMANENTLY
  → Like writing in a notebook — survives closing the program
```

### Why File Handling?
```
Problem without files:
  → Program runs → data stored in memory (RAM)
  → Program closes → ALL data is LOST forever
  → Cannot share data between program runs

Solution with files:
  → Write data to file on disk
  → File persists after program ends
  → Next program run can READ the saved data
  → Multiple programs can share the same file
```

### What is a Stream?
```
STREAM = a sequence/flow of data between your program and a source/destination

Types:
  Input stream  → data FLOWS INTO  your program (from file/keyboard)
  Output stream → data FLOWS OUT OF your program (to file/screen)

Think of a stream like a water pipe:
  → Data flows through it in one direction
  → You can read from it or write to it
```

---

## 🔷 SECTION 2: File Stream Classes — The Core Three

### Header Required:
```cpp
#include <fstream>   // includes all three file stream classes
```

### The Three File Stream Classes:

```
FILE STREAM HIERARCHY:
                    ios (base class)
                     │
              ┌──────┴──────┐
           istream        ostream
              │               │
           ifstream    ofstream
              │               │
              └──────┬──────┘
                  fstream
```

### 1. `ifstream` — Input File Stream
```
Purpose: READ data FROM a file INTO the program
Think:   i = input = "I want to READ"
Default mode: ios::in (open for reading)
```

```cpp
ifstream inFile;           // declare input file stream
inFile.open("data.txt");   // open file for reading
int x;
inFile >> x;               // read from file into variable
inFile.close();            // close the file
```

### 2. `ofstream` — Output File Stream
```
Purpose: WRITE data FROM the program INTO a file
Think:   o = output = "I want to WRITE"
Default mode: ios::out | ios::trunc (open for writing, truncates file)
```

```cpp
ofstream outFile;             // declare output file stream
outFile.open("result.txt");   // open file for writing
outFile << "Hello Bihar";     // write to file
outFile.close();              // close the file
```

### 3. `fstream` — File Stream (Both Read and Write)
```
Purpose: Both READ and WRITE to same file
Think:   f = file = "full access"
Must specify mode explicitly (no safe default for both operations)
```

```cpp
fstream file;
file.open("data.txt", ios::in | ios::out);  // open for both
file << "Write this";    // write
file >> someVar;         // read
file.close();
```

### Quick Comparison Table:

| Class | Purpose | Default Mode | Header |
|-------|---------|-------------|--------|
| `ifstream` | Read from file | `ios::in` | `<fstream>` |
| `ofstream` | Write to file | `ios::out \| ios::trunc` | `<fstream>` |
| `fstream` | Read + Write | Must specify | `<fstream>` |

---

## 🔷 SECTION 3: File Modes — The Exam Goldmine

### What are File Modes?
File modes tell the system **HOW** to open the file — should it read? write? append? start fresh?

### Complete File Modes Table:

| Mode Flag | Full Name | Meaning |
|-----------|-----------|---------|
| `ios::in` | input | Open file for **reading** |
| `ios::out` | output | Open file for **writing** |
| `ios::app` | append | Write at the **END** of file (existing content preserved) |
| `ios::trunc` | truncate | **DELETE** existing content when opening (start fresh) |
| `ios::binary` | binary | Open in **binary mode** (not text mode) |
| `ios::ate` | at end | Open and move file pointer to **end** of file |

---

## 🔷 SECTION 4: `ios::trunc` — The #1 PYQ Trap

### What Does `ios::trunc` Do?
```
ios::trunc = TRUNCATE = CUT/DELETE all existing content

When you open a file with ios::trunc:
→ If file EXISTS     → ALL existing content is DELETED
→ File becomes EMPTY → You start writing from scratch
→ If file DOES NOT EXIST → New file is created (same as ios::out)

"Trunc" comes from "truncate" = to cut short = to make zero length
```

### Visual Explanation:
```
BEFORE opening with ios::trunc:
┌─────────────────────────────────┐
│ data.txt                        │
│ Line 1: Hello                   │
│ Line 2: World                   │
│ Line 3: BPSC TRE 2026           │
└─────────────────────────────────┘

AFTER opening with ios::trunc:
┌─────────────────────────────────┐
│ data.txt                        │
│ (empty — all content deleted)   │
└─────────────────────────────────┘

NOW writing "New Content":
┌─────────────────────────────────┐
│ data.txt                        │
│ New Content                     │
└─────────────────────────────────┘
```

### `ios::trunc` vs `ios::app` — KEY DIFFERENCE:

```
ios::trunc (TRUNCATE):
  → DELETES old content
  → Starts writing from beginning
  → Old data is GONE FOREVER
  Example: Like tearing out all pages and writing fresh

ios::app (APPEND):
  → PRESERVES old content
  → Adds new content at the END
  → Old data is SAFE
  Example: Like turning to a new blank page and continuing
```

```cpp
// ios::trunc — DESTROYS old content:
ofstream f1("notes.txt", ios::out | ios::trunc);
f1 << "New note";  // Previous content erased, only "New note" remains

// ios::app — PRESERVES old content:
ofstream f2("notes.txt", ios::out | ios::app);
f2 << "Added note";  // Previous content + "Added note" at end
```

### 🚨 PYQ TRAP #1:
> **Default behavior of `ofstream`** when you just do `ofstream f("file.txt")`:
> It uses `ios::out | ios::trunc` by default.
> This means **simply opening a file with ofstream DESTROYS existing content!**
> To preserve content, you MUST explicitly use `ios::app`.

---

## 🔷 SECTION 5: Combining File Modes with `|`

### The Bitwise OR Operator for Modes:
```cpp
// Use | (bitwise OR) to combine multiple modes:
fstream f;
f.open("data.txt", ios::in | ios::out);              // read + write
f.open("data.txt", ios::out | ios::app);             // write + append
f.open("data.txt", ios::in | ios::out | ios::binary); // read + write + binary
```

### Common Mode Combinations:

| Combination | Effect |
|-------------|--------|
| `ios::in` | Read only |
| `ios::out` | Write only (truncates by default) |
| `ios::out \| ios::trunc` | Write + destroy old content |
| `ios::out \| ios::app` | Write + preserve old content (append) |
| `ios::in \| ios::out` | Read + write (file must exist) |
| `ios::in \| ios::binary` | Read binary file |
| `ios::out \| ios::binary` | Write binary file |
| `ios::in \| ios::out \| ios::binary` | Read + write binary file |

---

## 🔷 SECTION 6: File Operations — open(), close(), eof()

### Opening a File:

#### Method 1: Constructor (at object creation):
```cpp
ifstream fin("marks.txt");         // open at creation
ofstream fout("output.txt");       // open at creation
fstream f("data.txt", ios::in | ios::out);
```

#### Method 2: open() function:
```cpp
ifstream fin;
fin.open("marks.txt");             // open separately
fin.open("marks.txt", ios::in);    // with explicit mode
```

### Checking if File Opened Successfully:
```cpp
ifstream fin("data.txt");
if (!fin) {                        // if file failed to open
    cout << "Error: File not found!";
    return 1;
}
// OR:
if (fin.fail()) {
    cout << "File opening failed";
}
// OR:
if (!fin.is_open()) {
    cout << "File not open";
}
```

### 🚨 PYQ TRAP #2:
> Always check if file opened successfully before reading/writing.
> If you read from a file that doesn't exist without checking:
> → No compile error, but UNDEFINED BEHAVIOR at runtime

### Closing a File:
```cpp
fin.close();    // always close files when done!
fout.close();
```

**Why close?**
```
→ Flushes buffered data to disk (writes actually happen)
→ Releases file handle (OS resource)
→ Allows other programs to access the file
→ Prevents data loss (buffer may not be written without close)
```

### Reading from Files:

#### Using `>>` operator (word by word):
```cpp
ifstream fin("data.txt");
int num;
string word;
fin >> num;       // reads next integer
fin >> word;      // reads next word (stops at space)
```

#### Using `getline()` (line by line):
```cpp
ifstream fin("data.txt");
string line;
while (getline(fin, line)) {    // reads entire line
    cout << line << endl;
}
```

#### Using `get()` (character by character):
```cpp
ifstream fin("data.txt");
char ch;
while (fin.get(ch)) {          // reads one char at a time
    cout << ch;
}
```

### Writing to Files:
```cpp
ofstream fout("output.txt");
fout << "Hello" << endl;       // write string
fout << 42 << " " << 3.14;    // write numbers
fout.close();
```

---

## 🔷 SECTION 7: `eof()` — End of File Detection

### What is `eof()`?
```
eof() = End Of File function
Returns: true  (1) when file pointer has reached the END of file
         false (0) when there is still data to read
```

### Usage:
```cpp
ifstream fin("data.txt");
int num;
while (!fin.eof()) {        // loop until end of file
    fin >> num;
    cout << num << " ";
}
fin.close();
```

### 🚨 PYQ TRAP #3 — The eof() Trap:
```cpp
// WRONG approach:
while (!fin.eof()) {
    fin >> num;
    cout << num;   // ⚠️ May print last value TWICE!
}
// WHY? eof() becomes true AFTER the failed read, not before.
// The last read may fail (eof reached) but eof() returns false
// just BEFORE that last read — so loop runs one extra time.

// CORRECT approach:
while (fin >> num) {        // read and check in one step
    cout << num << " ";
}
// This is cleaner — loop exits when read fails (eof or error)
```

---

## 🔷 SECTION 8: Text File vs Binary File

### Text File:
```
→ Data stored as human-readable characters (ASCII)
→ Numbers stored as their text representation
   Example: 65 stored as '6' '5' (two characters = 2 bytes)
→ Newlines may be converted (\n → \r\n on Windows)
→ Used for: config files, source code, log files
→ Mode: default (no special flag needed)
```

### Binary File:
```
→ Data stored in raw binary format (exact memory representation)
→ Numbers stored as their binary value
   Example: 65 stored as 01000001 (1 byte, direct binary)
→ No newline conversion — exact bytes preserved
→ Used for: images, executables, databases, serialized data
→ Mode: ios::binary flag required
```

### Comparison:

| Feature | Text File | Binary File |
|---------|-----------|-------------|
| Storage format | ASCII characters | Raw binary bytes |
| Human readable | Yes (open in notepad) | No (appears as garbage) |
| Number storage | As text (65 = "6","5") | As binary (65 = 0x41) |
| Newline handling | OS-dependent conversion | No conversion |
| Size | Usually larger | Usually smaller |
| Mode flag | Default (no flag) | `ios::binary` |
| Used for | Text, config, logs | Images, exe, databases |

```cpp
// Text file write:
ofstream ftxt("text.txt");
ftxt << 65;          // writes "65" (two ASCII chars)

// Binary file write:
ofstream fbin("data.bin", ios::binary);
int n = 65;
fbin.write((char*)&n, sizeof(n));   // writes 4 bytes (binary int)
```

### Binary File Functions:
```cpp
// write() — write binary data:
fout.write((char*)&variable, sizeof(variable));

// read() — read binary data:
fin.read((char*)&variable, sizeof(variable));
```

---

## 🔷 SECTION 9: File Handling Workflow — Complete Picture

```
COMPLETE FILE HANDLING WORKFLOW:
═══════════════════════════════════════════════════════

Step 1: INCLUDE HEADER
  #include <fstream>

Step 2: DECLARE stream object
  ifstream fin;   OR   ofstream fout;   OR   fstream f;

Step 3: OPEN the file
  fin.open("filename.txt");
  fin.open("filename.txt", mode_flags);
  OR: ifstream fin("filename.txt");

Step 4: CHECK if opened
  if (!fin) { handle error; }

Step 5: PERFORM operations
  fin >> variable;          // read
  fout << data;             // write
  getline(fin, line);       // read line
  fin.get(ch);              // read char

Step 6: CHECK eof while reading
  while (fin >> data) { ... }
  OR: while (!fin.eof()) { ... }

Step 7: CLOSE the file
  fin.close();
  fout.close();

═══════════════════════════════════════════════════════
```

---

## 🔷 SECTION 10: Turbo C++ Shortcut

### Important Keyboard Shortcuts (Exam Context):

| Shortcut | Action |
|----------|--------|
| **Ctrl + F9** | Compile and Run the program |
| Alt + F9 | Compile only (without running) |
| Ctrl + F10 | Run without compiling |
| F8 | Step over (debugging) |
| F7 | Step into (debugging) |
| Alt + F5 | View output window |

### 🚨 PYQ TRAP #4:
> **Ctrl + F9** = "Compile AND Run" in Turbo C++
> This is the most frequently tested shortcut in BPSC TRE CS exams.
> Alt + F9 = Compile ONLY (not run)
> These two are commonly confused in exam questions!

---

## 📊 VISUAL SUMMARY — File Handling Complete Map

```
C++ FILE HANDLING — MASTER STRUCTURE
│
├── HEADER: #include <fstream>
│
├── CLASSES:
│   ├── ifstream  → READ  (default: ios::in)
│   ├── ofstream  → WRITE (default: ios::out | ios::trunc)
│   └── fstream   → BOTH  (must specify mode)
│
├── MODES:
│   ├── ios::in     → read
│   ├── ios::out    → write
│   ├── ios::app    → append (preserve old content)
│   ├── ios::trunc  → truncate (DELETE old content) ← #1 TRAP
│   ├── ios::binary → binary mode
│   └── ios::ate    → start at end of file
│
├── OPERATIONS:
│   ├── open()   → opens file
│   ├── close()  → closes + flushes buffer
│   ├── >>       → reads word/value
│   ├── <<       → writes value
│   ├── getline()→ reads entire line
│   ├── eof()    → checks end of file
│   ├── read()   → binary read
│   └── write()  → binary write
│
├── FILE TYPES:
│   ├── Text   → ASCII, human readable, default
│   └── Binary → raw bytes, ios::binary flag
│
└── SHORTCUT:
    └── Ctrl + F9 → Compile and Run (Turbo C++)
```

---
---

# PART 2: GENERAL STUDIES
## 🏛️ Civil Disobedience Movement (1930) — Story-Based Deep Dive

---

## 🔷 THE BACKGROUND — THREE TRIGGERS

### Background 1: Simon Commission — 1927

```
Why it was formed:
  → Government of India Act 1919 required review after 10 years
  → British government formed a 7-member commission in 1927

The Problem:
  → ALL 7 members were BRITISH — no Indian member!
  → "Indians can't decide their own constitutional future?"
  → This was seen as a deep insult

Indian Response:
  → ALL major parties boycotted: INC + Muslim League + others
  → "Simon Go Back" slogan — everywhere Simon went
  → Massive protests and demonstrations

Bihar Connection — Lala Lajpat Rai:
  → October 30, 1928: Simon Commission arrived in Lahore
  → Lala Lajpat Rai led a peaceful protest march
  → Police officer Saunders ordered a brutal lathi charge
  → Lala Lajpat Rai was severely beaten
  → He said: "Every blow struck on me is a nail in the coffin of British imperialism"
  → He died on November 17, 1928 from his injuries
  → Called: "Punjab Kesari" (Lion of Punjab)
  → Bhagat Singh vowed revenge → killed Saunders (mistaking for another officer)
```

### Background 2: Nehru Report — 1928
```
What: INC's own proposed constitution for India
Author: Motilal Nehru (committee chairman) → hence "Nehru Report"
Key demand: DOMINION STATUS (self-governance within British Empire)
              NOT complete independence

Jinnah's objection:
  → Wanted separate electorate for Muslims
  → Nehru Report rejected separate electorates
  → This widened INC–Muslim League divide

Subhas Bose and young Nehru:
  → They wanted COMPLETE INDEPENDENCE, not just Dominion Status
  → Congress gave British a 1-year deadline to grant Dominion Status
```

### Background 3: Lahore Session — December 1929
```
Date: December 31, 1929 (midnight)
Location: Banks of River Ravi, Lahore
President: Jawaharlal Nehru (just 39 years old)
Resolution: PURNA SWARAJ (Complete Independence)

The Midnight Moment:
  → As the clock struck midnight (Jan 1, 1930 began)
  → Congress passed the Purna Swaraj resolution
  → The tri-colour flag was hoisted on the riverbank
  → January 26, 1930 declared as "Independence Day"
    (celebrated annually until actual independence — this is
     why January 26 became our Republic Day in 1950)

Key declaration: "We believe it is the inalienable right of
the Indian people to have freedom"
```

---

## 🔷 GANDHI'S STRATEGY — WHY SALT?

### Gandhi's Letter to the Viceroy:
```
Date: March 2, 1930
Recipient: Lord Irwin (Viceroy of India)
Content: Gandhi gave ADVANCE WARNING of his plan
→ "I intend to break the salt law unless demands are met"
→ 11 demands listed (including reduction of land revenue, salt tax)
→ Gandhi gave the Viceroy a chance to respond

Lord Irwin's response: IGNORED Gandhi's letter

Gandhi's reaction: "I will launch Civil Disobedience"
```

### Why Salt? Gandhi's Brilliance:
```
Salt was the PERFECT symbol because:

1. UNIVERSAL: Every Indian — rich, poor, Hindu, Muslim,
   man, woman, farmer, trader — ALL use salt daily

2. BASIC NECESSITY: You cannot live without salt
   (Unlike sugar or cloth — salt is survival)

3. BRITISH MONOPOLY: British government had TOTAL control
   over salt production and sale

4. SALT TAX: Indians had to pay tax even on this basic necessity
   → Poor Indians suffered most from salt tax

5. ILLEGAL TO MAKE YOUR OWN: Indians couldn't collect salt
   from the sea — even though India has a vast coastline

Gandhi's genius: By choosing salt, he included EVERYONE in
the struggle, from the poorest peasant to the richest merchant.
```

---

## 🔷 THE DANDI MARCH — THE MOST ICONIC EVENT

### Complete Details:
```
Start date:   March 12, 1930
Start point:  Sabarmati Ashram, Ahmedabad, Gujarat
End point:    Dandi (a coastal village in Gujarat)
Distance:     241 miles (approximately 385 km)
Duration:     24 days (March 12 – April 5, 1930)
Participants: Gandhi + 78 selected volunteers (his disciples)
```

### The Route and Significance:
```
Day 1 (March 12):
  → Gandhi and 78 followers begin the march from Sabarmati
  → Each day, they walked through villages
  → Thousands joined along the way
  → Gandhi gave speeches in every village

April 5, 1930:
  → They reach Dandi on the Gujarat coast
  → Massive crowds gathered

April 6, 1930:
  → Gandhi picks up a handful of salt from the seashore
  → He MAKES salt — breaking the Salt Law
  → This act of picking up salt = Civil Disobedience begins!
  → This moment was witnessed and reported worldwide
```

### 🚨 PYQ TRAP — Exact Details:
```
Start: Sabarmati Ashram, Ahmedabad (NOT Sabarmati village)
End: DANDI (Gujarat coast) — NOT Champaran, NOT Karachi
Date of salt-making: APRIL 6, 1930 (NOT March 12 which was start of march)
Distance: 241 miles (sometimes given as ~388 km)
Number of initial volunteers: 78
Duration of march: 24 days
```

### Impact of the Salt March:
```
Immediate:
→ Civil Disobedience Movement launched nationwide
→ People everywhere began making salt illegally
→ Massive boycott of British goods
→ Police began arresting thousands

International:
→ Global media coverage — TIME magazine cover
→ World saw Britain's repression of peaceful protesters
→ International sympathy for India grew

In India:
→ Women participated massively for the first time
→ Merchants, lawyers, students all joined
→ British faced economic damage from boycott
```

---

## 🔷 KEY EVENTS DURING CDM

### Arrests and Repression:
```
April 1930: Jawaharlal Nehru arrested
May 4-5, 1930: Gandhi arrested (before Dharasana)
May 21, 1930: Dharasana Salt Works Raid
  → Sarojini Naidu led 2,500 volunteers to raid salt works
  → Police brutally beat the non-violent volunteers
  → Webb Miller (American journalist) reported it globally
  → This report turned world opinion against Britain

June 1930: Congress declared illegal organization
December 1930: Round Table Conference 1 (Gandhi NOT present — in jail)
```

### Spread Beyond Salt:
```
→ Forest laws broken (tribals cut forest wood)
→ No-revenue campaigns in various regions
→ Boycott of foreign cloth intensified
→ Picketing of liquor shops
→ Women's participation was historic (first large-scale)
```

---

## 🔷 CIVIL DISOBEDIENCE TIMELINE

```
CIVIL DISOBEDIENCE MOVEMENT — KEY DATES
══════════════════════════════════════════════════

December 31, 1929
   │  Lahore Session — Purna Swaraj declared
   │  January 26, 1930 = first "Independence Day" celebration
   │
March 2, 1930
   │  Gandhi writes to Lord Irwin — advance warning
   │
March 12, 1930
   │  DANDI MARCH BEGINS — Sabarmati Ashram
   │  Gandhi + 78 volunteers
   │
April 5, 1930
   │  Gandhi reaches Dandi (Gujarat coast)
   │
April 6, 1930 ← CIVIL DISOBEDIENCE OFFICIALLY LAUNCHES
   │  Gandhi makes salt at Dandi — breaks salt law
   │
April 1930
   │  Jawaharlal Nehru arrested
   │  Mass arrests across India
   │
May 4-5, 1930
   │  Gandhi arrested
   │
May 21, 1930
   │  Dharasana Salt Works Raid (Sarojini Naidu leads)
   │
1930 (Nov-Dec)
   │  Round Table Conference 1 — Gandhi ABSENT (in jail)
   │
January 26, 1931
   │  Gandhi released from jail
   │
March 5, 1931
   │  GANDHI-IRWIN PACT signed ← MOVEMENT SUSPENDED
   │
September 1931
   │  Round Table Conference 2 — Gandhi PRESENT
   │  RTC 2 fails (no agreement)
   │
January 1932
   │  Gandhi re-arrested — CDM re-launched (Phase 2)
   │
1932 (September)
   │  Poona Pact (Gandhi + Ambedkar)
   │
1934
   │  CDM formally withdrawn
```

---

## 🔷 GANDHI-IRWIN PACT — MARCH 5, 1931

### What Was the Pact?
```
Date: March 5, 1931
Parties: Gandhi (representing INC) + Lord Irwin (Viceroy)
Also called: "Delhi Pact"
```

### Terms of the Pact:
```
BRITISH AGREED TO:
→ Release all political prisoners (except those convicted of violence)
→ Return confiscated properties of satyagrahis
→ Allow collection of salt from coastal areas for personal use
→ Allow peaceful picketing of foreign goods

GANDHI/CONGRESS AGREED TO:
→ SUSPEND Civil Disobedience Movement
→ Attend Round Table Conference 2 in London
→ Cooperate with British constitutional process
```

### 🚨 PYQ TRAP #5:
> Pact only SUSPENDED the movement — NOT ended.
> Gandhi attended RTC 2 (September 1931) but it FAILED.
> CDM was RE-LAUNCHED in January 1932.
> CDM was formally WITHDRAWN only in 1934.

### Reactions to Pact:
```
Subhas Chandra Bose: Called it a "sell-out" — no Poorna Swaraj achieved
Bhagat Singh: Being hanged (March 23, 1931) — Gandhi's pact did not save him
              Controversy: Gandhi could have demanded Bhagat Singh's release but did not
```

---

## 🔷 KEY PERSONALITIES — MASTER TABLE

| Person | Role |
|--------|------|
| **Mahatma Gandhi** | Led CDM, Dandi March, Gandhi-Irwin Pact |
| **Lord Irwin** | Viceroy; signed Gandhi-Irwin Pact |
| **Jawaharlal Nehru** | Presided over Lahore Session (1929); arrested April 1930 |
| **Lala Lajpat Rai** | Died after Simon Commission lathi charge (1928) |
| **Sarojini Naidu** | Led Dharasana Salt Works Raid (May 1930) — "Nightingale of India" |
| **Subhas Chandra Bose** | Opposed Lahore session dominion status debate; critiqued Gandhi-Irwin Pact |
| **Motilal Nehru** | Authored Nehru Report (1928) |
| **Bhagat Singh** | Killed Saunders (to avenge Lala Lajpat Rai); hanged March 23, 1931 |

---

## 🔷 BIHAR CONNECTION — CDM

```
Bihar's role in Civil Disobedience Movement:
→ Salt marches organized in Bihar by Rajendra Prasad
→ Bihar farmers participated in no-revenue campaigns
→ Champaran and Saran districts saw strong participation
→ Rajendra Prasad was arrested during CDM
→ Bihar Vidyapeeth students boycotted studies to join CDM
```

---

## 🔷 MEMORY TRICKS

```
"SIMON → NEHRU REPORT → LAHORE → DANDI → CDM"
(The logical 5-step build-up to CDM)

"SABARMATI to DANDI = 241 miles in 24 days with 78 people"
(Numbers: 241, 24, 78 — learn all three!)

"April 6 = Salt Day" (Gandhi made salt on April 6, 1930)

"GANDHI-IRWIN PACT = March 5, 1931 = Delhi Pact"

"RTC Attendance:
  RTC 1 → Gandhi ABSENT (in jail)
  RTC 2 → Gandhi PRESENT (pact allowed release)
  RTC 3 → Gandhi ABSENT (back in jail)"

"DHARASANA = SAROJINI NAIDU" (her most famous act)

"LALA died in 1928 → BHAGAT SINGH avenged 1928 →
 BHAGAT hanged 1931 → DURING Gandhi-Irwin Pact negotiations"
```

---

## 🔷 COMPARISON: NCM vs CDM vs QUIT INDIA

| Feature | NCM (1920) | CDM (1930) | Quit India (1942) |
|---------|-----------|-----------|------------------|
| Key method | Boycott | Break laws (salt) | "Do or Die" rebellion |
| Trigger | JWB + Rowlatt | Simon + Lahore | WWII context |
| Ended by | Chauri Chaura | Gandhi-Irwin Pact | 1947 independence |
| Women's role | Limited | Large (first time) | Very large |
| International coverage | Limited | Massive (Dandi) | Significant |
| Gandhi arrested | 1922 | 1930 | 1942 |
| Phase 2? | No | Yes (relaunched 1932) | No |

---

# PART 3: PRACTICE QUESTIONS

## 📝 COMPUTER SCIENCE — 25 MCQs
### Topics: File Streams, File Modes, ios::trunc, Operations, Binary/Text

---

**Q1.** Which header file is required for file handling in C++?
(A) `<iostream>`
(B) `<fstream>`
(C) `<filestream>`
(D) More than one of the above
(E) None of the above

---

**Q2.** Which class is used to READ data from a file in C++?
(A) `ofstream`
(B) `fstream`
(C) `ifstream`
(D) More than one of the above
(E) None of the above

---

**Q3.** What does `ios::trunc` do when opening a file?
(A) Opens file at the end (truncates nothing)
(B) Appends new content after existing content
(C) Deletes all existing content in the file
(D) More than one of the above
(E) None of the above

---

**Q4.** What is the default mode when opening a file with `ofstream`?
(A) `ios::in`
(B) `ios::app`
(C) `ios::out | ios::trunc`
(D) More than one of the above
(E) None of the above

---

**Q5.** Which file mode should be used to ADD content at the END of an existing file without deleting old content?
(A) `ios::out`
(B) `ios::trunc`
(C) `ios::app`
(D) More than one of the above
(E) None of the above

---

**Q6.** What is the keyboard shortcut to Compile and Run a program in Turbo C++?
(A) `Alt + F9`
(B) `Ctrl + F9`
(C) `Ctrl + F5`
(D) More than one of the above
(E) None of the above

---

**Q7.** Which of the following is TRUE about `eof()` in C++?
(A) It returns true before reading the last element
(B) It returns true AFTER the file pointer has passed the end
(C) It is called before opening the file
(D) More than one of the above
(E) None of the above

---

**Q8.** To open a file for BOTH reading and writing, which class should be used?
(A) `ifstream`
(B) `ofstream`
(C) `fstream`
(D) More than one of the above
(E) None of the above

---

**Q9.** Which mode combination correctly opens a file for writing in binary format?
(A) `ios::in | ios::binary`
(B) `ios::out | ios::binary`
(C) `ios::app | ios::text`
(D) More than one of the above
(E) None of the above

---

**Q10.** Why must `close()` be called after file operations?
(A) To open the next file
(B) To flush buffered data to disk and release file resources
(C) Because the file becomes read-only after operations
(D) More than one of the above
(E) None of the above

---

**Q11.** In a binary file, how is the integer `65` stored?
(A) As the characters '6' and '5' (two bytes)
(B) As its raw binary representation (4 bytes for int)
(C) As the character 'A' (ASCII 65)
(D) More than one of the above
(E) None of the above

---

**Q12.** Which function is used to read binary data from a file?
(A) `get()`
(B) `getline()`
(C) `read()`
(D) More than one of the above
(E) None of the above

---

**Q13.** What happens if you open a non-existent file with `ifstream` without checking?
(A) File is created automatically
(B) Compile error
(C) File stream fails (no compile error, but stream state is bad)
(D) More than one of the above
(E) None of the above

---

**Q14.** `ios::ate` mode means:
(A) File is opened and pointer placed at END of file
(B) File content is deleted (truncated)
(C) File is opened in append mode
(D) More than one of the above
(E) None of the above

---

**Q15.** Which of the following is the correct way to check if a file opened successfully?
(A) `if (file.open()) { ... }`
(B) `if (!file) { ... }`
(C) `if (file.fail()) { ... }`
(D) More than one of the above
(E) None of the above

---

**Q16.** What is the difference between `ios::app` and `ios::ate`?
(A) No difference — both append to end
(B) `ios::app` always writes at end; `ios::ate` moves pointer to end but allows seeking
(C) `ios::ate` deletes content; `ios::app` does not
(D) More than one of the above
(E) None of the above

---

**Q17.** Which of the following reads an entire line from a file (including spaces)?
(A) `fin >> line;`
(B) `getline(fin, line);`
(C) `fin.get(line);`
(D) More than one of the above
(E) None of the above

---

**Q18.** What is Alt + F9 in Turbo C++?
(A) Compile and Run
(B) Compile ONLY (without running)
(C) Run without compiling
(D) More than one of the above
(E) None of the above

---

**Q19.** To open a binary file for reading, which mode is correct?
(A) `ios::out | ios::binary`
(B) `ios::in | ios::binary`
(C) `ios::binary` alone
(D) More than one of the above
(E) None of the above

---

**Q20.** In which of the following does the file stream `fstream` differ from `ifstream` and `ofstream`?
(A) `fstream` can both read and write; the others are specialized
(B) `fstream` does not support binary mode
(C) `fstream` automatically closes files
(D) More than one of the above
(E) None of the above

---

**Q21.** Which of the following classes is used to WRITE data TO a file?
(A) `ifstream`
(B) `ofstream`
(C) `iostream`
(D) More than one of the above
(E) None of the above

---

**Q22.** Which of the following is TRUE about text files vs binary files?
(A) Text files store numbers in ASCII; binary files store raw binary
(B) Binary files are always larger than text files
(C) Text files cannot store numbers
(D) More than one of the above
(E) None of the above

---

**Q23.** What does `fout.write((char*)&n, sizeof(n))` do?
(A) Writes n as a text string
(B) Writes the raw bytes of variable n to the file
(C) Writes the address of n to the file
(D) More than one of the above
(E) None of the above

---

**Q24.** If a file already has content and you open it with `ios::out` (default ofstream), what happens?
(A) New content is appended at the end
(B) Existing content is preserved; file pointer goes to beginning
(C) Existing content is DELETED (truncated) — new content replaces it
(D) More than one of the above
(E) None of the above

---

**Q25.** Which of the following is the parent/base class of `ifstream`, `ofstream`, and `fstream`?
(A) `iostream`
(B) `filebase`
(C) `ios`
(D) More than one of the above
(E) None of the above

---
---

## 📝 GENERAL STUDIES — 25 MCQs
### Civil Disobedience Movement 1930

---

**Q26.** The Civil Disobedience Movement was formally launched on:
(A) March 12, 1930 (start of Dandi March)
(B) April 6, 1930 (Gandhi made salt at Dandi)
(C) December 31, 1929 (Purna Swaraj declaration)
(D) More than one of the above
(E) None of the above

---

**Q27.** The Dandi March began from which location?
(A) Wardha Ashram, Maharashtra
(B) Sabarmati Ashram, Ahmedabad, Gujarat
(C) Sevagram Ashram, Nagpur
(D) More than one of the above
(E) None of the above

---

**Q28.** How many initial volunteers accompanied Gandhi on the Dandi March?
(A) 78
(B) 100
(C) 241
(D) More than one of the above
(E) None of the above

---

**Q29.** The Gandhi-Irwin Pact was signed on:
(A) April 6, 1930
(B) March 5, 1931
(C) January 26, 1931
(D) More than one of the above
(E) None of the above

---

**Q30.** The Lahore Session of INC (December 1929) was presided over by:
(A) Mahatma Gandhi
(B) Motilal Nehru
(C) Jawaharlal Nehru
(D) More than one of the above
(E) None of the above

---

**Q31.** The Simon Commission was opposed because:
(A) It recommended partition of India
(B) It had no Indian members — all 7 members were British
(C) It proposed heavy taxes on Indian farmers
(D) More than one of the above
(E) None of the above

---

**Q32.** Lala Lajpat Rai died due to injuries sustained during protests against:
(A) Rowlatt Act
(B) Simon Commission's visit to Lahore
(C) Salt Tax
(D) More than one of the above
(E) None of the above

---

**Q33.** Who led the raid on Dharasana Salt Works on May 21, 1930 after Gandhi's arrest?
(A) Kasturba Gandhi
(B) Aruna Asaf Ali
(C) Sarojini Naidu
(D) More than one of the above
(E) None of the above

---

**Q34.** The distance covered during the Dandi March was approximately:
(A) 100 miles
(B) 200 miles
(C) 241 miles
(D) More than one of the above
(E) None of the above

---

**Q35.** Purna Swaraj (Complete Independence) was declared at which Congress session?
(A) Nagpur Session, 1920
(B) Calcutta Session, 1928
(C) Lahore Session, December 1929
(D) More than one of the above
(E) None of the above

---

**Q36.** Gandhi gave ADVANCE WARNING to which Viceroy before starting the Civil Disobedience Movement?
(A) Lord Curzon
(B) Lord Irwin
(C) Lord Chelmsford
(D) More than one of the above
(E) None of the above

---

**Q37.** The Nehru Report (1928) was primarily authored under the chairmanship of:
(A) Jawaharlal Nehru
(B) Motilal Nehru
(C) Gandhi
(D) More than one of the above
(E) None of the above

---

**Q38.** January 26, 1930 was significant because:
(A) India got independence on this day
(B) The first "Independence Day" was celebrated after Lahore Purna Swaraj resolution
(C) Gandhi launched the Dandi March
(D) More than one of the above
(E) None of the above

---

**Q39.** Which of the following is TRUE about the Gandhi-Irwin Pact?
(A) It permanently ended the Civil Disobedience Movement
(B) It SUSPENDED CDM; Gandhi attended RTC 2; CDM was later relaunched
(C) Bhagat Singh was released as part of the pact
(D) More than one of the above
(E) None of the above

---

**Q40.** Bhagat Singh, Rajguru and Sukhdev were hanged on:
(A) March 23, 1930
(B) March 23, 1931
(C) April 6, 1931
(D) More than one of the above
(E) None of the above

---

**Q41.** Which of the following CORRECTLY describes why Gandhi chose salt as the symbol of Civil Disobedience?
(A) Salt was the most expensive commodity in India
(B) Salt was a universal necessity under British monopoly, taxed even on the poorest
(C) Salt was unique to coastal India only
(D) More than one of the above
(E) None of the above

---

**Q42.** Arrange in CORRECT CHRONOLOGICAL ORDER:
1. Gandhi-Irwin Pact
2. Dandi March begins
3. Gandhi makes salt at Dandi
4. Lahore Session — Purna Swaraj

(A) 4 → 2 → 3 → 1
(B) 2 → 4 → 3 → 1
(C) 4 → 3 → 2 → 1
(D) More than one of the above
(E) None of the above

---

**Q43.** At which Round Table Conference did Gandhi participate?
(A) RTC 1 (1930)
(B) RTC 2 (1931)
(C) RTC 3 (1932)
(D) More than one of the above
(E) None of the above

---

**Q44.** The "Simon Go Back" slogan was raised during protests against:
(A) Simon Commission (1927–28)
(B) Salt March (1930)
(C) Rowlatt Act (1919)
(D) More than one of the above
(E) None of the above

---

**Q45.** Which of the following statements about the Nehru Report (1928) is CORRECT?
(A) It demanded Purna Swaraj (complete independence)
(B) It demanded Dominion Status for India
(C) It was authored by Jawaharlal Nehru
(D) More than one of the above
(E) None of the above

---

**Q46.** Sarojini Naidu's title "Nightingale of India" was given because of her work as a:
(A) Singer
(B) Poet
(C) Dancer
(D) More than one of the above
(E) None of the above

---

**Q47.** MATCH THE FOLLOWING:
```
Event                              Year
1. Simon Commission formed         A. 1930 (March 12)
2. Dandi March begins              B. 1931 (March 5)
3. Gandhi-Irwin Pact               C. 1927
4. Purna Swaraj declared           D. 1929 (December)
```
(A) 1-C, 2-A, 3-B, 4-D
(B) 1-A, 2-C, 3-D, 4-B
(C) 1-D, 2-A, 3-B, 4-C
(D) More than one of the above
(E) None of the above

---

**Q48.** Which American journalist's report on the Dharasana Salt Works raid created international outrage?
(A) Ernest Hemingway
(B) Webb Miller
(C) Mark Twain
(D) More than one of the above
(E) None of the above

---

**Q49.** The Civil Disobedience Movement was formally WITHDRAWN in:
(A) 1931 (after Gandhi-Irwin Pact)
(B) 1932
(C) 1934
(D) More than one of the above
(E) None of the above

---

**Q50.** Which of the following is CORRECT about the Dandi March?
(A) It started on April 6 and ended on March 12
(B) It started on March 12, 1930 and Gandhi made salt on April 6, 1930
(C) Gandhi was accompanied by 500 volunteers from the start
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
| 1 | (B) | `<fstream>` contains all file stream classes |
| 2 | (C) | `ifstream` — i = input = read from file |
| 3 | (C) | ios::trunc = truncate = delete all existing content |
| 4 | (C) | Default for ofstream = ios::out | ios::trunc |
| 5 | (C) | ios::app = append = add at end, preserve old content |
| 6 | (B) | Ctrl + F9 = Compile and Run in Turbo C++ |
| 7 | (B) | eof() returns true after file pointer passes the end |
| 8 | (C) | fstream = both read AND write |
| 9 | (B) | ios::out | ios::binary for writing binary |
| 10 | (B) | Flushes buffer to disk + releases file resources |
| 11 | (B) | Binary file: raw binary representation of the integer |
| 12 | (C) | read() function for binary file reading |
| 13 | (C) | Stream state becomes bad — no compile error |
| 14 | (A) | ios::ate = "at end" — moves pointer to end of file |
| 15 | (D) | Both `if (!file)` and `if (file.fail())` work |
| 16 | (B) | ios::app always writes at end; ios::ate allows seeking |
| 17 | (B) | getline(fin, line) reads entire line including spaces |
| 18 | (B) | Alt + F9 = Compile ONLY (not run) |
| 19 | (B) | ios::in | ios::binary for reading binary |
| 20 | (A) | fstream can both read and write |
| 21 | (B) | ofstream — o = output = write to file |
| 22 | (A) | Text = ASCII representation; binary = raw binary |
| 23 | (B) | Writes raw bytes of variable n (binary write) |
| 24 | (C) | Default ofstream = ios::out | ios::trunc = deletes content |
| 25 | (C) | ios is the base class of all stream classes |

---

### GS Answers (Q26–Q50):

| Q | Answer | Key Reason |
|---|--------|-----------|
| 26 | (B) | April 6, 1930 = Gandhi made salt = CDM officially launched |
| 27 | (B) | Sabarmati Ashram, Ahmedabad, Gujarat |
| 28 | (A) | 78 volunteers accompanied Gandhi |
| 29 | (B) | March 5, 1931 = Gandhi-Irwin Pact = Delhi Pact |
| 30 | (C) | Jawaharlal Nehru presided over Lahore Session 1929 |
| 31 | (B) | All 7 members were British — no Indian representation |
| 32 | (B) | Lathi charge during Simon Commission protest in Lahore |
| 33 | (C) | Sarojini Naidu led Dharasana raid |
| 34 | (C) | 241 miles (approximately 385 km) |
| 35 | (C) | Lahore Session, December 1929 |
| 36 | (B) | Lord Irwin — Viceroy who received Gandhi's March 2 letter |
| 37 | (B) | Motilal Nehru chaired the committee |
| 38 | (B) | January 26, 1930 = first "Independence Day" after Purna Swaraj |
| 39 | (B) | Pact suspended CDM; CDM was relaunched in 1932 |
| 40 | (B) | March 23, 1931 — during Gandhi-Irwin Pact period |
| 41 | (B) | Universal necessity, British monopoly, taxed the poorest |
| 42 | (A) | Lahore(Dec 1929) → Dandi starts(Mar 12) → Salt made(Apr 6) → Pact(Mar 1931) |
| 43 | (B) | Gandhi attended only RTC 2 (September 1931) |
| 44 | (A) | Simon Commission — all British members |
| 45 | (B) | Nehru Report demanded Dominion Status (NOT Purna Swaraj) |
| 46 | (B) | Sarojini Naidu was a poet — "Nightingale of India" |
| 47 | (A) | Simon-1927, Dandi-Mar 12 1930, Pact-Mar 5 1931, Purna Swaraj-Dec 1929 |
| 48 | (B) | Webb Miller — American journalist who reported Dharasana |
| 49 | (C) | CDM formally withdrawn in 1934 |
| 50 | (B) | March 12 = start; April 6 = salt made at Dandi; 78 volunteers |

---
---

# 🔁 DAY 11 — CRISP REVISION NOTES

## ⚡ RAPID FIRE — C++ File Handling

### Stream Classes — One-Liners:
1. **ifstream** = INPUT from file = READ | **ofstream** = OUTPUT to file = WRITE
2. **fstream** = BOTH read and write (must specify mode manually)
3. **Header**: `#include <fstream>` — ALL three classes included
4. **Base class**: `ios` is parent of all stream classes

### File Modes Cheat Sheet:
```
ios::in     → READ only
ios::out    → WRITE only
ios::app    → ADD AT END (old content safe)    ← "app" = append = ADD
ios::trunc  → DELETE old content (start fresh) ← "trunc" = truncate = CUT
ios::binary → binary mode (not text)
ios::ate    → open and go to END (can seek back)

DEFAULT for ofstream = ios::out | ios::trunc ← MAJOR TRAP!
(Simply opening with ofstream DESTROYS existing file content!)
```

### Critical Traps:
1. **ofstream default** = `ios::out | ios::trunc` → old content DELETED automatically
2. **eof() trap**: eof() becomes true AFTER failed read, not before → use `while(fin >> x)` not `while(!fin.eof())`
3. **ios::trunc** = truncate = DELETE | **ios::app** = append = ADD AT END (know both!)
4. **`close()`** is essential — flushes buffer, releases OS file handle
5. **Binary `write()`**: `fout.write((char*)&n, sizeof(n))` — remember the cast to `char*`

### Turbo C++ Shortcuts:
```
Ctrl + F9  → Compile AND Run  ← most tested
Alt  + F9  → Compile ONLY (not run)
Alt  + F5  → View output window
```

---

## ⚡ RAPID FIRE — Civil Disobedience Movement

### Critical Dates:
```
1927       → Simon Commission formed (all-British, 7 members)
Oct 1928   → Lala Lajpat Rai beaten in Lahore (Simon protests)
Nov 1928   → Lala Lajpat Rai dies → "Punjab Kesari"
Dec 1928   → Bhagat Singh kills Saunders (to avenge Lala)
1928       → Nehru Report (Motilal Nehru — demands DOMINION STATUS)
Dec 1929   → Lahore Session (JN presides) — PURNA SWARAJ declared
Jan 26 1930→ First "Independence Day" celebrated (hence Republic Day)
Mar 2 1930 → Gandhi writes to Lord Irwin (11 demands, advance warning)
Mar 12 1930→ DANDI MARCH BEGINS — Sabarmati Ashram, 78 volunteers
Apr 6 1930 → Gandhi MAKES SALT at Dandi — CDM officially LAUNCHED
May 1930   → Gandhi arrested | Sarojini Naidu leads Dharasana raid
Dec 1930   → RTC 1 — Gandhi ABSENT (in jail)
Mar 5 1931 → GANDHI-IRWIN PACT — CDM SUSPENDED ("Delhi Pact")
Mar 23 1931→ Bhagat Singh, Rajguru, Sukhdev HANGED
Sep 1931   → RTC 2 — Gandhi PRESENT (pact allowed it); RTC fails
Jan 1932   → CDM RE-LAUNCHED; Gandhi re-arrested
1932       → Poona Pact (Gandhi + Ambedkar)
1934       → CDM formally WITHDRAWN
```

### Numbers to Remember:
```
Dandi March: 241 miles | 24 days | 78 volunteers | April 6 = salt made
Simon Commission: 7 members — all British
Lala died: November 17, 1928
Bhagat Singh hanged: March 23, 1931
RTC Gandhi attended: ONLY RTC 2 (1931)
```

### Common Exam Traps:
1. CDM LAUNCHED = **April 6** (salt made) NOT March 12 (march began)
2. Dandi March starts at **Sabarmati Ashram** (NOT Sabarmati village, NOT Wardha)
3. Nehru Report = **Motilal** Nehru (NOT Jawaharlal Nehru)
4. Nehru Report demanded **Dominion Status** (NOT Purna Swaraj)
5. Gandhi-Irwin Pact **suspended** CDM — CDM was relaunched 1932, withdrawn 1934
6. Gandhi attended **only RTC 2** — absent from RTC 1 and RTC 3
7. **Webb Miller** = American journalist who reported Dharasana (international impact)

---

## 🎯 TONIGHT'S 5-BULLET SUMMARY (Write in your notebook):
1. `ios::trunc` = DELETE old file content (default in ofstream); `ios::app` = add at END
2. `Ctrl+F9` = Compile + Run in Turbo C++; `Alt+F9` = Compile ONLY
3. Dandi March: March 12, 1930 (start) → April 6, 1930 (salt made); 78 volunteers; 241 miles
4. Gandhi-Irwin Pact (March 5, 1931) only SUSPENDED CDM; relaunched 1932; withdrawn 1934
5. Nehru Report (1928) by MOTILAL demanded DOMINION STATUS, NOT Purna Swaraj

---

*Next: Day 12 — C++ Functions (Types, Default Arguments, Inline, Recursion) + Quit India Movement 1942*
