### **Pointers in C++**

**Pointers** are variables that store the memory address of another variable. They are powerful tools in C++ for direct memory access, dynamic memory allocation, and efficient array and function handling.

---

## **Syntax of a Pointer**

```cpp
data_type* pointer_name;
```

> `*` indicates that the variable is a pointer to the specified `data_type`.

---

## **Basic Example**

```cpp
#include <iostream>
using namespace std;

int main() {
    int x = 10;
    int* ptr = &x;  // store address of x in ptr

    cout << "Value of x: " << x << endl;
    cout << "Address of x: " << &x << endl;
    cout << "Pointer ptr stores: " << ptr << endl;
    cout << "Value pointed by ptr: " << *ptr << endl;

    return 0;
}
```

---

## **Key Pointer Concepts**

### 1. **Address-of Operator `&`**

* Used to get the memory address of a variable.

```cpp
int x = 5;
int* ptr = &x;
```

### 2. **Dereference Operator `*`**

* Used to access the value at the memory address.

```cpp
cout << *ptr; // prints value of x
```

---

## **Pointer Arithmetic**

```cpp
int arr[3] = {10, 20, 30};
int* ptr = arr;

cout << *ptr << endl;     // 10
cout << *(ptr + 1) << endl; // 20
```

> In arrays, `ptr + 1` moves to the next element (next memory location).

---

## **Pointers and Functions**

**Pass-by-Reference using pointers:**

```cpp
void update(int* p) {
    *p = *p + 10;
}

int main() {
    int x = 5;
    update(&x);
    cout << "Updated x: " << x;  // Output: 15
    return 0;
}
```

---

## **Dynamic Memory Allocation**

Using `new` and `delete`:

```cpp
int* ptr = new int;    // dynamically allocate memory
*ptr = 50;
cout << *ptr << endl;
delete ptr;            // free the memory
```

For arrays:

```cpp
int* arr = new int[5]; // dynamic array
arr[0] = 10;
delete[] arr;          // free array memory
```

---

## **Null Pointer**

```cpp
int* ptr = nullptr;
```

> `nullptr` ensures the pointer is not pointing to any memory address.

---

## **Void Pointer**

Can point to any data type:

```cpp
void* ptr;
int x = 5;
ptr = &x;
// To access, need to typecast
cout << *(int*)ptr;
```

---

## Summary Table

| Pointer Concept       | Example             |
| --------------------- | ------------------- |
| Declaration           | `int* p;`           |
| Initialization        | `p = &x;`           |
| Dereferencing         | `*p`                |
| Pointer to Array      | `int* p = arr;`     |
| Function with Pointer | `void func(int* p)` |
| Dynamic Memory        | `int* p = new int;` |
| Free Memory           | `delete p;`         |
| Null Pointer          | `int* p = nullptr;` |

---

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

## **License**
This project is licensed under the MIT License.

---

Happy Coding!

