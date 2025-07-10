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

> Insert at position 1 and 3 — which is faster: **array** or **list**?

| Operation              | Array (Dynamic/Static) | Linked List        |
| ---------------------- | ---------------------- | ------------------ |
| Insert at 1st position | O(n)                   | O(1)               |
| Insert at 3rd position | O(n)                   | O(n) (to traverse) |

 **Conclusion**:

* Insert at beginning: List is faster (O(1))
* Insert at middle: Similar in time (O(n)), but lists avoid shifting.

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

#### **Q9. How to Insert an Element at 1st and 3rd Position in Array vs List**

| **Operation**              | **Array**                                                              | **Linked List**                                                                      |
| -------------------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| **Insert at 1st position** | Shift all elements to the right → Insert at `arr[0]`<br>Time: **O(n)** | Create a new node → Point it to current head → Update head pointer<br>Time: **O(1)** |
| **Insert at 3rd position** | Shift elements from 3rd onward → Insert at `arr[2]`<br>Time: **O(n)**  | Traverse to 2nd node → Insert after it<br>Time: **O(n)**                             |

 **Conclusion**:

* Inserting at the **beginning** is faster in **Linked List**.
* Inserting at the **middle** requires traversal in both, but **Array** may have faster cache performance for small sizes.

---

#### **Q10. Access (Print) Element at 1st and 3rd Position in Array vs List — Which One is Fast?**

| **Operation**          | **Array**                 | **Linked List**                   |
| ---------------------- | ------------------------- | --------------------------------- |
| **Access 1st element** | `arr[0]` → Time: **O(1)** | `head->data` → Time: **O(1)**     |
| **Access 3rd element** | `arr[2]` → Time: **O(1)** | Traverse 2 nodes → Time: **O(n)** |

 **Conclusion**:

* Arrays allow **random access**: constant time access to any position.
* Linked Lists allow only **sequential access**: slower for positions beyond the head.
* **Array is faster** for accessing elements at any position.


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

* **Encapsulation** – Binding data and functions together
* **Abstraction** – Hiding implementation details
* **Inheritance** – Reusing code via parent-child relationship
* **Polymorphism** – Multiple forms (function/method overloading & overriding)

### 8. **Explain method overloading vs overriding.**

* **Overloading**: Same function name, different parameters (compile-time).
* **Overriding**: Redefining base class function in derived class using `virtual` (runtime).

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

* Allows concurrent execution of code using threads.
* Improves performance and responsiveness.
* Use `<thread>` header in C++11+.

  ```cpp
  std::thread t1(function_name);
  ```

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

* **Example**: "Find the first non-repeating character in a stream of characters."

  * Tests hash maps, queues, and real-time processing.

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

**OOP (Object-Oriented Programming)** is a programming paradigm based on the concept of "objects," which contain data and methods.

**Four pillars of OOP:**

1. **Encapsulation:**
   Wrapping data and methods that operate on data into a single unit (class).
   *Example:*

   ```cpp
   class Car {
       private:
         int speed;
       public:
         void setSpeed(int s) { speed = s; }
         int getSpeed() { return speed; }
   };
   ```

2. **Abstraction:**
   Hiding internal details and showing only essential features.
   *Example:* Using methods like `startEngine()` without showing engine internals.

3. **Inheritance:**
   Deriving new classes from existing ones to reuse code.
   *Example:*

   ```cpp
   class Vehicle {
     public: void move() {}
   };
   class Car : public Vehicle {
     public: void openDoor() {}
   };
   ```

4. **Polymorphism:**
   Ability of a function to behave differently based on the object.
   *Example:* Function overriding (runtime polymorphism).

---

### Q2. Explain function overriding and write a program and explain code.

**Function Overriding:**
When a derived class provides its own implementation of a function already defined in its base class.

*Example:*

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void show() {
        cout << "Base class\n";
    }
};

class Derived : public Base {
public:
    void show() override {
        cout << "Derived class\n";
    }
};

int main() {
    Base* ptr;
    Derived d;
    ptr = &d;
    ptr->show();  // Calls Derived's show()
    return 0;
}
```

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

* Defines and immediately calls an **empty lambda function**. The program does nothing visible and returns 0.

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

### ✅ **Q2. In-place Transpose of a Matrix**

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

### ✅ **Q3. Find the second highest income in SQL**

```sql
SELECT MAX(salary) AS SecondHighest
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

---

### ✅ **Q4. Generate Fibonacci Sequence (first N terms)**

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

### ✅ **Q5. FizzBuzz Problem**

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

### ✅ **Q6. Why should we hire you?**

**Answer (Example):**

> "You should hire me because I have a strong foundation in programming, problem-solving, and experience with real-world projects. I adapt quickly to new technologies and consistently strive for excellence. I'm not only technically sound but also a good team player who believes in contributing to overall project success."

---

### ✅ **Q7. What is the Bin-Packing Problem?**

**Answer:**

> The Bin Packing Problem is an NP-Hard optimization problem where you aim to pack objects of different sizes into a finite number of bins of fixed capacity in a way that minimizes the number of bins used.

---

### ✅ **Q8. Calculate the Fibonacci Sequence (Recursive version)**

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

### ✅ **Q9. FizzBuzz Test**

(Already covered in Q5)

---

### ✅ **Q10. Difference between Array and ArrayList**

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

**Answer:**

> A LinkedList is a linear data structure where elements are stored in nodes and connected using pointers. Each node contains data and a pointer to the next node. It's dynamic in size and allows efficient insertions/deletions.

---

### **Q13. Implementations of a List in C++**

In C++, common list implementations include:

* `std::vector` – Dynamic array (random access)
* `std::list` – Doubly linked list
* `std::forward_list` – Singly linked list

Example of `std::list`:

```cpp
#include <iostream>
#include <list>
using namespace std;

int main() {
    list<int> l = {10, 20, 30};
    l.push_back(40);
    l.push_front(5);

    for (int val : l)
        cout << val << " ";
}
```

---
---

इंटरव्यू के अंत में जब इंटरव्यूअर आपसे पूछे, "Do you have any questions for us?" — तब आपके द्वारा पूछे गए सवाल आपकी curiosity, seriousness और कंपनी में genuine interest को दर्शाते हैं। नीचे कुछ बेहतरीन और **प्रभावशाली सवाल** दिए गए हैं जो आप इंटरव्यू के अंत में पूछ सकते हैं:

---

---
### iQuest - Interview Questions**
Round 1: 1hr
Here's the complete solution for all **4 C++ interview questions** you asked, well-explained and ready for Onnet Systems interview:

---

## ✅ Q1. Lambda Function in C++

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

## ✅ Q2. Check Palindrome String (Iterative + Recursive)

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
    if (start >= end) return true;
    if (s[start] != s[end]) return false;
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

## ✅ Q3. Pass by Value vs Pass by Reference

```cpp
#include <iostream>
using namespace std;

// Pass by Value
void incrementByValue(int x) {
    x++;
}

// Pass by Reference
void incrementByRef(int &x) {
    x++;
}

int main() {
    int a = 5;
    incrementByValue(a);
    cout << "After pass by value: " << a << endl;

    incrementByRef(a);
    cout << "After pass by reference: " << a << endl;

    return 0;
}
```

**Output:**

```
After pass by value: 5
After pass by reference: 6
```

---

## Q4. Count Binary Substrings Starting and Ending with 1

### Optimized Solution:

```cpp
#include <iostream>
using namespace std;

int countBinarySubstrings(string str) {
    int ones = 0;

    for (char ch : str) {
        if (ch == '1') ones++;
    }

    return (ones * (ones - 1)) / 2;
}

int main() {
    string str;
    cin >> str;

    cout << countBinarySubstrings(str);
    return 0;
}
```

### Example Input/Output:

**Input:**

```
00100101
```

**Output:**

```
3
```

Great question!

In C++, the syntax `[]() {}` is the basic structure of a **lambda function**. Let's break it down:

---

## 🔍 Syntax:

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

## 🧠 Detailed Breakdown

| Part                          | Description                                                                     |
| ----------------------------- | ------------------------------------------------------------------------------- |
| `[]`                          | **Capture list** – lets the lambda access variables from the surrounding scope. |
| `()`                          | **Parameter list** – like arguments to a function.                              |
| `{}`                          | **Function body** – code to run when lambda is called.                          |
| `-> return_type` *(optional)* | Specifies return type (can often be omitted if deducible).                      |

---

## ✅ Example 1: Basic Lambda

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

---

## ✅ Example 2: With Parameters

```cpp
auto add = [](int a, int b) {
    return a + b;
};
cout << add(3, 4);  // Output: 7
```

---

## ✅ Example 3: With Capture List

```cpp
int x = 10;
auto show = [x]() {
    cout << "Captured x = " << x << endl;
};
show();
```

---

## 🎯 Capture List Variants

| Syntax    | Meaning                                    |
| --------- | ------------------------------------------ |
| `[]`      | Capture nothing                            |
| `[x]`     | Capture variable `x` by value              |
| `[&x]`    | Capture variable `x` by reference          |
| `[=]`     | Capture all local variables by value       |
| `[&]`     | Capture all local variables by reference   |
| `[=, &y]` | Capture all by value, but `y` by reference |

---

## ✅ Example with `for_each` and Lambda

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    vector<int> v = {1, 2, 3, 4};
    int multiplier = 2;

    for_each(v.begin(), v.end(), [multiplier](int x) {
        cout << x * multiplier << " ";
    });
}
```

**Output:**

```
2 4 6 8
```

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
