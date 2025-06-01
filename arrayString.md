In C++, **an array** is a collection of **elements of the same data type**, stored in **contiguous memory locations**. Arrays are used to store multiple values in a single variable, instead of declaring separate variables for each value.

---

### **Why Use Arrays?**

* To group related data together
* To reduce code complexity (especially when using loops)
* To access elements by index easily

---

## Declaration and Initialization of Arrays

```cpp
#include <iostream>
using namespace std;

int main() {
    int numbers[5] = {10, 20, 30, 40, 50};

    for (int i = 0; i < 5; i++) {
        cout << "Element at index " << i << " is " << numbers[i] << endl;
    }

    return 0;
}
```

### Output:

```
Element at index 0 is 10
Element at index 1 is 20
Element at index 2 is 30
Element at index 3 is 40
Element at index 4 is 50
```

---

## 🔹 Types of Arrays in C++

| Type              | Description                                  | Example                   |
| ----------------- | -------------------------------------------- | ------------------------- |
| 1D Array          | One-dimensional, linear array                | `int arr[5];`             |
| 2D Array          | Matrix-like array (rows & columns)           | `int matrix[3][3];`       |
| Multi-D Array     | 3D or higher-dimensional arrays              | `int tensor[2][3][4];`    |
| Character Array   | Array of characters (like a string)          | `char name[10] = "John";` |
| Array of Pointers | Holds memory addresses                       | `int* ptrArr[5];`         |
| Dynamic Array     | Size can be set during runtime (heap memory) | `int* arr = new int[n];`  |

---

## 1. One-Dimensional Array

```cpp
int marks[4] = {90, 80, 85, 70};
```

---

## 2. Two-Dimensional Array

```cpp
int matrix[2][3] = {
    {1, 2, 3},
    {4, 5, 6}
};
```

### Access:

```cpp
cout << matrix[1][2];  // Output: 6
```

---

## 3. Multi-Dimensional Array (3D Example)

```cpp
int arr[2][2][2] = {
    { {1, 2}, {3, 4} },
    { {5, 6}, {7, 8} }
};
```

---

## 4. Character Array (C-style string)

```cpp
char name[6] = "Alice"; // Includes null character '\0'
```

---

## 5. Array of Pointers

```cpp
int a = 10, b = 20;
int* arr[2] = {&a, &b};
cout << *arr[1];  // Output: 20
```

---

## 6. Dynamic Array

```cpp
int n = 5;
int* arr = new int[n];

for (int i = 0; i < n; i++) {
    arr[i] = i + 1;
}

delete[] arr;  // Free the memory
```

---

## Key Points:

* Indexing starts from 0
* Size must be known at compile time for static arrays
* Use `new` and `delete` for dynamic memory allocation

---

### **String**

In C++, a **string** is a sequence of characters. C++ provides **two types of strings**:

---

## **1. C-Style Strings (Character Array)**

A **C-style string** is an array of characters terminated by a null character `'\0'`.

### Declaration & Initialization

```cpp
#include <iostream>
using namespace std;

int main() {
    char name[6] = "Alice"; // A-l-i-c-e-\0
    cout << "Name: " << name << endl;
    return 0;
}
```

### Notes:

* `char name[6]` includes 5 characters + 1 for `'\0'` (null terminator)
* You can also write: `char name[] = {'A','l','i','c','e','\0'};`

---

## **2. C++ Strings (Using `<string>` class)**

C++ Standard Library provides the `std::string` class which is more powerful and easier to use.

### Example:

```cpp
#include <iostream>
#include <string>  // Required for std::string
using namespace std;

int main() {
    string name = "Brijesh";
    cout << "Name is: " << name << endl;

    // Operations
    cout << "Length: " << name.length() << endl;
    cout << "First char: " << name[0] << endl;

    name += " Chaudhary";  // Concatenation
    cout << "Full Name: " << name << endl;

    return 0;
}
```

### Key Functions:

| Function               | Description              |
| ---------------------- | ------------------------ |
| `length()` or `size()` | Returns length of string |
| `append()`             | Appends to the string    |
| `substr(start, len)`   | Returns substring        |
| `find()`               | Searches substring       |
| `compare()`            | Compares two strings     |
| `c_str()`              | Returns C-style string   |

---

## Types of Strings in C++

| Type                 | Description                                | Example                                        |
| -------------------- | ------------------------------------------ | ---------------------------------------------- |
| **Character Array**  | C-style string using array of `char`       | `char str[10] = "Hello";`                      |
| **std::string**      | C++ style string using `#include <string>` | `string s = "Hello";`                          |
| **Array of Strings** | Array that holds multiple strings          | `string names[3] = {"Ram", "Shyam", "Mohan"};` |

---

## Example: Array of Strings

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string fruits[3] = {"Apple", "Banana", "Mango"};

    for (int i = 0; i < 3; i++) {
        cout << "Fruit " << i + 1 << ": " << fruits[i] << endl;
    }

    return 0;
}
```

---

### Difference Between C-String vs C++ String

| Feature       | C-String (`char[]`) | C++ String (`std::string`) |
| ------------- | ------------------- | -------------------------- |
| Header Needed | None or `<cstring>` | `<string>`                 |
| Terminated By | `'\0'`              | Not required               |
| Easy to Use   | ❌                   | ✅                          |
| Dynamic Size  | ❌                   | ✅                          |

---

