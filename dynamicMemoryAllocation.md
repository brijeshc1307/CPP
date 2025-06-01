### **Dynamic Memory Allocation in C++**

**Dynamic memory allocation** allows you to allocate memory **at runtime** (not at compile time), using **pointers**.
This is useful when:

* You don't know the required memory size in advance.
* You want to allocate memory during program execution.

---

## ✅ Operators Used

| Operator   | Purpose                   | Syntax                   |
| ---------- | ------------------------- | ------------------------ |
| `new`      | Allocates memory          | `int* p = new int;`      |
| `new[]`    | Allocates array of memory | `int* arr = new int[5];` |
| `delete`   | Deallocates single object | `delete p;`              |
| `delete[]` | Deallocates array         | `delete[] arr;`          |

---

## 🔶 Example 1: Allocate Single Variable

```cpp
#include <iostream>
using namespace std;

int main() {
    int* p = new int;     // allocate memory for 1 int
    *p = 42;              // assign value
    cout << *p << endl;   // Output: 42

    delete p;             // free memory
    return 0;
}
```

---

## 🔶 Example 2: Allocate Array

```cpp
#include <iostream>
using namespace std;

int main() {
    int* arr = new int[3];   // allocate memory for array of 3 ints

    for (int i = 0; i < 3; ++i)
        arr[i] = i * 10;

    for (int i = 0; i < 3; ++i)
        cout << arr[i] << " ";  // Output: 0 10 20

    delete[] arr;  // free memory
    return 0;
}
```

---

## 🔷 Important Points

* Memory allocated with `new`/`new[]` **stays until** you explicitly `delete`/`delete[]` it.
* Not deallocating memory causes **memory leaks**.
* Always use `delete`/`delete[]` after `new`/`new[]`.

---

## 🔷 Dynamic Memory for Custom Class

```cpp
class Student {
public:
    Student() {
        cout << "Constructor called\n";
    }
    ~Student() {
        cout << "Destructor called\n";
    }
};

int main() {
    Student* s = new Student();  // Constructor called
    delete s;                    // Destructor called

    Student* arr = new Student[2];  // Constructor called 2x
    delete[] arr;                   // Destructor called 2x
    return 0;
}
```

---

## 🔚 Summary

| Task              | Use                     |
| ----------------- | ----------------------- |
| Allocate 1 object | `ptr = new Type;`       |
| Allocate array    | `ptr = new Type[size];` |
| Free 1 object     | `delete ptr;`           |
| Free array        | `delete[] ptr;`         |

---

### 🔷 `delete` vs `delete[]` in C++

Both `delete` and `delete[]` are used to **deallocate memory** in C++ that was previously allocated using `new` or `new[]`.
But they are **not interchangeable**.

---

## ✅ 1. `delete`

* Used to **free memory** allocated for **a single object**.
* Matches with `new`.

### 🔹 Example:

```cpp
int* ptr = new int;   // allocate memory for 1 int
*ptr = 10;

delete ptr;           // correct
```

---

## ✅ 2. `delete[]`

* Used to **free memory** allocated for **an array of objects**.
* Matches with `new[]`.

### 🔹 Example:

```cpp
int* arr = new int[5];   // allocate memory for array of 5 ints

delete[] arr;            // correct
```

---

## ❌ What if you mix them up?

### 🔹 Using `delete` on an array:

```cpp
int* arr = new int[5];
delete arr;   // ❌ undefined behavior (may cause memory leak or crash)
```

### 🔹 Using `delete[]` on a single object:

```cpp
int* ptr = new int;
delete[] ptr; // ❌ also undefined behavior
```

---

## ✅ For Custom Classes

If your class allocates resources, calling the **destructor properly** for each element matters.

```cpp
class MyClass {
public:
    MyClass()  { cout << "Constructor\n"; }
    ~MyClass() { cout << "Destructor\n"; }
};

int main() {
    MyClass* obj1 = new MyClass;
    delete obj1;         // Calls 1 destructor

    MyClass* obj2 = new MyClass[3];
    delete[] obj2;       // Calls destructor 3 times
}
```

**Output:**

```
Constructor
Destructor
Constructor
Constructor
Constructor
Destructor
Destructor
Destructor
```

---

## ✅ Summary Table

| Keyword    | Use With         | Calls Destructors | Matches With |
| ---------- | ---------------- | ----------------- | ------------ |
| `delete`   | Single object    | One               | `new`        |
| `delete[]` | Array of objects | Multiple          | `new[]`      |


