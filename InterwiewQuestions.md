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
