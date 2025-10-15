
## Introduction to C++

**C++** is a general-purpose, high-performance programming language developed by **Bjarne Stroustrup** as an extension of the **C language**.
It supports **procedural**, **object-oriented**, and **generic** programming.

---


### **Timeline of Development**

| Year      | Event                                                                                                  |
| --------- | ------------------------------------------------------------------------------------------------------ |
| **1979**  | Bjarne Stroustrup begins working on "C with Classes" during his Ph.D. work.                            |
| **1983**  | Renamed to **C++** (where "++" is the increment operator in C).                                        |
| **1985**  | First official release of **C++** along with the first edition of *The C++ Programming Language* book. |
| **1989**  | Release of **C++ 2.0**, adding multiple inheritance, abstract classes, etc.                            |
| **1998**  | **C++98** standardized by ISO/IEC — the first international standard.                                  |
| **2003**  | **C++03**: A bug-fix release to C++98 with minor tweaks.                                               |
| **2011**  | **C++11**: Major update adding smart pointers, lambda expressions, auto keyword, etc.                  |
| **2014**  | **C++14**: Small updates and performance improvements.                                                 |
| **2017**  | **C++17**: More language simplifications and powerful STL improvements.                                |
| **2020**  | **C++20**: Introduced modules, coroutines, ranges, concepts, and more.                                 |
| **2023+** | **C++23** and beyond: Continued modernization and evolution of the language.                           |

---


### Features:

* Object-Oriented (Supports classes and objects)
* Fast and powerful
* Portable
* Rich Standard Template Library (STL)
* Supports low-level memory manipulation

---

### Version-Wise Feature Table

| C++ Version            | Release Year | Major Features                                                                                                                                                                                                                                                                                                                      |
| ---------------------- | ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **C++98 / C++03**      | 1998 / 2003  | - First standardized version<br>- Classes, inheritance, polymorphism<br>- Templates<br>- STL (Standard Template Library)<br>- Exception handling                                                                                                                                                                                    |
| **C++11**              | 2011         | 🚀 "Modern C++" begins<br>- `auto` keyword<br>- Range-based `for` loop<br>- Lambda expressions<br>- Smart pointers (`unique_ptr`, `shared_ptr`)<br>- `nullptr`<br>- Move semantics (rvalue references)<br>- `constexpr`, `static_assert`<br>- Variadic templates<br>- `enum class`                                                  |
| **C++14**              | 2014         | 🔧 Minor improvements<br>- Generic lambdas<br>- `decltype(auto)`<br>- Return type deduction<br>- Binary literals (`0b1010`)<br>- `make_unique`                                                                                                                                                                                      |
| **C++17**              | 2017         | 💪 More powerful syntax<br>- `if constexpr`<br>- Structured bindings (`auto [a, b] = ...`)<br>- Inline variables<br>- Fold expressions (for variadic templates)<br>- `std::optional`, `std::variant`, `std::any`<br>- `std::string_view`<br>- Parallel algorithms<br>- Filesystem library                                           |
| **C++20**              | 2020         | 🧠 Huge upgrade<br>- Concepts (type constraints)<br>- `ranges` library<br>- Coroutines (`co_await`, `co_yield`, `co_return`)<br>- Modules (replacing headers, still evolving)<br>- `consteval`, `constinit`<br>- `three-way comparison` (`<=>`)<br>- Calendar and time zone library                                                 |
| **C++23**              | 2023         | 🔄 Usability + performance<br>- `std::expected` (like `optional`, but with error info)<br>- `static operator()` for lambdas<br>- `std::print()` and `std::println()`<br>- `explicit` for operators<br>- `monadic` operations for `optional`, `variant`, etc.<br>- Improved `ranges`, `format` libraries<br>- More constexpr support |
| **C++26** *(Upcoming)* | ~2026        | 📈 In progress<br>- Executors and networking (likely)<br>- Reflection (compile-time introspection)<br>- Pattern matching (like `match` expressions)<br>- More AI/compiler-related tooling                                                                                                                                           |

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

##  Applications of C++

C++ is used in a wide range of domains due to its performance, flexibility, and system-level capabilities. Here are some key areas:

### 1. **System Software**

* Operating Systems (Windows, macOS, Linux components)
* Drivers and firmware
* File systems

### 2. **Game Development**

* High-performance 2D and 3D game engines
* Real-time physics and graphics rendering (e.g., Unreal Engine)

### 3. **Embedded Systems**

* IoT devices, microcontrollers
* Routers, washing machines, smartwatches, etc.

### 4. **GUI Applications**

* Desktop applications using frameworks like Qt, wxWidgets

### 5. **Database Software**

* MySQL and other database management systems use C++

### 6. **Web Browsers**

* Performance-critical parts of browsers like Chrome, Firefox are written in C++

### 7. **Financial Systems**

* Real-time trading systems
* Banking and risk management software

### 8. **Compilers and Interpreters**

* C++ is used to build compilers for other languages

### 9. **Scientific Computing**

* Simulation tools
* Data analysis frameworks

---

### Comparison: C vs C++ vs Python vs Java

| Feature / Language      | **C**                        | **C++**                                   | **Python**                        | **Java**                      |
| ----------------------- | ---------------------------- | ----------------------------------------- | --------------------------------- | ----------------------------- |
| **Developed By**        | Dennis Ritchie               | Bjarne Stroustrup                         | Guido van Rossum                  | James Gosling                 |
| **Year of Creation**    | 1972                         | 1983                                      | 1991                              | 1995                          |
| **Language Type**       | Procedural                   | Procedural + Object-Oriented              | Object-Oriented + Interpreted     | Pure Object-Oriented (mostly) |
| **Compilation**         | Compiled                     | Compiled                                  | Interpreted (can be compiled)     | Compiled to bytecode (JVM)    |
| **Speed**               | Very Fast                    | Fast                                      | Slower than C/C++                 | Slower than C/C++             |
| **Syntax**              | Complex                      | Slightly complex                          | Very simple and readable          | Verbose (needs more code)     |
| **Memory Management**   | Manual (via malloc/free)     | Manual or RAII (constructors/destructors) | Automatic (Garbage Collected)     | Automatic (Garbage Collected) |
| **Platform Dependence** | Platform Dependent           | Platform Dependent                        | Cross-platform                    | Cross-platform                |
| **Use Cases**           | System programming, Embedded | Games, System/Device software             | Web, AI, Data Science, Automation | Android, Enterprise Apps, Web |
| **OOP Support**         | ❌ No                         | ✅ Yes                                     | ✅ Yes                             | ✅ Full                        |
| **Standard Library**    | Small                        | Large (STL)                               | Very rich                         | Rich (Java API)               |
| **Pointers**            | ✅ Yes                        | ✅ Yes                                     | ❌ No direct use                   | ❌ No direct use               |
| **Main Extension**      | `.c`                         | `.cpp`                                    | `.py`                             | `.java`                       |

---

## Compiler

A **compiler** is a program that **translates source code written in a high-level programming language (like C++) into machine code (binary code)** that a computer's processor can execute.

### Example:

Suppose you write this C++ code in a file `hello.cpp`:

```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hello, World!" << endl;
    return 0;
}
```

Now, you compile it using a compiler like **G++**:

```bash
g++ hello.cpp -o hello
```

This creates an executable file `hello` that you can run:

```bash
./hello
```

Output:

```
Hello, World!
```
For mac/linux
```
g++ -std=c++11 code.cpp && ./a.out

or

g++ -std=c++11 code.cpp -o myprogram && ./myprogram

```



---

## Compilation Stages in C++

The C++ compilation process has **four main stages**:

### 1. **Preprocessing**

* Handled by the preprocessor (`#include`, `#define`, etc.)
* Produces a "pure" C++ code without macros and includes.

### 2. **Compilation**

* Translates the preprocessed code into **assembly code**.

### 3. **Assembly**

* Converts assembly code into **object code** (`.o` or `.obj` file).

### 4. **Linking**

* Links all object files and libraries to generate the final **executable**.

---

## Related Topics in C++

### 1. **Interpreter vs Compiler**

| Feature      | Compiler                | Interpreter                      |
| ------------ | ----------------------- | -------------------------------- |
| Output       | Machine code            | Line-by-line execution           |
| Speed        | Faster execution        | Slower execution                 |
| Example Lang | C, C++, Java (compiled) | Python, JavaScript (interpreted) |

---

### 2. **Header Files**

These files (like `<iostream>`) are included during the **preprocessing** stage. They contain function declarations and macros.

### 3. **Object Files**

Files with `.o` or `.obj` extensions are produced after the compilation stage, but before linking.

---

## Summary Diagram

```text
hello.cpp
   |
[Preprocessor] --> expanded code
   |
[Compiler] --> hello.s (Assembly)
   |
[Assembler] --> hello.o (Object Code)
   |
[Linker] --> hello (Executable)
```
---
 [Data Types ➡️](/datatypes.md) 
---

## **License**
This project is licensed under the MIT License.

---

Happy Coding!

