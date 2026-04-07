# 📅 BPSC TRE 4.0 — DAY 13 COMPLETE STUDY MATERIAL
## CS Topic: C++ Output Prediction + Bitwise Operators + struct vs class
## GS Topic: Bihar History — Dr. Rajendra Prasad + Modern India (Gandhi Era Revision)

> **Topper Mindset:** Day 13 CS topic is one of the HIGHEST-scoring topics in BPSC TRE exams.
> Output prediction questions appear **5–8 times** per paper. Master them today and you pocket easy marks.
> GS focus: Dr. Rajendra Prasad is Bihar's most important modern historical personality — MUST KNOW for Bihar-specific questions.

---

# ═══════════════════════════════════════════════════════════
# 🖥️ PART A — COMPUTER SCIENCE
# C++ Output Prediction, Bitwise Operators, struct vs class
# ═══════════════════════════════════════════════════════════

---

## 📌 SECTION 1: WHY OUTPUT PREDICTION QUESTIONS ARE GOLD IN BPSC TRE

In TRE 1.0 and TRE 2.0, output prediction questions were asked **directly**:
- "What is the output of the following code?"
- "What error will occur?"
- "Will this code compile? If yes, what is the output?"

These questions test whether you truly understand C++ mechanics — not just theory.

**The 6 categories of output prediction in BPSC TRE:**
1. Pre-increment vs Post-increment in expressions
2. Bitwise operators
3. Recursive functions (with wrong/correct base case)
4. `sizeof()` behavior
5. `struct` vs `class` access
6. Friend function access

---

## 📌 SECTION 2: PRE-INCREMENT vs POST-INCREMENT — THE MOST COMMON TRAP

### Core Rule:

```
++x  →  Pre-increment  →  INCREMENT FIRST, then USE the value
x++  →  Post-increment →  USE the value first, then INCREMENT
```

### Visualized:

```
int x = 5;

        PRE (++x)              POST (x++)
        ─────────              ──────────
Step 1: x becomes 6       Step 1: value 5 is used
Step 2: value 6 is used   Step 2: x becomes 6

Result: 6                  Result: 5
```

### Example 1 — Simple:

```cpp
int a = 5;
cout << ++a;   // Output: 6   (incremented BEFORE printing)
cout << a++;   // Output: 6   (current value 6 printed, THEN a becomes 7)
cout << a;     // Output: 7
```

### Example 2 — In Expression (PYQ Style):

```cpp
int a = 3, b = 4;
int c = a++ + ++b;
// Step by step:
// b is pre-incremented → b becomes 5, use 5
// a++ uses current a=3, then a becomes 4
// c = 3 + 5 = 8
cout << c;     // Output: 8
cout << a;     // Output: 4
cout << b;     // Output: 5
```

### Example 3 — Tricky (PYQ Pattern):

```cpp
int x = 10;
int y = x++ + x++;
// First x++ → uses 10, x becomes 11
// Second x++ → uses 11, x becomes 12
// y = 10 + 11 = 21
cout << y;     // Output: 21
cout << x;     // Output: 12
```

### ⚠️ PYQ TRAP:
```cpp
int a = 5;
int b = a++ + ++a;
// This is UNDEFINED BEHAVIOR in C++
// BPSC will NOT ask pure UB, but they may ask with clear step-by-step
// If asked: likely answer = D (More than one of the above) or E (None of the above)
```

---

## 📌 SECTION 3: BITWISE OPERATORS — COMPLETE MASTERY

### The 6 Bitwise Operators:

```
Operator  Symbol  Example          Meaning
─────────────────────────────────────────────────────
AND         &     5 & 3            Both bits must be 1
OR          |     5 | 3            At least one bit is 1
XOR         ^     5 ^ 3            Exactly one bit is 1
NOT         ~     ~5               Flip all bits
Left Shift  <<    5 << 1           Multiply by 2^n
Right Shift >>    5 >> 1           Divide by 2^n
```

### How to Convert for Bitwise Operations:

```
Decimal → Binary conversion (memorize these):

  0 = 0000     4 = 0100     8 = 1000    12 = 1100
  1 = 0001     5 = 0101     9 = 1001    13 = 1101
  2 = 0010     6 = 0110    10 = 1010    14 = 1110
  3 = 0011     7 = 0111    11 = 1011    15 = 1111
```

### Operator AND ( & ):

```
Rule: 1 & 1 = 1,  1 & 0 = 0,  0 & 1 = 0,  0 & 0 = 0
      (BOTH must be 1 to get 1)

Example: 5 & 3
  5 = 0101
  3 = 0011
  ─────────
    = 0001  → decimal 1

cout << (5 & 3);  // Output: 1
```

```
Example: 12 & 10
  12 = 1100
  10 = 1010
  ──────────
     = 1000  → decimal 8

cout << (12 & 10);  // Output: 8
```

### Operator OR ( | ):

```
Rule: 1 | 1 = 1,  1 | 0 = 1,  0 | 1 = 1,  0 | 0 = 0
      (AT LEAST ONE must be 1 to get 1)

Example: 5 | 3
  5 = 0101
  3 = 0011
  ─────────
    = 0111  → decimal 7

cout << (5 | 3);  // Output: 7
```

### Operator XOR ( ^ ):

```
Rule: 1 ^ 1 = 0,  1 ^ 0 = 1,  0 ^ 1 = 1,  0 ^ 0 = 0
      (EXACTLY ONE must be 1 to get 1)

Example: 5 ^ 3
  5 = 0101
  3 = 0011
  ─────────
    = 0110  → decimal 6

cout << (5 ^ 3);  // Output: 6
```

```
XOR SPECIAL PROPERTY (PYQ FAVORITE!):
  A ^ A = 0   (any number XOR itself = 0)
  A ^ 0 = A   (any number XOR 0 = the number itself)

Example: 7 ^ 7 = 0
         9 ^ 0 = 9
```

### Operator NOT ( ~ ) — Bitwise Complement:

```
Formula: ~n = -(n+1)    [For signed integers]

~5  = -(5+1) = -6
~0  = -(0+1) = -1
~-1 = -(-1+1) = 0

Why? Two's complement representation!
  5   = 00000101 (8-bit)
  ~5  = 11111010 → in two's complement = -6
```

### Left Shift ( << ) and Right Shift ( >> ):

```
Left Shift  <<  :  n << k = n × 2^k
Right Shift >>  :  n >> k = n ÷ 2^k  (integer division)

Examples:
  5 << 1 = 5 × 2^1 = 10
  5 << 2 = 5 × 2^2 = 20
  5 << 3 = 5 × 2^3 = 40
  
  20 >> 1 = 20 ÷ 2 = 10
  20 >> 2 = 20 ÷ 4 = 5
  16 >> 3 = 16 ÷ 8 = 2
```

### Code Example with Multiple Bitwise Ops (PYQ Style):

```cpp
int a = 6, b = 3;
cout << (a & b) << endl;   // 6=0110, 3=0011, AND=0010 → 2
cout << (a | b) << endl;   // 6=0110, 3=0011, OR =0111 → 7
cout << (a ^ b) << endl;   // 6=0110, 3=0011, XOR=0101 → 5
cout << (~a) << endl;      // ~6 = -(6+1) = -7
cout << (a << 1) << endl;  // 6 × 2 = 12
cout << (a >> 1) << endl;  // 6 ÷ 2 = 3
```

---

## 📌 SECTION 4: bool ARITHMETIC IN EXPRESSIONS

### Key Rules:

```
bool in arithmetic context:
  true  = 1
  false = 0

Any non-zero value treated as bool = true (= 1)
Zero treated as bool = false (= 0)
```

### Examples:

```cpp
bool a = true, b = false;
cout << a + b;        // 1 + 0 = 1
cout << a + a;        // 1 + 1 = 2  ← NOT true! It's int 2
cout << (bool)(a+a);  // (bool)2 = true = 1

int x = 5;
bool flag = (x > 3);  // 5 > 3 is true → flag = 1
cout << flag + 2;     // 1 + 2 = 3
```

### PYQ Pattern:

```cpp
int x = 10;
bool result = (x > 5) & (x < 20);
// (x > 5) = true = 1
// (x < 20) = true = 1
// 1 & 1 = 1 → true
cout << result;  // Output: 1
```

---

## 📌 SECTION 5: RECURSIVE FUNCTIONS — WHAT GOES WRONG

### Normal Working Recursion (for reference):

```cpp
int factorial(int n) {
    if (n == 0) return 1;      // ← Base case (stops recursion)
    return n * factorial(n-1); // ← Recursive call, goes DOWN
}
// factorial(4) → 4 * 3 * 2 * 1 = 24 ✓
```

### Recursion with WRONG Base Case → Segmentation Fault (PYQ!):

```cpp
int factorial(int a) {
    if (a == 0) return 1;
    return a * factorial(a + 1);  // ← Wrong! a+1 goes UP, never reaches 0
}
// factorial(3) → 3 * factorial(4) → 4 * factorial(5) → ... → INFINITE
// Result: STACK OVERFLOW → Segmentation Fault
```

```
VISUALIZE WHAT HAPPENS:

CORRECT (a-1):               WRONG (a+1):
factorial(4)                 factorial(4)
  4 * factorial(3)             4 * factorial(5)
    3 * factorial(2)             5 * factorial(6)
      2 * factorial(1)             6 * factorial(7)
        1 * factorial(0)             7 * ... → INFINITY!
          returns 1                        → SEGFAULT
          ↑ stops here
```

### PYQ Key Fact:
```
Wrong recursion direction (a+1 instead of a-1) → Segmentation Fault
This is because:
  1. Function calls keep stacking up on the call stack
  2. Stack memory is limited
  3. When stack is exhausted → Segmentation Fault / Stack Overflow
```

---

## 📌 SECTION 6: sizeof() OPERATOR — DOES NOT EVALUATE

### The Most Important Rule:

```
sizeof() computes the SIZE of the TYPE — it does NOT execute the expression inside it!
```

### Examples:

```cpp
int x = 5;
sizeof(x++);   // x is NOT incremented! sizeof just looks at type of x
cout << x;     // Output: 5 (NOT 6!)

int arr[10];
sizeof(arr);   // 10 × 4 = 40 bytes (for int on 32-bit)

// sizeof with expression:
int a = 3, b = 4;
sizeof(a + b);  // Does NOT compute a+b = 7. Just finds size of int = 4
```

### Data Type Sizes (Memorize!):

```
Data Type    Size (32-bit)    Size (64-bit)
─────────────────────────────────────────────
char              1 byte           1 byte
short             2 bytes          2 bytes
int               4 bytes          4 bytes
long              4 bytes          8 bytes
long long         8 bytes          8 bytes
float             4 bytes          4 bytes
double            8 bytes          8 bytes
bool              1 byte           1 byte
pointer           4 bytes          8 bytes
```

---

## 📌 SECTION 7: struct vs class IN C++ — THE ONLY DIFFERENCE

### The Most PYQ-Tested Rule:

```
╔══════════════════════════════════════════════════════════╗
║         struct          vs           class               ║
╠══════════════════════════════════════════════════════════╣
║  Default access = PUBLIC     Default access = PRIVATE    ║
║  struct S { int x; };        class C { int x; };         ║
║  S obj; obj.x = 5; ✓ OK      C obj; obj.x = 5; ✗ ERROR  ║
╚══════════════════════════════════════════════════════════╝

⭐ THIS IS THE ONLY DIFFERENCE BETWEEN struct AND class IN C++ ⭐
Everything else (methods, constructors, inheritance) is IDENTICAL.
```

### Demonstration:

```cpp
// STRUCT — default PUBLIC
struct Student {
    int rollNo;       // accessible outside (public by default)
    string name;      // accessible outside
};

Student s;
s.rollNo = 101;   // ✓ Compiles fine
s.name = "Prag";  // ✓ Compiles fine


// CLASS — default PRIVATE
class Teacher {
    int empId;        // NOT accessible outside (private by default)
    string name;      // NOT accessible outside
};

Teacher t;
t.empId = 1;    // ✗ ERROR: 'empId' is private
t.name = "XYZ"; // ✗ ERROR: 'name' is private
```

### Overriding Default with Access Specifiers:

```cpp
// You CAN make struct private and class public explicitly:

struct MyStruct {
private:
    int secret;   // Now private in struct
public:
    int open;     // Explicitly public
};

class MyClass {
public:
    int visible;  // Now public in class
private:
    int hidden;   // Still private
};
```

### In C vs C++ — Difference:

```
In C:
  struct is ONLY for data (no methods)
  No class keyword exists

In C++:
  struct = class with default public access
  Both can have methods, constructors, destructors, inheritance
```

---

## 📌 SECTION 8: SCOPE RESOLUTION OPERATOR ::

### What is :: ?

```
The :: (scope resolution operator) is used to:
1. Define member functions OUTSIDE the class body
2. Access global variables when a local variable has same name
3. Access static members of a class
4. Refer to members of namespace
```

### Usage 1 — Define member function outside class:

```cpp
class Circle {
    double radius;
public:
    void setRadius(double r);  // Declaration inside class
    double getArea();          // Declaration inside class
};

// Definition OUTSIDE class using ::
void Circle::setRadius(double r) {
    radius = r;
}

double Circle::getArea() {
    return 3.14159 * radius * radius;
}
```

### Usage 2 — Access global when local shadows it:

```cpp
int value = 100;  // Global variable

void display() {
    int value = 50;         // Local variable
    cout << value;          // Prints 50 (local)
    cout << ::value;        // Prints 100 (global) using ::
}
```

### Usage 3 — Static member access:

```cpp
class Counter {
public:
    static int count;
};
int Counter::count = 0;  // Initialize static member using ::

Counter::count = 5;  // Access static member using ::
```

---

## 📌 SECTION 9: FRIEND FUNCTION — ACCESS RULES

### What is a Friend Function?

```
A friend function:
  ✓ Is declared inside a class with keyword 'friend'
  ✓ Can access PRIVATE and PROTECTED members of that class
  ✗ Is NOT a member of the class
  ✗ Cannot use 'this' pointer
  ✗ Is called WITHOUT any object (like a normal function)
```

### Syntax:

```cpp
class BankAccount {
private:
    double balance;    // Private member
    
public:
    BankAccount(double b) : balance(b) {}
    
    friend void showBalance(BankAccount acc);  // Friend declaration
};

// Friend function definition (OUTSIDE class, no class:: prefix)
void showBalance(BankAccount acc) {
    // Can access private member because it's a friend!
    cout << "Balance: " << acc.balance;
}

int main() {
    BankAccount myAccount(50000);
    showBalance(myAccount);  // Called like normal function, NOT as member
    // myAccount.showBalance(); ← WRONG way to call
}
```

### Friend Class:

```cpp
class Engine;  // Forward declaration

class Car {
    friend class Engine;  // Engine can access all private members of Car
private:
    int horsepower = 200;
};

class Engine {
public:
    void displayPower(Car c) {
        cout << c.horsepower;  // ✓ Can access Car's private member
    }
};
```

### Key Rules for BPSC:

```
1. Friend is NOT inherited (child class does NOT get friend access)
2. Friendship is NOT mutual (if A is friend of B, B is NOT automatically friend of A)
3. Friend function does NOT have 'this' pointer
4. Friend function can be friend of MULTIPLE classes
5. Friend relationship is declared inside the class (NOT outside)
```

---

## 📌 SECTION 10: COMPLETE C++ OUTPUT PREDICTION — PRACTICE PROBLEMS (with analysis)

### Problem 1:

```cpp
#include<iostream>
using namespace std;
int main() {
    int x = 5;
    cout << x++ << " " << ++x << endl;
    return 0;
}
```

Step-by-step:
```
x = 5
x++  → prints 5, then x becomes 6
++x  → x becomes 7, then prints 7
Output: 5 7
```

### Problem 2:

```cpp
int main() {
    int a = 6, b = 4;
    cout << (a & b) << endl;
    cout << (a | b) << endl;
    cout << (a ^ b) << endl;
    return 0;
}
```

Step-by-step:
```
a = 6 = 0110
b = 4 = 0100

a & b: 0110 & 0100 = 0100 → 4
a | b: 0110 | 0100 = 0110 → 6
a ^ b: 0110 ^ 0100 = 0010 → 2

Output:
4
6
2
```

### Problem 3:

```cpp
struct Point {
    int x, y;
};
int main() {
    Point p;
    p.x = 10;
    p.y = 20;
    cout << p.x + p.y;
}
```

Output: `30` (struct members are public by default — no error)

### Problem 4:

```cpp
class Point {
    int x, y;   // private by default in class
};
int main() {
    Point p;
    p.x = 10;  // What happens?
}
```

Output: **Compile Error** — `x` is private in class Point

---

# ═══════════════════════════════════════════════════════════
# 🏛️ PART B — GENERAL STUDIES
# Bihar History: Dr. Rajendra Prasad + Gandhi Era Complete
# ═══════════════════════════════════════════════════════════

---

## 📌 SECTION 11: DR. RAJENDRA PRASAD — BIHAR'S PRIDE

### Quick Identity Card:

```
╔════════════════════════════════════════════════════════════╗
║             DR. RAJENDRA PRASAD — KEY FACTS               ║
╠════════════════════════════════════════════════════════════╣
║ Born:        3 December 1884                              ║
║ Birthplace:  Zeradei, Siwan district, Bihar (BPSC FAVORITE!)║
║ Died:        28 February 1963                             ║
║ Role:        1st President of India (1950–1962)           ║
║ Education:   Presidency College, Calcutta; Law degree     ║
║ Award:       Bharat Ratna (1962)                          ║
╚════════════════════════════════════════════════════════════╝
```

### His Role in Freedom Struggle:

```
1. CHAMPARAN SATYAGRAHA (1917):
   ► Gandhiji came to Champaran for indigo farmers
   ► Rajendra Prasad was among the first lawyers to JOIN Gandhi
   ► He organized relief work, collected testimonies of farmers
   ► This was his FIRST major connection with Gandhi

2. NON-COOPERATION MOVEMENT (1920-22):
   ► Left his successful law practice to join the movement
   ► Actively spread the movement in Bihar
   ► Arrested multiple times by British authorities

3. CIVIL DISOBEDIENCE MOVEMENT (1930):
   ► Participated actively in the Salt Satyagraha
   ► Was imprisoned along with other Congress leaders

4. QUIT INDIA MOVEMENT (1942):
   ► Played a key role; arrested and imprisoned
   ► Continued underground activities

5. CONSTITUENT ASSEMBLY:
   ► Elected President of the Constituent Assembly (1946)
   ► Presided over the drafting of the Indian Constitution
   ► Constitution adopted on 26 November 1949
```

### As India's First President:

```
► Sworn in as President on: 26 January 1950
► Served TWO full terms (unique — only president to do so)
► Term ended: 13 May 1962
► Awarded Bharat Ratna: 1962 (the same year he retired)
► He was the ONLY president to serve TWO terms

After Presidency:
► Retired to Sadaqat Ashram, Patna (Bihar)
► Died: 28 February 1963 at Sadaqat Ashram, Patna
```

### His Books & Writings:

```
Book/Work                    About
─────────────────────────────────────────────────────────
India Divided (1946)         Arguments against Partition
Atmakatha (Autobiography)    In Hindi, his life story
Mahatma Gandhi & Bihar       About Gandhi's work in Bihar
Satyagraha at Champaran      About the Champaran movement
```

### Bihar Connection Points (High BPSC Probability):

```
1. Born in Zeradei (now in Siwan district) — NOT Patna!
2. Completed schooling in Patna
3. Went to Calcutta for higher education
4. Returned to Bihar after meeting Gandhi in Champaran
5. His memorial at Sadaqat Ashram, Patna (now BPSC Exam Center)
6. Rajendra Prasad Central Agricultural University — Pusa, Bihar (named after him)
```

---

## 📌 SECTION 12: GANDHI ERA — COMPLETE REVISION WITH BIHAR FOCUS

### Timeline of Gandhi's Movements:

```
YEAR    EVENT                     KEY FACT / BIHAR ANGLE
────────────────────────────────────────────────────────────────
1917    Champaran Satyagraha      ► Gandhi's FIRST Satyagraha in India
                                  ► Against tinkathia system (indigo cultivation)
                                  ► Location: Champaran, Bihar
                                  ► Rajendra Prasad, Brajkishore Prasad joined

1918    Kheda Satyagraha          ► Gujarat; peasants demanded revenue remission
                                  ► NOT in Bihar

1918    Ahmedabad Mill Strike     ► First hunger strike by Gandhi
                                  ► NOT in Bihar

1919    Rowlatt Act Protest       ► Against "Black Act" — detention without trial
                                  ► Jallianwala Bagh massacre (April 13, 1919)
                                  ► General Dyer ordered firing → 379+ killed

1920-22 Non-Cooperation Movement ► Boycott of British goods, courts, schools
                                  ► Chauri Chaura incident (Feb 5, 1922) → Gandhi withdrew
                                  ► Chauri Chaura: Gorakhpur, UP (NOT Bihar)

1930    Civil Disobedience        ► Dandi March (Salt March) March 12–April 6, 1930
                                  ► Gandhi walked 241 miles from Sabarmati to Dandi
                                  ► Bihar saw mass civil disobedience

1930-32 Round Table Conferences  ► London; Gandhi attended 2nd RTC (1931)
                                  ► Gandhi-Irwin Pact (March 1931) before 2nd RTC

1934    Bihar Earthquake          ► Major earthquake hit Bihar
                                  ► Gandhi visited Bihar for relief work
                                  ► Said earthquake was punishment for untouchability

1940    Individual Satyagraha     ► Vinoba Bhave was first satyagrahi

1942    Quit India Movement       ► "Do or Die" — August 8, 1942
                                  ► Aruna Asaf Ali raised flag at Gowalia Tank
                                  ► Congress leaders arrested next day (Aug 9)
                                  ► Bihar saw massive uprising — Jayaprakash Narayan
```

---

## 📌 SECTION 13: CHAMPARAN SATYAGRAHA — DEEP DIVE (Bihar's Most Important Event)

### Background:

```
THE PROBLEM:
European planters forced farmers to grow INDIGO on 3/20 parts (3 kattha out of 20)
of their land. This was called the TINKATHIA SYSTEM.

WHY IT WAS UNFAIR:
1. Indigo prices were falling (due to synthetic dye)
2. Planters still forced cultivation
3. When planters wanted to end indigo cultivation, they demanded
   heavy payments (tawan) from farmers to release them from obligation
4. Farmers were exploited with high rents and illegal levies
```

### Gandhi's arrival and Action:

```
► Gandhi arrived in Champaran: April 1917
► His guide: Raj Kumar Shukla (Bihar farmer who persuaded Gandhi)
► Accompanied by: Rajendra Prasad, Brajkishore Prasad, Mazharul Haq,
                  J.B. Kriplani, Mahadev Desai

Gandhi's Method:
  1. Conducted a detailed survey of farmers' grievances
  2. Collected thousands of testimonies (evidence of exploitation)
  3. British officials tried to expel Gandhi → he refused to leave
  4. Massive public support forced British to back down

Result:
  ► Champaran Agrarian Bill (1917) passed
  ► Tinkathia system ABOLISHED
  ► Farmers were compensated (25% of tawan returned)
  ► Gandhi's FIRST successful Satyagraha in India
  ► Made Gandhi a national hero
```

### Why Champaran is Special for Bihar:

```
1. First Satyagraha on Indian soil by Gandhi
2. First time civil disobedience was used successfully in India
3. Launched the Indian national movement in Bihar
4. Rajendra Prasad's political career began here
5. Proved that non-violent resistance could work against British
6. Located in: North Bihar (now in East Champaran & West Champaran districts)
```

---

## 📌 SECTION 14: JAYAPRAKASH NARAYAN (JP) — BIHAR'S FREEDOM FIGHTER

### Quick Facts:

```
╔═══════════════════════════════════════════════════════════╗
║         JAYAPRAKASH NARAYAN (JP) — KEY FACTS             ║
╠═══════════════════════════════════════════════════════════╣
║ Born:        11 October 1902                             ║
║ Birthplace:  Sitabdiara, Saran district, Bihar           ║
║ Died:        8 October 1979                              ║
║ Title:       Loknayak (People's Leader)                  ║
║ Award:       Bharat Ratna (1999, posthumously)           ║
╚═══════════════════════════════════════════════════════════╝
```

### His Role:

```
1. QUIT INDIA MOVEMENT (1942):
   ► Most active in Bihar during the movement
   ► Led underground resistance
   ► Dramatically escaped from Hazaribagh Jail (Nov 1942)
   ► Organized guerrilla resistance against British

2. POST-INDEPENDENCE:
   ► Resigned from Congress (1954) — joined Praja Socialist Party
   ► Later became symbol of anti-corruption movement

3. JP MOVEMENT (1974-77):
   ► Led movement against Indira Gandhi's government
   ► Called for "Total Revolution" (Sampurna Kranti)
   ► Led from BIHAR (starting with Bihar Movement)
   ► Contributed to Emergency (1975-77) and its end
```

---

## 📌 SECTION 15: QUIT INDIA MOVEMENT (1942) — COMPLETE DETAILS

### Key Facts:

```
Full Name:     Quit India Movement / August Movement / Bharat Chhodo Andolan
Date:          August 8, 1942 (movement launched)
               August 9, 1942 (Congress leaders arrested — "Black Thursday")
Slogan:        "Do or Die" (Karo ya Maro) — by Gandhi
Location:      Gowalia Tank Maidan (August Kranti Maidan), Bombay
Flag Hoisted:  Aruna Asaf Ali at Gowalia Tank Maidan

Gandhi's Call:
  "Here is a mantra, a short one, that I give you.
   You may imprint it on your hearts and let every breath
   of yours give expression to it. The mantra is:
   'Do or Die'"
```

### Congress Leaders Arrested (August 9, 1942):

```
Gandhi   → Aga Khan Palace, Pune (not a jail, but detained)
Nehru    → Ahmadnagar Fort (where he wrote 'Discovery of India')
Rajendra Prasad → Bankipur Jail, Patna (Bihar!)
Sardar Patel → Ahmadnagar Fort
```

### Bihar in Quit India Movement:

```
Bihar was one of the most active states:
  ► Arrah, Balia, Bhagalpur, Sitamarhi — centers of uprising
  ► Parallel governments (Azad Dasta) formed in rural areas
  ► Jayaprakash Narayan escaped Hazaribagh Jail and led underground resistance
  ► Ballia (UP) and some Bihar areas declared free from British rule temporarily
```

---

## 📌 SECTION 16: IMPORTANT DATES TABLE — MODERN INDIA (Exam Ready)

```
YEAR    EVENT                                          LOCATION
──────────────────────────────────────────────────────────────────
1885    Indian National Congress founded               Bombay
        By: A.O. Hume; 1st President: W.C. Banerjee
1905    Partition of Bengal                            Curzon's decision
1906    Muslim League founded                          Dhaka
1907    Surat Split (Congress divided)                 Surat
1911    Partition of Bengal reversed (Delhi Durbar)    Delhi
1915    Gandhi returned from South Africa              India
1916    Lucknow Pact (Congress-League)                 Lucknow
1917    Champaran Satyagraha                           Bihar ⭐
1919    Rowlatt Act; Jallianwala Bagh massacre         Punjab
1920    Non-Cooperation Movement started               All India
1920    Khilafat Movement (Ali Brothers)               All India
1922    Chauri Chaura Incident → NCM withdrawn         Gorakhpur, UP
1923    Swaraj Party formed (Motilal Nehru, C.R. Das) 
1927    Simon Commission (boycotted — all British)     
1929    Lahore Session — "Purna Swaraj" declared       Lahore
        Nehru President; January 26 → Independence Day
1930    Civil Disobedience/Dandi March (Mar 12)        Sabarmati, Gujarat
1930    Poona Pact (Gandhi-Ambedkar)                   Pune (1932)
1931    Gandhi-Irwin Pact                              
1931    2nd Round Table Conference (Gandhi attended)   London
1935    Government of India Act 1935                   
1940    Lahore Resolution (Pakistan demand — Jinnah)   Lahore
1942    Quit India Movement (August 8)                 Bombay ⭐
1946    Direct Action Day (Muslim League)              Calcutta
1947    India's Independence (August 15)               India
1950    Constitution enacted (January 26)              India
```

---

## 📌 SECTION 17: IMPORTANT ROUNDS TABLE CONFERENCES

```
RTC       Year    Gandhi?    Result
──────────────────────────────────────────────────────────
1st RTC   1930    No         Congress boycotted; minorities discussed
2nd RTC   1931    YES        Gandhi attended; no agreement on minorities
3rd RTC   1932    No         Congress boycotted; irrelevant
```

### Gandhi-Irwin Pact (1931) — Before 2nd RTC:

```
Gandhi agreed to:
  1. Suspend Civil Disobedience Movement
  2. Attend 2nd Round Table Conference
  3. Release political prisoners (non-violent)

British agreed to:
  1. Release prisoners arrested during CDM
  2. Permit salt manufacture on coast
  3. Withdraw emergency ordinances
```

---

## 📌 SECTION 18: NEHRU, BOSE AND THE CONGRESS PRESIDENCY

```
IMPORTANT CONGRESS SESSIONS AND PRESIDENTS:

Year    Location        President            Significance
─────────────────────────────────────────────────────────────────
1885    Bombay          W.C. Banerjee        1st Session
1896    Calcutta        Rahimtulla Sayani    "Vande Mataram" sung first time
1905    Varanasi        G.K. Gokhale         Boycott & Swadeshi discussed
1906    Calcutta        Dadabhai Naoroji     "Swaraj" word used first time
1907    Surat           Ras Bihari Ghosh     Surat Split (Moderates vs Extremists)
1916    Lucknow         Ambika Charan        Lucknow Pact
1920    Calcutta/Nagpur C.R. Das/C.V. Mehta Non-Cooperation adopted
1927    Madras          M.A. Ansari          Simon Commission boycott
1929    Lahore          Jawaharlal Nehru     "Purna Swaraj" declared ⭐
1931    Karachi         Sardar Patel         Fundamental Rights resolution
1938    Haripura        Subhas Chandra Bose  
1939    Tripuri         Subhas Chandra Bose  Resigned → formed Forward Bloc
```

---

## 📌 SECTION 19: SUBHAS CHANDRA BOSE — INA & AZAD HIND

```
╔═══════════════════════════════════════════════════════════╗
║         SUBHAS CHANDRA BOSE — KEY FACTS                  ║
╠═══════════════════════════════════════════════════════════╣
║ Born:        23 January 1897, Cuttack (Odisha)           ║
║ Title:       Netaji (Beloved Leader)                     ║
║ Education:   ICS exam cleared; resigned to join struggle ║
╚═══════════════════════════════════════════════════════════╝

Timeline:
  1938-39: Congress President (twice elected)
  1939: Resigned from Congress; formed FORWARD BLOC
  1941: Escaped India (Calcutta → Peshawar → Kabul → Moscow → Berlin)
  1943: Reached Japan; took over Indian National Army (INA)
         INA originally formed by Rash Behari Bose and Mohan Singh (1942)
  1943: Declared Provisional Government of Free India (Azad Hind)
  1944: INA captured Kohima and parts of Manipur
         Famous march: "Delhi Chalo" (March to Delhi)
  1945: Japan surrendered; INA collapsed
  August 18, 1945: Died in plane crash near Taiwan

Slogans by Bose:
  "Jai Hind" — National salute he popularized
  "Delhi Chalo" — March toward Delhi
  "Tum Mujhe Khoon Do, Main Tumhe Azadi Dunga"
  ("Give me blood, I will give you freedom")

INA Trials (1945-46):
  ► Shah Nawaz Khan, P.K. Sehgal, G.S. Dhillon — INA officers tried
  ► Jawaharlal Nehru defended them
  ► Public sympathy was massive → British backed off
  ► These trials accelerated independence
```

---

## 📌 SECTION 20: BHARAT RATNA RECIPIENTS FROM BIHAR / CONNECTED TO BIHAR

```
Name                    Year    Connection to Bihar
─────────────────────────────────────────────────────────────
Dr. Rajendra Prasad     1962    Born in Siwan, Bihar ⭐
Jayaprakash Narayan     1999    Born in Saran, Bihar ⭐
Bismillah Khan          2001    Born in Dumraon, Bihar ⭐
```

---

# ═══════════════════════════════════════════════════════════
# ✏️ PRACTICE QUESTIONS — DAY 13
# ═══════════════════════════════════════════════════════════

> ⚠️ **INSTRUCTIONS:** Attempt ALL 50 questions BEFORE looking at answers.
> Answers are provided at the VERY END of this file.
> Cover the answer section while solving questions.

---

# 💻 SECTION A — COMPUTER SCIENCE (25 Questions)

### CS-Q1.
What is the output of the following C++ code?
```cpp
int x = 5;
cout << x++ << " " << ++x;
```
(A) 5 6  
(B) 5 7  
(C) 6 7  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q2.
What is the result of the bitwise expression `7 & 5` in C++?
(A) 3  
(B) 5  
(C) 7  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q3.
Evaluate `6 | 3` (bitwise OR):
(A) 3  
(B) 6  
(C) 7  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q4.
What does `~5` evaluate to in C++ (assuming int is 32-bit, signed)?
(A) -4  
(B) -5  
(C) -6  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q5.
What is the output of `cout << (5 ^ 3)`?
(A) 15  
(B) 6  
(C) 8  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q6.
Which of the following statements about `sizeof()` in C++ is CORRECT?
(A) sizeof() evaluates the expression inside it  
(B) sizeof(x++) will increment x  
(C) sizeof() only works with basic data types  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q7.
What is the ONLY difference between `struct` and `class` in C++?
(A) struct cannot have methods; class can  
(B) struct default access is public; class default access is private  
(C) struct cannot be inherited; class can  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q8.
Consider the code:
```cpp
class Box {
    int length;
};
Box b;
b.length = 10;
```
What happens?
(A) Output is 10  
(B) Compile error — length is private  
(C) Runtime error  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q9.
Consider the code:
```cpp
struct Box {
    int length;
};
Box b;
b.length = 10;
cout << b.length;
```
What is the output?
(A) 0  
(B) Compile error  
(C) 10  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q10.
What is the output?
```cpp
int a = 3, b = 5;
int c = ++a + b++;
cout << c;
```
(A) 8  
(B) 9  
(C) 10  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q11.
In C++, the scope resolution operator `::` is used for:
(A) Accessing private members of a class  
(B) Defining member functions outside the class  
(C) Declaring pointer variables  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q12.
A friend function in C++:
(A) Is a member of the class  
(B) Can access private members of the class it is a friend of  
(C) Uses 'this' pointer  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q13.
What is the output of the following code?
```cpp
int a = 8;
cout << (a >> 2);
```
(A) 2  
(B) 32  
(C) 4  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q14.
What is the output of the following?
```cpp
int a = 3;
cout << (a << 3);
```
(A) 6  
(B) 12  
(C) 24  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q15.
Which of the following is TRUE about a recursive function that calls itself with `(n+1)` instead of `(n-1)`?
(A) It compiles but gives wrong output  
(B) It results in segmentation fault due to infinite recursion  
(C) It gives compilation error  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q16.
What is the result of `10 ^ 10` (XOR) in C++?
(A) 10  
(B) 100  
(C) 0  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q17.
What is the result of `A ^ 0` for any integer A?
(A) 0  
(B) 1  
(C) A  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q18.
Friendship in C++ is:
(A) Mutual — if A is friend of B, then B is friend of A  
(B) Inherited — a derived class inherits friend status  
(C) Neither mutual nor inherited  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q19.
Which of the following can a friend function access in the class it befriends?
(A) Only public members  
(B) Only private members  
(C) Both private and protected members  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q20.
What will happen when this code is executed?
```cpp
int x = 5;
int result = sizeof(x++);
cout << x;
```
(A) 6  
(B) 5  
(C) 4  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q21.
In C++, `struct` keyword in C:
(A) Can have methods just like in C++  
(B) Only holds data — no methods allowed  
(C) Has private default access specifier  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q22.
What is the output of the following code?
```cpp
bool a = true;
bool b = false;
cout << (a + b);
```
(A) true  
(B) false  
(C) 1  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q23.
Which operator is the bitwise XOR operator in C++?
(A) `&&`  
(B) `^`  
(C) `|`  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q24.
What is the value of `15 & 9`?
(A) 15  
(B) 9  
(C) 6  
(D) More than one of the above  
(E) None of the above  

---

### CS-Q25.
A class in C++ can have a friend function that:
(A) Is defined completely outside the class  
(B) Accesses private data of the class  
(C) Is called like a normal function, not as a member function  
(D) More than one of the above  
(E) None of the above  

---

# 🏛️ SECTION B — GENERAL STUDIES (25 Questions)

### GS-Q1.
Dr. Rajendra Prasad was born in which district of Bihar?
(A) Patna  
(B) Champaran  
(C) Siwan  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q2.
Dr. Rajendra Prasad served as President of India for how many terms?
(A) One term  
(B) Two terms  
(C) Three terms  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q3.
Rajendra Prasad received Bharat Ratna in which year?
(A) 1950  
(B) 1955  
(C) 1962  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q4.
Dr. Rajendra Prasad was the President of which important body that drafted India's Constitution?
(A) Drafting Committee  
(B) Constituent Assembly  
(C) Parliament  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q5.
The Champaran Satyagraha (1917) was launched against which system?
(A) Ryotwari System  
(B) Zamindari System  
(C) Tinkathia System  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q6.
Who persuaded Mahatma Gandhi to visit Champaran?
(A) Rajendra Prasad  
(B) Brajkishore Prasad  
(C) Raj Kumar Shukla  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q7.
The Quit India Movement was launched on which date?
(A) 8 August 1942  
(B) 9 August 1942  
(C) 15 August 1942  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q8.
"Do or Die" slogan was given by Mahatma Gandhi during:
(A) Non-Cooperation Movement  
(B) Civil Disobedience Movement  
(C) Quit India Movement  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q9.
Aruna Asaf Ali hoisted the Congress flag during Quit India Movement at:
(A) Sabarmati Ashram, Ahmedabad  
(B) Gowalia Tank Maidan, Bombay  
(C) Lal Qila, Delhi  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q10.
Jayaprakash Narayan was born in which district of Bihar?
(A) Patna  
(B) Siwan  
(C) Saran  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q11.
The title "Loknayak" is associated with which leader?
(A) Rajendra Prasad  
(B) Jayaprakash Narayan  
(C) Subhas Chandra Bose  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q12.
Jayaprakash Narayan's famous "Total Revolution" (Sampurna Kranti) movement was launched from:
(A) Delhi  
(B) Bihar  
(C) Gujarat  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q13.
In 1929, which Congress Session declared "Purna Swaraj" as the goal?
(A) Calcutta Session  
(B) Lahore Session  
(C) Karachi Session  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q14.
Who presided over the 1929 Lahore Congress Session that declared Purna Swaraj?
(A) Mahatma Gandhi  
(B) Subhas Chandra Bose  
(C) Jawaharlal Nehru  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q15.
The Dandi March (Salt March) started on which date?
(A) 26 January 1930  
(B) 12 March 1930  
(C) 6 April 1930  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q16.
Gandhi attended which Round Table Conference in London?
(A) First RTC (1930)  
(B) Second RTC (1931)  
(C) Third RTC (1932)  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q17.
The Chauri Chaura incident (1922) that led Gandhi to withdraw Non-Cooperation Movement occurred in:
(A) Bihar  
(B) Uttar Pradesh  
(C) Bengal  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q18.
Subhas Chandra Bose's famous slogan "Tum Mujhe Khoon Do, Main Tumhe Azadi Dunga" translates to:
(A) Give me victory, I will give you freedom  
(B) Give me blood, I will give you freedom  
(C) Give me strength, I will give you independence  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q19.
The Indian National Army (INA) was originally formed in 1942 by:
(A) Subhas Chandra Bose and Mohan Singh  
(B) Rash Behari Bose and Mohan Singh  
(C) JP Narayan and Subhas Chandra Bose  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q20.
Bismillah Khan, who received Bharat Ratna in 2001, was born in which district of Bihar?
(A) Patna  
(B) Muzaffarpur  
(C) Dumraon (Buxar)  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q21.
Rajendra Prasad Central Agricultural University is located in:
(A) Patna, Bihar  
(B) Pusa, Samastipur, Bihar  
(C) Muzaffarpur, Bihar  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q22.
Dr. Rajendra Prasad spent his last days and died at:
(A) Rajghat, Delhi  
(B) Sadaqat Ashram, Patna  
(C) Sevagram Ashram, Wardha  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q23.
Nehru wrote "The Discovery of India" while imprisoned in which fort?
(A) Red Fort, Delhi  
(B) Nahargarh Fort, Jaipur  
(C) Ahmadnagar Fort  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q24.
The Gandhi-Irwin Pact was signed in:
(A) 1930  
(B) 1931  
(C) 1932  
(D) More than one of the above  
(E) None of the above  

---

### GS-Q25.
Which of the following events occurred in Bihar specifically?
(A) Champaran Satyagraha (1917)  
(B) Rajendra Prasad imprisoned in Bankipur Jail during Quit India  
(C) Jayaprakash Narayan escaped from Hazaribagh Jail (1942)  
(D) More than one of the above  
(E) None of the above  

---

# ═══════════════════════════════════════════════════════════
# 📝 ANSWER KEY — DAY 13
# ═══════════════════════════════════════════════════════════

> ✅ Check your answers ONLY after attempting ALL 50 questions.

---

## 💻 CS ANSWERS

| Q# | Answer | Explanation |
|----|--------|-------------|
| CS-Q1 | (B) 5 7 | x=5; x++ prints 5 then x=6; ++x makes x=7 then prints 7 |
| CS-Q2 | (B) 5 | 7=0111, 5=0101, AND=0101=5 |
| CS-Q3 | (C) 7 | 6=0110, 3=0011, OR=0111=7 |
| CS-Q4 | (C) -6 | ~n = -(n+1); ~5 = -6 |
| CS-Q5 | (B) 6 | 5=0101, 3=0011, XOR=0110=6 |
| CS-Q6 | (E) None of the above | sizeof() does NOT evaluate expression; it does NOT increment x; it works with all types, not just basic |
| CS-Q7 | (B) | struct default = public; class default = private. ONLY difference |
| CS-Q8 | (B) | length is private by default in class — compile error |
| CS-Q9 | (C) 10 | struct members are public by default — no error; outputs 10 |
| CS-Q10 | (B) 9 | ++a makes a=4, b++ uses 5 → 4+5=9 |
| CS-Q11 | (B) | :: is used to define member functions outside class (also for global access and static members) |
| CS-Q12 | (B) | Friend function can access private members; it is NOT a member; does NOT use 'this' |
| CS-Q13 | (A) 2 | 8 >> 2 = 8 ÷ 4 = 2 |
| CS-Q14 | (C) 24 | 3 << 3 = 3 × 8 = 24 |
| CS-Q15 | (B) | n+1 means infinite recursion → stack overflow → segmentation fault |
| CS-Q16 | (C) 0 | A ^ A = 0 always |
| CS-Q17 | (C) A | A ^ 0 = A always |
| CS-Q18 | (C) | Friendship is neither mutual nor inherited in C++ |
| CS-Q19 | (C) | Friend can access private AND protected members |
| CS-Q20 | (B) 5 | sizeof(x++) does NOT evaluate x++; x remains 5 |
| CS-Q21 | (B) | In C, struct cannot have methods — only data |
| CS-Q22 | (C) 1 | true=1, false=0; 1+0=1 (int value 1) |
| CS-Q23 | (B) | ^ is bitwise XOR; && is logical AND; \| is bitwise OR |
| CS-Q24 | (B) 9 | 15=1111, 9=1001, AND=1001=9 |
| CS-Q25 | (D) More than one | All three: defined outside, accesses private, called like normal function — ALL are true |

---

## 🏛️ GS ANSWERS

| Q# | Answer | Explanation |
|----|--------|-------------|
| GS-Q1 | (C) Siwan | Born in Zeradei village, Siwan district, Bihar |
| GS-Q2 | (B) Two terms | 1950–1962; only president to serve two full terms |
| GS-Q3 | (C) 1962 | Bharat Ratna awarded in 1962, same year he retired |
| GS-Q4 | (B) Constituent Assembly | President of Constituent Assembly; Ambedkar chaired Drafting Committee |
| GS-Q5 | (C) Tinkathia System | Forced indigo cultivation on 3/20 parts of land |
| GS-Q6 | (C) Raj Kumar Shukla | Bihar farmer who persuaded Gandhi to visit Champaran |
| GS-Q7 | (A) 8 August 1942 | Movement LAUNCHED on Aug 8; leaders ARRESTED Aug 9 |
| GS-Q8 | (C) Quit India Movement | "Do or Die" (Karo ya Maro) — Quit India Movement 1942 |
| GS-Q9 | (B) Gowalia Tank Maidan, Bombay | Now called August Kranti Maidan |
| GS-Q10 | (C) Saran | Born in Sitabdiara village, Saran district, Bihar |
| GS-Q11 | (B) Jayaprakash Narayan | JP = Loknayak |
| GS-Q12 | (B) Bihar | JP movement started from Bihar (Bihar Movement 1974) |
| GS-Q13 | (B) Lahore Session | 1929 Lahore Session declared Purna Swaraj |
| GS-Q14 | (C) Jawaharlal Nehru | Nehru was Congress President at 1929 Lahore Session |
| GS-Q15 | (B) 12 March 1930 | Dandi March START date; ended April 6, 1930 at Dandi |
| GS-Q16 | (B) Second RTC (1931) | Gandhi attended only 2nd RTC; boycotted 1st and 3rd |
| GS-Q17 | (B) Uttar Pradesh | Chauri Chaura is in Gorakhpur district, UP (NOT Bihar) |
| GS-Q18 | (B) Give me blood, I will give you freedom | Correct translation of Bose's famous slogan |
| GS-Q19 | (B) Rash Behari Bose and Mohan Singh | INA formed in 1942 in Singapore; Subhas later took command |
| GS-Q20 | (C) Dumraon (Buxar) | Bismillah Khan born in Dumraon, now Buxar district, Bihar |
| GS-Q21 | (B) Pusa, Samastipur, Bihar | Named after Rajendra Prasad; major agricultural university |
| GS-Q22 | (B) Sadaqat Ashram, Patna | Died there on 28 February 1963 |
| GS-Q23 | (C) Ahmadnagar Fort | Nehru wrote Discovery of India at Ahmadnagar Fort jail |
| GS-Q24 | (B) 1931 | Gandhi-Irwin Pact: March 1931, before 2nd Round Table Conference |
| GS-Q25 | (D) More than one | ALL THREE events — Champaran, Bankipur Jail, Hazaribagh Jail — are in Bihar |

---

# ═══════════════════════════════════════════════════════════
# 🌙 NIGHT REVISION — 5 KEY BULLET POINTS (Day 13)
# ═══════════════════════════════════════════════════════════

## CS Points to Remember Tonight:
```
1. struct = public by default; class = private by default (ONLY difference in C++)
2. ~n = -(n+1)  |  A ^ A = 0  |  A ^ 0 = A  (XOR magic rules)
3. sizeof() does NOT evaluate — sizeof(x++) does not increment x
4. Recursive function with wrong direction (n+1 instead of n-1) → Segmentation Fault
5. Friend function: NOT a member, NO 'this' pointer, accesses private/protected,
   friendship is NOT mutual and NOT inherited
```

## GS Points to Remember Tonight:
```
1. Rajendra Prasad: Born Siwan (Zeradei), 1st President (2 terms), Bharat Ratna 1962
2. Champaran Satyagraha (1917): Gandhi's 1st Satyagraha in India; against Tinkathia system;
   Raj Kumar Shukla brought Gandhi; Rajendra Prasad was key supporter
3. Quit India (1942): "Do or Die"; Aug 8 launched; Gowalia Tank Maidan; Aruna Asaf Ali
4. Jayaprakash Narayan: Born Saran (Sitabdiara); Loknayak; escaped Hazaribagh Jail 1942;
   Bharat Ratna 1999 (posthumous)
5. Three Bharat Ratna from Bihar: Rajendra Prasad (1962), JP Narayan (1999), Bismillah Khan (2001)
```

---

# ═══════════════════════════════════════════════════════════
# ⚡ TOPPER TIPS — DAY 13 SPECIAL
# ═══════════════════════════════════════════════════════════

```
CS TIP 1: For bitwise questions, ALWAYS convert to binary first.
          Don't try to calculate in your head — draw the bits column by column.
          This takes 10 seconds and gives you 100% accuracy.

CS TIP 2: In output prediction questions, always check:
          - Is there pre/post increment?
          - Is there sizeof()?
          - Is it struct or class? (access specifier trap)

CS TIP 3: The answer "D — More than one of the above" often appears when
          a friend function question lists multiple correct properties.
          Watch for this pattern.

GS TIP 1: BPSC loves Bihar-specific questions. Always remember:
          Champaran → North Bihar → Rajendra Prasad was THERE.
          JP Narayan → Saran → Hazaribagh escape.
          Bismillah Khan → Dumraon → shehnai maestro.

GS TIP 2: For Gandhi's movements, remember the location pattern:
          Champaran (Bihar), Kheda (Gujarat), Ahmedabad (Gujarat),
          Dandi (Gujarat), Chauri Chaura (UP — NOT Bihar!),
          Quit India (Bombay).

GS TIP 3: Distinguish carefully:
          - Constituent Assembly President = Rajendra Prasad
          - Constituent Assembly Drafting Committee Chairman = B.R. Ambedkar
          BPSC traps you by mixing these two — they are DIFFERENT roles!
```

---

*Day 13 Complete | BPSC TRE 4.0 Preparation | Target: TOP RANK*
*Next: Day 14 — C++ Week Revision + Full PYQ Practice*
