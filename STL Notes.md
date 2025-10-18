### **What is STL in C++?**  
**STL (Standard Template Library)** is a powerful feature of C++ that provides a collection of **generic classes and functions** to handle common data structures and algorithms. It enables efficient and reusable code by providing pre-implemented solutions for complex operations such as searching, sorting, and manipulation of data.

---

### **Key Components of STL**  
STL consists of four main components:  

1. **Containers:**  
2. **Algorithms:**  
3. **Iterators:**  
4. **Functors (Function Objects):**
   
---

### **1. Containers** 
- Used to store and manage collections of data.

STL containers are categorized into 4 types:

#### **A. Sequence Containers**  
Stores elements sequentially (like arrays).  
| Container  | Description           | Example Operations        |
|----------------|---------------------------|--------------------------------|
| `array`         | Static array (fixed size) | `at()`, `size()`, `fill()`     |
| [vector](#vector) | Dynamic array              | `push_back()`, `pop_back()`, `size()` |
| [deque](#deque)     | Double-ended queue         | `push_front()`, `push_back()`, `pop_front()`, `pop_back()` |
| [list](#list)       | Doubly linked list         | `push_front()`, `push_back()`, `pop_front()`, `pop_back()` |
| `forward_list`  | Singly linked list          | `push_front()`, `pop_front()`, `insert_after()` |

---

#### **B. Associative Containers**  
Stores elements in a sorted/unordered fashion using keys.  
| Container     | Description              | Example Operations      |
|---------------|--------------------------|-------------------------|
| [set](#set)         | Unique sorted elements    | `insert()`, `erase()`    |
| [map](#map)         | Key-value pairs (sorted)  | `insert()`, `find()`     |
| [multiset](#multiset)    | Allows duplicate elements | `count()`, `equal_range()` |
| [multimap](#multimap)    | Multiple key-value pairs  | `insert()`, `find()`     |

---

#### **C. Unordered Associative Containers**  
Stores elements with no specific order, offering faster access compared to ordered containers.  
| Container             | Description                 |
|----------------------------|----------------------------------|
| [unordered_set](#unordered_set)            | Unique elements, no specific order |
| [unordered_map](#unordered_map)            | Key-value pairs, no specific order |
| [unordered_multiset](#unordered_multiset)  | Allows duplicate elements, no specific order |
| [unordered_multimap](#unordered_multimap)  | Allows duplicate key-value pairs, no specific order |

---

#### **D. Containers Adapters**  
Stores elements with no specific order, offering faster access compared to ordered containers.  
| **Container**          | **Description**                            |
|------------------------|--------------------------------------------|
| [queue](#queue)                | FIFO (First-In-First-Out) container, elements are processed in the order they are added |
| [priority_queue](#priority_queue)       | Elements are ordered based on priority (default: max-heap) |
| [stack](#stack)                | LIFO (Last-In-First-Out) container, elements are processed in reverse order of addition |

---

### **1. Pair**
The `pair` in C++ STL is a utility that allows storing two heterogeneous values (of possibly different types) in a single unit. It is commonly used to combine two values and pass them together, such as key-value pairs in maps.
 
>Pair एक Class है , जो दो Value Store करती है ये Pair रिलेशन Maintain करने लिए के Use करते है

---

### **Syntax of `pair`**  
```cpp
#include <iostream>
#include <utility>
using namespace std;

// Declaration of a pair
pair<T1, T2> variable_name;
```

- `T1` → Data type of the first element  
- `T2` → Data type of the second element  

---

### **Example of `pair`**  

```cpp
#include <iostream>
#include <utility>
using namespace std;

int main() {
    pair<int, string> p1;  
    p1.first = 10;  
    p1.second = "Brijesh";

    cout << "First: " << p1.first << ", Second: " << p1.second << endl;
    return 0;
}
```

**Output:**  
```
First: 10, Second: Brijesh
```

---

### **Ways to Initialize a `pair`**  

1. **Using the constructor:**  
   ```cpp
   pair<int, string> p1(1, "Apple");
   ```

2. **Using the `make_pair()` function:**  
   ```cpp
   pair<int, double> p2 = make_pair(2, 3.14);
   ```

3. **Using assignment:**  
   ```cpp
   pair<int, char> p3;
   p3 = {3, 'A'};
   ```

---

### **Accessing Elements of a `pair`**  
You can access the elements of a `pair` using the `first` and `second` members.

```cpp
pair<string, double> product = {"Laptop", 75000.50};
cout << "Product: " << product.first << ", Price: " << product.second << endl;
```

**Output:**  
```
Product: Laptop, Price: 75000.5
```

---

### **Modifying Elements of a `pair`**  
```cpp
pair<int, string> person = {101, "Alice"};
person.second = "Bob";  // Changing the second element

cout << person.first << " " << person.second;
```

**Output:**  
```
101 Bob
```

---

### **Comparing Pairs**  
Pairs can be compared lexicographically (first elements first, then second elements if first are equal).

```cpp
pair<int, int> p1 = {2, 50};
pair<int, int> p2 = {2, 30};

if (p1 > p2)
    cout << "p1 is greater";
else
    cout << "p2 is greater";
```

**Output:**  
```
p1 is greater
```

---

### **Advantages of `pair` in STL**  
- Helps in storing related data together.  
- Can be used as a key-value pair for efficient lookup operations.  
- Supports easy comparison and sorting.

---

### **Limitations of `pair`**  
- Only stores two values; for more, use `tuple` or structures.  
- Readability can suffer when used extensively in complex programs.

---


### **2. STL Algorithms (Header: `<algorithm>`)** 
- Provide commonly used operations such as sorting, searching, and manipulating data.

STL provides powerful algorithms for manipulating data in containers.

| Algorithm         | Purpose                                       |
| ----------------- | --------------------------------------------- |
| `sort()`          | Sorts range                                   |
| `reverse()`       | Reverses elements in range                    |
| `count()`         | Counts occurrences of an element              |
| `find()`          | Finds first occurrence of a value             |
| `accumulate()`    | Sums elements (needs `<numeric>`)             |
| `binary_search()` | Checks if value exists in sorted range        |
| `lower_bound()`   | Returns first element ≥ value in sorted range |
| `upper_bound()`   | Returns first element > value in sorted range |
| `for_each()`      | Applies function to each element              |
| `copy()`          | Copies one range to another                   |
| `remove()`        | Removes value logically (use with erase)      |
| `unique()`        | Removes consecutive duplicates                |

---

### **3. STL Iterators**  
- Used to traverse elements in containers.

Iterators are used to traverse through elements in containers.

| Operation        | Description                              |
| ---------------- | ---------------------------------------- |
| `begin()`        | Returns iterator to first element        |
| `end()`          | Returns iterator to past-the-end element |
| `rbegin()`       | Reverse begin                            |
| `rend()`         | Reverse end                              |
| `advance(it, n)` | Moves iterator forward by `n` steps      |
| `next(it)`       | Returns iterator advanced by one         |
| `prev(it)`       | Returns iterator moved back by one       |


---

### **4. STL Functors (Function Objects)**  
- Objects that behave like functions and can be passed as arguments to algorithms.

A **functor** is an object that behaves like a function by overloading the `()` operator.

| Functor                         | Description                                      |
| ------------------------------- | ------------------------------------------------ |
| `greater<>()`                   | Comparison functor for descending order          |
| `less<>()`                      | Comparison functor for ascending order (default) |
| `not_equal_to<>()`              | Checks inequality                                |
| `plus<>()`, `minus<>()`         | Arithmetic operations                            |
| `multiplies<>()`, `divides<>()` | Multiplicative operations                        |
| Custom functor                  | Define with overloaded `operator()`              |

**Example of a Functor:**  
```cpp
#include <iostream>
#include <algorithm>
using namespace std;

class MultiplyBy2 {
public:
    int operator()(int x) const {
        return x * 2;
    }
};

int main() {
    MultiplyBy2 m;
    cout << m(10);  // Output: 20
    return 0;
}
```

---

### **Advantages of Using STL in C++**  
- **Code Reusability:** Saves development time by providing ready-to-use solutions.  
- **Performance Optimization:** Efficient algorithms and data structures are implemented internally.  
- **Type Safety:** Uses templates to ensure type safety.  
- **Consistency:** Common interfaces across different container types.

---

### **Disadvantages of STL**  
- **Overhead:** Generic implementations might introduce memory and runtime overhead.  
- **Complexity:** Debugging STL-based code can be challenging due to abstraction.  
- **Less Control:** Direct memory control is limited compared to low-level implementations.

---
---

###  **STL Operations Table**

| Category      | STL Component    | Common Operations                                          | Description                                    |
| ------------- | ---------------- | ---------------------------------------------------------- | ---------------------------------------------- |
| **Container** | `vector`         | `push_back()`, `pop_back()`, `size()`, `at()`, `clear()`   | Dynamic array; fast access and push/pop at end |
|               | `list`           | `push_front()`, `push_back()`, `pop_front()`, `remove()`   | Doubly linked list                             |
|               | `deque`          | `push_front()`, `push_back()`, `pop_front()`, `pop_back()` | Double-ended queue                             |
|               | `stack`          | `push()`, `pop()`, `top()`, `empty()`                      | LIFO stack (based on deque or vector)          |
|               | `queue`          | `push()`, `pop()`, `front()`, `back()`                     | FIFO queue (based on deque)                    |
|               | `priority_queue` | `push()`, `pop()`, `top()`                                 | Max-heap by default                            |
|               | `set`            | `insert()`, `erase()`, `find()`, `count()`                 | Sorted unique elements (RB-tree)               |
|               | `unordered_set`  | `insert()`, `erase()`, `find()`, `count()`                 | Hash-based, faster access                      |
|               | `map`            | `insert()`, `erase()`, `find()`, `[]`                      | Key-value pairs with sorted keys               |
|               | `unordered_map`  | `insert()`, `erase()`, `find()`, `[]`                      | Hash-based key-value pairs                     |
|               | `multiset`       | `insert()`, `erase()`, `count()`                           | Allows duplicate elements                      |
|               | `multimap`       | `insert()`, `equal_range()`, `find()`                      | Multiple values per key allowed                |

---


###  **5. Utility**

| **Utility**  | **Description**                                         |
| ------------ | ------------------------------------------------------- |
| `pair`       | Stores two heterogeneous objects as a single unit       |
| `make_pair`  | Creates a `pair` object conveniently                    |
| `tuple`      | Fixed-size collection of heterogeneous values           |
| `make_tuple` | Creates a `tuple` object                                |
| `tie`        | Unpacks tuple into individual variables                 |
| `ignore`     | Placeholder to ignore elements when unpacking a tuple   |
| `function`   | General-purpose polymorphic function wrapper            |
| `bind`       | Binds arguments to functions, creating callable objects |
| `ref`        | Wraps a reference to be passed to functions             |
| `cref`       | Wraps a const reference                                 |

---

###  **6. Allocators** 

| **Allocator**                     | **Description**                                                            |
| --------------------------------- | -------------------------------------------------------------------------- |
| `std::allocator`                  | Default allocator that handles memory allocation and deallocation.         |
| `std::pmr::polymorphic_allocator` | Allocator that supports polymorphic memory resource allocation (C++17).    |
| Custom Allocator                  | User-defined allocator for customized memory management and optimizations. |

---
## Vector

A **`vector`** is a **sequence container** that uses **dynamic arrays** internally. It allows **random access**, **fast insertion/removal at the end**, and is **resizable**.

###  Key Features:

* Automatically resizes itself.
* Allows direct access to elements using the `[]` operator or `.at()`.
* Stored in **contiguous memory** (like arrays).
* Belongs to the `<vector>` header in C++.
* The std::vector object itself is stored wherever you declare it (stack or heap).
* But the elements (i.e., the actual data inside the vector) are stored on the heap.

---

## Syntax:

```cpp
#include <vector>
#include <iostream>

std::vector<int> vec; // Declaring a vector of integers
```

You can initialize vectors in various ways:

```cpp
std::vector<int> v1;                       // Empty vector
std::vector<int> v2(5);                    // Vector of size 5 with default values (0)
std::vector<int> v3(5, 10);                // Vector of size 5 with all elements = 10
std::vector<int> v4 = {1, 2, 3, 4};        // Initializer list
```

---

## Common Member Functions of `vector`:

| Function             | Description                                  |
| -------------------- | -------------------------------------------- |
| `push_back(val)`     | Adds element at the end                      |
| `pop_back()`         | Removes last element                         |
| `size()`             | Returns the number of elements               |
| `capacity()`         | Returns current allocated space              |
| `resize(n)`          | Resizes vector to contain `n` elements       |
| `clear()`            | Removes all elements                         |
| `empty()`            | Checks if vector is empty                    |
| `insert(pos, val)`   | Inserts element at specified position        |
| `erase(pos)`         | Removes element from position                |
| `front()` / `back()` | Returns first/last element                   |
| `begin()` / `end()`  | Returns iterator to first/after-last element |

---

## Example:

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> v;

    v.push_back(10);
    v.push_back(20);
    v.push_back(30);

    cout << "Vector contents: ";
    for (int i = 0; i < v.size(); i++) {
        cout << v[i] << " ";
    }

    cout << "\nFirst element: " << v.front();
    cout << "\nLast element: " << v.back();
    cout << "\nSize: " << v.size();

    return 0;
}
```

---

## Difference Between `size()` and `capacity()`

| Term         | Meaning                                                                                |
| ------------ | -------------------------------------------------------------------------------------- |
| `size()`     | The **number of elements** currently in the vector                                     |
| `capacity()` | The **number of elements the vector can hold** before it needs to allocate more memory |


---

##  Vector vs Other STL Containers:

| Feature       | `vector`    | `list`           | `deque`            | `set`           |
| ------------- | ----------- | ---------------- | ------------------ | --------------- |
| Memory        | Contiguous  | Doubly linked    | Double-ended array | Tree-based      |
| Random Access | ✅ Fast      | ❌ Slow           | ✅ Fast             | ❌ Not allowed   |
| Insert/Erase  | End: ✅ Fast | Anywhere: ✅ Fast | Ends: ✅ Fast       | ❌ Only Unique   |
| Duplicate     | ✅ Allowed   | ✅ Allowed        | ✅ Allowed          | ❌ Not Allowed   |
| Sorting       | Manual      | Manual           | Manual             | ✅ Automatically |

---

## When to Use `vector`?

Use `vector` when:

* You need **fast random access**.
* You frequently **add or remove elements at the end**.
* You don’t need frequent insertions/deletions in the middle.

---
###  Pros of `std::vector` :

* Automatically resizes and provides dynamic array functionality.
* Fast random access due to contiguous memory storage.
* Works well with STL algorithms and is easy to use.

###  Cons of `std::vector` :

* Inserting/removing elements (especially in the middle) is slow.
* Reallocations can be costly and may invalidate pointers/iterators.
* Not efficient for frequent insertions/removals at the front.

---

## Deque

A **`deque`** is a dynamic array that allows fast:

* `push_front()` / `pop_front()` (front operations)
* `push_back()` / `pop_back()` (back operations)

It is more flexible than `vector` which only allows fast operations at the back.

###  Header:

```cpp
#include <deque>
```

---

##  Syntax:

```cpp
#include <deque>

std::deque<int> dq;
```

You can initialize like:

```cpp
deque<int> dq1;                  // Empty deque
deque<int> dq2(5);               // Deque of size 5 with default value 0
deque<int> dq3(5, 100);          // Deque of size 5 with value 100
deque<int> dq4 = {1, 2, 3};      // Initializer list
```

---

## 🔩 Common Operations:

| Function             | Description                      |
| -------------------- | -------------------------------- |
| `push_back(val)`     | Insert at the end                |
| `push_front(val)`    | Insert at the front              |
| `pop_back()`         | Remove from the end              |
| `pop_front()`        | Remove from the front            |
| `front()` / `back()` | Access first/last element        |
| `size()`             | Number of elements               |
| `clear()`            | Remove all elements              |
| `empty()`            | Check if deque is empty          |
| `at(index)`          | Access element with bounds check |
| `operator[]`         | Access element (no bounds check) |
| `insert(pos, val)`   | Insert at a given position       |
| `erase(pos)`         | Erase element at position        |

---

##  Example:

```cpp
#include <iostream>
#include <deque>
using namespace std;

int main() {
    deque<int> dq;

    dq.push_back(10);
    dq.push_front(5);
    dq.push_back(20);

    cout << "Deque contents: ";
    for (int x : dq)
        cout << x << " "; // Output: 5 10 20

    dq.pop_front(); // removes 5
    dq.pop_back();  // removes 20

    cout << "\nAfter popping: ";
    for (int x : dq)
        cout << x << " "; // Output: 10

    return 0;
}
```

---

##  `deque` vs Other STL Containers

| Feature                  | `vector`   | `deque`                 | `list`     |
| ------------------------ | ---------- | ----------------------- | ---------- |
| Random access            | ✅ Fast     | ✅ Fast                  | ❌ Slow     |
| push\_back / pop\_back   | ✅ Fast     | ✅ Fast                  | ✅ Fast     |
| push\_front / pop\_front | ❌ Slow     | ✅ Fast                  | ✅ Fast     |
| Insert in middle         | ❌ Slow     | ❌ Slow                  | ✅ Fast     |
| Memory layout            | Contiguous | Chunks (non-contiguous) | Node-based |

---

##  When to Use `deque`?

Use `deque` when:

* You need **fast insertion/removal from both ends**.
* You also want **random access** like `vector`.
* You don't need contiguous memory like `vector`.

Avoid if:

* You need frequent insert/delete in the middle → use `list`.

---

## Map 
A `map` stores elements as **pairs**:

```cpp
key -> value
```

* Each key is **unique**.
* Internally implemented using a **balanced BST** (typically a Red-Black Tree).
* Automatically **sorted by key** in ascending order.
>a **`map`** is an **associative container** in STL that stores key-value pairs in **sorted order** (by key) and allows **fast retrieval** based on the key.

### Header:

```cpp
#include <map>
```

---

## Syntax:

```cpp
std::map<KeyType, ValueType> map_name;
```

### Example:

```cpp
map<int, string> m;
m[1] = "One";
m[2] = "Two";
```

---

## Common Member Functions:

| Function            | Description                              |
| ------------------- | ---------------------------------------- |
| `insert({k, v})`    | Inserts key-value pair                   |
| `m[key] = value`    | Inserts/updates key                      |
| `m.at(key)`         | Access value at key with bounds checking |
| `m.find(key)`       | Returns iterator to key if found         |
| `m.erase(key)`      | Removes element by key                   |
| `m.size()`          | Number of elements                       |
| `m.clear()`         | Removes all elements                     |
| `m.empty()`         | Returns true if map is empty             |
| `m.begin()/m.end()` | Iterators to start/end                   |

---

## Example:

```cpp
#include <iostream>
#include <map>
using namespace std;

int main() {
    map<int, string> m;

    m[101] = "Alice";
    m[102] = "Bob";
    m[100] = "Charlie";

    for (auto &entry : m) {
        cout << entry.first << ": " << entry.second << endl;
    }

    return 0;
}
```

### Output:

```
100: Charlie
101: Alice
102: Bob
```

 Notice the keys are automatically sorted.

---

## `map` vs `unordered_map`

| Feature            | `map`              | `unordered_map`          |
| ------------------ | ------------------ | ------------------------ |
| Internal Structure | Red-Black Tree     | Hash Table               |
| Order              | Sorted by key      | No specific order        |
| Time Complexity    | O(log n)           | O(1) average, O(n) worst |
| Key Type           | Must be comparable | Must be hashable         |

---

## 🚀 Real Use Cases:

* Counting frequency: `map<char, int> freq`
* Index mapping: `map<int, int>`
* Adjacency list for graphs
* Caching or dictionary-based lookups

---

###  Pros:

1. Keeps keys in sorted order automatically.
2. Efficient O(log n) insert, find, and erase operations.
3. Supports ordered iteration and range-based queries.

---

###  Cons:

1. Slower than `unordered_map` for key lookups.
2. Uses more memory due to tree structure.
3. Doesn’t allow duplicate keys (use `multimap` if needed).


##   List

`std::list` is a **doubly linked list** in the Standard Template Library (STL).

* Each element (node) stores:

  * **Data**
  * **Pointer to the next node**
  * **Pointer to the previous node**

Because of this structure:

* **Insertion and deletion** at any position (beginning, middle, or end) are **fast (O(1))**.
* But **random access** (like accessing `list[3]`) is **slow (O(n))**.

---

##  Syntax

```cpp
#include <list>
using namespace std;

list<int> l;           // Empty list of integers
list<string> names;    // Empty list of strings
list<int> l2 = {1, 2, 3, 4};  // Initialize list with values
```

---

##  Common Functions

| Function        | Description                                           |
| --------------- | ----------------------------------------------------- |
| `push_back(x)`  | Insert element at the end                             |
| `push_front(x)` | Insert element at the beginning                       |
| `pop_back()`    | Remove last element                                   |
| `pop_front()`   | Remove first element                                  |
| `insert(it, x)` | Insert `x` before iterator `it`                       |
| `erase(it)`     | Remove element at iterator `it`                       |
| `remove(x)`     | Remove all occurrences of `x`                         |
| `clear()`       | Remove all elements                                   |
| `size()`        | Returns number of elements                            |
| `empty()`       | Checks if list is empty                               |
| `front()`       | Returns first element                                 |
| `back()`        | Returns last element                                  |
| `reverse()`     | Reverses the list                                     |
| `sort()`        | Sorts the list in ascending order                     |
| `unique()`      | Removes consecutive duplicate elements                |
| `merge(l2)`     | Merges another sorted list `l2` into the current list |

---

## Example Program

```cpp
#include <iostream>
#include <list>
using namespace std;

int main() {
    list<int> l = {10, 20, 30};

    l.push_front(5);
    l.push_back(40);

    cout << "List elements: ";
    for (int x : l)
        cout << x << " ";

    cout << "\nFirst element: " << l.front();
    cout << "\nLast element: " << l.back();

    l.pop_front();
    l.pop_back();

    cout << "\nAfter popping front and back: ";
    for (int x : l)
        cout << x << " ";

    l.reverse();
    cout << "\nAfter reverse: ";
    for (int x : l)
        cout << x << " ";

    l.sort();
    cout << "\nAfter sort: ";
    for (int x : l)
        cout << x << " ";
}
```

###  Output:

```
List elements: 5 10 20 30 40 
First element: 5
Last element: 40
After popping front and back: 10 20 30 
After reverse: 30 20 10 
After sort: 10 20 30
```

---

##  Advantages

* Fast insertion/deletion anywhere (`O(1)` with iterator).
* No reallocation (unlike `vector`).

##  Disadvantages

* No random access.
* Extra memory overhead (due to node pointers).
* Traversing is slower compared to `vector`.

---

## When to Use `std::list`

Use `list` when:

* You frequently **insert or delete** elements in the **middle**.
* You **don’t need random access**.

---

# `std::stack` — Last In First Out (LIFO)

A **stack** stores elements such that the **last inserted element is the first one to be removed**.

###  Syntax:

```cpp
#include <stack>
using namespace std;

stack<int> s;         // Empty stack of integers
stack<string> names;  // Stack of strings
```

---

###  Common Functions

| Function  | Description                    |
| --------- | ------------------------------ |
| `push(x)` | Adds element `x` to the top    |
| `pop()`   | Removes top element            |
| `top()`   | Access the top element         |
| `empty()` | Checks if stack is empty       |
| `size()`  | Returns the number of elements |

---

###  Example:

```cpp
#include <iostream>
#include <stack>
using namespace std;

int main() {
    stack<int> s;

    s.push(10);
    s.push(20);
    s.push(30);

    cout << "Top element: " << s.top() << endl; // 30

    s.pop();  // removes 30

    cout << "After pop, top: " << s.top() << endl; // 20
    cout << "Size: " << s.size() << endl;

    while (!s.empty()) {
        cout << s.top() << " ";
        s.pop();
    }
}
```

 **Output:**

```
Top element: 30
After pop, top: 20
Size: 2
20 10 
```

---

### Characteristics

* **Follows LIFO (Last In, First Out)**
* No iteration (can’t traverse elements)
* Used for **expression evaluation**, **backtracking**, **undo operations**, etc.

---

#  `std::queue` — First In First Out (FIFO)

A **queue** stores elements such that the **first inserted element is the first to be removed**.

###  Syntax:

```cpp
#include <queue>
using namespace std;

queue<int> q;          // Empty queue of integers
queue<string> names;   // Queue of strings
```

---

###  Common Functions

| Function  | Description                   |
| --------- | ----------------------------- |
| `push(x)` | Add element to the back       |
| `pop()`   | Remove element from the front |
| `front()` | Access the first element      |
| `back()`  | Access the last element       |
| `empty()` | Check if queue is empty       |
| `size()`  | Returns number of elements    |

---

###  Example:

```cpp
#include <iostream>
#include <queue>
using namespace std;

int main() {
    queue<int> q;

    q.push(10);
    q.push(20);
    q.push(30);

    cout << "Front: " << q.front() << endl; // 10
    cout << "Back: " << q.back() << endl;   // 30

    q.pop(); // Removes 10

    cout << "After pop, front: " << q.front() << endl; // 20
    cout << "Size: " << q.size() << endl;

    while (!q.empty()) {
        cout << q.front() << " ";
        q.pop();
    }
}
```

 **Output:**

```
Front: 10
Back: 30
After pop, front: 20
Size: 2
20 30 
```

---

###  Characteristics

* **Follows FIFO (First In, First Out)**
* No iteration (no direct traversal)
* Useful in **scheduling**, **message queues**, **BFS traversal**, etc.

---

#  Summary Table

| Feature        | `stack`                                | `queue`                    |
| -------------- | -------------------------------------- | -------------------------- |
| Order          | LIFO                                   | FIFO                       |
| Insert element | `push()` (top)                         | `push()` (back)            |
| Remove element | `pop()` (top)                          | `pop()` (front)            |
| Access element | `top()`                                | `front()` & `back()`       |
| Use cases      | Undo, recursion, expression evaluation | BFS, scheduling, buffering |

---



