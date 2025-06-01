## **Smart Pointers in C++**

**Smart pointers** are wrappers around raw pointers that automatically manage memory. They are part of the C++ Standard Library (`<memory>` header) and help avoid memory leaks and dangling pointers.

>  Automatically delete memory when it’s no longer needed.
>  No need to call `delete` manually.

---

### **Types of Smart Pointers**

| Smart Pointer | Description                                               |
| ------------- | --------------------------------------------------------- |
| `unique_ptr`  | Owns memory exclusively. No sharing.                      |
| `shared_ptr`  | Multiple smart pointers can share ownership.              |
| `weak_ptr`    | Observes `shared_ptr` without increasing reference count. |

---

### **1. `unique_ptr`**

* Only one `unique_ptr` can own the resource at a time.
* Automatically deletes memory when it goes out of scope.

**Syntax:**

```cpp
#include <iostream>
#include <memory>
using namespace std;

int main() {
    unique_ptr<int> ptr = make_unique<int>(10);
    cout << "Value: " << *ptr << endl;
    return 0;
}
```

---

### **2. `shared_ptr`**

* Multiple `shared_ptr`s can own the same resource.
* Memory is freed when the last `shared_ptr` is destroyed.

**Syntax:**

```cpp
#include <iostream>
#include <memory>
using namespace std;

int main() {
    shared_ptr<int> p1 = make_shared<int>(20);
    shared_ptr<int> p2 = p1; // shared ownership

    cout << "Value from p1: " << *p1 << endl;
    cout << "Value from p2: " << *p2 << endl;
    cout << "Use count: " << p1.use_count() << endl;

    return 0;
}
```

---

### **3. `weak_ptr`**

* Used to break circular references in `shared_ptr`.
* Does **not** increase reference count.

**Syntax:**

```cpp
#include <iostream>
#include <memory>
using namespace std;

int main() {
    shared_ptr<int> sp = make_shared<int>(30);
    weak_ptr<int> wp = sp; // does not affect use_count

    cout << "Use count: " << sp.use_count() << endl;

    if (auto temp = wp.lock()) {
        cout << "Value: " << *temp << endl;
    } else {
        cout << "Pointer expired";
    }

    return 0;
}
```

---

## **Comparison: Raw Pointers vs Smart Pointers**

| Feature             | Raw Pointer (`int*`)     | Smart Pointer (`unique_ptr`, `shared_ptr`) |
| ------------------- | ------------------------ | ------------------------------------------ |
| Memory management   | Manual (`new/delete`)    | Automatic                                  |
| Safety              | Unsafe (can cause leaks) | Safe (RAII-based)                          |
| Ownership control   | No                       | Yes (`unique`, `shared`, `weak`)           |
| Requires `<memory>` | No                       | Yes                                        |

---

## Summary Code Using All Pointer Types

```cpp
#include <iostream>
#include <memory>
using namespace std;

void rawPointerExample() {
    int* ptr = new int(5);
    cout << "Raw pointer: " << *ptr << endl;
    delete ptr;
}

void uniquePtrExample() {
    unique_ptr<int> ptr = make_unique<int>(10);
    cout << "Unique pointer: " << *ptr << endl;
}

void sharedPtrExample() {
    shared_ptr<int> sp1 = make_shared<int>(20);
    shared_ptr<int> sp2 = sp1;
    cout << "Shared pointer: " << *sp1 << ", use count: " << sp1.use_count() << endl;
}

void weakPtrExample() {
    shared_ptr<int> sp = make_shared<int>(30);
    weak_ptr<int> wp = sp;
    if (auto temp = wp.lock()) {
        cout << "Weak pointer locked: " << *temp << endl;
    }
}

int main() {
    rawPointerExample();
    uniquePtrExample();
    sharedPtrExample();
    weakPtrExample();
    return 0;
}
```
---

## Common Smart Pointer Functions

| Function      | Applies to                 | Description                                                              |
| ------------- | -------------------------- | ------------------------------------------------------------------------ |
| `reset()`     | `unique_ptr`, `shared_ptr` | Releases ownership of the current object and optionally takes a new one. |
| `get()`       | All smart pointers         | Returns the raw pointer without releasing ownership.                     |
| `use_count()` | `shared_ptr`               | Returns the number of `shared_ptr` instances managing the same object.   |
| `unique()`    | `shared_ptr`               | Returns `true` if the smart pointer is the only owner.                   |
| `swap()`      | All smart pointers         | Swaps the managed objects of two smart pointers.                         |
| `release()`   | `unique_ptr`               | Releases ownership and returns the raw pointer (must delete manually).   |
| `lock()`      | `weak_ptr`                 | Converts to `shared_ptr` if the managed object still exists.             |
| `move()`      | All (via `std::move`)      | Transfers ownership (especially in `unique_ptr`).                        |

---

## 1. `reset()`

**Purpose:** Deletes the managed object and sets pointer to `nullptr` (or a new object).

**Syntax:**

```cpp
ptr.reset();              // deletes current object
ptr.reset(new int(100));  // deletes old and assigns new
```

**Example:**

```cpp
shared_ptr<int> sp = make_shared<int>(10);
sp.reset();  // now sp is empty
```

---

## 2. `get()`

**Purpose:** Returns the raw pointer, **without** transferring ownership.

**Syntax:**

```cpp
int* raw = ptr.get();
```

**Example:**

```cpp
shared_ptr<int> sp = make_shared<int>(20);
int* raw = sp.get();
cout << "Raw pointer value: " << *raw;
```

---

## 3. `use_count()`

**Purpose:** Returns how many `shared_ptr` instances share ownership.

**Syntax:**

```cpp
sp.use_count();
```

**Example:**

```cpp
shared_ptr<int> sp1 = make_shared<int>(30);
shared_ptr<int> sp2 = sp1;
cout << sp1.use_count();  // Output: 2
```

---

## 4. `unique()`

**Purpose:** Checks if this `shared_ptr` is the sole owner.

**Syntax:**

```cpp
sp.unique();
```

**Example:**

```cpp
shared_ptr<int> sp1 = make_shared<int>(40);
cout << sp1.unique(); // true (1)
shared_ptr<int> sp2 = sp1;
cout << sp1.unique(); // false (0)
```

---

## 5. `swap()`

**Purpose:** Swaps two smart pointers.

**Syntax:**

```cpp
sp1.swap(sp2);
```

**Example:**

```cpp
shared_ptr<int> sp1 = make_shared<int>(10);
shared_ptr<int> sp2 = make_shared<int>(20);
sp1.swap(sp2);  // now sp1 points to 20, sp2 to 10
```

---

## 6. `release()` *(only for `unique_ptr`)*

**Purpose:** Releases ownership and returns raw pointer. You must `delete` it manually.

**Syntax:**

```cpp
int* raw = up.release();
```

**Example:**

```cpp
unique_ptr<int> up = make_unique<int>(60);
int* raw = up.release();  // up is now empty
cout << *raw;
delete raw;               // manual delete required
```

---

## 7. `lock()` *(for `weak_ptr`)*

**Purpose:** Converts a `weak_ptr` into a `shared_ptr` if object still exists.

**Syntax:**

```cpp
if (auto sp = wp.lock()) {
    // use sp
}
```

**Example:**

```cpp
shared_ptr<int> sp = make_shared<int>(70);
weak_ptr<int> wp = sp;
if (auto temp = wp.lock()) {
    cout << *temp;
}
```

---

## 8. `std::move()` with Smart Pointers

**Purpose:** Transfers ownership of `unique_ptr`.

**Syntax:**

```cpp
unique_ptr<int> up1 = make_unique<int>(80);
unique_ptr<int> up2 = std::move(up1); // up1 is now null
```

---

## Summary Table

| Function      | For                        | Description                                     |
| ------------- | -------------------------- | ----------------------------------------------- |
| `reset()`     | `shared_ptr`, `unique_ptr` | Replaces the managed object                     |
| `get()`       | All                        | Returns raw pointer without releasing ownership |
| `use_count()` | `shared_ptr`               | Returns number of owners                        |
| `unique()`    | `shared_ptr`               | Checks if it's the only owner                   |
| `swap()`      | All                        | Swaps pointers                                  |
| `release()`   | `unique_ptr`               | Releases ownership (manual delete required)     |
| `lock()`      | `weak_ptr`                 | Converts to `shared_ptr` if not expired         |
| `move()`      | All                        | Transfers ownership                             |

---

## **License**
This project is licensed under the MIT License.

---

Happy Coding!

