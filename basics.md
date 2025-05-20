
## Introduction to C++

**C++** is a general-purpose, high-performance programming language developed by **Bjarne Stroustrup** as an extension of the **C language**.
It supports **procedural**, **object-oriented**, and **generic** programming.

### Features:

* Object-Oriented (Supports classes and objects)
* Fast and powerful
* Portable
* Rich Standard Template Library (STL)
* Supports low-level memory manipulation

---

## Basic Syntax of C++

Here are the basic components of a C++ program:

### Elements of C++ Code:

| Element     | Description                                 |
| ----------- | ------------------------------------------- |
| `#include`  | Preprocessor directive (includes libraries) |
| `main()`    | Entry point of any C++ program              |
| `{ }`       | Denote the body/block of code               |
| `//`        | Single-line comment                         |
| `/* */`     | Multi-line comment                          |
| `;`         | Ends a statement                            |
| `<<` / `>>` | Output/Input stream operators               |

---

## First Program in C++

### Program: Print "Hello, World!"

```cpp
#include <iostream>   // Header file for input/output

using namespace std;  // Use standard namespace

int main() {          // Main function - execution starts here
    cout << "Hello, World!" << endl;  // Output statement
    return 0;         // Return 0 to indicate successful execution
}
```

### Explanation:

* `#include <iostream>`: Includes the input/output library.
* `using namespace std;`: Allows us to use `cout`, `cin` without `std::` prefix.
* `int main()`: Every C++ program must have a `main()` function.
* `cout << "Hello, World!"`: Displays the text on the console.
* `return 0;`: Ends the program.

---
## **License**
This project is licensed under the MIT License.

---

Happy Coding!

