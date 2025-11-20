##Q1. Write all operation in vector and its time complexity (Tech mahindra) vector<int> 
v={1,2,3,4}; 

##  **Vector in C++ — Deep Explanation**

A `vector` in C++ is a **dynamic array** provided by STL. Unlike raw arrays, it can **automatically resize** when needed.

Internally, vector maintains:

* `size` → number of elements stored
* `capacity` → allocated memory (can store elements without reallocation)

Growth rule: **When capacity is full, vector grows by approx. 2x (implementation dependent).**
This involves:

* Allocating new memory
* Copying/moving existing elements → **costly operation**

---

###  `vector<int> v = {1,2,3,4};`

Initial:

| Operation | Result                              |
| --------- | ----------------------------------- |
| size      | 4                                   |
| capacity  | implementation-defined (usually ≥4) |

---

---

##  Operations on Vector & Time Complexity

| Operation               | Syntax Example    | Time Complexity | Notes                         |
| ----------------------- | ----------------- | --------------- | ----------------------------- |
| **Access (read/write)** | `v[i]`, `v.at(i)` | **O(1)**        | `at()` checks bounds → slower |
| **Front element**       | `v.front()`       | **O(1)**        |                               |
| **Last element**        | `v.back()`        | **O(1)**        |                               |
| **Check size**          | `v.size()`        | **O(1)**        |                               |
| **Check capacity**      | `v.capacity()`    | **O(1)**        |                               |
| **Check empty**         | `v.empty()`       | **O(1)**        |                               |

---

###  Modification Operations

| Operation                       | Syntax                            | Time Complexity                            | Reason                                      |
| ------------------------------- | --------------------------------- | ------------------------------------------ | ------------------------------------------- |
| **Push back**                   | `v.push_back(5)`                  | **Amortized O(1)** <br>Worst case **O(n)** | Reallocation and copying when capacity full |
| **Pop back**                    | `v.pop_back()`                    | **O(1)**                                   | Just reduces size                           |
| **Insert at beginning**         | `v.insert(v.begin(),100)`         | **O(n)**                                   | Shifts all elements                         |
| **Insert at middle**            | `v.insert(v.begin()+2,10)`        | **O(n)**                                   | Shifts elements after position              |
| **Erase last element**          | `v.erase(v.end()-1)`              | **O(1)**                                   |                                             |
| **Erase from beginning/middle** | `v.erase(v.begin()+1)`            | **O(n)**                                   | Shifts elements left                        |
| **Erase range**                 | `v.erase(v.begin(), v.begin()+3)` | **O(n)**                                   | Move remaining elements                     |
| **Resize**                      | `v.resize(10)`                    | **O(n)**                                   | New memory may be allocated                 |
| **Assign**                      | `v.assign(5,10)`                  | **O(n)**                                   | Replace contents                            |

---

###  Memory Operations

| Operation           | Syntax              | Time Complexity                   | Use                                 |
| ------------------- | ------------------- | --------------------------------- | ----------------------------------- |
| **Reserve memory**  | `v.reserve(100)`    | **O(n)** (if reallocation occurs) | Prevents multiple memory expansions |
| **Shrink capacity** | `v.shrink_to_fit()` | **O(n)**                          | Requests freeing unused capacity    |
| **Clear**           | `v.clear()`         | **O(n)**                          | Sets size to 0 (capacity unchanged) |
| **Swap**            | `v.swap(v2)`        | **O(1)**                          | Just swaps internal pointers        |

---

---

##  Example Code with Above Vector

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> v = {1, 2, 3, 4};

    // Access
    cout << v[2] << endl;      // O(1)
    cout << v.at(1) << endl;   // O(1) with bound check
    cout << v.front() << endl; // O(1)
    cout << v.back() << endl;  // O(1)

    // Insert operations
    v.push_back(5);            // Amortized O(1)
    v.insert(v.begin(), 10);   // O(n)
    v.erase(v.begin()+2);      // O(n)

    // Memory operations
    v.reserve(100);            // O(n) if reallocation
    v.shrink_to_fit();         // O(n)

    // Loop
    for(int x : v) cout << x << " ";
}
```

---

## Important Interview Notes

* Vector stores elements **contiguously in memory** like arrays → supports fast random access.
* **Reallocation happens when size exceeds capacity** → expensive.
* `push_back()` is **amortized constant time**, not always constant.
* `insert()` and `erase()` in middle are **O(n)** because shifting occurs.

---
##Q2. What is C++ (CPP)? (Seimens) 
---
##Q3. Explain the major differences between C++98,3.0, C++11, C++14, C++17, and C++20. Which features have you used most, which version have u used? (FlexTrade) 

## **Evolution of Modern C++ Standards**

C++ has evolved significantly from **C++98 → C++20**, mainly focusing on:

* **Performance**
* **Code readability**
* **Compile-time programming**
* **Safety**
* **Concurrency support**

---

# **C++98 / C++03 (Baseline C++)**

> C++03 is largely a bug-fix update to C++98. Both are considered the same in interviews.

###  Key Features

| Category             | Examples                                        |
| -------------------- | ----------------------------------------------- |
| Basic OOP features   | Classes, inheritance, abstraction, polymorphism |
| Templates            | Class & function templates                      |
| STL                  | vector, list, map, set, queue, stack            |
| Exception Handling   | try-catch-throw                                 |
| Operator overloading | Custom operators                                |
| Memory Management    | `new`, `delete`, RAII                           |

###  Limitations

* No move semantics → **expensive copies**
* No automatic type deduction (`auto`)
* No lambda expressions
* Weak concurrency support

---

#  **C++11 – The Biggest Change ("Modern C++")**

> Major shift improving performance and usability.

###  Key Features

| Feature                                | Example                                | Benefit                           |
| -------------------------------------- | -------------------------------------- | --------------------------------- |
| **Move semantics / Rvalue references** | `std::move()`                          | Avoids expensive deep copies      |
| **auto keyword**                       | `auto x = 10;`                         | Type inference                    |
| **Smart pointers**                     | `shared_ptr`, `unique_ptr`, `weak_ptr` | Memory safety (no raw new/delete) |
| **Lambda expressions**                 | `[&](int x){ return x+1; };`           | Functional-style compact code     |
| **Range-based for loop**               | `for(auto x:v)`                        | Cleaner iteration                 |
| **nullptr**                            | replaces `NULL`                        | Type-safe null                    |
| **std::thread**                        | Native threading                       | Improved concurrency              |
| **unordered_map**                      | Hash-based containers                  | O(1) avg lookup                   |

---

# **C++14 – Incremental Improvements**

> Mostly refinements to C++11.

### Key Features:

* **Generic lambdas**

```cpp
auto f = [](auto x, auto y){ return x + y; };
```

* **Return type deduction**

```cpp
auto func(){ return 10; }
```

* **make_unique()**

```cpp
auto ptr = std::make_unique<int>(10);
```

➡ Makes C++11 easier and safer.

---

# **C++17 – Standard Becoming Production-Friendly**

### Major Features

| Category             | Features                                                                  |
| -------------------- | ------------------------------------------------------------------------- |
| Memory + Performance | `std::optional`, `std::variant`, `std::any`                               |
| Algorithms           | Parallel STL algorithms (`std::reduce`, `std::sort(std::execution::par)`) |
| Language constructs  | `if constexpr`, structured bindings, fold expressions                     |
| File System API      | `<filesystem>`                                                            |

#### Example:

```cpp
if constexpr(std::is_integral_v<T>) {
    // Compile-time branching
}
```

---

#  **C++20 – Compile-Time Power + Concepts**

> Big step toward high-level, safe and performant programming.

### Key Features

| Area            | Features                                          |
| --------------- | ------------------------------------------------- |
| Template Safety | **Concepts** (constraint-based templates)         |
| Coroutines      | `co_yield`, `co_return`, asynchronous programming |
| Ranges          | `std::ranges::filter`, `std::views`               |
| Modules         | Replaces headers (faster compile, cleaner code)   |
| Updated Lambdas | constexpr lambdas                                 |

#### Example (Concepts)

```cpp
template<typename T>
requires std::integral<T>
T add(T a, T b) { return a + b; }
```

---

##Q4. WAP in CPP for Define integer array {1,2,3,4,5}, Calculate the size of the array, Print each element on a newline (Planystech.com)
---
```cpp
#include <iostream>   
using namespace std;

/*
Define integer array {1,2,3,4,5}
Calculate the size of the array
Print each element on a newline
*/

int main() {
    int arr[] = {1, 2, 3, 4, 5};
    
    // Calculate number of elements
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Array size: " << n << endl;

    // Print elements
    for (int i = 0; i < n; ++i) {
        cout << arr[i] << endl;
    }

    return 0;
}
```
---
##Q5. What is a list, vector? What are the pros and cons of using std::list and std::vector in C++?(Apexon)
---
##Q6. How to insert, access, delete an element at 1st and 3rd position in Array vs Linked List, and explain the time complexity (Planystech.com) 

## 1) **ARRAY**

Arrays store elements **contiguously**, so accessing is fast (index-based), but inserting or deleting requires **shifting elements**.

---

### ** A) INSERT**

#### Example: Insert at **1st position (index 0)**

```cpp
int arr[10] = {1,2,3,4,5};
int n = 5;
int value = 10;

// Shift elements
for(int i = n; i > 0; i--)
    arr[i] = arr[i-1];

arr[0] = value;
n++;
```

#### Insert at **3rd position (index 2)**

```cpp
int pos = 2;
int value2 = 99;

for(int i = n; i > pos; i--)
    arr[i] = arr[i-1];

arr[pos] = value2;
n++;
```

**Time Complexity:**
`O(n)` (because shifting is required)

---

### ** B) ACCESS**

```cpp
cout << arr[0]; // 1st position
cout << arr[2]; // 3rd position
```

**Time Complexity:**
 `O(1)` (direct indexing)

---

### ** C) DELETE**

#### Delete **1st element**

```cpp
for(int i = 0; i < n-1; i++)
    arr[i] = arr[i+1];
n--;
```

#### Delete **3rd element (index 2)**

```cpp
int posDelete = 2;
for(int i = posDelete; i < n-1; i++)
    arr[i] = arr[i+1];
n--;
```

 **Time Complexity:**
 `O(n)` (because shifting left)

---

---

#  **2) LINKED LIST**

A singly linked list stores elements **non-contiguously** using nodes and pointers, so no shifting is needed — only pointer updates.

---

### **Node Structure**

```cpp
struct Node {
    int data;
    Node* next;
};
```

---

### ** A) INSERT**

#### Insert at **1st position (Head)** → **O(1)**

```cpp
Node* newNode = new Node{10, head};
head = newNode;
```

#### Insert at **3rd position**

```cpp
Node* temp = head;
for(int i = 0; i < 1; i++)   // reach node at position 2 - 1
    temp = temp->next;

Node* newNode = new Node{99, temp->next};
temp->next = newNode;
```

 Complexity:

* Traversal: `O(n)`
* Insert itself: `O(1)`
  ➡️ Total: **O(n)**

---

### ** B) ACCESS**

```cpp
cout << head->data;  // 1st

Node* temp2 = head;
for(int i = 0; i < 2; i++)
    temp2 = temp2->next;

cout << temp2->data; // 3rd
```

 **Time Complexity:**
 **O(n)** (because no random access)

---

### ** C) DELETE**

#### Delete **1st node**

```cpp
Node* temp = head;
head = head->next;
delete temp;
```

 Complexity: **O(1)**

---

#### Delete **3rd node**

```cpp
Node* temp = head;
for(int i = 0; i < 1; i++)
    temp = temp->next;

Node* toDelete = temp->next;
temp->next = toDelete->next;
delete toDelete;
```

 Complexity: **O(n)**


---

## **Comparison Table**

| Operation  | Position   | Array    | Linked List |
| ---------- | ---------- | -------- | ----------- |
| **Access** | 1st or 3rd | **O(1)** | **O(n)**    |
| **Insert** | 1st        | **O(n)** | **O(1)**    |
| **Insert** | 3rd        | **O(n)** | **O(n)**    |
| **Delete** | 1st        | **O(n)** | **O(1)**    |
| **Delete** | 3rd        | **O(n)** | **O(n)**    |

---
## Q.8 Array vs Map, Vector vs Queue, Vector vs Array, Vector vs List, Set vs HashMap (HCL, gentrack, Intelizign, FlexTrade, Apexon, Jhon dhere, L&T (Larsen & Toubro) )

---

## ** Array vs Map**

| Feature  | Array                                       | Map (`std::map` or `std::unordered_map`)              |
| -------- | ------------------------------------------- | ----------------------------------------------------- |
| Storage  | Sequential collection of same type elements | Stores key–value pairs                                |
| Access   | `O(1)` using index                          | `map`: `O(log n)` <br>`unordered_map`: `O(1)` average |
| Ordering | Maintains index order                       | `map` sorted by key, `unordered_map` not sorted       |
| Search   | `O(n)` (linear search)                      | `O(log n)` or `O(1)`                                  |
| Memory   | Contiguous                                  | Not contiguous (nodes or buckets)                     |
| Use case | Fixed-size collections, numeric access      | Fast lookup by key                                    |

**Example:**

```cpp
int arr[3] = {10, 20, 30};
unordered_map<int, string> map1 = {{1,"A"}, {2,"B"}};
```

---

## ** Vector vs Queue**

| Feature             | Vector (`std::vector`)                   | Queue (`std::queue`)                             |
| ------------------- | ---------------------------------------- | ------------------------------------------------ |
| Access              | Random access: `O(1)`                    | No random access                                 |
| Insert/Remove       | End: `O(1)` amortized <br>Middle: `O(n)` | Push at back, pop from front: **O(1)**           |
| Data Structure Type | Dynamic array                            | FIFO                                             |
| Use Case            | General storage, iteration               | Processing in order (printing tasks, scheduling) |

**Example:**

```cpp
vector<int> v = {1,2,3};
queue<int> q;
q.push(10); q.push(20);
```

---

## ** Vector vs Array**

| Feature       | Vector                                   | Array             |
| ------------- | ---------------------------------------- | ----------------- |
| Size          | Dynamic (grows as needed)                | Fixed size        |
| Memory        | Heap allocated                           | Stack or static   |
| Access        | `O(1)`                                   | `O(1)`            |
| Insert/Delete | Middle: `O(n)`                           | Middle: `O(n)`    |
| Convenience   | Built-in functions (`push_back`, `size`) | Manual management |

Use Case:

* **Array:** small fixed collections.
* **Vector:** dynamic runtime size.

**Example:**

```cpp
int arr[5];
vector<int> v = {1,2,3};
```

---

## ** Vector vs List (`std::list`)**

| Feature            | Vector                            | List                              |
| ------------------ | --------------------------------- | --------------------------------- |
| Memory             | Contiguous                        | Non-contiguous nodes              |
| Access             | Random: **O(1)**                  | Sequential: **O(n)**              |
| Insertion/Deletion | Middle: **O(n)** (shifting)       | Middle: **O(1)** (pointer update) |
| Cache friendly     | Yes                               | No                                |
| Use Case           | Frequent reading/index operations | Frequent insertions/deletions     |

**Example:**

```cpp
vector<int> v = {1,2,3};
list<int> l = {1,2,3};
```

---

## ** Set vs HashMap**

> Comparing `std::set` with `std::unordered_map`.

| Feature            | Set (`std::set`)             | HashMap (`std::unordered_map`)  |
| ------------------ | ---------------------------- | ------------------------------- |
| Storage            | Stores unique elements       | Stores key-value pairs          |
| Ordering           | Sorted (Red-Black tree)      | Not sorted (hash table)         |
| Duplicate allowed? | ❌ No duplicates              | Keys must be unique             |
| Complexity         | Insert/search: **O(log n)**  | Insert/search: **O(1)** average |
| Use case           | Maintain sorted unique items | Fast lookup by key              |

**Example:**

```cpp
set<int> s = {1,2,3};
unordered_map<int,string> h = {{1,"A"}};
```

---

---

###  Summary Cheat Sheet (Interview-Quick View)

| Comparison          | Best When                        | Avoid When                       |
| ------------------- | -------------------------------- | -------------------------------- |
| **Array vs Map**    | Index-based access needed        | You need key-based lookup        |
| **Vector vs Queue** | Need random access and iteration | Need strict FIFO processing      |
| **Vector vs Array** | Size grows dynamically           | Memory must be fixed/small       |
| **Vector vs List**  | Mostly reading and random access | Frequent insert/delete in middle |
| **Set vs HashMap**  | Need ordered unique elements     | Need fastest key lookup          |

---

##Q9. size() vs capacity() in std::vector, How memory allocation in vector (BMW, Sutherland)

---

#  `size()` vs `capacity()` in `std::vector`

| Function         | Meaning                                                           | Changes When                              | Complexity |
| ---------------- | ----------------------------------------------------------------- | ----------------------------------------- | ---------- |
| **`size()`**     | Number of elements currently stored in the vector                 | When you add/remove elements              | **O(1)**   |
| **`capacity()`** | Amount of memory allocated (available space) without reallocation | Increases only when size exceeds capacity | **O(1)**   |

---

### Example:

```cpp
std::vector<int> v;
v.push_back(10); // size = 1, capacity = often 1 or 2 depending on implementation
v.push_back(20); // size = 2, capacity may grow (2 or 4)
```

Output example:

```
size = 2
capacity = 4
```

 **Key Point:**

* `size()` ≤ `capacity()` always.
* `capacity()` grows **in chunks**, not incrementally by 1.

---

---

#  How Memory Allocation Works in `std::vector`

Vectors use **dynamic array allocation** under the hood.

###  Steps when pushing elements:

1. If `size < capacity` → new element stored directly (no cost, **O(1)**).
2. If `size == capacity` → vector **reallocates** memory:

   * Allocate **new larger block**
   * Copy/move all existing elements to new memory
   * Destroy old memory

---

###  Growth Pattern

Most implementations grow capacity using **exponential growth**:

```
new_capacity ≈ old_capacity * 2
```

**Growth factor may vary** (1.5x–2x depending on compiler), but doubling is common.

---

### Example Allocation Flow:

| Operation      | size | capacity         |
| -------------- | ---- | ---------------- |
| Start          | 0    | 0                |
| `push_back(1)` | 1    | 1                |
| `push_back(2)` | 2    | 2                |
| `push_back(3)` | 3    | 4                |
| `push_back(4)` | 4    | 4                |
| `push_back(5)` | 5    | 8  ← Reallocated |

---

###  Why vector grows exponentially?

* To avoid frequent allocations (expensive)
* To maintain **amortized constant time `O(1)` push_back()`**

---

---

#  Capacity Control Functions

| Function          | Purpose                                                |
| ----------------- | ------------------------------------------------------ |
| `reserve(n)`      | Pre-allocate memory to avoid multiple reallocations    |
| `shrink_to_fit()` | Reduce unused capacity (not guaranteed)                |
| `resize(n)`       | Changes size (adds default values or removes elements) |

---

### Example:

```cpp
std::vector<int> v;
v.reserve(100);   // avoids multiple reallocations
```

Best practice when you **know size in advance** (e.g., reading file, buffer).
---

#  Common Interview Follow-Up Questions & Short Answers

### **Q: Does `erase()` reduce capacity?**

❌ No. It reduces only `size()`.

### **Q: Does `clear()` reduce capacity?**

❌ No. `clear()` removes elements but keeps memory.

### **Q: When does reallocation NOT happen?**

If inserting element and `capacity > size`, no reallocation.

### **Q: Why can iterators become invalid in vector?**

Because reallocation moves the entire memory block → old addresses become invalid.

---
## Q10. Binary Search vs Linear Search (Planystech.com) 
## Q11. polymorphism ? , Compile and Runtime polymorphism or Function Overloading and Method Overriding — Write Programs (XYZ Company, Akkodis, Johndhere, nCircle, Tietoevry)
---
## Q12. Dynamic Memory Allocation — Explain with Example in C and C++ (XYZ Company, LNT)  
Below is a **clean interview-ready answer** for **Dynamic Memory Allocation in C vs C++**, suitable for **L&T, XYZ Company, John Deere, TCS, etc.**

---

# ✅ **Q9. Dynamic Memory Allocation — Explanation with Examples (C & C++)**

Dynamic memory allocation means allocating memory **at runtime**, instead of compile time.
This is useful when:

* Size is not known in advance
* Memory needs to grow or shrink
* Data structures like Linked List, Trees, Graphs, Queue, Stack are required

---

---

## 🔹 **Dynamic Memory Allocation in C**

In C, dynamic memory is allocated using:

| Function    | Purpose                                   |
| ----------- | ----------------------------------------- |
| `malloc()`  | Allocates raw memory (uninitialized)      |
| `calloc()`  | Allocates memory and initializes with `0` |
| `realloc()` | Resizes previously allocated memory       |
| `free()`    | Releases memory                           |

🔸 Memory is allocated from the **heap**.

### ✔ Example in C:

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int n = 5;

    // Allocate memory for 5 integers
    int* arr = (int*)malloc(n * sizeof(int)); 

    if(arr == NULL) {
        printf("Memory allocation failed");
        return 1;
    }

    // Assign values
    for(int i = 0; i < n; i++)
        arr[i] = i + 1;

    // Print values
    for(int i = 0; i < n; i++)
        printf("%d ", arr[i]);

    // Free allocated memory
    free(arr);

    return 0;
}
```

### 🔎 Key Points:

* `malloc()` returns `void*`, so explicit typecast is common.
* Memory must be freed using `free()` to avoid **memory leaks**.
* No automatic cleanup.

---

---

## 🔹 **Dynamic Memory Allocation in C++**

In C++, dynamic memory is allocated using:

| Operator   | Purpose                        |
| ---------- | ------------------------------ |
| `new`      | Allocates memory (initialized) |
| `new[]`    | Allocates memory for array     |
| `delete`   | Frees single allocated object  |
| `delete[]` | Frees array memory             |

C++ encourages **RAII** and **smart pointers** to avoid manual memory handling.

---

### ✔ Example in C++ (Using `new` / `delete`)

```cpp
#include <iostream>
using namespace std;

int main() {
    int n = 5;

    // Allocate array dynamically
    int* arr = new int[n];

    for(int i = 0; i < n; i++)
        arr[i] = i + 10;

    for(int i = 0; i < n; i++)
        cout << arr[i] << " ";

    // Deallocate memory
    delete[] arr;

    return 0;
}
```

---

### Modern C++ Example (Smart Pointer — Best Practice)

```cpp
#include <iostream>
#include <memory>
using namespace std;

int main() {
    int n = 5;

    unique_ptr<int[]> arr(new int[n]);

    for(int i = 0; i < n; i++)
        arr[i] = i * 2;

    for(int i = 0; i < n; i++)
        cout << arr[i] << " ";

    return 0;
}
```

 No need for `delete[]` — memory auto-released.

---

---

##  Key Differences: C vs C++ Dynamic Allocation

| Feature         | C                                     | C++                                                  |
| --------------- | ------------------------------------- | ---------------------------------------------------- |
| Keyword         | `malloc`, `calloc`, `realloc`, `free` | `new`, `new[]`, `delete`, `delete[]`                 |
| Initialization  | ❌ Not initialized (`malloc`)          | ✔ Value initialization                               |
| Type Safety     | ❌ No type checking                    | ✔ Strong type checking                               |
| Memory Cleanup  | Manual `free()`                       | Manual or automatic (`smart pointer`)                |
| Modern Approach | Not recommended for complex apps      | Preferred: `unique_ptr`, `shared_ptr`, `make_unique` |

---

## Q13. Describe static and const variables in C++ (63 Moons, Intelizen) 
## Q14. What are storage classes in C++ and their types? (63 Moons) 
## Q15. What is constructor?,What is a copy constructor? Why define it manually in C++? , What are the cpp scenario when copy constructor is called ?, What happen when we don't use & in copy constructor? (63 Moons, Tech Mahindra) 

---

## ** Why do we define a Copy Constructor manually?**

C++ provides a **default copy constructor**, which performs **shallow copy** (bit-wise copy).

But we define a custom copy constructor when:

| Reason            | Explanation                                                      |
| ----------------- | ---------------------------------------------------------------- |
| Deep Copy Needed  | Class contains raw pointers or dynamic memory (`new`)            |
| Avoid Double Free | Prevent two objects from freeing same memory                     |
| Custom logic      | Logging, duplicate resource handle, mutex, file descriptor, etc. |

---

### ✔ Example Showing Why Manual Copy Constructor is Needed

```cpp
class Demo {
public:
    int *ptr;

    Demo(int val) {
        ptr = new int(val);
    }

    // Custom Copy Constructor → Deep Copy
    Demo(const Demo &d) {
        ptr = new int(*d.ptr);
    }
};
```

If we don’t define it, **both objects share same pointer** → leads to **double delete crash**.

---

---

## ** When is Copy Constructor Called in C++?**

| Case                                          | Example                                |
| --------------------------------------------- | -------------------------------------- |
| Copy initialization                           | `Demo d2 = d1;`                        |
| Passing object **by value** to a function     | `func(d1);`                            |
| Returning object **by value** from a function | `return d1;` (may be optimized by RVO) |
| Explicit call                                 | `Demo d3(d1);`                         |

---

### ✔ Example Code:

```cpp
void test(Demo d) {} // Pass by value → copy constructor

Demo create() {
    Demo temp(20);
    return temp; // copy/move depending on optimization
}
```

---

---

## ** What happens if we do NOT use `&` in the copy constructor?**

If you write:

```cpp
Demo(Demo d); // ❌ WRONG
```

Then:

* Argument `d` must be copied **by value**
* To copy it, the compiler needs a **copy constructor**
* But the copy constructor **requires itself again**
* Leads to **infinite recursion → compiler error**

 Result: **Compilation fails.**

So correct signature is:

```cpp
Demo(const Demo &d);  // ✔ MUST take object by reference.
```

`const` is recommended to allow copying temporary and const objects.

---
## Q15. What is call by value and call by reference? (63 Moons, Tech Mahindra) , Pass by Value vs Pass by Reference(IQuest, Intelizign)

##  What is **Call / Pass by Value**?

In **call by value**, a **copy of the actual variable** is passed to the function.

* The function works on its own **local copy**
* Changes **do not affect** the original variable

✔ Safe
✔ Memory independent
❌ No modification possible to original data

---

### ✔ Example (Call by Value)

```cpp
#include <iostream>
using namespace std;

void change(int x) {
    x = 100;
}

int main() {
    int a = 10;
    change(a);
    cout << "Value of a: " << a << endl;  // Output: 10
}
```

📌 Output:

```
Value of a: 10
```

 `a` remains unchanged because the function modifies a **copy**, not the actual variable.

---

---

##  What is **Call / Pass by Reference**?

In **call by reference**, the function receives the **reference (alias)** of the actual variable.

* No copy is created
* Function modifies the original data directly

✔ Efficient
✔ Allows modifying original data
❌ Must be used carefully to avoid unwanted changes

---

### ✔ Example (Call by Reference using Reference Variable)

```cpp
#include <iostream>
using namespace std;

void change(int &x) {  // Reference parameter
    x = 100;
}

int main() {
    int a = 10;
    change(a);
    cout << "Value of a: " << a << endl;  // Output: 100
}
```

📌 Output:

```
Value of a: 100
```

 Original value is updated because function works on **actual variable**.

---

---

##  Pass by Reference using Pointer

```cpp
void change(int *x) {
    *x = 200;
}

int main() {
    int a = 20;
    change(&a);
    cout << a;  // Output: 200
}
```

---

---

##  Difference Table

| Feature                     | Call by Value                   | Call by Reference                    |
| --------------------------- | ------------------------------- | ------------------------------------ |
| Parameter Passed            | Copy of variable                | Actual variable address/reference    |
| Effect on Original Variable | ❌ No                            | ✔ Yes                                |
| Memory Usage                | Higher (copy created)           | Lower (same memory used)             |
| Safety                      | Higher (safe from modification) | Lower (can accidentally modify data) |
| Best Used When              | Only reading data               | Modifying original data              |

---


> “In Modern C++, **pass by const reference (`const &`)** is preferred when passing large objects to avoid copying while preventing modification.”

Example:

```cpp
void print(const string& s) {
    cout << s;
}
```

---




