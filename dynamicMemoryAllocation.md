### **Dynamic Memory Allocation in C**

In C, **dynamic memory allocation** allows you to allocate memory at runtime (i.e., while the program is running), rather than at compile time. This is essential when the amount of memory required is not known in advance.

---

### **Key Functions for Dynamic Memory Allocation** (in `<stdlib.h>`):

| Function    | Purpose                                                  |
| ----------- | -------------------------------------------------------- |
| `malloc()`  | Allocates a specified number of bytes                    |
| `calloc()`  | Allocates memory for an array and initializes it to zero |
| `realloc()` | Reallocates memory to change its size                    |
| `free()`    | Frees dynamically allocated memory                       |

---

### **1. `malloc()` (Memory Allocation)**

* Allocates memory block of given size (in bytes).
* Does **not initialize** memory (contains garbage values).

```c
#include <stdlib.h>

int *ptr = (int *) malloc(5 * sizeof(int));  // Allocates memory for 5 integers
```

---

### **2. `calloc()` (Contiguous Allocation)**

* Allocates memory for an array of elements.
* Initializes all bytes to **zero**.

```c
int *ptr = (int *) calloc(5, sizeof(int));  // Allocates memory for 5 integers and initializes to 0
```

---

### **3. `realloc()` (Reallocation)**

* Changes the size of memory previously allocated.
* May return a **new memory location**.

```c
ptr = (int *) realloc(ptr, 10 * sizeof(int));  // Resize to 10 integers
```

---

###  **4. `free()`**

* Frees memory allocated by `malloc`, `calloc`, or `realloc`.
* Prevents memory leaks.

```c
free(ptr);  // Deallocates memory
```

---

###  **Example:**

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *arr;
    int n = 5;

    arr = (int *) malloc(n * sizeof(int));  // Allocate memory

    if (arr == NULL) {
        printf("Memory not allocated!\n");
        return 1;
    }

    for (int i = 0; i < n; i++) {
        arr[i] = i + 1;
    }

    printf("Array: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }

    free(arr);  // Deallocate memory
    return 0;
}
```

---

### **Why Use Dynamic Memory?**

* When array size is not known during compilation.
* For flexible and efficient memory usage.
* To avoid wastage of stack memory.

---

### **Dynamic Memory Allocation in C++**

**Dynamic memory allocation** allows you to allocate memory **at runtime** (not at compile time), using **pointers**.
This is useful when:

* You don't know the required memory size in advance.
* You want to allocate memory during program execution.

---

## Operators Used

| Operator   | Purpose                   | Syntax                   |
| ---------- | ------------------------- | ------------------------ |
| `new`      | Allocates memory          | `int* p = new int;`      |
| `new[]`    | Allocates array of memory | `int* arr = new int[5];` |
| `delete`   | Deallocates single object | `delete p;`              |
| `delete[]` | Deallocates array         | `delete[] arr;`          |

---

## Example 1: Allocate Single Variable

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

## Example 2: Allocate Array

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

## Important Points

* Memory allocated with `new`/`new[]` **stays until** you explicitly `delete`/`delete[]` it.
* Not deallocating memory causes **memory leaks**.
* Always use `delete`/`delete[]` after `new`/`new[]`.

---

## Dynamic Memory for Custom Class

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

### `delete` vs `delete[]` in C++

Both `delete` and `delete[]` are used to **deallocate memory** in C++ that was previously allocated using `new` or `new[]`.
But they are **not interchangeable**.

---

## 1. `delete`

* Used to **free memory** allocated for **a single object**.
* Matches with `new`.

### Example:

```cpp
int* ptr = new int;   // allocate memory for 1 int
*ptr = 10;

delete ptr;           // correct
```

---

## 2. `delete[]`

* Used to **free memory** allocated for **an array of objects**.
* Matches with `new[]`.

### Example:

```cpp
int* arr = new int[5];   // allocate memory for array of 5 ints

delete[] arr;            // correct
```

---

## What if you mix them up?

### Using `delete` on an array:

```cpp
int* arr = new int[5];
delete arr;   // ❌ undefined behavior (may cause memory leak or crash)
```

### Using `delete[]` on a single object:

```cpp
int* ptr = new int;
delete[] ptr; // ❌ also undefined behavior
```

---

## For Custom Classes

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

## Summary Table

| Keyword    | Use With         | Calls Destructors | Matches With |
| ---------- | ---------------- | ----------------- | ------------ |
| `delete`   | Single object    | One               | `new`        |
| `delete[]` | Array of objects | Multiple          | `new[]`      |

---
---

###  **1. How is memory freed in C?**

In C, memory allocated dynamically using `malloc()`, `calloc()`, or `realloc()` must be released using the `free()` function to prevent memory leaks.

####  Example:

```c
int* ptr = (int*)malloc(sizeof(int) * 5);  // allocate memory
// use ptr...
free(ptr);  // free allocated memory
```

---

###  **2. How do you allocate memory for a single object and an array in C++?**

Use the `new` operator for dynamic memory allocation in C++.

####  Single Object:

```cpp
int* p = new int;   // allocates memory for one int
*p = 10;
```

#### � Array:

```cpp
int* arr = new int[5];  // allocates memory for array of 5 ints
```

Memory should be released using `delete` or `delete[]`:

```cpp
delete p;
delete[] arr;
```

---

###  **3. What happens if you use `delete` on memory allocated with `malloc()`?**

💥 **Undefined behavior.**
You **must not mix** C and C++ memory management functions.

* `malloc()` → `free()`
* `new` → `delete`
* `new[]` → `delete[]`

Using the wrong deallocator may cause **crashes** or **corruption**.

---

### **4. What is a memory leak? How does it occur in C++?**

A **memory leak** occurs when:

* Memory is allocated dynamically,
* But is **not deallocated** (no `delete`/`free` called),
* So it remains **unusable until program exits**.

#### Example:

```cpp
int* p = new int(10);
// No delete ⇒ memory leak
```

In long-running apps (like servers), leaks can lead to **performance degradation or crashes**.

---

### **5. Explain the use of `new[]` and `delete[]` in C++.**

* `new[]` allocates memory for an **array of objects**.
* `delete[]` deallocates that array.

#### Example:

```cpp
int* arr = new int[5];   // allocates memory for 5 integers
// ... use arr
delete[] arr;            // properly deallocates the array
```

> ❗ Using `delete` instead of `delete[]` on an array results in **undefined behavior**.

---

### **6. What are the differences between stack and heap memory?**

| Feature          | Stack                            | Heap                            |
| ---------------- | -------------------------------- | ------------------------------- |
| Allocation speed | Fast                             | Slower                          |
| Lifetime         | Automatically managed            | Manually managed                |
| Size limit       | Limited (depends on OS)          | Much larger (depends on RAM)    |
| Allocation       | At compile-time or function call | At runtime using `new`/`malloc` |
| Deallocation     | Automatic (function return)      | Manual (`delete` / `free`)      |

---

### **7. How can tools like Valgrind help with dynamic memory?**

**Valgrind** is a tool that:

* Detects **memory leaks**.
* Identifies **invalid memory access** (e.g., using after free).
* Tracks **uninitialized memory reads**.
* Shows **exact line numbers** causing leaks.

#### Example Usage (Linux):

```bash
valgrind ./your_program
```

It reports:

* Blocks of memory that were never freed.
* Locations of memory mismanagement.

---

###  **8. Is it possible to allocate memory for a 2D array dynamically? How?**

Yes. You can allocate a 2D array using **pointers to pointers**.

####  Example in C/C++:

```cpp
int rows = 3, cols = 4;

// Step 1: Allocate memory for row pointers
int** arr = new int*[rows];

// Step 2: Allocate memory for each row
for (int i = 0; i < rows; i++) {
    arr[i] = new int[cols];
}

// ... use arr[i][j]

// Free memory
for (int i = 0; i < rows; i++) {
    delete[] arr[i];
}
delete[] arr;
```

This is commonly used when the array dimensions are not known at compile-time.

---

## **License**
This project is licensed under the MIT License.

---

Happy Coding!




