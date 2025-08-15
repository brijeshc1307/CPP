### **Planystech.com - Interview Questions**

#### **Q1. Vehicle Number Plate Combinations**

> In a vehicle number plate, we have 4 integer digits. How many unique numbers can we make using these digits?

* **Assumption**: Each digit can be from 0 to 9.
* **If repetition is allowed**:
  Total combinations = $10 \times 10 \times 10 \times 10 = 10^4 = \boxed{10,000}$
* **If repetition is *not* allowed**:
  Total combinations = $10 \times 9 \times 8 \times 7 = \boxed{5,040}$

---

#### **Q2. Solve Linear Equations**

Solve the following system of equations:

```
2x + y = 1  
x  - 5y = 4
```

**Solution**:
From 2nd equation:
  $x = 4 + 5y$

Substitute into 1st:
  $2(4 + 5y) + y = 1$
  $8 + 10y + y = 1$
  $11y = -7 \Rightarrow y = -7/11$

Then,
  $x = 4 + 5(-7/11) = 4 - 35/11 = (44 - 35)/11 = 9/11$

 **Answer**: $\boxed{x = \frac{9}{11},\ y = -\frac{7}{11}}$

---

#### **Q3. Probability of Choosing 2 Queens from a Deck**

> What is the probability of selecting 2 Queens from a standard deck of 52 cards?

* Total ways to choose 2 cards from 52 = $\binom{52}{2} = 1326$
* Ways to choose 2 Queens = $\binom{4}{2} = 6$
* Probability = $\frac{6}{1326} = \boxed{\frac{1}{221}} \approx 0.452\%$

---

#### **Q4. C++ Array Program (Fix the Error)**

```cpp
#include <iostream>
// Fix the incorrect header
#include <vector>
using namespace std;

/*
1. Define integer array {1,2,3,4,5}
2. Calculate the size of the array
3. Print each element on a newline
*/

int main() {
    int arr[] = {1, 2, 3, 4, 5};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Array size: " << n << endl;
    for (int i = 0; i < n; ++i) {
        cout << arr[i] << endl;
    }
    return 0;
}
```

 Fixes:

* `#include <bits/stdc++.h>` (not `<bits/sdtc++>`)
* Used `sizeof(arr)` instead of `arr.size()`, which works only for vectors.

---

#### **Q5. Insert at Position in Array vs List**
#### **Q5.1. How to Insert, access, delete an Element at 1st and 3rd Position in Array vs Linked List also tell me time complexty


| **Operation**              | **Array**                                                 | **Time** | **Linked List**                                                    | **Time** |
| -------------------------- | --------------------------------------------------------- | -------- | ------------------------------------------------------------------ | -------- |
| **Insert at 1st position** | Shift all elements to the right → Insert at `arr[0]`      | O(n)     | Create a new node → Point it to current head → Update head pointer | O(1)     |
| **Insert at 3rd position** | Shift elements from index 2 onward → Insert at `arr[2]`   | O(n)     | Traverse to 2nd node → Insert after it                             | O(n)     |
| **Access 1st element**     | Access `arr[0]`                                           | O(1)     | Access `head`                                                      | O(1)     |
| **Access 3rd element**     | Access `arr[2]`                                           | O(1)     | Traverse two nodes from `head`                                     | O(n)     |
| **Delete 1st element**     | Shift all elements left from index 1 → Remove `arr[0]`    | O(n)     | Update `head` to point to next node                                | O(1)     |
| **Delete 3rd element**     | Shift elements left from index 3 onward → Remove `arr[2]` | O(n)     | Traverse to 2nd node → Change pointer to skip 3rd node             | O(n)     |

---

### 🔍 Summary:

* **Arrays** provide **fast random access** but are **expensive for insert/delete** at arbitrary positions.
* **Linked Lists** allow **efficient insert/delete at the beginning**, but **slow access and insert** at arbitrary positions due to traversal.


---

#### **Q6. Binary Search vs Linear Search**

**Linear Search (Unsorted or Sorted List)**:

```cpp
int linearSearch(int arr[], int n, int key) {
    for (int i = 0; i < n; ++i)
        if (arr[i] == key) return i;
    return -1;
}
```

**Binary Search (Sorted List only)**:

```cpp
int binarySearch(int arr[], int low, int high, int key) {
    while (low <= high) {
        int mid = (low + high) / 2;
        if (arr[mid] == key) return mid;
        else if (arr[mid] < key) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}
```

 **Complexity**:

* Linear Search: O(n)
* Binary Search: O(log n)

---

#### **Q7. How to Check Connection to Another Computer in Linux**

```bash
ping <IP_ADDRESS>       # Basic reachability
telnet <IP> <PORT>      # Check if specific port is open (if installed)
ssh <user>@<IP_ADDRESS> # Try connecting via SSH
```

---

#### **Q8. How to Check Your IP in Linux**

```bash
hostname -I           # Shows all IPs assigned
ifconfig              # (Old) shows network info
ip addr show          # (Modern replacement)
```

---

### **XYZ Company - Interview Questions**

---

#### **Q1. Function Overloading — Write Program**

 **Definition**:
Function Overloading allows multiple functions with the same name but different parameter types or counts.

### Example:

```cpp
#include <iostream>
using namespace std;

class Print {
public:
    void show(int a) {
        cout << "Integer: " << a << endl;
    }

    void show(double b) {
        cout << "Double: " << b << endl;
    }

    void show(string s) {
        cout << "String: " << s << endl;
    }
};

int main() {
    Print obj;
    obj.show(10);
    obj.show(3.14);
    obj.show("Hello");
    return 0;
}
```

 **Output**:

```
Integer: 10  
Double: 3.14  
String: Hello
```

---

#### **Q2. Method Overriding — Write Program**

 **Definition**:
**Method Overriding** happens in **inheritance**, where a **child class redefines a base class function** using the same signature.
Requires **virtual** keyword for polymorphism.

### Example:

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    virtual void sound() {
        cout << "Animal makes sound" << endl;
    }
};

class Dog : public Animal {
public:
    void sound() override {
        cout << "Dog barks" << endl;
    }
};

int main() {
    Animal* a;        // Base class pointer
    Dog d;
    a = &d;
    a->sound();       // Calls Dog's version due to virtual function
    return 0;
}
```

 **Output**:

```
Dog barks
```

---

#### **Q3. Dynamic Allocation — Explain with Example**

 **Explanation**:
Dynamic memory allocation allows memory to be allocated during **runtime** using the `new` keyword in C++.

```cpp
int* p = new int;
```

* `int* p` → Declares a pointer to an integer.
* `new int` → Allocates memory for one `int` on the heap and returns its address.
* `p` now points to that memory.

You can assign value like this:

```cpp
*p = 42;
cout << *p << endl;  // Output: 42
```

 **Important**:
After usage, free memory using:

```cpp
delete p;
```

### Full Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    int* p = new int;  // Dynamic allocation
    *p = 42;           // Assign value
    cout << "Value at p: " << *p << endl;

    delete p;          // Free memory
    return 0;
}
```

 **Output**:

```
Value at p: 42
```

---
### **63 Moons - Interview Questions**
---

##  **C++ Core Concepts**

### 1. **Describe `static` and `const` variables in C++.**

* **`static`**: A static variable retains its value between function calls. It is initialized only once.
* **`const`**: A `const` variable cannot be modified after initialization. It enforces read-only access.

### 2. **What are storage classes in C++ and their types?**

* Storage classes define scope, lifetime, and visibility of variables.
* Types:

  * `auto`
  * `register`
  * `static`
  * `extern`
  * `mutable` (special case for class members)

### 3. **What is a copy constructor? Why define it manually in C++?**

* A **copy constructor** initializes an object using another object of the same class.
* C++ provides a default one, but:

  * You define it manually to handle **deep copies**, especially when your class manages dynamic memory (pointers).

### 4. **What is the use of pointers in C++?**

* Pointers are used to:

  * Access memory directly
  * Allocate dynamic memory (`new` / `delete`)
  * Enable function parameters to be passed by reference
  * Build complex structures like linked lists and trees

### 5. **What is call by value and call by reference?**

* **Call by Value**: A copy of the argument is passed. Changes don’t affect the original variable.
* **Call by Reference**: The actual variable is passed using references (`&`), so changes affect the original.

### 6. **What is a namespace in C++?**

* A **namespace** groups named entities (like functions, classes) to avoid name conflicts.
* Example:

  ```cpp
  namespace MySpace {
      int val = 10;
  }
  ```

---

##  **OOP (Object-Oriented Programming)**

### 7. **What are the basic OOP concepts in C++?**

### 8. **Explain method overloading vs overriding.**

### 9. **What is an abstract class in C++?**

* A class with at least one **pure virtual function**.
* Cannot be instantiated, only inherited.

  ```cpp
  class Shape {
      virtual void draw() = 0;
  };
  ```

---

##  **STL and Multithreading**

### 10. **Basics of STL in C++?**

* STL (Standard Template Library) provides:

  * **Containers**: vector, list, map, etc.
  * **Algorithms**: sort, find, etc.
  * **Iterators**: like pointers to navigate containers

### 11. **What is multithreading in C++?**

---

##  **Advanced Concepts**

### 12. **What is memory leak in C++?**

* Memory that is allocated but never deallocated.
* Causes:

  * Missing `delete` after `new`
  * Losing pointer reference to allocated memory

### 13. **How to convert 2 stacks into a heap?**

* **If you mean implementing a heap using two stacks:**

  * This is unconventional; heaps are best implemented with arrays or vectors.
  * Two stacks are more suited for simulating queues or tracking call stacks.
  * Clarify this question if it was metaphorical or a misstatement.

---

##  **Miscellaneous**

### 14. **What’s your favorite DSA question?**

---
### **HCL - Interview Questions**
Round 1: 20 MCQ, 1 Program for 1hr
---

### **1. If A + B means A is the mother of B; A - B means A is the brother of B; A % B means A is the father of B and A x B means A is the sister of B, which of the following shows that P is the maternal uncle of Q?**

**Options:**

* (A) Q - N + M x P
* (B) P + S x N - Q
* (C) P - M + N x Q
* (D) Q - S % P

**Solution:**

We want:
**P is male (brother) of Q’s mother** ⇒ "maternal uncle"

Check Option (C): `P - M + N x Q`
→ `P - M`: P is **brother** of M
→ `M + N`: M is **mother** of N
→ `N x Q`: N is **sister** of Q

So M is Q's mother, and P is her brother ⇒ **P is maternal uncle of Q**

**Correct Answer: (C) P - M + N x Q**

---

### **2. Reena took a loan of Rs. 1200 with simple interest for as many years as the rate of interest. If she paid Rs. 432 as interest at the end of the loan period, what was the rate of interest?**

**Options:**
A. 3, B. 6, C. 18, D. Cannot be determined, E. None of these

**Solution:**

Let rate = time = `x` years
SI = (P × R × T) / 100 = (1200 × x × x) / 100 = 432
→ 12x² = 432
→ x² = 36
→ x = 6

**Correct Answer: 6**

---

### **3. A alone can do a piece of work in 6 days and B alone in 8 days. A and B undertook to do it for Rs. 3200. With the help of C, they completed the work in 3 days. How much is to be paid to C?**

**Options:**
A. Rs. 375, B. Rs. 400, C. Rs. 600, D. Rs. 800

**Solution:**

* A’s 1-day work = 1/6
* B’s 1-day work = 1/8
* Together in 1 day: A + B = (1/6 + 1/8) = 7/24
* In 3 days: 3 × 7/24 = 7/8
* So, C did (1 - 7/8) = 1/8 of work
* C’s share = 1/8 × 3200 = ₹400

**Correct Answer: ₹400**

---

### **4. If a person walks at 14 km/hr instead of 10 km/hr, he would have walked 20 km more. The actual distance travelled by him is:**

**Options:**
A.50 km,  B.56 km,  C.70 km,  D.80 km

**Solution:**

Let time = t hours
Distance at 14 km/h = 14t
Distance at 10 km/h = 10t
Difference = 14t - 10t = 4t = 20
→ t = 5
→ Actual distance = 10 × 5 = **50 km**

**Correct Answer: 50 km**

---

### **5. A train running at the speed of 60 km/hr crosses a pole in 9 seconds. What is the length of the train?**

**Options:**
A.120 m,  B.180 m,  C.324 m,  D.150 m

**Solution:**
* Speed = 60 km/hr = (60 × 1000) / 3600 = 16.67 m/s
* Length = speed × time = 16.67 × 9 ≈ **150 m**

 **Correct Answer: 150 metres**

---

### **6. Three unbiased coins are tossed. What is the probability of getting at most two heads?**

**Options:**
A.3/4  B.1/4  C.3/8  D.7/8
 **Solution:**
Total outcomes = 2³ = 8
Favorable outcomes for **at most 2 heads** = all except 3 heads = 7 outcomes
→ Probability = 7/8

**Correct Answer: D. 7/8**
---
### **7. Given a sentence, rearrange the words in order of increasing length. The first word in the resulting sentence should be capitalized, and all other words should be in lowercase. Ignore punctuation and the original capitalization of words, except that the first word in the final result must start with a capital letter.

*Input:*
A sentence: "The quick brown fox jumps over the lazy dog"

*Output:*
"The fox the dog over lazy quick brown jumps"

 **Solution:**
 ```cpp
#include <iostream>
#include <sstream>
#include <vector>
#include <algorithm>
#include <cctype>

using namespace std;

// Function to convert a string to lowercase
string toLower(const string& str) {
    string result = str;
    for (char& c : result)
        c = tolower(c);
    return result;
}

// Function to capitalize the first character
string capitalizeFirst(const string& str) {
    if (str.empty()) return str;
    string result = toLower(str);
    result[0] = toupper(result[0]);
    return result;
}

int main() {
    string sentence = "The quick brown fox jumps over the lazy dog";
    stringstream ss(sentence);
    string word;
    vector<string> words;

    // Split sentence into words
    while (ss >> word) {
        // Remove punctuation
        word.erase(remove_if(word.begin(), word.end(), ::ispunct), word.end());
        words.push_back(toLower(word));
    }

    // Sort by word length
    sort(words.begin(), words.end(), [](const string& a, const string& b) {
        return a.length() < b.length();
    });

    // Capitalize the first word
    if (!words.empty()) {
        words[0] = capitalizeFirst(words[0]);
    }

    // Print result
    for (size_t i = 0; i < words.size(); ++i) {
        cout << words[i];
        if (i != words.size() - 1) cout << " ";
    }

    return 0;
}

```
Output
```
The fox the dog over lazy quick brown jumps
```
---
### **8. Given a string s, return the first character that does not repeat (i.e., appears exactly once) in the string.
If there is no such character, return -1.

You must return the character as-is (not index), or -1 if no unique character is found.

Function Signature:

char firstUniqueChar(const std::string& s);
Input:

A single string s consisting of lowercase English letters ('a' to 'z').
1 <= s.length <= 10^5
Output:

Return the first non-repeating character in the string.
If no such character exists, return -1.
Examples:

Input: "abbacddhh"
Output: 'c'

Input: "abacdhdh"
Output: 'b'

Input: "abbaddhh"
Output: -1
Constraints:

The input string contains only lowercase English letters.
Must return the first non-repeating character in order of appearance.
Return character as char, and return -1 if none found.

 **Solution:**
```cpp
#include <iostream>
#include <unordered_map>
#include <string>

char firstUniqueChar(const std::string& s) {
    std::unordered_map<char, int> freq;

    // First pass: Count frequencies
    for (char ch : s) {
        freq[ch]++;
    }

    // Second pass: Find first character with frequency 1
    for (char ch : s) {
        if (freq[ch] == 1)
            return ch;
    }

    // If no unique character
    return -1;
}
int main() {
    cout << firstUniqueChar("abbacddhh") << endl; // Output: c
    cout << firstUniqueChar("abacdhdh") << endl;  // Output: b
    cout << firstUniqueChar("abbaddhh") << endl;  // Output: -1
    return 0;
}
```
Output
```
c
b
-1
```
---
### **9. A faulty watch loses 20 seconds every 3 hours. It was set correctly at 2:00 AM. What is the correct time when the watch shows 6:30 PM the next day?

**A.** 6:28:15 PM
**B.** 6:34:30 PM
**C.** 6:36:00 PM
**D.** 6:32:45 PM

**Correct Answer: B. 6:34:30 PM**

* Watch loses 20 seconds every 3 hours.
* Total time from 2:00 AM to 6:30 PM next day = 40.5 hours.
* Number of 3-hour intervals in 40.5 hours = 40.5 ÷ 3 = 13.5.
* Total loss = 13.5 × 20 seconds = 270 seconds = 4 minutes 30 seconds.
* When watch shows 6:30 PM, actual time = 6:30 PM + 4 min 30 sec = **6:34:30 PM**.

**Answer: 6:34:30 PM**
---
Round 2: F2F Interview 30 min
---

### Q1. What is OOP? Explain all pillars with examples.

---

### Q2. Explain function overriding and write a program and explain code.
---

### Q3. Map, Array vs Map, Vector, Vector vs Array

* **Map:** Associative container storing key-value pairs (sorted by key).
* **Array:** Fixed-size collection of elements (contiguous memory).
* **Vector:** Dynamic array (resizable, provides many utility functions).

| Feature  | Array              | Vector               | Map                         |
| -------- | ------------------ | -------------------- | --------------------------- |
| Size     | Fixed              | Dynamic              | Dynamic                     |
| Memory   | Contiguous         | Contiguous           | Node-based (not contiguous) |
| Access   | Fast (index-based) | Fast (index-based)   | Key-based                   |
| Use case | When size is known | When size can change | Key-value storage           |

---

### Q5. What does this code do?

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    []{}();
    return 0;
}
```

* Defines and immediately calls an **empty [lambda](/LambdaExpressions.md) function**. The program does nothing visible and returns 0.

---

### Q6. Is this code valid? Why or why not?

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int a;
    int &&b = a;
    return 0;
}
```
* Status :Compilation error
* **Invalid.**
* You cannot bind an **rvalue reference** (`int&&`) to an **lvalue** (`a`).
* Correct usage: `int&& b = 5;` or use `std::move(a)` to cast `a` to an rvalue.
---
### **Lvalue**

* An **Lvalue** refers to an **object that has a name and a memory address**.
* You can take the address of an lvalue.
* Can appear on the **left-hand side** of an assignment.

**Example:**

```cpp
int x = 10;   // x is an lvalue
x = 20;       // OK: lvalue can be assigned
```

### **Lvalue Reference** (`&`) 
* An lvalue reference in C++ is a reference (alias) to an lvalue — that is, a variable or object that has a persistent memory address.
* It is declared using a single ampersand &.

**Example:**
```cpp
int x = 10;
int& ref = x;   // ref is an lvalue reference to x
```
---

### **Rvalue**

* An **Rvalue** is a **temporary object** or literal with **no persistent memory address**.
* Can only appear on the **right-hand side** of an assignment.
* **Cannot take its address**.

**Example:**

```cpp
int y = x + 5;   // (x + 5) is an rvalue
```

---

### **Rvalue Reference** (`&&`)

* Introduced in C++11.
* Allows binding to **rvalues (temporaries)**.
* Enables **move semantics** and optimization by avoiding deep copies.

**Syntax:**

```cpp
void process(int&& r) {
    std::cout << "Rvalue reference: " << r << std::endl;
}
```

---

###  **Rvalue Reference vs Lvalue Reference:**

| Feature  | Lvalue Reference (`&`)   | Rvalue Reference (`&&`)      |
| -------- | ------------------------ | ---------------------------- |
| Binds to | Named objects (lvalues)  | Temporary objects (rvalues)  |
| Use case | Normal parameter passing | Move semantics, optimization |
| Example  | `int& a = x;`            | `int&& b = 5;`               |

---

### **Code Example**: Lvalue vs Rvalue Reference

```cpp
#include <iostream>
#include <utility>

void foo(int& x) {
    std::cout << "Lvalue reference called: " << x << "\n";
}

void foo(int&& x) {
    std::cout << "Rvalue reference called: " << x << "\n";
}

int main() {
    int a = 10;
    foo(a);        // Calls lvalue version
    foo(20);       // Calls rvalue version
    foo(std::move(a)); // Forces rvalue, calls rvalue version
}
```

**Output:**

```
Lvalue reference called: 10
Rvalue reference called: 20
Rvalue reference called: 10
```

---

### Q7. Print the pattern:

```
      * * * * 
    * * * * 
  * * * * 
* * * * 
```

**Corrected (aligned) version:**

```cpp
#include <iostream>
using namespace std;

int main() {
    for(int i = 4; i >= 1; i--) {
        for(int j = 1; j < i; j++) cout << "  ";
        for(int k = 1; k <= 4; k++) cout << "* ";
        cout << "\n";
    }
    /* OR
    for(int i = 1; i <= 4; i++) {
        for(int j = i; j < 4; j++) cout << "  ";
        for(int k = 1; k <= 4; k++) cout << "* ";
        cout << "\n";
    }*/

    return 0;
}
```
Output
```
      * * * * 
    * * * * 
  * * * * 
* * * * 
```

### Q8. pointer vs refrence?

| Feature            | Pointer                                                               | Reference                                                             |
| ------------------ | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| **Definition**     | A variable that holds the address of another variable.                | An alias for another variable.                                        |
| **Syntax**         | `int* p;`                                                             | `int& r = x;`                                                         |
| **Initialization** | Can be initialized to `nullptr` or any address; can be uninitialized. | Must be initialized when declared; cannot be null.                    |
| **Reassignment**   | Can point to different variables during its lifetime.                 | Cannot be reseated; always refers to the original variable.           |
| **Dereferencing**  | Requires `*` operator to access value.                                | Acts like the variable itself; no extra syntax needed.                |
| **Memory**         | Takes its own memory (stores an address).                             | No extra memory; just another name for the variable.                  |
| **Nullability**    | Can be null (i.e., point to nothing).                                 | Cannot be null.                                                       |
| **Use cases**      | Dynamic data structures, optional referencing, pointer arithmetic.    | Pass-by-reference in functions, operator overloading, safer aliasing. |

---

### Example:

```cpp
int x = 10;

// Pointer
int* p = &x;
*p = 20;   // Changes x to 20

// Reference
int& r = x;
r = 30;    // Changes x to 30

// Reassign pointer
int y = 40;
p = &y;    // Now p points to y

// Reference cannot be reassigned
// r = y;  // This assigns value of y to x, but r still refers to x
```
---
### Q9. Is this code valid? Why or why not?
```cpp
#include <iostream>

int main() {
    int&& r1 = 10;     // OK: rvalue reference binds to a literal (rvalue)
    std::cout << r1 << "\n";  // prints 10

    // int a = 5;
    // int&& r2 = a;   // ERROR: cannot bind rvalue reference to lvalue

    return 0;
}
```
Output
```
10
```
### Explanation:

* `int&& r1 = 10;` is **valid** because `10` is an rvalue (a temporary literal), and rvalue references can bind to rvalues.
* Uncommenting the lines:

  ```cpp
  int a = 5;
  int&& r2 = a;   // ERROR
  ```

  would produce an error because `a` is an lvalue, and an rvalue reference cannot bind directly to an lvalue.

---

### Additional notes:

* If you want to bind an rvalue reference to an lvalue, you have to explicitly cast it to an rvalue using `std::move` or `std::forward`:

```cpp
int a = 5;
int&& r2 = std::move(a);  // OK: std::move converts lvalue to rvalue
```
---
### **Gentrack.com - Interview Questions**
---
### ** STL Containers Comparison Table**

| **Container**        | **Header**        | **Underlying Structure** | **Order Maintained** | **Duplicates Allowed** | **Random Access** | **Insertion/Deletion Efficiency** | **Use Case**                          |
| -------------------- | ----------------- | ------------------------ | -------------------- | ---------------------- | ----------------- | --------------------------------- | ------------------------------------- |
| `array`              | `<array>`         | Static array             | Yes                  | Yes                    | ✅ Yes             | ❌ Fixed-size, inefficient         | Fixed-size array with bounds checking |
| `vector`             | `<vector>`        | Dynamic array            | Yes                  | Yes                    | ✅ Yes             | ✅ End: O(1), Middle: O(n)         | Dynamic resizing, fast access         |
| `deque`              | `<deque>`         | Double-ended array       | Yes                  | Yes                    | ✅ Yes             | ✅ Front/Back: O(1)                | Insert/remove at both ends            |
| `queue`              | `<queue>`         | Adapter over `deque`     | Yes (FIFO)           | Yes                    | ❌ No              | ✅ Front/Back: O(1)                | FIFO queue                            |
| `forward_list`       | `<forward_list>`  | Singly linked list       | Yes                  | Yes                    | ❌ No              | ✅ O(1) insert/delete after node   | Lightweight linked list               |
| `list`               | `<list>`          | Doubly linked list       | Yes                  | Yes                    | ❌ No              | ✅ O(1) insert/delete anywhere     | Frequent insertion/deletion           |
| `set`                | `<set>`           | Balanced BST (Red-Black) | Yes (sorted)         | ❌ No                   | ❌ No              | ✅ O(log n)                        | Unique sorted elements                |
| `multiset`           | `<set>`           | Balanced BST             | Yes (sorted)         | ✅ Yes                  | ❌ No              | ✅ O(log n)                        | Sorted with duplicates                |
| `map`                | `<map>`           | Balanced BST             | Yes (sorted by key)  | ❌ No (unique keys)     | ❌ No              | ✅ O(log n)                        | Key-value pairs, unique keys          |
| `multimap`           | `<map>`           | Balanced BST             | Yes                  | ✅ Yes (duplicate keys) | ❌ No              | ✅ O(log n)                        | Multiple values per key               |
| `unordered_set`      | `<unordered_set>` | Hash table               | ❌ No                 | ❌ No                   | ❌ No              | ✅ Avg O(1), Worst O(n)            | Fast lookup, unique elements          |
| `unordered_multiset` | `<unordered_set>` | Hash table               | ❌ No                 | ✅ Yes                  | ❌ No              | ✅ Avg O(1), Worst O(n)            | Fast lookup with duplicates           |
| `unordered_map`      | `<unordered_map>` | Hash table               | ❌ No                 | ❌ No (unique keys)     | ❌ No              | ✅ Avg O(1), Worst O(n)            | Key-value with fast access            |
| `unordered_multimap` | `<unordered_map>` | Hash table               | ❌ No                 | ✅ Yes (duplicate keys) | ❌ No              | ✅ Avg O(1), Worst O(n)            | Key-value pairs with duplicates       |

---

### 📌 Tips for Use

* Use **`vector`** when you need fast random access and dynamic resizing.
* Use **`list`/`forward_list`** when frequent insertions/deletions happen at arbitrary positions.
* Use **`set`/`map`** for sorted elements with fast lookup.
* Use **`unordered_set`/`unordered_map`** for faster average lookups when ordering is not needed.
* Use **`deque`** if you need to insert/remove from both front and back.
* Use **`queue`** or **`stack`** when order of processing (FIFO/LIFO) is needed.

---

###  **Q1. Remove duplicate elements while maintaining the order**

**Problem Statement:**
Write a C++ program to remove duplicate elements from an array while maintaining the original order of appearance.

```cpp
#include <iostream>
#include <vector>
#include <unordered_set>
using namespace std;

vector<int> removeDuplicates(vector<int>& nums) {
    unordered_set<int> seen;
    vector<int> result;
    for (int num : nums) {
        if (seen.find(num) == seen.end()) {
            seen.insert(num);
            result.push_back(num);
        }
    }
    return result;
}

int main() {
    vector<int> nums = {1, 2, 2, 3, 4, 1, 5};
    vector<int> res = removeDuplicates(nums);
    for (int num : res) cout << num << " ";
}
```

---

###  **Q2. In-place Transpose of a Matrix**

**Problem Statement:**
Write a C++ function to transpose a square matrix in-place.

```cpp
#include <iostream>
using namespace std;

void transpose(int matrix[][3], int n) {
    for (int i = 0; i < n; i++)
        for (int j = i + 1; j < n; j++)
            swap(matrix[i][j], matrix[j][i]);
}

int main() {
    int mat[3][3] = {{1,2,3}, {4,5,6}, {7,8,9}};
    transpose(mat, 3);
    for (int i = 0; i < 3; i++){
        for (int j = 0; j < 3; j++)
            cout << mat[i][j] << " ";
        cout << endl;
    }
}
```

---

###  **Q3. Find the second highest income in SQL**

```sql
SELECT MAX(salary) AS SecondHighest
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

---

###  **Q4. Generate Fibonacci Sequence (first N terms)**

```cpp
#include <iostream>
using namespace std;

void fibonacci(int n) {
    int a = 0, b = 1, next;
    cout << a << " " << b << " ";
    for (int i = 2; i < n; ++i) {
        next = a + b;
        cout << next << " ";
        a = b;
        b = next;
    }
}

int main() {
    fibonacci(10);
}
```

---

###  **Q5. FizzBuzz Problem**

**Problem Statement:**
Print numbers from 1 to N. For multiples of 3 print "Fizz", for 5 print "Buzz", and for both print "FizzBuzz".

```cpp
#include <iostream>
using namespace std;

void fizzBuzz(int n) {
    for (int i = 1; i <= n; i++) {
        if (i % 15 == 0) cout << "FizzBuzz\n";
        else if (i % 3 == 0) cout << "Fizz\n";
        else if (i % 5 == 0) cout << "Buzz\n";
        else cout << i << endl;
    }
}

int main() {
    fizzBuzz(20);
}
```

---

###  **Q6. Why should we hire you?**

**Answer (Example):**

> "You should hire me because I have a strong foundation in programming, problem-solving, and experience with real-world projects. I adapt quickly to new technologies and consistently strive for excellence. I'm not only technically sound but also a good team player who believes in contributing to overall project success."

---

###  **Q7. What is the Bin-Packing Problem?**

**Answer:**

> The Bin Packing Problem is an NP-Hard optimization problem where you aim to pack objects of different sizes into a finite number of bins of fixed capacity in a way that minimizes the number of bins used.

---

###  **Q8. Calculate the Fibonacci Sequence (Recursive version)**

```cpp
#include <iostream>
using namespace std;

int fibonacci(int n) {
    if (n <= 1) return n;
    return fibonacci(n - 1) + fibonacci(n - 2);
}

int main() {
    int n = 10;
    for (int i = 0; i < n; i++)
        cout << fibonacci(i) << " ";
}
```

---

###  **Q9. FizzBuzz Test**

(Already covered in Q5)

---

###  **Q10. Difference between Array and ArrayList**

| Array                     | ArrayList                               |
| ------------------------- | --------------------------------------- |
| Fixed size                | Dynamic size                            |
| Can store primitive types | Stores objects only                     |
| Faster access             | Slight overhead due to dynamic resizing |
| No in-built methods       | Rich set of methods (add, remove, etc.) |

(*Note: ArrayList is from Java, not applicable in C++ but similar to `vector` in STL*)

---

### **Q11. Difference between List, Set, and HashMap**

| Feature        | List                      | Set                            | HashMap              |
| -------------- | ------------------------- | ------------------------------ | -------------------- |
| Order          | Maintains insertion order | Unordered or insertion ordered | Unordered            |
| Duplicates     | Allowed                   | Not allowed                    | Keys must be unique  |
| Example in C++ | `std::vector`             | `std::unordered_set`           | `std::unordered_map` |

---

### **Q12. Describe LinkedList**
---

### **Q13. Implementations of a List in C++**

### **Q14. **Nearest Floor Request in Given Direction**

### 📝 Problem Description:

A lift (elevator) is currently at a floor and moving in a specific direction (`"Up"` or `"Down"`). It has received exactly 3 floor requests from users waiting on different floors.

Write a function to determine **which one of the requested floors is nearest to the current floor in the same direction as the lift is moving**.
Return that floor number.

If no floor request is valid in the given direction, return `-1`.

---

### 🔧 Function Signature:

```cpp
int nearestFloor(int currLocation, string curDir, vector<int>& demandArr);
```

---

### 🧪 Input:

* `currLocation` (1 ≤ currLocation ≤ 100): current floor of the lift
* `curDir`: a string `"Up"` or `"Down"` representing the direction
* `demandArr`: a list of 3 integers (1 ≤ demandArr\[i] ≤ 100) representing requested floors

---

### 📤 Output:

* Return the floor that is closest to `currLocation` in the specified `curDir` direction.
* If no valid floor in the given direction exists, return `-1`.

---

### ✅ Example 1:

```cpp
Input: 
currLocation = 5  
curDir = "Down"  
demandArr = [2, 4, 6]

Output: 
4

Explanation:
Valid "Down" requests (i.e. less than 5): 2, 4  
Among these, 4 is the closest to 5.
```

---

```cpp
#include <iostream>
#include <string>
#include <climits>
using namespace std;

int main() {
    int demandArr[3];
    int currLocation;
    string curDir;

    cin >> currLocation;
    cin >> curDir;

    for (int i = 0; i < 3; i++) {
        cin >> demandArr[i];
    }

    int nearest = -1;
    int minDiff = INT_MAX;

    if (curDir == "Up") {
        for (int i = 0; i < 3; i++) {
            if (demandArr[i] > currLocation) {
                int diff = demandArr[i] - currLocation;
                if (diff < minDiff) {
                    minDiff = diff;
                    nearest = demandArr[i];
                }
            }
        }
    } else if (curDir == "Down") {
        for (int i = 0; i < 3; i++) {
            if (demandArr[i] < currLocation) {
                int diff = currLocation - demandArr[i];
                if (diff < minDiff) {
                    minDiff = diff;
                    nearest = demandArr[i];
                }
            }
        }
    } else {
        cout << "Invalid direction\n";
        return 1;
    }

    if (nearest != -1) {
        cout << "Stop at floor: " << nearest << endl;
    } else {
        cout << "No valid floor in the given direction.\n";
    }

    return 0;
}
```

---
#### Input:

```
5
Down
2 4 1
```

#### Output:

```
Stop at floor: 4
```

*(Among 2, 4, 1, only 4 is just below 5 and is the closest.)*

#### Input:

```
3
Up
6 5 9
```

#### Output:

```
Stop at floor: 5
```

---
### iQuest - Interview Questions**
Round 1: 1hr

Q1. [lambda](/LambdaExpressions.md) Function: In C++, the syntax `[]() {}` is the basic structure of a **lambda function**. Let's break it down:

## Syntax:

```cpp
[capture](parameter_list) -> return_type { function_body }
```

Your minimal example:

```cpp
[]() {}
```

Means:

* `[]` → Capture list (what variables you want to access from outside)
* `()` → Parameters (like a normal function)
* `{}` → Function body (what the lambda does)

---

## Detailed Breakdown

| Part                          | Description                                                                     |
| ----------------------------- | ------------------------------------------------------------------------------- |
| `[]`                          | **Capture list** – lets the lambda access variables from the surrounding scope. |
| `()`                          | **Parameter list** – like arguments to a function.                              |
| `{}`                          | **Function body** – code to run when lambda is called.                          |
| `-> return_type` *(optional)* | Specifies return type (can often be omitted if deducible).                      |


##  Example 1: Basic Lambda

```cpp
auto greet = []() {
    cout << "Hello from lambda!" << endl;
};
greet();
```

**Output:**

```
Hello from lambda!
```

##  Example 2: With Parameters

```cpp
auto add = [](int a, int b) {
    return a + b;
};
cout << add(3, 4);  // Output: 7
```
##  Example 3: With Capture List

```cpp
int x = 10;
auto show = [x]() {
    cout << "Captured x = " << x << endl;
};
show();
```
##  Example 4
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    vector<int> v = {5, 2, 8, 1, 3};

    // Lambda to sort in ascending order
    sort(v.begin(), v.end(), [](int a, int b) {
        return a < b;
    });

    // Lambda to print elements
    auto print = [](int x) {
        cout << x << " ";
    };

    for_each(v.begin(), v.end(), print);
    return 0;
}
```

**Output:**

```
1 2 3 5 8
```
---

## Q2. Check Palindrome String (Iterative + Recursive)

### Iterative Method

```cpp
bool isPalindromeIter(string s) {
    int start = 0, end = s.length() - 1;
    while (start < end) {
        if (s[start] != s[end]) return false;
        start++;
        end--;
    }
    return true;
}
```

### Recursive Method

```cpp
bool isPalindromeRec(string s, int start, int end) {
    if (start >= end)
        return true;
    if (s[start] != s[end])
        return false;
    return isPalindromeRec(s, start + 1, end - 1);
}
```

### Usage

```cpp
#include <iostream>
using namespace std;

int main() {
    string str;
    cout << "Enter string: ";
    cin >> str;

    cout << "Iterative: " << (isPalindromeIter(str) ? "Yes" : "No") << endl;
    cout << "Recursive: " << (isPalindromeRec(str, 0, str.size() - 1) ? "Yes" : "No") << endl;
    return 0;
}
```

---

## Q3. Pass by Value vs Pass by Reference

```cpp
#include <iostream>
using namespace std;

// Pass by Value
void incrementByValue(int x) {
    x++; // Only modifies local copy
}

// Pass by Reference using &
void incrementByRef1(int &x) {
    x++; // Modifies original variable
}

// Pass by Reference using *
void incrementByRef2(int *x) {
    (*x)++; // Modifies original variable via pointer
}

int main() {
    int a = 5;

    incrementByValue(a);
    cout << "After pass by value: " << a << endl; // Outputs 5

    incrementByRef1(a);
    cout << "After pass by reference (&): " << a << endl; // Outputs 6

    incrementByRef2(&a);
    cout << "After pass by reference (*): " << a << endl; // Outputs 7

    return 0;
}

```

**Output:**

```
After pass by value: 5
After pass by reference (&): 6
After pass by reference (*): 7
```

---

## Q4. Count Binary Substrings Starting and Ending with 1
```cpp
#include <iostream>
using namespace std;

int main() {
    string str;
    int count = 0;
    cin >> str;

    int n = str.size();

    // Check all substrings
    for (int i = 0; i < n; i++) {
        if (str[i] == '1') {
            for (int j = i + 1; j < n; j++) {
                if (str[j] == '1') {
                    count++;
                }
            }
        }
    }

    cout << count;
    return 0;
}
```
```
Sample Input
00100101
Output
3
```
### Optimized Solution:

```cpp
#include <iostream>
using namespace std;

int countBinarySubstrings(string str) {
    int ones = 0;

    for (char ch : str) {
        if (ch == '1') ones++;
    }
    // Number of substrings =  nC2 = n * (n - 1) / 2 
    return (ones * (ones - 1)) / 2;
}

int main() {
    string str;
    cin >> str;

    cout << countBinarySubstrings(str);
    return 0;
}
```
```
Sample Input
00100101
Output
3
```

---
### Expleo - Interview Questions** : 30 min
---
### **Q1: Find the Most Frequently Occurring Character in a Word
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string str;
    cin >> str;

    int freq[26] = {0};  // For 'a' to 'z'

    // Count frequency of each lowercase character
    for (int i = 0; i < str.length(); i++) {
        if (str[i] >= 'a' && str[i] <= 'z') {
            freq[str[i] - 'a']++;
        }
    }

    // Find the most frequent character
    int maxFreq = 0;
    char maxChar = '\0';

    for (int i = 0; i < 26; i++) {
        if (freq[i] > maxFreq) {
            maxFreq = freq[i];
            maxChar = 'a' + i;
        }
    }

    cout <<maxChar<< " -> " << maxFreq  << endl;

    return 0;
}
```
Output
```cpp
Sample Input
banana
Your Output
a -> 3
```
OR using STL
```cpp
#include <iostream>
#include <unordered_map>
using namespace std;

int main() {
    string word;
    cin >> word;

    unordered_map<char, int> freq;

    // Count frequency of each character
    for (char ch : word) {
        freq[ch]++;
    }

    // Find the most frequent character
    char maxChar = '\0';
    int maxFreq = 0;

    for (auto pair : freq) {
        if (pair.second > maxFreq) {
            maxFreq = pair.second;
            maxChar = pair.first;
        }
    }

    cout << maxChar<< "-> " << maxFreq << endl;

    return 0;
}

```
---
### **Q1: Frequency of Each Character in a word
```cpp
#include <iostream>
#include <map>
#include <string>
using namespace std;

void countCharFrequency(string word) {
    map<char, int> freq;

    // Count frequency of each character
    for (char ch : word) {
        freq[ch]++;
    }

    // Display frequencies
    cout << "Character Frequencies:\n";
    for (auto pair : freq) {
        cout << pair.first << " : " << pair.second << endl;
    }
}

int main() {
    string word;

    cout << "Enter a word: ";
    cin >> word;

    countCharFrequency(word);

    return 0;
}

```
OR 
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string str;
    cin >> str;

    int freq[26] = {0};  // For 'a' to 'z'

    // Count frequency of each lowercase character
    for (int i = 0; i < str.length(); i++) {
        if (str[i] >= 'a' && str[i] <= 'z') {
            freq[str[i] - 'a']++;
        }
    }

    // Display frequency of each character
    for (int i = 0; i < 26; i++) {
        if (freq[i] > 0) {
            char ch = 'a' + i;
            cout << ch << " : " << freq[i] << endl;
        }
    }

    return 0;
}
```
Output
```cpp
Sample Input
banana
Your Output
a : 3
b : 1
n : 2
```
---
### IBM - Interview Questions** : 30 min
---
### **Q1: `char *str;` vs `char str[];` in C++**

**Answer:**

| Aspect            | `char *str;`                       | `char str[];`                 |
| ----------------- | ---------------------------------- | ----------------------------- |
| Type              | Pointer to char                    | Array of chars                |
| Memory Allocation | Can point to dynamic/static memory | Size is fixed at compile time |
| Resizable?  | ✅ Yes (if dynamically allocated)     | ❌ No (cannot resize after declaration) |
| Modifiable        | Pointer can be reassigned          | Array cannot be reassigned    |
| Example           | `char *str = "Hello";`             | `char str[] = "Hello";`       |


```cpp
char *str1 = "Hello";       // Pointer to a string literal (read-only)
char str2[] = "Hello";      // Array initialized with string (modifiable)
char str[10] = "Hello";
// str = new char[20];  // ❌ Error: cannot reassign an array
```
```cpp
    char* str = new char[10];
    strcpy(str, "Hi");

    // Resize
    char* temp = new char[20];
    strcpy(temp, str);
    delete[] str;
    str = temp;
```
---

### **Q2: class vs structure in C++**

**Answer:**

| Feature          | `class`                     | `struct`                    |
| ---------------- | --------------------------- | --------------------------- |
| Default Access   | Private                     | Public                      |
| Inheritance      | Default private inheritance | Default public inheritance  |
| Usage            | Typically for OOP           | Typically for data grouping |
| Function Members | Allowed                     | Allowed                     |

```cpp
class MyClass {
private:
    int x;
public:
    void setX(int val) { x = val; }
};

struct MyStruct {
    int x;
    void setX(int val) { x = val; }
};
```

---

### **Q3: Program for Insertion (`<<`) Operator Overloading**
  * `<<` = Insertion Operator:  Used with cout to output data to the console.
  * `>>` = Extraction Operator: Used with cin to input data from the user.

Example:
```cpp
#include <iostream>
using namespace std;

class Student {
    int id;
    string name;

public:
    friend istream& operator>>(istream& in, Student& s) {
        in >> s.id >> s.name;  // input from user
        return in;
    }

    friend ostream& operator<<(ostream& out, const Student& s) {
        out << "ID: " << s.id << ", Name: " << s.name;  // output to console
        return out;
    }
};

int main() {
    Student s;
    cin >> s;     // calls overloaded >>
    cout << s;    // calls overloaded <<
    return 0;
}

```
---

### **Q4: What is OOP (Object-Oriented Programming) explain all pillers**

---
### **Q5: What is **[Operator](/Operators.md)** and its type in CPP?

---

### **Q6: Do you know Linux?**

**Answer:**
Yes, Linux is a widely used open-source operating system. In development, it's commonly used for:

* Command-line operations
* Shell scripting
* System-level programming
* Managing servers and deployment
* Tools like `gcc`, `g++`, `gdb`, `make`, etc.

Example Linux commands:

```bash
ls       # list files
cd       # change directory
g++ app.cpp -o app  # compile C++ code
./app    # run the program
```

---

 ### **BMW C++ Interview** 

---

### **1. What is Name Mangling in C++?**

**Q:** What is **name mangling**, and why is it used?

**A:**
Name mangling is the process by which the C++ compiler **modifies function names** (especially overloaded or templated ones) into unique names before compilation.
This allows the linker to differentiate between functions with the same name but different signatures.

 Example:

```cpp
void foo(int);     // Might become _Z3fooi
void foo(float);   // Might become _Z3foof
```

> You can prevent mangling using `extern "C"` for C linkage.

---

### **2. Size of a Class in C++**

**Q:** What determines the **size of a class**?

**A:**
Size of a class depends on:

* Data members (int, char, etc.)
* **Padding** and alignment
* Presence of **virtual functions** (adds vptr)
* Inheritance

**Example:**

```cpp
class A {
    int x;   // 4 bytes
    char y;  // 1 byte + 3 bytes padding
};
```

 Size = 8 bytes (due to padding)

---

### **3. `size()` vs `capacity()` in `std::vector`**

| `vector.size()`                           | `vector.capacity()`                                 |
| ----------------------------------------- | --------------------------------------------------- |
| Number of elements actually in the vector | Number of elements that can be held before resizing |
| Always ≤ capacity                         | Can be greater than size                            |

```cpp
vector<int> v;
v.push_back(1);
v.push_back(2);

cout << v.size();     // 2
cout << v.capacity(); // maybe 4 or 8 depending on growth
```

---

### **4. What is a Template Class in C++?**

A template class allows you to create a **generic class** that works with any data type.

```cpp
template <typename T>
class Box {
    T value;
public:
    void set(T v) { value = v; }
    T get() { return value; }
};
```

Use:

```cpp
Box<int> intBox;
Box<string> strBox;
```

---

### **5. Constructor and Vtables**

* A class with at least one **virtual function** will have a **vtable**.
* Each object will get a hidden **vptr** pointing to the vtable.
* The **constructor** sets up the `vptr`.

> **Vtable** = Table of function pointers to virtual functions
> **Vptr** = Pointer inside object that points to the class’s vtable

---

### **6. If a class has a virtual function, what is its size?**
Even with **no members**, the class will have a **vptr** (usually 4 or 8 bytes depending on platform).

```cpp
class A {
    virtual void fun() {}
};

int main() {
    cout << sizeof(A); // Output: 8 (on 64-bit), 4 (on 32-bit)
}
```

> Size increases if data members or multiple/virtual inheritance is used.

---
Here’s a list of **interview questions** based on what you mentioned (like Cyient interviews), along with **brief answers and code examples** to help you prepare thoroughly.

---

### **Cyient - Technical Round Interview**
---
Round 1: 20 Questions C++ MCQ 20 min
Round 2: 20 Questions C++ MCQ 20 min + Virtual Interview 30 min
---

---

### 1. What is your role and responsibility?

---

### 2. What is a Virtual Constructor?
* In C++, constructors cannot be declared `virtual`. But we can use **virtual clone() methods** or factory patterns to simulate behavior similar to virtual constructors.
* It's used when we want to create an object of derived class using a base class pointer.

**Example using `clone()`:**

```cpp
class Base {
public:
    virtual Base* clone() {
        return new Base(*this);
    }
    virtual void show() {
        std::cout << "Base class\n";
    }
};

class Derived : public Base {
public:
    Derived* clone() override {
        return new Derived(*this);
    }
    void show() override {
        std::cout << "Derived class\n";
    }
};
```

---

### 3. What is Multithreading?

---

### 4. Write a Multithreading Example in C++

```cpp
#include <iostream>
#include <thread>

void function1() {
    cout << "Function 1 running\n";
}

void function2() {
    cout << "Function 2 running\n";
}

int main() {
    thread t1(function1);
    thread t2(function2);

    t1.join(); // Wait for t1 to finish
    t2.join(); // Wait for t2 to finish

    cout << "Main thread done\n";
    return 0;
}
```

---

### 5. What is `join()` in threads? What happens if we don’t use `join()`?
* `join()` is used to make the main thread **wait for the child thread to finish execution**.
* If we don't call `join()` and the main thread ends before the child thread, it can cause:

* Program to terminate before child thread finishes.
* Undefined behavior or crash, depending on compiler/system.

---
### 6. Do you use desgine pattern in your project?

---
### 7. What will come output of following Program?

```cpp
#include <bits/stdc++.h>
using namespace std;

class A 
    { public: 
        A() 
        { 
            cout << "A constructor"<<endl;
            
        } 
        ~A() {
            cout << "A Destructor"<<endl;
            
        }
    };
    
class B : public A{ 
    public:
    B(){
    cout << "B constructor"<<endl;
    
    } 
    ~B() {
    cout << "B Destructor"<<endl;
        
    } 
}; 

int main() {
	// your code goes here
	A *p = new B();
	delete p;
	return 0;

}

```
Output
```
A constructor
B constructor
A Destructor
```
---
### 8. What make you changes that `B Destructor` will call ?

```cpp
#include <bits/stdc++.h>
using namespace std;

class A {
public:
    A() { cout << "A constructor" << endl; }
    virtual ~A() { cout << "A Destructor" << endl; } // use vitaul destructor
};

class B : public A {
public:
    B() { cout << "B constructor" << endl; }
    ~B() { cout << "B Destructor" << endl; }
};

int main() {
    A *p = new B();  // dynamic allocation
    delete p;        // deleting via base class pointer
    return 0;
}
```

### Key Concept:

* `A *p = new B();` means we are creating an object of class `B` but pointing to it using a base class (`A`) pointer.
* When we call `delete p;`, **only the base class destructor (`~A`) will be called**, unless the base class destructor is declared `virtual`.

### Output Explanation:

1. During `new B();`

   * First, `A`'s constructor runs → prints `A constructor`
   * Then, `B`'s constructor runs → prints `B constructor`

2. During `delete p;`

   * Only `A`'s destructor runs → prints `A Destructor`
   * `B`'s destructor **does not run** because `~A()` is **not virtual**

### **Incorrect behavior** (memory/resource leak) due to missing `virtual` destructor.

### Final Output:

```
A constructor
B constructor
A Destructor
```

### Correct Fix:

To ensure proper destruction, declare the base class destructor as `virtual`:

```cpp
virtual ~A() {
    cout << "A Destructor" << endl;
}
```

Then output would be:

```
A constructor
B constructor
B Destructor
A Destructor
```
---
### **Zwayam.com - Technical Round Interview**
Round 1: 45 min
---

### **Q1. Roles and Responsibilities and do u have testing**

### **Q2. WAP in C++ to Reverse a Line Word by Word**
* Step 1: Input String
  	string str;
	getline(cin, str);
* Step 2: Reverse whole string
  	Using 2 pointer approach
	Or revrse function
* Step 3: reverse word by word

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	// your code goes here
	string str;
	getline(cin, str);
	//cin>>str; //do not use
    string ans = "";
    int n = str.size();

    reverse(str.begin(), str.end()); // fix spelling: revrse -> reverse

    for (int i = 0; i < n; i++) {
        string word = "";
        // collect characters of a word
        while (i < n && str[i] != ' ') {
            word += str[i];
            i++;
        }
        reverse(word.begin(), word.end()); // reverse individual word
        if (word.length() > 0) {
            ans += word + " ";
        }
    }
    cout << ans << endl;

    return 0;
}

```

---

### **Q3. Dangling Pointer with Example**

A **dangling pointer** is a pointer that points to a memory location that has been **freed/deallocated**.

#### **Example:**

```cpp
#include <iostream>
using namespace std;

int* createPointer() {
    int x = 10;
    return &x; // returns address of local variable
}

int main() {
    int* ptr = createPointer(); // dangling pointer
    cout << *ptr << endl;       // undefined behavior
    return 0;
}
```

> The variable `x` goes out of scope after `createPointer()` finishes, so `ptr` points to an invalid location.

---

### **Q4. Shallow Copy vs Deep Copy**

#### **Shallow Copy:**

* Copies object **without duplicating referenced memory**.
* Changes to the original affect the copy.

#### **Deep Copy:**

* Copies **all fields** and duplicates any **dynamically allocated memory**.

#### **Example in C++:**

```cpp
#include <iostream>
#include <cstring>
using namespace std;

class Sample {
public:
    char* name;

    // Constructor
    Sample(const char* n) {
        name = new char[strlen(n) + 1];
        strcpy(name, n);
    }

    // Shallow copy constructor
    Sample(const Sample& s) {
        name = s.name;
    }

    // Deep copy constructor
    Sample deepCopy() {
        return Sample(name); // creates new memory
    }

    void show() {
        cout << "Name: " << name << endl;
    }

    ~Sample() {
        delete[] name;
    }
};

int main() {
    Sample s1("Alice");
    Sample s2 = s1;        // Shallow copy (dangerous)
    Sample s3 = s1.deepCopy(); // Deep copy (safe)

    s1.show();
    s2.show();
    s3.show();

    return 0;
}
```

---

### **Q5.** Memory Leak with Example & How to Prevent It**
A **memory leak** happens when a program **allocates memory on the heap** but **fails to release (deallocate) it** after it's no longer needed. This causes a **gradual increase in memory usage**, leading to performance issues or crashes.

---

### **Example of a Memory Leak in C++**

```cpp
#include <iostream>
using namespace std;

void memoryLeakExample() {
    int* ptr = new int(10);  // Dynamically allocate memory
    cout << *ptr << endl;
    // Forgot to delete the allocated memory -> memory leak
}

int main() {
    for (int i = 0; i < 1000; ++i) {
        memoryLeakExample(); // Each call leaks memory
    }
    return 0;
}
```

---

### **Q6.** How to Prevent Memory Leaks

1. **Always deallocate memory** using `delete` or `delete[]` after `new` or `new[]`.

   ```cpp
   int* ptr = new int(20);
   // Use the pointer
   delete ptr; // Free memory
   ```

2. **Use smart pointers (C++11 and above)**:

   * `std::unique_ptr`
   * `std::shared_ptr`
   * Automatically manage memory and prevent leaks.

   ```cpp
   #include <memory>
   std::unique_ptr<int> ptr = std::make_unique<int>(10);
   // Automatically deleted when ptr goes out of scope
   ```

3. **Avoid raw pointers** when possible; use containers like `std::vector`, `std::string`, etc.

4. **Use tools to detect memory leaks:**

   * Valgrind (Linux)
   * Visual Studio Diagnostic Tools (Windows)
   * AddressSanitizer

---
### ** Siemens.com - Technical Round Interview**
Round 1: 30 min

## 1. **What is C++ (CPP)?**

**C++** is a general-purpose, object-oriented programming language developed by **Bjarne Stroustrup** as an extension of the C language.
It supports both **procedural** and **object-oriented** programming (multi-paradigm), offering features like:

* Classes & Objects
* Inheritance
* Polymorphism
* Encapsulation
* Abstraction
* Templates
* Exception handling
* STL (Standard Template Library)

---

## 2. **Difference between Class and Object**

| Feature    | Class                               | Object                             |
| ---------- | ----------------------------------- | ---------------------------------- |
| Definition | A blueprint or template for objects | An instance of a class             |
| Memory     | No memory is allocated              | Memory is allocated at runtime     |
| Example    | `class Car { };`                    | `Car myCar;`                       |
| Purpose    | Defines behavior and properties     | Implements behavior and holds data |

---

## 3. **Explain OOPs Pillars One by One**

1. **Encapsulation**

   * Wrapping data and methods into a single unit (class).
   * Protects data using access specifiers (`private`, `public`, etc.).

2. **Abstraction**

   * Hiding internal details and showing only essential features.
   * Achieved using abstract classes or interfaces.

3. **Inheritance**

   * One class (child) can inherit properties and behavior from another class (parent).
   * Promotes code reuse.

4. **Polymorphism**

   * Same function or operator behaves differently in different contexts.
   * Types: Compile-time (Function Overloading) and Runtime (Virtual Functions).

---

## 4. **C++ Program: Insert an Element into a Sorted Array**

** Problem:**
Given a sorted array, insert an element and maintain the sorted order.

** Input:**

```cpp
int arr[] = {1, 3, 5, 7};
int n = 6;
```

** Output:**

```
1, 3, 5, 6, 7
```

### C++ Code (In-place Insertion):

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[100] = {1, 3, 5, 7}; // allocate extra space
    int n = 4;                   // current number of elements
    int element = 6;

    // Find the position to insert
    int i = n - 1;
    while (i >= 0 && arr[i] > element) {
        arr[i + 1] = arr[i]; // shift elements right
        i--;
    }

    // Insert the new element
    arr[i + 1] = element;
    n++; // increment size after insertion

    // Print the updated array
    cout << "Updated array: ";
    for (int j = 0; j < n; j++) {
        cout << arr[j];
        if (j < n - 1) cout << ", ";
    }
    cout << endl;

    return 0;
}
```
---

### Output:

```
Updated array: 1, 3, 5, 6, 7
```

---
### ** Intelizign - Technical Round Interview**
Round 1: 30 min

---
### **Q1. What is OOPs? Explain.**
---

### **Q3. Pattern:**

```
1
1 2
1 2 3
```

**Code in C++:**

```cpp
#include <iostream>
using namespace std;

int main() {
    for (int i = 1; i <= 3; ++i) {
        for (int j = 1; j <= i; ++j) {
            cout << j << " ";
        }
        cout << endl;
    }
    return 0;
}
```

---

### **Q4. What is `shared_ptr`?**

`shared_ptr` is a **smart pointer** in C++ that manages shared ownership of a dynamically allocated object.

* Multiple `shared_ptr`s can point to the same object.
* When the last `shared_ptr` is destroyed or reset, the object is deleted.

**Example:**

```cpp
#include <memory>
#include <iostream>
using namespace std;

int main() {
    shared_ptr<int> p1 = make_shared<int>(10);
    shared_ptr<int> p2 = p1; // shared ownership

    cout << *p1 << " " << *p2 << endl; // 10 10
    return 0;
}
```

---

### **Q5. Move Constructor, Default Constructor, Default Destructor**

* **Default Constructor**: A constructor with no arguments.

```cpp
class A {
public:
    A() {}  // default constructor
};
```

* **Move Constructor**: Transfers resources from one object to another without copying.

```cpp
class A {
    int* data;
public:
    A(A&& other) {
        data = other.data;
        other.data = nullptr;
    }
};
```

* **Default Destructor**: Automatically deletes/cleans up when object goes out of scope.

```cpp
class A {
public:
    ~A() {}  // default destructor
};
```

---

### **Q6. STL: Array vs Vector vs List**

| Feature   | `array` (std::array) | `vector`             | `list` (std::list)      |
| --------- | -------------------- | -------------------- | ----------------------- |
| Size      | Fixed                | Dynamic              | Dynamic                 |
| Memory    | Contiguous           | Contiguous           | Non-contiguous (nodes)  |
| Insertion | Costly at middle     | Costly at middle     | Fast at any position    |
| Access    | Fast (random access) | Fast (random access) | Slow (no random access) |
| Use Case  | Known size, speed    | Dynamic arrays       | Frequent insert/delete  |

---

### **Q7. Pass by Reference vs Pass by Value**

* **Pass by Value**: A copy is passed. Changes do **not** reflect outside.

```cpp
void func(int x) { x = 10; }
```

* **Pass by Reference**: Reference is passed. Changes reflect outside.

```cpp
void func(int &x) { x = 10; }
```

---

### **Q7 (code): Pointer behavior**

```cpp
  
int* p1;
int m = 100;

p1 = &m;
*p1++;  // increment pointer, not value. Equivalent to p1 = p1 + 1
++m;    // m = 101
printf("%d\n", *p1); // Undefined behavior
printf("%d\n", m);   // 101
```
Output
```
-122846152
101

```
But 
```cpp
int m = 100;
int* p1;
p1 = &m;
(*p1)++;  // increment pointer, not value. Equivalent to p1 = p1 + 1
++m;    // m = 101
printf("%d\n", *p1); //102
printf("%d\n", m);   // 102
```
Output
```
102
102

```


---

### **Q8: Call dosomething function i main() **

#### Case 1:

```cpp
#include <iostream>
using namespace std;

void dosomething(int *p) {
    cout << "Inside function: " << *p << endl;  // prints the value pointed by p
}

int main() {
    int P = 10;
    int *ptr = &P;       // create pointer to P
    dosomething(ptr);    // pass pointer to function
    return 0;
}

```
Output
```
Inside function: 10
```
And

```cpp
void dosomething(int &p) {
    cout << "Inside function: " << p << endl;  // no dereferencing needed
}

int main() {
    int P = 10;
    dosomething(P);  // pass variable by reference
}

```
Output
```
Inside function: 10
```
---
### **Q9: Static

In C++, the `static` keyword has **different meanings depending on the context** (variables, functions, class members). Here's a clear breakdown:

---

##  1. **Static Variables (Inside a Function)**

```cpp
void demo() {
    static int count = 0;
    count++;
    std::cout << count << std::endl;
}
```

* **Lifetime:** Exists for the entire program (not destroyed when the function ends).
* **Scope:** Local to the function.
* **Use case:** To retain the value between function calls.

**Output:**

```cpp
demo(); // 1
demo(); // 2
demo(); // 3
```

---

##  2. **Static Variables (Global/Namespace Scope)**

```cpp
static int globalVar = 5;
```

* **Limits visibility to the current translation unit (.cpp file).**
* Useful in large projects to avoid name collisions.

---

##  3. **Static Member Variables in Class**

```cpp
class MyClass {
public:
    static int count;
};
int MyClass::count = 0;  // Must be defined outside the class

MyClass::count++;  // Access without object
```

* Shared among all objects (only **one copy** exists).
* Can be accessed using the class name (`MyClass::count`).
* Must be **defined outside** the class.

---

##  4. **Static Member Functions in Class**

```cpp
class MyClass {
public:
    static void show() {
        std::cout << "Static function\n";
    }
};
```

* Can be called without an object.
* Cannot access non-static members (no `this` pointer).

---

##  5. **Static Inside a Class (Private Helper)**

```cpp
class Helper {
private:
    static int secret;  // Hidden from outside
};
```

* Encapsulation: Hide implementation details.

---

## Summary Table:

| Context          | Meaning of `static`                             |
| ---------------- | ----------------------------------------------- |
| Inside function  | Retains value across function calls             |
| Global/namespace | Limits scope to file                            |
| Class variable   | Shared across all instances                     |
| Class function   | Can be called without object; no `this` pointer |

---

### **Q10: Solid Principal

### SOLID Principles in Object-Oriented Programming

The **SOLID** principles are five key design principles intended to make software designs more understandable, flexible, and maintainable. These are especially important in **Object-Oriented Programming (OOP)** like C++, Java, C#, etc.

---

### What does SOLID stand for?

| Principle                                     | Description                                                                                                                                |
| --------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| **S – Single Responsibility Principle (SRP)** | A class should have **only one reason to change**. It should do **one job only**.                                                          |
| **O – Open/Closed Principle (OCP)**           | A class should be **open for extension** but **closed for modification**. You can extend behavior without changing existing code.          |
| **L – Liskov Substitution Principle (LSP)**   | Subclasses should be able to **replace** their parent classes without breaking the functionality.                                          |
| **I – Interface Segregation Principle (ISP)** | Don’t force a class to implement **interfaces it doesn’t use**. Break large interfaces into smaller ones.                                  |
| **D – Dependency Inversion Principle (DIP)**  | Depend on **abstractions, not concretions**. High-level modules shouldn’t depend on low-level modules; both should depend on abstractions. |

---

### Simple Example: (in C++)

---

### 1. **Single Responsibility Principle (SRP)**

**Each class should have one and only one responsibility.**

```cpp
class FileReader {
public:
    void readFile(const std::string& filename) {
        // logic to read file
    }
};

class FileWriter {
public:
    void writeFile(const std::string& filename) {
        // logic to write file
    }
};
```

*Each class has a single reason to change — reading or writing.*

---

### 2. **Open/Closed Principle (OCP)**

**Software entities should be open for extension, but closed for modification.**

```cpp
class Shape {
public:
    virtual double area() = 0;
};

class Circle : public Shape {
public:
    double radius;
    Circle(double r) : radius(r) {}
    double area() override {
        return 3.14 * radius * radius;
    }
};

class Rectangle : public Shape {
public:
    double width, height;
    Rectangle(double w, double h) : width(w), height(h) {}
    double area() override {
        return width * height;
    }
};
```

*You can add new shapes without modifying existing code.*

---

### 3. **Liskov Substitution Principle (LSP)**

**Derived classes must be substitutable for their base classes.**

```cpp
class Bird {
public:
    virtual void fly() {
        std::cout << "Flying\n";
    }
};

class Sparrow : public Bird {};

void letBirdFly(Bird* bird) {
    bird->fly();
}
```

*Sparrow can be used in place of Bird without breaking code.*

---

### 4. **Interface Segregation Principle (ISP)**

**Clients should not be forced to depend on methods they don’t use.**

```cpp
class IPrinter {
public:
    virtual void print() = 0;
};

class IScanner {
public:
    virtual void scan() = 0;
};

class AllInOnePrinter : public IPrinter, public IScanner {
public:
    void print() override {
        std::cout << "Printing\n";
    }
    void scan() override {
        std::cout << "Scanning\n";
    }
};
```

*Separate interfaces keep implementation clean and focused.*

---

### 5. **Dependency Inversion Principle (DIP)**

**Depend on abstractions, not concrete classes.**

```cpp
class IMessage {
public:
    virtual void send(const std::string& msg) = 0;
};

class Email : public IMessage {
public:
    void send(const std::string& msg) override {
        std::cout << "Sending Email: " << msg << "\n";
    }
};

class Notification {
    IMessage* message;
public:
    Notification(IMessage* msg) : message(msg) {}
    void notify(const std::string& text) {
        message->send(text);
    }
};
```

*Notification depends on abstraction (IMessage), not on a specific Email class.*

---
### **Tietoevry.com - Technical Round Interview**
Round 1: 30 min
---

### **Q1: Create a class with const, reference, char pointer, static data member**

```cpp
#include <iostream>
using namespace std;

class A {
public:
    const int a;       // constant data member
    int &r;            // reference data member
    char *ch;          // pointer to char
    static int n;      // static data member

    // Constructor to initialize const and reference
    A(int val, int &ref, const char* str) 
        : a(val), r(ref) {
        ch = new char[strlen(str) + 1];
        strcpy(ch, str);
    }

    ~A() {
        delete[] ch;  // Free allocated memory
    }
};

// Define static member outside class
int A::n = 0;

int main() {
    int x = 100;
    A obj(10, x, "Hello");
    cout << "Const a: " << obj.a << ", Reference r: " << obj.r << ", Char*: " << obj.ch << ", Static n: " << A::n << endl;
    return 0;
}
```

---

### **Q2: Create all types of constructors + destructor. Why use them?**

```cpp
#include <iostream>
using namespace std;

class B {
    int x;
public:
    // Default constructor
    B() {
        x = 0;
        cout << "Default Constructor" << endl;
    }

    // Parameterized constructor
    B(int val) {
        x = val;
        cout << "Parameterized Constructor" << endl;
    }

    // Copy constructor
    B(const B &obj) {
        x = obj.x;
        cout << "Copy Constructor" << endl;
    }

    // Destructor
    ~B() {
        cout << "Destructor called" << endl;
    }
};

int main() {
    B b1;         // default
    B b2(10);     // parameterized
    B b3 = b2;    // copy

    return 0;
}
```

**Why use them?**

* **Constructor** initializes objects when created.
* **Destructor** cleans up resources when the object goes out of scope.
* **Copy constructor** used when copying objects (e.g., passing by value).

---

###  **Q3: Write output**

```cpp
int arr[] = {10, 20, 30, 40, 50};
int *p = arr;

cout << *p;        // Output: 10
cout << *p++;      // Output: 10 (p now points to arr[1])
cout << (*p)++;    // Output: 20 (then arr[1] becomes 21)
```

 **Final Output:**

```
1020
```

� `*p++` increments the pointer (not the value). `(*p)++` increments the value at that pointer.

---

### **Q4: Write output & explain**

```cpp
int x = 10, y = 20;
const int* p1 = &x; // Pointer to const int (data is const, pointer not)
int* const p2 = &x; // Constant pointer to int (pointer const, data not)

*p1 = 20;    // Error: can't modify value through pointer to const
p1 = &y;     // OK: pointer itself can point elsewhere

*p2 = 30;    // OK: data can be modified
p2 = &y;     // Error: can't change address held by const pointer
```

**Explanation:**

* `const int* p1` → **data is const**, pointer is not.
* `int* const p2` → **pointer is const**, data is not.

---

###  **Q5: Insert pairs in `map` and print using iterator**

```cpp
#include <iostream>
#include <map>
using namespace std;

int main() {
    map<int, int> mp;

    // Insert values
    mp.insert({1, 1});
    mp.insert({2, 2});
    mp.insert({3, 3});
    mp.insert({4, 4});
    mp.insert({5, 5});

    // Print using iterator
    for (auto it = mp.begin(); it != mp.end(); ++it) {
        cout << it->first << " => " << it->second << endl;
    }

    return 0;
}
```

 **Output:**

```
1 => 1
2 => 2
3 => 3
4 => 4
5 => 5
```

---

### **Q6: What is VPtr and VTable?**

**VTable (Virtual Table)** and **VPtr (Virtual Pointer)** are mechanisms used in **runtime polymorphism** (when using virtual functions).

* **VTable:**

  * A lookup table used to resolve function calls to virtual functions at runtime.
  * Each class with virtual functions has its own vtable.

* **VPtr:**

  * A hidden pointer in each object of a class having virtual functions.
  * Points to the class’s VTable.

Example:

```cpp
class Base {
public:
    virtual void show() { cout << "Base" << endl; }
};

class Derived : public Base {
public:
    void show() override { cout << "Derived" << endl; }
};
```

* When you call `show()` via a `Base*` pointer pointing to a `Derived` object, VTable is used to dynamically resolve the correct function.

---

### **Q7: If we do not create a constructor, how is it handled in C++?**

###  **Compiler-Generated Default Constructor**

If you write:

```cpp
class A {
public:
    int x;
};
```

Then C++ automatically generates a constructor like this:

```cpp
A() { }  // Implicit default constructor
```

You can still create objects:

```cpp
A obj;    // Works fine — compiler provides a default constructor
```

---

### **Important Notes:**

####  **Case 1: No constructor defined**

* Compiler provides **default constructor**.
* Members like `int`, `float` are **not initialized** automatically (they hold garbage values unless initialized).

```cpp
class B {
public:
    int x;
};

int main() {
    B obj;
    cout << obj.x << endl;  // Garbage value
}
```

---

####  \*\*Case 2: You define **any** constructor, but **not the default one**

```cpp
class C {
public:
    C(int a) {}  // Parameterized constructor only
};

int main() {
    C obj;       //  Error: No default constructor
}
```

* If **you define a parameterized constructor**, the compiler **does NOT generate** a default one.
* You must manually define it if needed.

```cpp
class C {
public:
    C() {}         // Default constructor
    C(int a) {}    // Parameterized
};
```

---

### **Calsoft Inc - Technical Round Interview**
Round 1: 30 min
### **Q1: Eliminate duplicate characters from "Hello World!!!" without using STL
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string str;
    getline(cin, str); // take full line with spaces

    int freq[256] = {0}; // all ASCII chars
    string result;

    for (char ch : str) {
        if (freq[(unsigned char)ch] == 0) { // first occurrence
            result.push_back(ch);
        }
        freq[(unsigned char)ch]++;
    }

    cout << result;
    return 0;
}


```
```
Input:
hello world!!!

Output:
helo wrd!
```

Without STL
```
#include <iostream>
#include <cstdio>  // for getchar()
using namespace std;

int main() {
    char str[1000]; // input buffer (max 999 chars + '\0')
    int len = 0;

    // Read input manually (including spaces)
    char ch;
    while ((ch = getchar()) != '\n' && ch != EOF) {
        str[len++] = ch;
    }
    str[len] = '\0'; // null-terminate

    int freq[256] = {0}; // ASCII frequency
    int index = 0;       // position to place unique chars

    for (int i = 0; i < len; i++) {
        unsigned char c = str[i];
        if (freq[c] == 0) { // first occurrence
            str[index++] = c;
        }
        freq[c]++;
    }

    str[index] = '\0'; // terminate final string

    // Output result
    cout << str;
    return 0;
}

```
Remove Duplicate in a word
```cpp
#include <iostream>
#include <cstring>
using namespace std;

void removeDuplicates(char str[]) {
    int freq[256] = {0}; // frequency of ASCII chars
    int len = strlen(str);
    int index = 0;

    for (int i = 0; i < len; i++) {
        unsigned char ch = str[i];
        if (freq[ch] == 0) { // first occurrence
            str[index++] = ch;
        }
        freq[ch]++; // increment frequency
    }
    str[index] = '\0'; // terminate string
}

int main() {
    char str[] = "programming";
    cout << "Original: " << str << endl;
    removeDuplicates(str);
    cout << "Without duplicates: " << str << endl;
    return 0;
}


```

---

### **Apexon - Technical Round Interview**
Round 1: 30 min

## **1. What is a Race Condition? How to Prevent it?**

**Definition:**
A **race condition** occurs when multiple threads access and modify shared data **concurrently**, and the final result depends on the timing of their execution.

###  How to prevent it?

Use **mutual exclusion** mechanisms like:

* `std::mutex`
* `std::lock_guard`
* `std::atomic`

### **C++ Example (Using `std::mutex`):**

```cpp
#include <iostream>
#include <thread>
#include <mutex>

int counter = 0;
std::mutex mtx;

void increment() {
    for (int i = 0; i < 1000; ++i) {
        std::lock_guard<std::mutex> lock(mtx);
        ++counter;
    }
}

int main() {
    std::thread t1(increment);
    std::thread t2(increment);
    t1.join();
    t2.join();
    std::cout << "Counter: " << counter << std::endl;
    return 0;
}
```

---

## **2. What is Mutual Exclusion?**

---

## **3. What is Multithreading?**
---

## **4. OOPs Pillars in C++**

---

## **5. Explain Function Overloading  Overriding**

---

## **6. First Non Repeating Character in a String**

```cpp
#include <iostream>
using namespace std;

int main() {
    string str;
    cin >> str;
    int found = 0;

    for (int i = 0; str[i] != '\0'; i++) {
        found = 0;
        for (int j = 0; str[j] != '\0'; j++) {
            if (str[i] == str[j] && i != j) {
                found = 1;
                break;
            }
        }
        if (!found) {
            cout << "First non-repeating character: " << str[i] << endl;
            return 0;
        }
    }

    cout << "No non-repeating character found." << endl;
    return 0;
}

```
```
Sample Input
aabcd
Your Output
First non-repeating character: b
```

---

## **7. Check if a String is a Palindrome**

```cpp
#include <iostream>
using namespace std;

bool isPalindrome(string s) {
    int i = 0, j = s.length() - 1;
    while (i < j) {
        if (s[i] != s[j]) return false;
        i++; j--;
    }
    return true;
}

int main() {
    string str = "madam";
    if (isPalindrome(str))
        cout << str << " is a palindrome." << endl;
    else
        cout << str << " is not a palindrome." << endl;
}
```

---
---

इंटरव्यू के अंत में जब इंटरव्यूअर आपसे पूछे, "Do you have any questions for us?" — तब आपके द्वारा पूछे गए सवाल आपकी curiosity, seriousness और कंपनी में genuine interest को दर्शाते हैं। नीचे कुछ बेहतरीन और **प्रभावशाली सवाल** दिए गए हैं जो आप इंटरव्यू के अंत में पूछ सकते हैं:

---
### Team और Role को लेकर:

1. **Can you tell me more about the day-to-day responsibilities of this role?**
   (इस रोल में मेरी डेली responsibilities कैसी होंगी?)

2. **What does the team structure look like, and who will I be working closely with?**
   (टीम का structure कैसा है और मैं किन लोगों के साथ मिलकर काम करूंगा?)

---

### Project और Tech Stack को लेकर:

3. **What kind of projects is the team currently working on?**
   (टीम फिलहाल किन तरह के प्रोजेक्ट्स पर काम कर रही है?)

4. **What technologies and tools are most commonly used in the team?**
   (टीम में कौन से technologies और tools का ज़्यादा उपयोग होता है?)

---

### Growth और Development:

5. **What are the opportunities for learning and professional growth in this role?**
   (इस रोल में सीखने और प्रोफेशनल ग्रोथ के क्या अवसर हैं?)

6. **Are there any training or upskilling programs provided for employees?**
   (क्या कंपनी किसी तरह के training या upskilling प्रोग्राम देती है?)

---

### Performance और Expectation:

7. **How is success typically measured for this role?**
   (इस रोल में success को कैसे मापा जाता है?)

8. **What are your expectations from someone joining this role in the first 3 to 6 months?**
   (पहले 3 से 6 महीनों में इस रोल में आने वाले व्यक्ति से आपकी क्या उम्मीदें होती हैं?)

---

### Final Impactful Question:

9. **What do you personally enjoy most about working at this company?**
   (आपको इस कंपनी में काम करने में सबसे ज़्यादा क्या पसंद आता है?)

10. **Is there anything in my profile that concerns you or that you'd like me to clarify further?**
    (क्या मेरी प्रोफ़ाइल में ऐसा कुछ है जिसे आप लेकर unsure हैं या जिसे मैं और अच्छे से explain कर सकूं?)

---
