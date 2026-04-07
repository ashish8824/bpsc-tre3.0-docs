# 📅 DAY 11 — BPSC TRE 4.0 COMPLETE STUDY MATERIAL
### CS Topic: File Handling in C++ | GS Topic: Civil Disobedience Movement & Salt March (1930)
**Target: TOP RANK | Prepared for Prag | Phase 1 — Week 2**

---

> **⚡ TOPPER MINDSET FOR TODAY:**
> File Handling is a **DIRECT PYQ TOPIC** — file modes (`ios::trunc`, `ios::app`) appeared
> in TRE 1.0 and TRE 2.0 with exact option-matching questions.
> Civil Disobedience / Dandi March = **MOST HIGH-VALUE Modern History topic** in Bihar GS.
> Learn both cold today → guaranteed 4–6 marks in the real exam.

---

# ═══════════════════════════════════════════
# PART A — COMPUTER SCIENCE
## File Handling in C++ — Complete Concept Guide
# ═══════════════════════════════════════════

---

## 🔷 1. WHY FILE HANDLING?

When a program runs, data is stored in **RAM (temporary)**. When the program ends, all data is lost.

**File Handling** allows a program to store data **permanently on disk** (hard drive/SSD) so it can be read later.

```
WITHOUT FILE HANDLING:          WITH FILE HANDLING:
Program runs                    Program runs
↓                               ↓
Data in RAM ──→ Program ends    Data in RAM ──→ Written to FILE on disk
↓                               ↓
Data LOST ❌                    Data SAVED PERMANENTLY ✅
                                ↓
                                Next program run → READ from file
```

---

## 🔷 2. THE THREE STREAM CLASSES

C++ uses **stream classes** from the `<fstream>` header for file I/O:

```
          <fstream> header
               │
    ┌──────────┼──────────┐
    ▼          ▼          ▼
ifstream   ofstream   fstream
(Input     (Output    (Both Input
 only)      only)      AND Output)

ifstream = "input file stream"  → READ from file
ofstream = "output file stream" → WRITE to file
fstream  = "file stream"        → READ + WRITE both
```

### Declaration and Opening:
```cpp
#include <fstream>
using namespace std;

// Method 1: Declare + open in one step
ifstream fin("input.txt");      // open for reading
ofstream fout("output.txt");    // open for writing
fstream  fio("data.txt");       // open for both

// Method 2: Declare first, then open separately
ifstream fin;
fin.open("input.txt");

// Closing a file
fin.close();
fout.close();
```

---

## 🔷 3. FILE MODES — THE HEART OF BPSC PYQs

File modes are **flags** that tell C++ HOW to open a file. They are defined in the `ios` class.

### Complete File Mode Table:

| Mode Flag | Full Name | Meaning |
|-----------|-----------|---------|
| `ios::in` | input | Open file for **reading** |
| `ios::out` | output | Open file for **writing** (creates file if not exists) |
| `ios::app` | append | **Append** — write at END of file (existing data preserved) |
| `ios::trunc` | truncate | **Truncate** — delete all existing content, start fresh (zero length) |
| `ios::binary` | binary | Open in **binary mode** (not text mode) |
| `ios::ate` | at end | Open and move pointer to **end** of file immediately |

---

### 🔴 MOST IMPORTANT — `ios::trunc` vs `ios::app`

This distinction is **the #1 BPSC PYQ topic** in file handling:

```
ios::app  (APPEND)                    ios::trunc (TRUNCATE)
─────────────────────────             ──────────────────────────
File BEFORE opening:                  File BEFORE opening:
Hello World                           Hello World
This is Line 2                        This is Line 2

After opening and writing "NEW":      After opening and writing "NEW":
Hello World                           NEW
This is Line 2
NEW

→ PRESERVES old data                  → DESTROYS old data
→ Adds new content at END             → File becomes ZERO LENGTH first
                                      → Then writes new content
```

> **🎯 PYQ GOLD FACT:** `ios::trunc` truncates the file to **zero length** (empties it completely) when the file is opened. `ios::out` **also** truncates by default if the file exists (same as `ios::out | ios::trunc`).

---

## 🔷 4. DEFAULT FILE MODES

```cpp
// ifstream default mode:
ifstream fin("file.txt");
// Equivalent to: fin.open("file.txt", ios::in)

// ofstream default mode:
ofstream fout("file.txt");
// Equivalent to: fout.open("file.txt", ios::out | ios::trunc)
// ⚠️ TRAP: ofstream TRUNCATES by default!

// fstream default mode:
fstream fio("file.txt");
// Equivalent to: fio.open("file.txt", ios::in | ios::out)
```

> **⚠️ CRITICAL TRAP:** When you open a file with `ofstream` (or `ios::out`), it **automatically truncates** the existing content! If you want to preserve content, you MUST use `ios::app`.

---

## 🔷 5. COMBINING FILE MODES WITH `|` OPERATOR

Modes can be **combined using the bitwise OR operator `|`**:

```cpp
// Open for both reading AND writing:
fstream f("data.txt", ios::in | ios::out);

// Open for writing in binary mode:
ofstream f("data.bin", ios::out | ios::binary);

// Open for appending in binary mode:
ofstream f("log.bin", ios::app | ios::binary);

// Open for reading + writing + append:
fstream f("data.txt", ios::in | ios::out | ios::app);

// Open for reading and KEEP existing content (no truncation):
fstream f("data.txt", ios::in | ios::out);
// vs
fstream f("data.txt", ios::in | ios::out | ios::trunc); // EMPTIES file first
```

> **🎯 PYQ FACT:** The `|` operator (bitwise OR) is used to combine file modes. This is a direct answer choice in BPSC TRE questions.

---

## 🔷 6. READING AND WRITING OPERATIONS

### Reading from a file:
```cpp
ifstream fin("marks.txt");
int x;
string name;

fin >> x;        // reads one integer (stops at whitespace)
fin >> name;     // reads one word
getline(fin, name);  // reads entire line including spaces

fin.close();
```

### Writing to a file:
```cpp
ofstream fout("result.txt");

fout << "Prag scored: " << 95 << endl;
fout << "Subject: Computer Science" << endl;

fout.close();
```

### Checking End of File:
```cpp
ifstream fin("data.txt");
int val;

while (!fin.eof()) {    // eof() = end of file reached?
    fin >> val;
    cout << val << " ";
}
fin.close();
```

---

## 🔷 7. FILE OPEN AND CLOSE — GOOD PRACTICES

```cpp
ifstream fin;
fin.open("data.txt");

// Always check if file opened successfully:
if (!fin) {
    cout << "Error: File could not be opened!" << endl;
    return 1;
}
// OR:
if (!fin.is_open()) {
    cout << "File not found!" << endl;
}

// Process file...

fin.close();  // Always close the file when done!
```

> **🎯 PYQ FACT:** `is_open()` returns `true` if the file was opened successfully, `false` otherwise.

---

## 🔷 8. BINARY FILE OPERATIONS

Binary mode stores data as **raw bytes** (not human-readable text):

```cpp
// Writing binary data:
ofstream fout("student.dat", ios::binary);
int roll = 101;
fout.write((char*)&roll, sizeof(roll));
fout.close();

// Reading binary data:
ifstream fin("student.dat", ios::binary);
int roll;
fin.read((char*)&roll, sizeof(roll));
cout << roll;  // 101
fin.close();
```

```
TEXT MODE vs BINARY MODE:
─────────────────────────────────────────────
Text:   Stores 65 as characters '6','5' + '\n' converted to '\r\n' on Windows
Binary: Stores 65 as binary 01000001 (exact byte representation)

Binary is FASTER and more COMPACT for large data
Text is HUMAN-READABLE
```

---

## 🔷 9. COMPLETE FILE HANDLING EXAMPLE

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    // WRITE to file
    ofstream fout("bpsc.txt");
    fout << "BPSC TRE 4.0" << endl;
    fout << "Computer Science" << endl;
    fout.close();

    // READ from file
    ifstream fin("bpsc.txt");
    string line;
    while (getline(fin, line)) {
        cout << line << endl;
    }
    fin.close();

    // APPEND to file
    ofstream fapp("bpsc.txt", ios::app);
    fapp << "Added New Line" << endl;
    fapp.close();

    return 0;
}
/*
Output on screen:
BPSC TRE 4.0
Computer Science
*/
// After append, bpsc.txt contains:
// BPSC TRE 4.0
// Computer Science
// Added New Line
```

---

## 🔷 10. TURBO C++ SHORTCUTS — PYQ DIRECT QUESTION

| Shortcut | Action |
|----------|--------|
| **Ctrl + F9** | **Compile and Run** the program |
| Alt + F9 | Compile only |
| F9 | Make (link + compile) |
| Ctrl + F5 | User screen |
| Alt + X | Exit Turbo C++ |

> **🎯 PYQ GOLD:** `Ctrl + F9` = Compile and Run in Turbo C++. This appeared as a direct question in TRE PYQs.

---

## 🔷 11. SEEK FUNCTIONS — RANDOM FILE ACCESS

```cpp
// seekg = seek get (for reading) → moves READ pointer
// seekp = seek put (for writing) → moves WRITE pointer
// tellg = tell get → returns current READ position
// tellp = tell put → returns current WRITE position

ifstream fin("data.txt");
fin.seekg(10);         // move read pointer to byte 10
fin.seekg(5, ios::beg);  // 5 bytes from beginning
fin.seekg(-3, ios::end); // 3 bytes before end
fin.seekg(2, ios::cur);  // 2 bytes from current position

long pos = fin.tellg(); // get current position
```

---

## 🔷 12. MASTER SUMMARY TABLE

```
┌─────────────────────────────────────────────────────────────────┐
│              C++ FILE HANDLING QUICK REFERENCE                  │
├────────────────┬───────────────────────────────────────────────┤
│ Class          │ Purpose                                       │
├────────────────┼───────────────────────────────────────────────┤
│ ifstream       │ Read only                                     │
│ ofstream       │ Write only (TRUNCATES by default!)           │
│ fstream        │ Read + Write                                  │
├────────────────┼───────────────────────────────────────────────┤
│ Mode           │ Effect                                        │
├────────────────┼───────────────────────────────────────────────┤
│ ios::in        │ Open for reading                              │
│ ios::out       │ Open for writing                              │
│ ios::app       │ Append — add at END, preserves data          │
│ ios::trunc     │ Truncate — EMPTIES file to zero length       │
│ ios::binary    │ Binary mode                                   │
│ ios::ate       │ Open and go to END immediately               │
├────────────────┼───────────────────────────────────────────────┤
│ Function       │ Purpose                                       │
├────────────────┼───────────────────────────────────────────────┤
│ open()         │ Open a file                                   │
│ close()        │ Close a file                                  │
│ eof()          │ Check if end of file reached                  │
│ is_open()      │ Check if file opened successfully             │
│ read()         │ Binary read                                   │
│ write()        │ Binary write                                  │
│ seekg/seekp    │ Move file pointer (random access)             │
│ tellg/tellp    │ Get current file pointer position             │
├────────────────┼───────────────────────────────────────────────┤
│ Turbo C++      │ Ctrl+F9 = Compile and Run                    │
└────────────────┴───────────────────────────────────────────────┘
```

---

## 🔷 13. TRICKY OUTPUT PREDICTION EXAMPLES

### Example 1 — ios::trunc trap:
```cpp
// File "test.txt" contains: "Hello World"
ofstream f("test.txt");  // opens with ios::out (which includes ios::trunc)
f << "Hi";
f.close();

// What does test.txt contain NOW?
// Answer: "Hi"   (NOT "Hi World" — trunc deleted "Hello World" first!)
```

### Example 2 — ios::app:
```cpp
// File "test.txt" contains: "Hello"
ofstream f("test.txt", ios::app);
f << " World";
f.close();

// What does test.txt contain NOW?
// Answer: "Hello World"   (app PRESERVED "Hello" and added " World")
```

### Example 3 — eof() loop:
```cpp
// File contains: 10 20 30
ifstream f("nums.txt");
int n;
while(f >> n) {       // reads until EOF
    cout << n << " ";
}
// Output: 10 20 30
```

---

# ═══════════════════════════════════════════
# CS PRACTICE QUESTIONS — 25 MCQs
## File Handling in C++ | BPSC TRE Pattern
# ═══════════════════════════════════════════

> **📌 INSTRUCTIONS:** Solve ALL 25 questions FIRST. Answers are given AFTER question 25 (after the GS section). Cover the answer key with paper while solving!

---

**Q1.** Which header file must be included for file handling in C++?

(A) `<iostream>`
(B) `<stdio.h>`
(C) `<fstream>`
(D) More than one of the above is correct
(E) None of the above

---

**Q2.** Which C++ class is used ONLY for reading from a file?

(A) `ofstream`
(B) `fstream`
(C) `ifstream`
(D) More than one of the above is correct
(E) None of the above

---

**Q3.** What does `ios::trunc` do when a file is opened?

(A) Moves the file pointer to the end of the file
(B) Truncates (empties) the file to zero length before writing
(C) Appends new data at the end of the existing content
(D) More than one of the above is correct
(E) None of the above

---

**Q4.** A file named "data.txt" already contains the text: `"Old Data"`.
The following code is executed:
```cpp
ofstream f("data.txt");
f << "New";
f.close();
```
What does "data.txt" contain after execution?

(A) `"Old DataNew"`
(B) `"New"`
(C) `"NewOld Data"`
(D) More than one of the above is correct
(E) None of the above

---

**Q5.** Which file mode should be used if you want to **add** new content at the END of a file WITHOUT destroying existing content?

(A) `ios::out`
(B) `ios::trunc`
(C) `ios::app`
(D) More than one of the above is correct
(E) None of the above

---

**Q6.** What is the keyboard shortcut to **Compile and Run** a program in Turbo C++?

(A) `Alt + F9`
(B) `Ctrl + F5`
(C) `Ctrl + F9`
(D) More than one of the above is correct
(E) None of the above

---

**Q7.** Which operator is used to **combine** two or more file modes in C++?

(A) `&&` (logical AND)
(B) `+` (addition)
(C) `|` (bitwise OR)
(D) More than one of the above is correct
(E) None of the above

---

**Q8.** Which of the following correctly opens a file for **both reading and writing** without truncating it?

(A) `fstream f("data.txt", ios::in | ios::out);`
(B) `fstream f("data.txt", ios::in | ios::out | ios::trunc);`
(C) `ofstream f("data.txt", ios::in);`
(D) More than one of the above is correct
(E) None of the above

---

**Q9.** What does the `eof()` function return?

(A) The size of the file in bytes
(B) `true` when the end of the file has been reached
(C) The current position of the file pointer
(D) More than one of the above is correct
(E) None of the above

---

**Q10.** Which class is used to handle BOTH reading AND writing to the same file?

(A) `ifstream`
(B) `ofstream`
(C) `fstream`
(D) More than one of the above is correct
(E) None of the above

---

**Q11.** What is the **default mode** when a file is opened using `ofstream`?

(A) `ios::in`
(B) `ios::out | ios::app`
(C) `ios::out | ios::trunc`
(D) More than one of the above is correct
(E) None of the above

---

**Q12.** Consider: `fstream f("log.txt", ios::app | ios::binary);`
Which of the following is TRUE about this file opening?

(A) The file is opened in text mode and existing data is deleted
(B) The file is opened in binary mode and new data is appended at the end
(C) The file is opened in binary mode and existing data is truncated
(D) More than one of the above is correct
(E) None of the above

---

**Q13.** What does `is_open()` return if the file was successfully opened?

(A) `false`
(B) `0`
(C) `true`
(D) More than one of the above is correct
(E) None of the above

---

**Q14.** What is the purpose of `seekg()` in C++ file handling?

(A) To write data at a specific position in a file
(B) To move the **read** pointer to a specific position in the file
(C) To check if end of file is reached
(D) More than one of the above is correct
(E) None of the above

---

**Q15.** Which of the following file modes is used when you want to open a file in **binary mode** for writing?

(A) `ios::out`
(B) `ios::binary`
(C) `ios::out | ios::binary`
(D) More than one of the above is correct
(E) None of the above

---

**Q16.** A file "marks.txt" contains:
```
85
90
78
```
What will the following code output?
```cpp
ifstream fin("marks.txt");
int n, sum = 0;
while (fin >> n) {
    sum += n;
}
cout << sum;
fin.close();
```
(A) 85
(B) 78
(C) 253
(D) More than one of the above is correct
(E) None of the above

---

**Q17.** What is the difference between `seekg()` and `seekp()` in C++?

(A) `seekg()` is for reading position; `seekp()` is for writing position
(B) `seekg()` is used in binary files; `seekp()` is for text files
(C) They are identical functions with different names
(D) More than one of the above is correct
(E) None of the above

---

**Q18.** Which mode flag moves the file pointer to the END of the file immediately after opening?

(A) `ios::end`
(B) `ios::app`
(C) `ios::ate`
(D) More than one of the above is correct
(E) None of the above

---

**Q19.** When `getline(fin, str)` is used with a file stream, it reads:

(A) Only one word from the file
(B) An entire line including spaces, until newline or EOF
(C) Only numeric values
(D) More than one of the above is correct
(E) None of the above

---

**Q20.** Consider the following code:
```cpp
ofstream f1("test.txt");
f1 << "BPSC";
f1.close();

ofstream f2("test.txt", ios::app);
f2 << " TRE";
f2.close();
```
What does "test.txt" contain after both operations?

(A) `" TRE"`
(B) `"BPSC"`
(C) `"BPSC TRE"`
(D) More than one of the above is correct
(E) None of the above

---

**Q21.** What does the `write()` function in C++ file handling do?

(A) Writes formatted text data to a file
(B) Writes a block of raw binary data (specified number of bytes) to a file
(C) Writes only integers to a file
(D) More than one of the above is correct
(E) None of the above

---

**Q22.** Which of the following statements about `ios::app` is/are CORRECT?

(A) It opens the file and positions the write pointer at the end
(B) Existing data in the file is preserved
(C) New data is always written at the end regardless of `seekp()` calls
(D) More than one of the above is correct
(E) None of the above

---

**Q23.** The `tellg()` function in C++ file handling:

(A) Tells the total size of the file
(B) Returns the current position of the READ pointer
(C) Returns the current position of the WRITE pointer
(D) More than one of the above is correct
(E) None of the above

---

**Q24.** What will happen if you try to open a file for reading (`ifstream`) that does NOT exist?

(A) A new empty file is created automatically
(B) The file stream goes into a FAIL state (is_open() returns false)
(C) Compiler gives an error
(D) More than one of the above is correct
(E) None of the above

---

**Q25.** Which of the following is/are TRUE about file handling in C++?

(A) `ios::out` by default truncates the file (same effect as `ios::out | ios::trunc`)
(B) `fstream` requires `<fstream>` header
(C) `close()` should be called after file operations are done
(D) More than one of the above is correct
(E) None of the above

---

---

# ═══════════════════════════════════════════════
# PART B — GENERAL STUDIES
## Civil Disobedience Movement & Salt March (1930)
# ═══════════════════════════════════════════════

---

## 🔶 1. BACKGROUND — WHY 1930?

After the **suspension of the Non-Cooperation Movement (1922)** and the disappointing results of the Simon Commission, Gandhi needed a new strategy. Several events set the stage:

```
TIMELINE OF EVENTS LEADING TO CIVIL DISOBEDIENCE:

1922 → NCM suspended (Chauri Chaura)
1923 → Swaraj Party formed (C.R. Das + Motilal Nehru)
1927 → Simon Commission appointed (ALL BRITISH — no Indian member)
        → "Simon Go Back" protests; Lala Lajpat Rai lathi-charged → dies
1928 → Nehru Report (Motilal Nehru) — demands Dominion Status
1929 → Lahore Session of Congress
        → Jawaharlal Nehru becomes Congress President
        → "PURNA SWARAJ" (Complete Independence) declared on Dec 19, 1929
        → January 26, 1930 = First Independence Day celebrated
           (This is why Jan 26 was chosen as Republic Day in 1950!)
1930 → Civil Disobedience Movement launched
```

> **🎯 BPSC KEY FACT:** **Purna Swaraj** was declared at the **Lahore Session (1929)** presided by **Jawaharlal Nehru**. **January 26, 1930** was celebrated as the first Independence Day — which is why **January 26, 1950** was chosen as Republic Day.

---

## 🔶 2. THE SIMON COMMISSION — TRIGGER

| Fact | Detail |
|------|--------|
| Appointed | November 1927 by British PM Baldwin |
| Purpose | Review the Government of India Act 1919 |
| Problem | All 7 members were BRITISH — NO Indian member |
| Protests | "Simon Go Back" — boycotted by all parties |
| Lala Lajpat Rai | Led protest in Lahore; lathi-charged by Superintendent Scott; died November 1928 |
| Bhagat Singh | Avenged Lajpat Rai's death by shooting J.P. Saunders (1928) |

---

## 🔶 3. THE DANDI MARCH — SALT SATYAGRAHA

### Why SALT?

```
BRITISH SALT TAX FACTS:
─────────────────────────────────────────────────────
• British had MONOPOLY on salt production
• Indians could NOT make or sell salt without British permission
• Heavy tax on salt — poorest people most affected
• Salt used by EVERYONE — rich, poor, Hindu, Muslim, farmer, worker
• Gandhi chose salt because:
  → Universal — affects every Indian regardless of religion/caste
  → Symbolic — British control over basic necessity
  → Non-violent — making salt is not violent
  → Easy for masses to understand and participate
```

### Dandi March Details:

```
DANDI MARCH ROUTE:
Sabarmati Ashram (Ahmedabad)
         │
         │ 241 miles (388 km) on foot
         │ 24 days of walking
         │ March 12, 1930 → April 6, 1930
         │
         ▼
    Dandi (coastal village, Gujarat)
    April 6, 1930 → Gandhi picks up salt from seashore
    → Breaks the salt law → Civil Disobedience officially begins!
```

| Fact | Detail |
|------|--------|
| **Start date** | March 12, 1930 |
| **End date (reached Dandi)** | April 6, 1930 |
| **Starting point** | Sabarmati Ashram, Ahmedabad |
| **Destination** | Dandi, coastal village in Gujarat |
| **Distance** | 241 miles / 388 km |
| **Duration** | 24 days |
| **Companions** | 78 selected volunteers/followers |
| **Gandhi's age** | 61 years old |

> **🎯 BPSC DIRECT FACT:** Gandhi started the Dandi March on **March 12, 1930** from **Sabarmati Ashram** with **78 followers**, reached **Dandi** on **April 6, 1930**, and broke the salt law.

---

## 🔶 4. SPREAD OF CIVIL DISOBEDIENCE ACROSS INDIA

After Gandhi broke the salt law at Dandi, CDM spread across India:

```
REGIONAL MANIFESTATIONS:

Northwest Frontier Province (NWFP):
→ Khan Abdul Ghaffar Khan ("Frontier Gandhi") / "Badshah Khan"
→ Led the "Khudai Khidmatgar" (Servants of God) / Red Shirts movement
→ Non-violent Pashtun movement — very significant

Tamil Nadu (Vedaranyam):
→ C. Rajagopalachari (Rajaji) led salt march

Dharasana Salt Works (Gujarat):
→ May 1930 — Sarojini Naidu led march on salt depot
→ Police beat non-violent protesters with steel-tipped batons
→ American journalist Webb Miller reported this → global outrage

Bihar:
→ Rajendra Prasad led movement in Bihar
→ Massive peasant participation

Bengal / Maharashtra / UP:
→ Widespread no-tax campaigns, forest law violations, picketing of liquor shops
```

---

## 🔶 5. THE GANDHI-IRWIN PACT (1931)

```
Context:
Gandhi arrested → March 1930
Released → January 1931
↓
Negotiations between Gandhi and Lord Irwin (Viceroy)
↓
Gandhi-Irwin Pact signed: March 5, 1931
```

### Terms of the Pact:

| British Agreed To | Congress Agreed To |
|-------------------|--------------------|
| Release all political prisoners | Suspend the Civil Disobedience Movement |
| Allow Indians to make salt near sea | Participate in 2nd Round Table Conference |
| Return confiscated properties | Stop boycott of foreign cloth |
| Allow peaceful picketing | |

> **⚠️ CONTROVERSY:** Bhagat Singh, Rajguru, and Sukhdev were to be hanged on **March 23, 1931** (just 18 days after the pact). Congress could not get their sentences commuted. Subhas Bose and others criticized Gandhi for signing the pact without saving Bhagat Singh.

---

## 🔶 6. ROUND TABLE CONFERENCES

| Conference | Year | Gandhi's Participation | Key Points |
|-----------|------|------------------------|------------|
| **1st RTC** | Nov 1930 – Jan 1931 | **NOT attended** (CDM ongoing) | Muslim League, princes attended; no outcome |
| **2nd RTC** | Sep–Dec 1931 | **ATTENDED** (after Gandhi-Irwin Pact) | No agreement on communal representation |
| **3rd RTC** | Nov–Dec 1932 | **NOT attended** (re-arrested) | Minor reforms discussed; Congress absent |

> **🎯 PYQ FACT:** Gandhi attended **only the 2nd Round Table Conference** in London (1931). He represented the Indian National Congress.

---

## 🔶 7. POONA PACT (1932) — DR. AMBEDKAR & GANDHI

```
Communal Award (August 1932) by British PM Ramsay MacDonald:
→ Separate electorates for Depressed Classes (Dalits/Harijans)
→ Gandhi OPPOSED this — feared it would permanently divide Hindu society

Gandhi's response:
→ Started FAST UNTO DEATH in Yerwada Jail (September 20, 1932)

Negotiations:
→ Dr. B.R. Ambedkar (leader of Depressed Classes)
→ Agreed to negotiate

Poona Pact (September 24, 1932):
→ No separate electorates for Depressed Classes
→ BUT reserved seats increased significantly (from 71 to 147 seats)
→ Gandhi ended his fast

Gandhi's term for Dalits: "HARIJANS" (Children of God)
Ambedkar disagreed with this term
```

> **🎯 BPSC KEY FACT:** **Poona Pact** was signed on **September 24, 1932** between Gandhi and Ambedkar. Gandhi was in **Yerwada Jail** (Pune) during the fast. Ramsay MacDonald's Communal Award gave separate electorates to Dalits — which Gandhi fasted against.

---

## 🔶 8. CDM SUSPENSION AND REVIVAL

```
CDM Timeline:
March 12, 1930 → Dandi March begins
April 6, 1930 → Salt law broken; CDM begins
March 5, 1931 → Gandhi-Irwin Pact; CDM SUSPENDED (1st time)
Sep 1931 → Gandhi attends 2nd RTC in London
Dec 1931 → Returns; re-arrested
Jan 4, 1932 → Gandhi re-arrested; CDM RESUMED
1932–33 → CDM continues weakly
May 1933 → Gandhi suspends CDM (second time) for his fast
April 1934 → CDM FORMALLY WITHDRAWN
```

---

## 🔶 9. SIGNIFICANCE AND RESULTS OF CDM

### Major Achievements:

```
✅ OUTCOMES:
├── Made India's freedom struggle INTERNATIONAL news
│   (Dharasana — Webb Miller's reports went worldwide)
├── Women participated massively for first time
│   (Sarojini Naidu, Kamala Nehru, Kasturba Gandhi)
├── Government of India Act 1935 — direct result of RTC discussions
├── Salt — symbol of self-reliance and swadeshi
├── Broke psychological barrier — showed Indians could defy British law
└── Khan Abdul Ghaffar Khan proved non-violence works even among Pathans

❌ LIMITATIONS:
├── CDM did not achieve immediate independence
├── Gandhi-Irwin Pact criticized for not saving Bhagat Singh
└── 2nd RTC failed to produce agreement
```

---

## 🔶 10. KEY PERSONALITIES — CDM

| Person | Role |
|--------|------|
| **Mahatma Gandhi** | Launched CDM, Dandi March |
| **Jawaharlal Nehru** | Congress President 1929, Purna Swaraj declaration |
| **Khan Abdul Ghaffar Khan** | "Frontier Gandhi" — NWFP movement, Khudai Khidmatgar |
| **Sarojini Naidu** | Led Dharasana march after Gandhi's arrest |
| **C. Rajagopalachari** | Led Vedaranyam salt march in Tamil Nadu |
| **Subhas Chandra Bose** | Critical of Gandhi-Irwin Pact |
| **Lord Irwin** | Viceroy — signed Gandhi-Irwin Pact |
| **Ramsay MacDonald** | British PM — gave Communal Award 1932 |
| **Dr. B.R. Ambedkar** | Signed Poona Pact with Gandhi |
| **Rajendra Prasad** | Led CDM in **Bihar** |

---

## 🔶 11. COMPARISON: NCM vs CDM

| Feature | Non-Cooperation (1920–22) | Civil Disobedience (1930–34) |
|---------|--------------------------|------------------------------|
| Launch | August 1, 1920 | March 12, 1930 (Dandi March) |
| Trigger | Jallianwala + Rowlatt + Khilafat | Simon Commission + Salt Tax |
| Method | Non-cooperation, boycott | Direct law-breaking |
| Key symbol | Khadi | Salt |
| Ended by | Chauri Chaura violence | Gandhi-Irwin Pact (1931) |
| Key demand | Swaraj | Purna Swaraj (already declared) |
| Muslim unity | Strong (Khilafat link) | Weaker |
| Women | Moderate | Very large-scale |
| International coverage | Limited | Global (Webb Miller reports) |

---

## 🔶 12. KEY DATES — RAPID MEMORIZATION CHART

```
Dec 19, 1929  → Purna Swaraj declared at Lahore Session (Nehru presides)
Jan 26, 1930  → First Independence Day celebrated
Mar 12, 1930  → Dandi March begins (Sabarmati → 78 followers)
Apr 6, 1930   → Dandi reached; salt law broken; CDM officially begins
May 1930      → Dharasana salt works march (Sarojini Naidu)
              → Gandhi arrested
Mar 5, 1931   → Gandhi-Irwin Pact signed
Mar 23, 1931  → Bhagat Singh, Rajguru, Sukhdev hanged
Sep 1931      → Gandhi attends 2nd Round Table Conference (London)
Aug 1932      → Communal Award (Ramsay MacDonald)
Sep 20, 1932  → Gandhi begins fast unto death in Yerwada Jail
Sep 24, 1932  → Poona Pact (Gandhi + Ambedkar)
Apr 1934      → CDM formally withdrawn
```

---

## 🔶 13. BIHAR CONNECTION — BPSC SPECIAL

Since this is a **Bihar exam**, these Bihar-specific facts are EXAM-CRITICAL:

| Bihar Fact | Detail |
|-----------|--------|
| **Rajendra Prasad** | Led CDM in Bihar; first President of India |
| **Champaran** | Gandhi's first Satyagraha (1917) — already happened here |
| **Bihar Earthquake (1934)** | Gandhi called it "divine punishment for untouchability" — controversial |
| **Bihar's salt movement** | Peasants participated actively in CDM |
| **Jayaprakash Narayan (JP)** | Was active in Bihar politics during this era (though major role came later) |

---

# ═══════════════════════════════════════════
# GS PRACTICE QUESTIONS — 25 MCQs
## Civil Disobedience Movement | BPSC TRE Pattern
# ═══════════════════════════════════════════

> **📌 INSTRUCTIONS:** Solve ALL 25 questions FIRST. Answers appear AFTER question 50 (below). Don't peek!

---

**Q26.** The Dandi March (Salt March) was started by Mahatma Gandhi on:

(A) January 26, 1930
(B) March 12, 1930
(C) April 6, 1930
(D) More than one of the above is correct
(E) None of the above

---

**Q27.** Gandhi started the Dandi March from which place?

(A) Dandi, Gujarat
(B) Wardha Ashram
(C) Sabarmati Ashram, Ahmedabad
(D) More than one of the above is correct
(E) None of the above

---

**Q28.** How many followers accompanied Gandhi at the start of the Dandi March?

(A) 100
(B) 25
(C) 78
(D) More than one of the above is correct
(E) None of the above

---

**Q29.** "Purna Swaraj" (Complete Independence) was declared at which session of the Indian National Congress?

(A) Calcutta Session, 1928
(B) Lahore Session, 1929
(C) Nagpur Session, 1929
(D) More than one of the above is correct
(E) None of the above

---

**Q30.** Who presided over the Lahore Session of Congress (1929) where Purna Swaraj was declared?

(A) Mahatma Gandhi
(B) Subhas Chandra Bose
(C) Jawaharlal Nehru
(D) More than one of the above is correct
(E) None of the above

---

**Q31.** The Civil Disobedience Movement was officially launched when Gandhi:

(A) Declared Purna Swaraj at Lahore
(B) Picked up salt at Dandi beach, breaking the salt law on April 6, 1930
(C) Signed the Gandhi-Irwin Pact
(D) More than one of the above is correct
(E) None of the above

---

**Q32.** Why did Gandhi choose SALT as the symbol of Civil Disobedience?

(A) Salt was a luxury item used only by the rich
(B) Salt was used by every Indian regardless of religion, caste, or economic status — making it universally relatable
(C) Salt was the most highly taxed item under British rule
(D) More than one of the above is correct
(E) None of the above

---

**Q33.** The Gandhi-Irwin Pact was signed on:

(A) April 6, 1930
(B) March 5, 1931
(C) September 24, 1932
(D) More than one of the above is correct
(E) None of the above

---

**Q34.** Khan Abdul Ghaffar Khan was associated with which movement during the Civil Disobedience era?

(A) Red Shirts / Khudai Khidmatgar movement in the Northwest Frontier Province
(B) Khilafat Movement in Bengal
(C) Moplah Rebellion in Kerala
(D) More than one of the above is correct
(E) None of the above

---

**Q35.** The Poona Pact (September 24, 1932) was signed between:

(A) Gandhi and Lord Irwin
(B) Gandhi and Dr. B.R. Ambedkar
(C) Gandhi and Muhammad Ali Jinnah
(D) More than one of the above is correct
(E) None of the above

---

**Q36.** What was the Communal Award (1932) given by British PM Ramsay MacDonald?

(A) Separate electorates for Muslims only
(B) Separate electorates for Depressed Classes (Dalits)
(C) Partition of India into Hindu and Muslim zones
(D) More than one of the above is correct
(E) None of the above

---

**Q37.** In which PRISON was Gandhi fasting when the Poona Pact was signed?

(A) Cellular Jail, Andaman
(B) Alipore Jail, Calcutta
(C) Yerwada Jail, Pune
(D) More than one of the above is correct
(E) None of the above

---

**Q38.** Gandhi attended which of the Round Table Conferences?

(A) First Round Table Conference (1930–31)
(B) Second Round Table Conference (1931)
(C) Third Round Table Conference (1932)
(D) More than one of the above is correct
(E) None of the above

---

**Q39.** The Dharasana Salt Works incident (1930) was significant because:

(A) Gandhi personally led the march and broke the salt law there
(B) Sarojini Naidu led non-violent protesters; brutal police beating was reported internationally by journalist Webb Miller
(C) It was where Gandhi signed the Gandhi-Irwin Pact
(D) More than one of the above is correct
(E) None of the above

---

**Q40.** Why is January 26, 1950 celebrated as Republic Day (and not any other date)?

(A) It was the date the Constitution of India was written
(B) January 26, 1930 was the first Independence Day (Purna Swaraj Day) — so this date was chosen for the Republic
(C) It was Mahatma Gandhi's birthday
(D) More than one of the above is correct
(E) None of the above

---

**Q41.** Bhagat Singh, Rajguru, and Sukhdev were hanged on:

(A) March 5, 1931
(B) March 23, 1931
(C) April 6, 1931
(D) More than one of the above is correct
(E) None of the above

---

**Q42.** The Simon Commission (1927) was boycotted by Indians because:

(A) It proposed the partition of India
(B) All its 7 members were British — no Indian was included
(C) It recommended abolishing the Indian National Congress
(D) More than one of the above is correct
(E) None of the above

---

**Q43.** Lala Lajpat Rai died as a result of injuries sustained during:

(A) Jallianwala Bagh Massacre (1919)
(B) Protests against the Simon Commission in Lahore (1928)
(C) Chauri Chaura incident (1922)
(D) More than one of the above is correct
(E) None of the above

---

**Q44.** Who led the Civil Disobedience Movement in Bihar?

(A) Mazharul Haque
(B) Jayaprakash Narayan
(C) Rajendra Prasad
(D) More than one of the above is correct
(E) None of the above

---

**Q45.** The term "Harijans" (Children of God) was used by Gandhi to refer to:

(A) Poor farmers of Bihar
(B) Depressed Classes / Dalits / Untouchables
(C) Muslim participants in the Khilafat Movement
(D) More than one of the above is correct
(E) None of the above

---

**Q46.** The approximate distance of the Dandi March from Sabarmati Ashram to Dandi was:

(A) 100 miles
(B) 241 miles (about 388 km)
(C) 500 km
(D) More than one of the above is correct
(E) None of the above

---

**Q47.** Which of the following is/are correctly matched?

(A) Vedaranyam salt march → C. Rajagopalachari → Tamil Nadu
(B) Dharasana salt works → Sarojini Naidu → Gujarat
(C) NWFP → Khan Abdul Ghaffar Khan → Khudai Khidmatgar
(D) More than one of the above is correct
(E) None of the above

---

**Q48.** The Government of India Act 1935, which was a landmark in Indian constitutional history, was a direct outcome of discussions at:

(A) Lahore Session of Congress 1929
(B) Round Table Conferences (1930–32)
(C) Gandhi-Irwin Pact (1931)
(D) More than one of the above is correct
(E) None of the above

---

**Q49.** What did the Gandhi-Irwin Pact allow Indians to do as a key concession from the British?

(A) Run their own government in the provinces
(B) Make and collect salt for personal use near the seashore
(C) Boycott British courts permanently
(D) More than one of the above is correct
(E) None of the above

---

**Q50.** Which of the following statements about the Civil Disobedience Movement is/are TRUE?

(A) Women participated in large numbers, especially in picketing liquor shops and foreign cloth bonfires
(B) Khan Abdul Ghaffar Khan's success proved non-violence could work among Pashtuns (Pathans)
(C) The Dharasana incident led to international coverage of Indian freedom struggle
(D) More than one of the above is correct
(E) None of the above

---

---
---
---
---
---

# ═══════════════════════════════════════════════════════
# ✅ ANSWER KEY — DID YOU TRY ALL 50 FIRST?
# ═══════════════════════════════════════════════════════

---

## CS ANSWERS (Q1–Q25) — File Handling in C++

| Q# | Answer | Key Explanation |
|----|--------|-----------------|
| **Q1** | **(C) `<fstream>`** | `<fstream>` is the header for ifstream, ofstream, fstream |
| **Q2** | **(C) `ifstream`** | `ifstream` = input file stream = read only |
| **Q3** | **(B) Truncates to zero length** | `ios::trunc` empties the file completely before writing |
| **Q4** | **(B) `"New"`** | `ofstream` uses `ios::out \| ios::trunc` by default → "Old Data" was DELETED first |
| **Q5** | **(C) `ios::app`** | `app` = append = preserves existing content, adds at end |
| **Q6** | **(C) Ctrl + F9** | Classic PYQ — Ctrl+F9 = Compile and Run in Turbo C++ |
| **Q7** | **(C) `\|` (bitwise OR)** | File modes are combined with the `\|` operator |
| **Q8** | **(A) `fstream f("data.txt", ios::in \| ios::out);`** | Opens for R+W without truncating |
| **Q9** | **(B) Returns true at EOF** | `eof()` = `true` when end of file is reached |
| **Q10** | **(C) `fstream`** | Only `fstream` supports both reading AND writing |
| **Q11** | **(C) `ios::out \| ios::trunc`** | `ofstream` truncates by default — CRITICAL TRAP |
| **Q12** | **(B) Binary mode, appends at end** | `ios::app` preserves data; `ios::binary` = binary mode |
| **Q13** | **(C) `true`** | `is_open()` returns `true` if file opened successfully |
| **Q14** | **(B) Moves the READ pointer** | `seekg` = seek-get = controls READ position |
| **Q15** | **(C) `ios::out \| ios::binary`** | Need both flags: `out` for writing + `binary` for binary mode |
| **Q16** | **(C) 253** | 85 + 90 + 78 = 253; while loop reads all three values |
| **Q17** | **(A) seekg = read; seekp = write** | g = get (read), p = put (write) |
| **Q18** | **(C) `ios::ate`** | `ate` = "at end" — moves pointer to end on open; `ios::app` also goes to end but for writes only |
| **Q19** | **(B) Entire line with spaces** | `getline()` reads the whole line until `\n` or EOF |
| **Q20** | **(C) `"BPSC TRE"`** | First `ofstream` writes "BPSC"; second opens with `ios::app` → appends " TRE" |
| **Q21** | **(B) Raw binary data** | `write()` writes specified bytes of raw binary data |
| **Q22** | **(D) More than one** | Both (A) and (B) are correct — `ios::app` positions at end AND preserves data |
| **Q23** | **(B) Returns current READ pointer position** | `tellg` = tell-get = returns current read position |
| **Q24** | **(B) Stream enters FAIL state** | `ifstream` of non-existent file → fails; `is_open()` returns false; no auto-creation |
| **Q25** | **(D) More than one** | All three (A), (B), (C) are correct statements |

---

## GS ANSWERS (Q26–Q50) — Civil Disobedience Movement

| Q# | Answer | Key Explanation |
|----|--------|-----------------|
| **Q26** | **(B) March 12, 1930** | Dandi March STARTED March 12; REACHED Dandi April 6 |
| **Q27** | **(C) Sabarmati Ashram, Ahmedabad** | Starting point of Dandi March |
| **Q28** | **(C) 78** | Exactly 78 followers accompanied Gandhi |
| **Q29** | **(B) Lahore Session, 1929** | Purna Swaraj declared December 19, 1929, Lahore |
| **Q30** | **(C) Jawaharlal Nehru** | Nehru presided over Lahore 1929; youngest Congress President at 40 |
| **Q31** | **(B) Broke salt law at Dandi, April 6, 1930** | CDM officially started when Gandhi violated salt law |
| **Q32** | **(D) More than one** | Both (B) and (C) are correct — salt was universal AND heavily taxed |
| **Q33** | **(B) March 5, 1931** | Gandhi-Irwin Pact = March 5, 1931 |
| **Q34** | **(A) Khudai Khidmatgar / Red Shirts, NWFP** | "Frontier Gandhi" = Khan Abdul Ghaffar Khan |
| **Q35** | **(B) Gandhi and Dr. B.R. Ambedkar** | Poona Pact on Dalit representation |
| **Q36** | **(B) Separate electorates for Depressed Classes** | Communal Award gave Dalits separate electorates — Gandhi opposed this |
| **Q37** | **(C) Yerwada Jail, Pune** | Gandhi fasted in Yerwada (also spelled Yeravda) Jail |
| **Q38** | **(B) Second Round Table Conference (1931)** | Gandhi attended ONLY the 2nd RTC in London |
| **Q39** | **(B) Sarojini Naidu led; Webb Miller reported** | Dharasana = Sarojini Naidu + international media coverage |
| **Q40** | **(B) Jan 26, 1930 was first Independence Day** | Jan 26, 1930 = first Purna Swaraj Day → Jan 26, 1950 = Republic Day |
| **Q41** | **(B) March 23, 1931** | Bhagat Singh, Rajguru, Sukhdev hanged March 23, 1931 |
| **Q42** | **(B) All members were British** | "Simon Go Back" — 7 British members, 0 Indians |
| **Q43** | **(B) Simon Commission protests, Lahore, 1928** | Lathi-charged by Scott; died November 17, 1928 |
| **Q44** | **(C) Rajendra Prasad** | Later became India's first President; led CDM in Bihar |
| **Q45** | **(B) Depressed Classes / Dalits** | Gandhi coined "Harijans"; Ambedkar later rejected this term |
| **Q46** | **(B) 241 miles (about 388 km)** | 24 days walking, 241 miles from Sabarmati to Dandi |
| **Q47** | **(D) More than one** | All three (A), (B), (C) are correctly matched |
| **Q48** | **(B) Round Table Conferences** | Government of India Act 1935 came from RTC discussions |
| **Q49** | **(B) Make salt near seashore** | Key British concession in Gandhi-Irwin Pact |
| **Q50** | **(D) More than one** | All three (A), (B), (C) are TRUE about CDM |

---

# ═══════════════════════════════════════════
# 📝 NIGHT REVISION — 5 BULLET POINTS EACH
## Write These from Memory Before Sleeping
# ═══════════════════════════════════════════

### CS — File Handling:
1. **Three classes:** `ifstream` (read), `ofstream` (write), `fstream` (both) — all from `<fstream>`
2. **`ios::trunc`** = empties file to ZERO LENGTH; `ios::app` = APPENDS at end, preserves data
3. **`ofstream` default** = `ios::out | ios::trunc` — opens with AUTO-TRUNCATION (trap!)
4. **Turbo C++ Ctrl+F9** = Compile and Run; modes combined with `|` (bitwise OR)
5. **`seekg`** = move READ pointer; **`seekp`** = move WRITE pointer; **`eof()`** = true at end of file

### GS — Civil Disobedience Movement:
1. **Dandi March:** March 12, 1930 → April 6, 1930; Sabarmati → Dandi; 78 followers; 241 miles
2. **Purna Swaraj** declared at **Lahore Session 1929** by **Jawaharlal Nehru** (Congress President); Jan 26, 1930 = first Independence Day
3. **Gandhi-Irwin Pact** = March 5, 1931; Gandhi attended only **2nd Round Table Conference** (1931, London)
4. **Poona Pact** = Sep 24, 1932; Gandhi (Yerwada Jail) + **Dr. Ambedkar**; against Communal Award
5. **Bihar:** Rajendra Prasad led CDM; Gandhi's first Satyagraha was **Champaran 1917** (Bihar!)

---

# 📊 DAY 11 PERFORMANCE TRACKER

| Section | Questions | Target Score | My Score |
|---------|-----------|-------------|----------|
| CS — File Handling | 25 | 22+ | _______ |
| GS — CDM + Salt March | 25 | 22+ | _______ |
| **Total** | **50** | **44+** | _______ |

**If score < 38/50:** Re-read the flagged 🎯 facts and redo those questions.
**If score 38–45/50:** Solid — review mistakes only, proceed to Day 12.
**If score 46–50/50:** Topper level! 🏆 You're on track for TOP RANK.

---

> **⚡ TOPPER TIP FOR TOMORROW (Day 12):**
> Day 12 covers **Exception Handling** (`try-catch-throw`) + **Inline Functions** (CS)
> and **Quit India Movement 1942** (GS — "Do or Die!")
> Notice today's D-option answers: Q12, Q22, Q25, Q32, Q47, Q50 were all "More than one"
> — this is exactly the BPSC 20–25% D-option pattern. Never skip option D!

---

*Day 11 Complete | Day 12: Exception Handling + Inline Functions | GS: Quit India Movement 1942*
*Study plan: Phase 1, Week 2 | April 2026 | Target: 130+/150 → TOP RANK in BPSC TRE 4.0*
