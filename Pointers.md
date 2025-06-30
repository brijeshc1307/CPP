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
[⬅️ Functions](/functions.md)          |        [Arrays ➡️](/array.md) 
---
## **License**
This project is licensed under the MIT License.

---

Happy Coding!
