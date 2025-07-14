

### 🔹 **C++ Core & OOP**

---

#### **1. Difference between C and C++**

**Definition:**

* **C** is a procedural programming language.
* **C++** is a multi-paradigm language (procedural + object-oriented).

**Key Differences:**

| Feature              | C             | C++             |
| -------------------- | ------------- | --------------- |
| Paradigm             | Procedural    | Object-Oriented |
| Encapsulation        | Not supported | Supported       |
| Function Overloading | Not supported | Supported       |
| STL                  | Not available | Available       |

**Example:**

```c
// C
#include <stdio.h>
void sayHello() { printf("Hello from C\n"); }
```

```cpp
// C++
#include <iostream>
class Greeter {
public:
    void sayHello() { std::cout << "Hello from C++\n"; }
};
```

---

#### **2. How does memory management work in C++?**

**Definition:**
Memory in C++ is managed using **stack** (automatic) and **heap** (dynamic). Developers use `new/delete` or smart pointers.

**Example:**

```cpp
int* p = new int(5); // Allocates memory on heap
delete p;            // Frees the memory
```

---

#### **3. What is RAII in C++?**

**Definition:**
**RAII (Resource Acquisition Is Initialization)** is a design pattern where resource allocation is tied to object lifetime.

**Example:**

```cpp
#include <fstream>
void readFile() {
    std::ifstream file("data.txt"); // File opened here
    // File automatically closed when `file` goes out of scope
}
```

---

#### **4. Rule of 3 / Rule of 5 / Rule of 0**

**Rule of 3:** If a class defines **copy constructor, copy assignment operator, or destructor**, it likely needs all three.

**Rule of 5:** Also includes **move constructor** and **move assignment operator** (C++11 onwards).

**Rule of 0:** Prefer not to define any, use smart pointers to avoid manual memory management.

**Example:**

```cpp
class RuleOfFive {
    int* data;
public:
    RuleOfFive() : data(new int(0)) {}
    ~RuleOfFive() { delete data; }
    RuleOfFive(const RuleOfFive& other); // Copy constructor
    RuleOfFive& operator=(const RuleOfFive& other); // Copy assignment
    RuleOfFive(RuleOfFive&& other); // Move constructor
    RuleOfFive& operator=(RuleOfFive&& other); // Move assignment
};
```

---

#### **5. Shallow copy vs Deep copy**

**Shallow Copy:** Copies pointer, not actual data.
**Deep Copy:** Allocates new memory and copies data.

**Example:**

```cpp
class Copy {
    int* data;
public:
    Copy(int val) { data = new int(val); }
    Copy(const Copy& other) { data = new int(*other.data); } // Deep copy
};
```

---

#### **6. Features of C++ useful for system-level programming**

* Direct memory access with pointers
* Manual memory management
* Low-level bitwise operations
* Inline assembly support
* Deterministic object destruction (RAII)
* STL for efficient data handling

---

#### **7. Pointer vs Reference**

| Feature           | Pointer | Reference |
| ----------------- | ------- | --------- |
| Can be null       | Yes     | No        |
| Can be reassigned | Yes     | No        |
| Syntax            | `*`     | `&`       |

**Example:**

```cpp
int x = 10;
int* p = &x; // Pointer
int& r = x;  // Reference
```

---

#### **8. Use of `const` in C++**

**Definition:**
`const` makes variables or functions **read-only**.

**Example:**

```cpp
void print(const int& x) {
    // x cannot be modified
}
```

---

#### **9. Virtual function and vtable**

**Virtual Function:** Enables **runtime polymorphism**.
**vtable:** A lookup table storing addresses of virtual functions.

**Example:**

```cpp
class Base {
public:
    virtual void show() { std::cout << "Base\n"; }
};

class Derived : public Base {
public:
    void show() override { std::cout << "Derived\n"; }
};
```

---

#### **10. What is object slicing?**

**Definition:**
Occurs when a derived class object is assigned to a base class object, slicing off derived parts.

**Example:**

```cpp
class Base { int x; };
class Derived : public Base { int y; };

Base b = Derived(); // y is sliced off
```

---

#### **11. Multiple Inheritance & Ambiguity**

**Definition:**
C++ allows a class to inherit from multiple classes.
Ambiguity arises if both base classes have same member.

**Solution:** Use **virtual inheritance**.

**Example:**

```cpp
class A { public: void greet() {} };
class B { public: void greet() {} };
class C : public A, public B {}; // Ambiguity: greet()
```

---

#### **12. Dynamic Dispatch**

**Definition:**
The mechanism that selects function implementation at **runtime** using virtual functions.

---

#### **13. Compile-time vs Run-time polymorphism**

| Type         | Example              | Resolved At  |
| ------------ | -------------------- | ------------ |
| Compile-time | Function overloading | Compile time |
| Run-time     | Virtual functions    | Runtime      |

---

#### **14. Five default special member functions**

1. Default constructor
2. Copy constructor
3. Copy assignment operator
4. Destructor
5. Move constructor (C++11)
6. Move assignment operator (C++11)

---

#### **15. Undefined behavior in C++**

**Definition:**
Code that leads to unpredictable results (crashes, silent bugs, etc.)

**Example:**

```cpp
int x = 10;
int y = x++ + ++x; // UB: modifies and accesses x in same expression
```

---

#### **16. Operator Overloading & Pitfalls**

**Definition:**
Allows redefining operators for user-defined types.

**Pitfalls:**

* Overloading can reduce code clarity
* Must not change operator meaning too much

**Example:**

```cpp
class Point {
    int x;
public:
    Point(int x) : x(x) {}
    Point operator+(const Point& p) { return Point(x + p.x); }
};
```

---

#### **17. Diamond Problem & Solution**

**Definition:**
Occurs in multiple inheritance when two base classes share a common base.

**Solution:** Use **virtual inheritance**.

**Example:**

```cpp
class A { public: int x; };
class B : virtual public A {};
class C : virtual public A {};
class D : public B, public C {}; // Only one A part exists
```

---

Absolutely! Here's a detailed explanation with **definition, solution, and example** for each question under:

---

### 🔹 **Memory Management & Allocation**

---

#### **18. How to prevent C++ object from being created on heap?**

**Definition:**
To restrict a class so that objects can **only** be created on the **stack**, you can make the `operator new` and `operator delete` private or delete them.

**Solution:** Disable heap allocation by deleting `new`.

**Example:**

```cpp
class OnlyStack {
public:
    OnlyStack() {}
    ~OnlyStack() {}

    void* operator new(size_t) = delete;
    void operator delete(void*) = delete;
};

int main() {
    OnlyStack obj;       // OK: Stack allocation
    // OnlyStack* p = new OnlyStack(); // Error: new is deleted
}
```

---

#### **19. How does `new/delete` differ from `malloc/free`?**

| Feature          | `new/delete` | `malloc/free` |
| ---------------- | ------------ | ------------- |
| Language         | C++          | C             |
| Constructor Call | Yes          | No            |
| Type Safety      | Type-safe    | Not type-safe |
| Overloadable     | Yes          | No            |

**Example:**

```cpp
// C++
int* p = new int(10);  // Allocates and initializes
delete p;

// C-style
int* q = (int*)malloc(sizeof(int));
*q = 10;
free(q);
```

---

#### **20. How to avoid memory leaks in C++?**

**Definition:**
A memory leak occurs when memory is allocated but not deallocated.

**Solutions:**

* Always `delete` what you `new`
* Use **smart pointers** (`std::unique_ptr`, `std::shared_ptr`)
* Follow **RAII** (Resource Acquisition Is Initialization)
* Use tools like **Valgrind**, **AddressSanitizer**

**Example (using smart pointer):**

```cpp
#include <memory>

void useMemory() {
    std::unique_ptr<int> ptr = std::make_unique<int>(10); // Automatically deallocated
}
```

---

#### **21. What is a deleted copy constructor?**

**Definition:**
A **deleted copy constructor** prevents copying of an object.

**Use Case:** To make class **non-copyable**, such as for singleton or resource-handling classes.

**Example:**

```cpp
class NonCopyable {
public:
    NonCopyable() {}
    NonCopyable(const NonCopyable&) = delete; // Prevent copy
    NonCopyable& operator=(const NonCopyable&) = delete;
};

int main() {
    NonCopyable a;
    // NonCopyable b = a; // Error: copy constructor is deleted
}
```

---

#### **22. How is memory stored for structs in C++?**

**Definition:**
Struct members are stored **contiguously in memory**, and **aligned** based on the largest member’s alignment requirements.

**Important Concepts:**

* **Padding** may be added for alignment.
* Size can be more than sum of all member sizes.

**Example:**

```cpp
struct MyStruct {
    char a;     // 1 byte
    int b;      // 4 bytes (likely starts at offset 4)
    double c;   // 8 bytes
};

// Use sizeof(MyStruct) to check total size (may include padding)
```

---

#### **23. What is garbage collection? Does C++ support it?**

**Definition:**
**Garbage Collection (GC)** is an automatic memory management process that reclaims memory no longer in use.

**Does C++ support GC?**

* **No**, C++ does not have built-in garbage collection.
* But it offers **deterministic destruction** using RAII.
* **Smart pointers** serve similar purpose as GC by automatically managing memory.

**Example using `shared_ptr`:**

```cpp
#include <memory>
void example() {
    std::shared_ptr<int> ptr = std::make_shared<int>(42);
    // Memory automatically freed when last reference is destroyed
}
```

---

Here’s a complete explanation with **definition, solution, and example** for each question in the **STL (Standard Template Library)** section:

---

### 🔹 **STL (Standard Template Library)**

---

#### **24. Difference between `vector`, `list`, `deque`, `array`, `set`, `map`, `unordered_map`**

| Container       | Description                  | Underlying Structure    | Best Use                        |
| --------------- | ---------------------------- | ----------------------- | ------------------------------- |
| `vector`        | Dynamic array                | Contiguous array        | Fast access, slow insert/remove |
| `list`          | Doubly linked list           | Doubly linked list      | Fast insert/delete anywhere     |
| `deque`         | Double-ended queue           | Segmented dynamic array | Fast insert/remove at both ends |
| `array`         | Fixed-size array (C++11)     | Contiguous array        | Simple fixed-size arrays        |
| `set`           | Unique sorted elements       | Balanced BST            | Ordered unique elements         |
| `map`           | Key-value pairs (ordered)    | Balanced BST            | Ordered key-value lookup        |
| `unordered_map` | Key-value pairs (hash table) | Hash Table              | Fast lookup (O(1) avg)          |

---

#### **25. Time Complexity of Insertion/Access in STL Containers**

| Container       | Access      | Insertion (avg/worst)         |
| --------------- | ----------- | ----------------------------- |
| `vector`        | O(1)        | O(1) / O(n)                   |
| `list`          | O(n)        | O(1) (anywhere with iterator) |
| `deque`         | O(1)        | O(1) / O(n)                   |
| `array`         | O(1)        | Fixed size (no insertion)     |
| `set`/`map`     | O(log n)    | O(log n)                      |
| `unordered_map` | O(1) / O(n) | O(1) / O(n)                   |

---

#### **26. What are iterators? What are their types?**

**Definition:**
An iterator is an object that points to elements of a container, similar to pointers.

**Types of Iterators:**

* **Input Iterator**
* **Output Iterator**
* **Forward Iterator**
* **Bidirectional Iterator**
* **Random Access Iterator**

**Example:**

```cpp
std::vector<int> v = {1, 2, 3};
for (std::vector<int>::iterator it = v.begin(); it != v.end(); ++it)
    std::cout << *it << " ";
```

---

#### **27. Difference between `emplace()` and `insert()`**

| Feature     | `insert()`                  | `emplace()`         |
| ----------- | --------------------------- | ------------------- |
| Efficiency  | Constructs temporary object | Constructs in-place |
| Performance | May copy/move               | Avoids copy/move    |

**Example:**

```cpp
std::vector<std::pair<int, int>> v;
v.insert(v.end(), std::make_pair(1, 2));
v.emplace_back(3, 4); // More efficient
```

---

#### **28. What are `multimap` and `unordered_multimap`?**

**Definition:**

* `multimap`: Allows **duplicate keys**, sorted by keys.
* `unordered_multimap`: Allows **duplicate keys**, not sorted (uses hash table).

**Example:**

```cpp
std::multimap<int, std::string> m;
m.insert({1, "A"});
m.insert({1, "B"}); // Duplicate key allowed
```

---

#### **29. Use of `lower_bound()` and `upper_bound()`**

**Definition:**

* `lower_bound(x)`: First element **≥ x**
* `upper_bound(x)`: First element **> x**

**Only works on sorted containers or with custom comparator.**

**Example:**

```cpp
std::vector<int> v = {10, 20, 30, 40};
auto it1 = std::lower_bound(v.begin(), v.end(), 25); // -> 30
auto it2 = std::upper_bound(v.begin(), v.end(), 30); // -> 40
```

---

#### **30. How does `std::sort()` work internally?**

**Definition:**
`std::sort()` (from `<algorithm>`) uses **Introsort**, a hybrid of:

* Quicksort (fast average case)
* Heapsort (guaranteed worst case)
* Insertion sort (for small ranges)

**Example:**

```cpp
std::vector<int> v = {3, 1, 4, 2};
std::sort(v.begin(), v.end());
```

---

#### **31. What is a lambda function in C++? Provide example**

**Definition:**
A lambda is an **anonymous function** that can be defined inline.

**Syntax:**

```cpp
[capture](params) -> return_type { body }
```

**Example:**

```cpp
auto add = [](int a, int b) { return a + b; };
std::cout << add(2, 3); // Output: 5
```

---

#### **32. What are smart pointers? (`unique_ptr`, `shared_ptr`, `weak_ptr`)**

| Smart Pointer | Description                             |
| ------------- | --------------------------------------- |
| `unique_ptr`  | Single ownership, cannot be copied      |
| `shared_ptr`  | Shared ownership via reference counting |
| `weak_ptr`    | Non-owning reference to `shared_ptr`    |

**Example:**

```cpp
std::unique_ptr<int> u = std::make_unique<int>(10);
std::shared_ptr<int> s1 = std::make_shared<int>(20);
std::weak_ptr<int> w = s1; // Does not increase ref count
```

---

#### **33. What are functors and how are they used in STL algorithms?**

**Definition:**
A **functor** is an object that behaves like a function — it overloads `operator()`.

**Use Case:** Custom comparison, transformation, filtering in STL algorithms.

**Example:**

```cpp
struct Square {
    int operator()(int x) const { return x * x; }
};

std::transform(v.begin(), v.end(), v.begin(), Square());
```

---

Here is a complete set of **definitions, solutions, and examples** for each topic under:

---

### 🔹 **DSA (Data Structures & Algorithms)**

---

#### **34. How to remove duplicates while maintaining order?**

**Definition:**
Keep only the first occurrence of each element while preserving order.

**Solution (C++):**

```cpp
std::vector<int> nums = {1, 2, 2, 3, 1, 4};
std::unordered_set<int> seen;
std::vector<int> result;

for (int num : nums) {
    if (seen.insert(num).second)
        result.push_back(num);
}
```

---

#### **35. Implement in-place transpose of a matrix**

**Definition:**
Transpose: swap `matrix[i][j]` with `matrix[j][i]`.

**Solution (Square matrix):**

```cpp
for (int i = 0; i < n; ++i)
    for (int j = i + 1; j < n; ++j)
        std::swap(matrix[i][j], matrix[j][i]);
```

---

#### **36. Find second highest salary in SQL**

**Query:**

```sql
SELECT MAX(salary)
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

---

#### **37. Implement Fibonacci sequence (recursive/iterative)**

**Recursive:**

```cpp
int fib(int n) {
    if (n <= 1) return n;
    return fib(n - 1) + fib(n - 2);
}
```

**Iterative:**

```cpp
int fib(int n) {
    int a = 0, b = 1;
    for (int i = 2; i <= n; ++i) {
        int tmp = b;
        b = a + b;
        a = tmp;
    }
    return n ? b : a;
}
```

---

#### **38. Implement FizzBuzz**

**Definition:**
Print numbers 1 to n, but:

* “Fizz” for multiples of 3
* “Buzz” for multiples of 5
* “FizzBuzz” for both

**Solution:**

```cpp
for (int i = 1; i <= 100; ++i) {
    if (i % 15 == 0) std::cout << "FizzBuzz\n";
    else if (i % 3 == 0) std::cout << "Fizz\n";
    else if (i % 5 == 0) std::cout << "Buzz\n";
    else std::cout << i << "\n";
}
```

---

#### **39. What is the bin-packing problem?**

**Definition:**
Pack items of different sizes into finite bins of fixed capacity to **minimize bin usage**.

**Example:**
Given items `[4, 8, 1, 4, 2, 1]` and bin size 10, use **greedy** or **DP** to pack efficiently.

---

#### **40. Reverse a linked list**

**Solution:**

```cpp
ListNode* reverseList(ListNode* head) {
    ListNode *prev = nullptr, *curr = head;
    while (curr) {
        ListNode* next = curr->next;
        curr->next = prev;
        prev = curr;
        curr = next;
    }
    return prev;
}
```

---

#### **41. Detect cycle in a linked list**

**Solution (Floyd’s Algorithm):**

```cpp
bool hasCycle(ListNode* head) {
    ListNode *slow = head, *fast = head;
    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;
        if (slow == fast) return true;
    }
    return false;
}
```

---

#### **42. Merge two sorted arrays/lists**

**Solution (C++ STL for arrays):**

```cpp
std::vector<int> result;
std::merge(arr1.begin(), arr1.end(), arr2.begin(), arr2.end(), std::back_inserter(result));
```

**Manual Merge (lists):**

```cpp
ListNode* merge(ListNode* l1, ListNode* l2) {
    ListNode dummy, *tail = &dummy;
    while (l1 && l2) {
        if (l1->val < l2->val) { tail->next = l1; l1 = l1->next; }
        else { tail->next = l2; l2 = l2->next; }
        tail = tail->next;
    }
    tail->next = l1 ? l1 : l2;
    return dummy.next;
}
```

---

#### **43. Kth smallest/largest element**

**Solution using Min/Max Heap:**

```cpp
// Kth largest
std::priority_queue<int, std::vector<int>, std::greater<>> minHeap;

for (int num : nums) {
    minHeap.push(num);
    if (minHeap.size() > k) minHeap.pop();
}
return minHeap.top();
```

---

#### **44. Longest substring without repeating characters**

**Sliding Window Approach:**

```cpp
int lengthOfLongestSubstring(std::string s) {
    std::unordered_set<char> seen;
    int left = 0, maxLen = 0;
    for (int right = 0; right < s.length(); ++right) {
        while (seen.count(s[right]))
            seen.erase(s[left++]);
        seen.insert(s[right]);
        maxLen = std::max(maxLen, right - left + 1);
    }
    return maxLen;
}
```

---

#### **45. Top K frequent elements using priority queue**

**Solution:**

```cpp
std::unordered_map<int, int> freq;
for (int n : nums) freq[n]++;

std::priority_queue<std::pair<int, int>> pq;
for (auto& [num, count] : freq)
    pq.push({count, num});

std::vector<int> result;
for (int i = 0; i < k; ++i) {
    result.push_back(pq.top().second);
    pq.pop();
}
```

---

#### **46. Remove duplicates in vector of strings with better than O(n²)**

**Efficient Solution:**

```cpp
std::unordered_set<std::string> seen;
std::vector<std::string> result;

for (const auto& str : strings) {
    if (seen.insert(str).second)
        result.push_back(str);
}
```

---

#### **47. Solve Knapsack using Dynamic Programming (0/1 Knapsack)**

**Problem:**
Maximize value with given weight limit.

**Solution (DP Table):**

```cpp
int knapsack(int W, const std::vector<int>& wt, const std::vector<int>& val) {
    int n = wt.size();
    std::vector<std::vector<int>> dp(n+1, std::vector<int>(W+1, 0));

    for (int i = 1; i <= n; ++i)
        for (int w = 0; w <= W; ++w)
            if (wt[i-1] <= w)
                dp[i][w] = std::max(dp[i-1][w], dp[i-1][w - wt[i-1]] + val[i-1]);
            else
                dp[i][w] = dp[i-1][w];
    
    return dp[n][W];
}
```

---

Here’s a detailed explanation with **definitions, code examples, and solutions** for each topic in:

---

### 🔹 **Multithreading & Concurrency**

---

#### **48. What is a thread-safe function?**

**Definition:**
A **thread-safe function** can be safely called by multiple threads at the same time **without causing data races or inconsistent results**.

**Solution:**
Use **mutex**, **atomic operations**, or avoid shared mutable state.

**Example:**

```cpp
std::mutex mtx;

void incrementCounter(int& counter) {
    std::lock_guard<std::mutex> lock(mtx); // Ensures thread safety
    ++counter;
}
```

---

#### **49. How to create threads in C++11?**

**Solution:**
Use `std::thread`.

**Example:**

```cpp
#include <iostream>
#include <thread>

void sayHello() {
    std::cout << "Hello from thread!\n";
}

int main() {
    std::thread t(sayHello); // Create thread
    t.join(); // Wait for thread to finish
    return 0;
}
```

---

#### **50. Difference between `join()` and `detach()` in C++ threads**

| Function   | Description                                                   |
| ---------- | ------------------------------------------------------------- |
| `join()`   | Waits for thread to finish execution                          |
| `detach()` | Detaches thread to run independently (cannot be joined later) |

**Example:**

```cpp
std::thread t1(task);
t1.join(); // Main waits

std::thread t2(task);
t2.detach(); // Main does NOT wait
```

---

#### **51. What is a race condition and how to avoid it?**

**Definition:**
A **race condition** occurs when two or more threads access shared data concurrently and at least one modifies it, leading to unpredictable results.

**Solution:** Use synchronization primitives like **mutex**.

**Example (Race fixed):**

```cpp
int counter = 0;
std::mutex m;

void increment() {
    std::lock_guard<std::mutex> lock(m);
    ++counter;
}
```

---

#### **52. How to handle multiple threads reading and writing to the same file?**

**Solution:**

* Use `std::mutex` to **synchronize file access**.
* Consider using **read/write locks** (e.g., `std::shared_mutex` in C++17).

**Example:**

```cpp
std::mutex file_mutex;

void writeToFile(std::ofstream& file, const std::string& msg) {
    std::lock_guard<std::mutex> lock(file_mutex);
    file << msg << std::endl;
}
```

---

#### **53. How to allow 3 threads to read and 1 to write without blocking readers?**

**Solution:**
Use **read-write locks** (`std::shared_mutex` in C++17).

**Example:**

```cpp
#include <shared_mutex>

std::shared_mutex rw_mutex;

void reader() {
    std::shared_lock lock(rw_mutex); // multiple readers allowed
    // read data
}

void writer() {
    std::unique_lock lock(rw_mutex); // exclusive access
    // write data
}
```

---

#### **54. What are mutex, semaphore, and condition variables?**

| Mechanism               | Description                                |
| ----------------------- | ------------------------------------------ |
| **mutex**               | Locks shared resource for one thread       |
| **semaphore**           | Counting mechanism to allow limited access |
| **condition\_variable** | Allows threads to wait for some condition  |

**Example:**

```cpp
std::mutex mtx;
std::condition_variable cv;
bool ready = false;

void worker() {
    std::unique_lock<std::mutex> lock(mtx);
    cv.wait(lock, [] { return ready; });
    // Proceed when ready
}
```

---

#### **55. How to prevent deadlock?**

**Solutions:**

* Lock resources in a consistent order
* Use `std::lock()` to lock multiple mutexes atomically
* Avoid nested locks
* Use timeout with `try_lock()`

**Example:**

```cpp
std::mutex m1, m2;

void safe_lock() {
    std::lock(m1, m2);
    std::lock_guard<std::mutex> lock1(m1, std::adopt_lock);
    std::lock_guard<std::mutex> lock2(m2, std::adopt_lock);
}
```

---

#### **56. Difference between `std::mutex` and `std::lock_guard`**

| Feature          | `std::mutex`   | `std::lock_guard` |
| ---------------- | -------------- | ----------------- |
| Manual unlocking | Required       | Automatic (RAII)  |
| Exception safety | Not guaranteed | Guaranteed        |

**Example:**

```cpp
std::mutex m;

void safe() {
    std::lock_guard<std::mutex> lock(m); // automatically released
    // critical section
}
```

---

#### **57. How to measure the time taken by a function/code block?**

**Solution:** Use `<chrono>`.

**Example:**

```cpp
#include <chrono>
#include <iostream>

auto start = std::chrono::high_resolution_clock::now();

// Code block
std::this_thread::sleep_for(std::chrono::milliseconds(100));

auto end = std::chrono::high_resolution_clock::now();
auto duration = std::chrono::duration_cast<std::chrono::milliseconds>(end - start);
std::cout << "Time taken: " << duration.count() << " ms\n";
```

---

Great! Here's the final section with **definitions, solutions, and examples** for:

---

### 🔹 **System & OS Related**

---

#### **58. What are IPC mechanisms used in Linux/C++?**

**Definition:**
IPC (Inter-Process Communication) allows processes to **communicate and share data**.

**Common IPC mechanisms:**

* **Pipes** (`pipe()`)
* \*\*Named Pipes (FIFOs)` (`mkfifo()\`)
* **Message Queues**
* **Shared Memory** (`shmget()`, `shmat()`)
* **Sockets**
* **Signals**

**Example (Pipe):**

```cpp
int fd[2];
pipe(fd);
write(fd[1], "hello", 5);
char buffer[6];
read(fd[0], buffer, 5);
buffer[5] = '\0';
std::cout << buffer; // Output: hello
```

---

#### **59. What is the difference between `select()` and `poll()`?**

| Feature     | `select()`               | `poll()`                    |
| ----------- | ------------------------ | --------------------------- |
| FD Limit    | Limited (typically 1024) | No hard limit               |
| Data Struct | Bitmask (fd\_set)        | Array of `pollfd` structs   |
| Performance | Slower for many FDs      | Scales better for large FDs |

**Use Case:** Monitoring multiple file descriptors (I/O readiness).

---

#### **60. What are blocking system calls in socket programming?**

**Definition:**
A **blocking call** waits until the operation completes (e.g., `accept()`, `recv()`, `read()`).

**Example:**

```cpp
int client = accept(server_fd, nullptr, nullptr); // Blocks until a client connects
```

**To make non-blocking:**

```cpp
fcntl(sock_fd, F_SETFL, O_NONBLOCK);
```

---

#### **61. What is memory-mapped I/O?**

**Definition:**
Memory-mapped I/O maps a file or device into memory, allowing file data to be accessed like an array.

**Benefits:**

* Faster file I/O
* Efficient shared memory

**Example:**

```cpp
int fd = open("file.txt", O_RDONLY);
char* data = (char*)mmap(nullptr, filesize, PROT_READ, MAP_PRIVATE, fd, 0);
// Access file like an array: data[0], data[1], ...
```

---

#### **62. What is a file descriptor?**

**Definition:**
A **file descriptor** is a non-negative integer used to access files and I/O streams in Unix/Linux.

| Descriptor | Meaning |
| ---------- | ------- |
| 0          | stdin   |
| 1          | stdout  |
| 2          | stderr  |

**Example:**

```cpp
int fd = open("data.txt", O_RDONLY);
read(fd, buffer, size); // Use fd to read from file
close(fd);
```

---

#### **63. How does Linux file management system work?**

**Definition:**
The Linux file system uses a **hierarchical structure** and manages files via:

* **Inodes**: store metadata (owner, permissions, etc.)
* **Directories**: map names to inodes
* **Virtual File System (VFS)**: abstraction over ext4, NTFS, etc.

**Key Components:**

* `open()` → gets file descriptor
* `read()/write()` → performs I/O
* `close()` → releases file descriptor

**Example:**

```cpp
int fd = open("notes.txt", O_WRONLY | O_CREAT, 0644);
write(fd, "Hello", 5);
close(fd);
```

---


### 1. **Find the Largest and Smallest Element**

#### Pseudocode:

```
Initialize max = INT_MIN, min = INT_MAX
Loop through each element:
    if element > max → update max
    if element < min → update min
```

#### C++ Code:

```cpp
int max = INT_MIN, min = INT_MAX;
for (int i = 0; i < n; i++) {
    if (arr[i] > max) max = arr[i];
    if (arr[i] < min) min = arr[i];
}
```

---

### 2. **Find the Second Largest Element**

#### Pseudocode:

```
Initialize largest = second = INT_MIN
Loop:
    if element > largest:
        second = largest
        largest = element
    else if element > second and element != largest:
        second = element
```

#### C++ Code:

```cpp
int largest = INT_MIN, second = INT_MIN;
for (int i = 0; i < n; i++) {
    if (arr[i] > largest) {
        second = largest;
        largest = arr[i];
    } else if (arr[i] > second && arr[i] != largest) {
        second = arr[i];
    }
}
```

---

### 3. **Reverse an Array**

#### Pseudocode:

```
Use two pointers (start, end)
Swap elements at start and end until they meet
```

#### C++ Code:

```cpp
int start = 0, end = n - 1;
while (start < end) {
    std::swap(arr[start], arr[end]);
    start++;
    end--;
}
```

---

### 4. **Check if Array is Sorted**

#### Pseudocode:

```
Loop from 1 to n-1:
    if arr[i] < arr[i-1], return false
Return true
```

#### C++ Code:

```cpp
bool isSorted = true;
for (int i = 1; i < n; i++) {
    if (arr[i] < arr[i - 1]) {
        isSorted = false;
        break;
    }
}
```

---

### 5. **Left/Right Rotate by K Positions**

#### C++ Code (Left Rotate):
```cpp
void reverse(int arr[], int start, int end) {
    while (start < end)
        std::swap(arr[start++], arr[end--]);
}
void leftRotateReversal(int arr[], int n, int k) {
    k = k % n;
    reverse(arr, 0, k - 1);
    reverse(arr, k, n - 1);
    reverse(arr, 0, n - 1);
}
```


#### Pseudocode (Right Rotate):

```
k = k % n
Reverse whole array
Reverse first k elements
Reverse rest
```

#### C++ Code (Right Rotate):

```cpp
void rightRotateEfficient(int arr[], int n, int k) {
    k = k % n;
    reverse(arr, n - k, n - 1);
    reverse(arr, 0, n - k - 1);
    reverse(arr, 0, n - 1);
}
```

---

### 6. **Remove Duplicates from Sorted Array**

#### Pseudocode:

```
Use two pointers (i, j)
If arr[i] != arr[j], copy to next position
```

#### C++ Code:

```cpp
int j = 0;
for (int i = 1; i < n; i++) {
    if (arr[i] != arr[j]) {
        j++;
        arr[j] = arr[i];
    }
}
int newLength = j + 1;
```

---

### 7. **Find Missing Number (1 to N)**

#### Pseudocode:

```
Sum of 1 to N = n*(n+1)/2
Subtract actual sum from expected
```

#### C++ Code:

```cpp
int total = n * (n + 1) / 2;
int sum = 0;
for (int i = 0; i < n - 1; i++) sum += arr[i];
int missing = total - sum;
```

---

### 8. **Frequency of Each Element**

#### Pseudocode:

```
Use a hashmap (unordered_map)
Loop and increment count
```

#### C++ Code:

```cpp
std::unordered_map<int, int> freq;
for (int i = 0; i < n; i++) freq[arr[i]]++;
```

---

### 9. **Merge Two Sorted Arrays**

#### Pseudocode:

```
Use two pointers to compare and merge into new array
```

#### C++ Code:

```cpp
int i = 0, j = 0, k = 0;
while (i < n1 && j < n2) {
    if (a[i] < b[j]) c[k++] = a[i++];
    else c[k++] = b[j++];
}
while (i < n1) c[k++] = a[i++];
while (j < n2) c[k++] = b[j++];
```

---

###  10. **Kadane's Algorithm (Max Subarray Sum)**

#### Pseudocode:

```
Initialize current_sum = 0, max_sum = INT_MIN
Loop through array:
    current_sum = max(element, current_sum + element)
    max_sum = max(max_sum, current_sum)
```

#### C++ Code:

```cpp
int maxSum = INT_MIN, currSum = 0;
for (int i = 0; i < n; i++) {
    currSum = std::max(arr[i], currSum + arr[i]);
    maxSum = std::max(maxSum, currSum);
}
```

---


## 11. **Sort 0s, 1s, and 2s** (Dutch National Flag Problem)

### Pseudocode:

```
Initialize low = 0, mid = 0, high = n - 1
While mid <= high:
    if arr[mid] == 0 → swap with arr[low], low++, mid++
    if arr[mid] == 1 → mid++
    if arr[mid] == 2 → swap with arr[high], high--
```

### C++ Code:

```cpp
void sort012(int arr[], int n) {
    int low = 0, mid = 0, high = n - 1;
    while (mid <= high) {
        if (arr[mid] == 0)
            std::swap(arr[low++], arr[mid++]);
        else if (arr[mid] == 1)
            mid++;
        else
            std::swap(arr[mid], arr[high--]);
    }
}
```

---

## 12. **Find All Pairs with a Given Sum**

### Pseudocode:

```
Initialize an empty hash set
For each element x:
    Check if (target - x) exists in set
    If yes, it's a valid pair
    Insert x into the set
```

### C++ Code:

```cpp
void findPairs(int arr[], int n, int target) {
    std::unordered_set<int> seen;
    for (int i = 0; i < n; i++) {
        int complement = target - arr[i];
        if (seen.count(complement))
            std::cout << "(" << arr[i] << ", " << complement << ")\n";
        seen.insert(arr[i]);
    }
}
```

---

## 13. **Find Leaders in an Array**

*A leader is an element greater than all elements to its right.*

### Pseudocode:

```
Start from the rightmost element, mark it as current leader
Loop from n-2 to 0:
    if arr[i] > current leader → it’s a new leader
```

### C++ Code:

```cpp
void printLeaders(int arr[], int n) {
    int maxRight = arr[n - 1];
    std::cout << maxRight << " ";
    for (int i = n - 2; i >= 0; i--) {
        if (arr[i] > maxRight) {
            maxRight = arr[i];
            std::cout << maxRight << " ";
        }
    }
}
```

---

## 14. **Find Majority Element (Moore’s Voting Algorithm)**

*A majority element appears more than n/2 times.*

### Pseudocode:

```
Phase 1 (Find candidate):
    Initialize count = 0, candidate = None
    Loop:
        if count == 0 → candidate = current
        if current == candidate → count++
        else → count--

Phase 2 (Verify candidate):
    Count actual frequency of candidate
```

### C++ Code:

```cpp
int findMajority(int arr[], int n) {
    int count = 0, candidate = -1;
    for (int i = 0; i < n; i++) {
        if (count == 0)
            candidate = arr[i];
        count += (arr[i] == candidate) ? 1 : -1;
    }

    count = 0;
    for (int i = 0; i < n; i++)
        if (arr[i] == candidate)
            count++;

    return (count > n / 2) ? candidate : -1;
}
```

---

## 15. **Subarray with Given Sum** (Positive integers only)

### Pseudocode:

```
Use sliding window:
Initialize start = 0, currSum = arr[0]
Loop i = 1 to n:
    while currSum > target → subtract arr[start++]
    if currSum == target → print start to i-1
    add arr[i] to currSum
```

### C++ Code:

```cpp
void subarrayWithSum(int arr[], int n, int target) {
    int start = 0, currSum = arr[0];
    for (int end = 1; end <= n; end++) {
        while (currSum > target && start < end - 1)
            currSum -= arr[start++];

        if (currSum == target) {
            std::cout << "Subarray found from index " << start
                      << " to " << end - 1 << std::endl;
            return;
        }

        if (end < n)
            currSum += arr[end];
    }
    std::cout << "No subarray with given sum\n";
}
```

---
String
---

## 1. **Reverse a String**

### Pseudocode:

```
Use two pointers: start = 0, end = length - 1
Swap characters at start and end
Move start++, end--
```

### C++ Code:

```cpp
#include <iostream>
#include <string>
#include <algorithm>

void reverseString(std::string &s) {
    int start = 0, end = s.length() - 1;
    while (start < end) {
        std::swap(s[start++], s[end--]);
    }
}
```

---

## 2. **Check if a String is Palindrome**

### Pseudocode:

```
Compare characters from both ends
If any mismatch → not a palindrome
```

### C++ Code:

```cpp
bool isPalindrome(const std::string &s) {
    int start = 0, end = s.length() - 1;
    while (start < end) {
        if (s[start++] != s[end--])
            return false;
    }
    return true;
}
```

---

## 3. **Find Frequency of Characters in a String**

### Pseudocode:

```
Use an array or map to count frequency of each character
```

### C++ Code:

```cpp
#include <unordered_map>

void charFrequency(const std::string &s) {
    std::unordered_map<char, int> freq;
    for (char c : s) freq[c]++;
    
    for (auto &p : freq)
        std::cout << p.first << " : " << p.second << std::endl;
}
```

---

## 4. **Check for Anagram**

### Pseudocode:

```
If lengths are different → not anagram
Sort both strings and compare
OR
Count character frequencies and compare
```

### C++ Code (using frequency):

```cpp
bool isAnagram(const std::string &a, const std::string &b) {
    if (a.length() != b.length()) return false;
    
    int count[256] = {0};  // assuming ASCII

    for (char c : a) count[c]++;
    for (char c : b) count[c]--;

    for (int i = 0; i < 256; i++) {
        if (count[i] != 0) return false;
    }
    return true;
}
```

---

## 5. **Remove All Duplicates from a String (Preserve Order)**

### Pseudocode:

```
Use a visited set or boolean array
Loop through the string, add to result only if not seen
```

### C++ Code:

```cpp
std::string removeDuplicates(const std::string &s) {
    bool seen[256] = {false};
    std::string result;

    for (char c : s) {
        if (!seen[c]) {
            result += c;
            seen[c] = true;
        }
    }
    return result;
}
```

---

## ✅ 1. **Print All Substrings of a String**

### 🧠 Pseudocode:

```
Loop over all starting indices i
Loop over ending indices j (from i to n)
Print substring from i to j
```

### 💻 C++ Code:

```cpp
void printAllSubstrings(const std::string &s) {
    int n = s.length();
    for (int i = 0; i < n; ++i)
        for (int j = i; j < n; ++j)
            std::cout << s.substr(i, j - i + 1) << std::endl;
}
```

---

## ✅ 2. **Longest Common Prefix (LCP) Among Strings**

### 🧠 Pseudocode:

```
Take the first string as base
Compare characters at each position with all strings
Break if mismatch found
```

### 💻 C++ Code:

```cpp
#include <vector>

std::string longestCommonPrefix(const std::vector<std::string> &strs) {
    if (strs.empty()) return "";

    for (int i = 0; i < strs[0].size(); ++i) {
        char c = strs[0][i];
        for (int j = 1; j < strs.size(); ++j) {
            if (i >= strs[j].size() || strs[j][i] != c)
                return strs[0].substr(0, i);
        }
    }
    return strs[0];
}
```

---

## ✅ 3. **Longest Palindromic Substring (Expand Around Center)**

### 🧠 Pseudocode:

```
For each character, expand around center (odd and even)
Track max length and start index
```

### 💻 C++ Code:

```cpp
std::string longestPalindrome(std::string s) {
    int start = 0, maxLen = 1;
    int n = s.size();

    for (int i = 0; i < n; ++i) {
        // Odd length
        int l = i, r = i;
        while (l >= 0 && r < n && s[l] == s[r]) {
            if (r - l + 1 > maxLen) {
                start = l;
                maxLen = r - l + 1;
            }
            l--; r++;
        }

        // Even length
        l = i, r = i + 1;
        while (l >= 0 && r < n && s[l] == s[r]) {
            if (r - l + 1 > maxLen) {
                start = l;
                maxLen = r - l + 1;
            }
            l--; r++;
        }
    }

    return s.substr(start, maxLen);
}
```

---

## ✅ 4. **Implement `strlen`, `strcpy`, `strcat`, `strcmp`**

### 💻 C++ Code:

```cpp
int myStrlen(const char *s) {
    int len = 0;
    while (*s++) len++;
    return len;
}

void myStrcpy(char *dest, const char *src) {
    while ((*dest++ = *src++));
}

void myStrcat(char *dest, const char *src) {
    while (*dest) dest++;  // Move to end
    while ((*dest++ = *src++));
}

int myStrcmp(const char *s1, const char *s2) {
    while (*s1 && (*s1 == *s2)) {
        s1++; s2++;
    }
    return *(unsigned char*)s1 - *(unsigned char*)s2;
}
```

---

## ✅ 5. **Count Vowels, Consonants, Digits, and Spaces**

### 🧠 Pseudocode:

```
Loop through each character:
    if vowel → count++
    if digit → digit++
    if space → space++
    if letter but not vowel → consonant++
```

### 💻 C++ Code:

```cpp
void countChars(const std::string &s) {
    int vowels = 0, consonants = 0, digits = 0, spaces = 0;

    for (char c : s) {
        if (std::isdigit(c)) digits++;
        else if (std::isspace(c)) spaces++;
        else if (std::isalpha(c)) {
            char lower = std::tolower(c);
            if (lower == 'a' || lower == 'e' || lower == 'i' || lower == 'o' || lower == 'u')
                vowels++;
            else
                consonants++;
        }
    }

    std::cout << "Vowels: " << vowels << "\nConsonants: " << consonants
              << "\nDigits: " << digits << "\nSpaces: " << spaces << "\n";
}
```

---


## ✅ 1. **Toggle Case of Each Character**

### 🧠 Pseudocode:

```
Loop through each character:
    if lowercase → convert to uppercase
    if uppercase → convert to lowercase
```

### 💻 C++ Code:

```cpp
void toggleCase(std::string &s) {
    for (char &c : s) {
        if (std::islower(c))
            c = std::toupper(c);
        else if (std::isupper(c))
            c = std::tolower(c);
    }
}
```

---

## ✅ 2. **Convert String to Integer (atoi)**

### 🧠 Pseudocode:

```
Skip leading whitespaces
Handle optional sign
Convert digit characters to integer
Stop if non-digit encountered
```

### 💻 C++ Code:

```cpp
int myAtoi(const std::string &s) {
    int i = 0, result = 0, sign = 1;

    // Skip whitespaces
    while (i < s.length() && s[i] == ' ') i++;

    // Sign
    if (s[i] == '-') { sign = -1; i++; }
    else if (s[i] == '+') { i++; }

    // Convert digits
    while (i < s.length() && std::isdigit(s[i])) {
        result = result * 10 + (s[i] - '0');
        i++;
    }

    return result * sign;
}
```

---

## ✅ 3. **Find the Most Frequent Character**

### 🧠 Pseudocode:

```
Create a frequency map
Track max frequency and character
```

### 💻 C++ Code:

```cpp
char mostFrequentChar(const std::string &s) {
    int freq[256] = {0};
    for (char c : s) freq[(unsigned char)c]++;

    int maxFreq = 0;
    char result = '\0';
    for (int i = 0; i < 256; i++) {
        if (freq[i] > maxFreq) {
            maxFreq = freq[i];
            result = i;
        }
    }
    return result;
}
```

---

## ✅ 4. **Check if Two Strings Are Rotations of Each Other**

### 🧠 Pseudocode:

```
If lengths differ → false
Check if str2 is a substring of str1 + str1
```

### 💻 C++ Code:

```cpp
bool areRotations(const std::string &s1, const std::string &s2) {
    if (s1.length() != s2.length()) return false;
    return (s1 + s1).find(s2) != std::string::npos;
}
```
Pointer
---

## ✅ 1. **Swap Two Variables Using Pointers**

```cpp
void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}
```

---

## ✅ 2. **Print Array Using Pointer Notation**

```cpp
void printArray(int *arr, int n) {
    for (int i = 0; i < n; i++)
        std::cout << *(arr + i) << " ";
}
```

---

## ✅ 3. **Reverse a String Using Pointers**

```cpp
void reverseString(char *str) {
    char *end = str;
    while (*end) end++;
    end--;

    while (str < end) {
        std::swap(*str, *end);
        str++;
        end--;
    }
}
```

---

## ✅ 4. **Find Length of String Using Pointer**

```cpp
int stringLength(const char *str) {
    const char *p = str;
    while (*p) p++;
    return p - str;
}
```

---

## ✅ 5. **Access 2D Array Using Pointers**

```cpp
void print2D(int *arr, int rows, int cols) {
    for (int i = 0; i < rows; i++)
        for (int j = 0; j < cols; j++)
            std::cout << *(arr + i * cols + j) << " ";
}
```

---

## ✅ 6. **Dynamic Memory Allocation Using `malloc`/`calloc`**

```cpp
int *arr = (int *)malloc(n * sizeof(int));     // malloc
int *arr = (int *)calloc(n, sizeof(int));      // calloc
```

---

## ✅ 7. **Implement `memcpy` Using Pointers**

```cpp
void *myMemcpy(void *dest, const void *src, size_t n) {
    char *d = (char *)dest;
    const char *s = (const char *)src;
    while (n--) *d++ = *s++;
    return dest;
}
```

---

## ✅ 8. **Program Using Function Pointer**

```cpp
void greet() {
    std::cout << "Hello, Pointer to Function!\n";
}

int main() {
    void (*fp)() = greet;
    fp();  // call the function via pointer
}
```

---

## ✅ 9. **Pass Array to Function Using Pointer**

```cpp
void sum(int *arr, int n) {
    int total = 0;
    for (int i = 0; i < n; i++) total += *(arr + i);
    std::cout << "Sum: " << total;
}
```

---

## ✅ 10. **Use Pointer to Struct**

```cpp
struct Point {
    int x, y;
};

int main() {
    Point p = {3, 4};
    Point *ptr = &p;
    std::cout << ptr->x << " " << ptr->y;
}
```

---




