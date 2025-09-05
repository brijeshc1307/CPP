In C++, **functions** are blocks of code that perform a specific task. Functions help make code modular, reusable, and easier to manage.

---

## **Function Types in C++**

1. **Built-in functions** – Provided by C++ libraries (e.g., `sqrt()`, `pow()`)
2. **User-defined functions** – Created by the programmer
3. **Recursive functions** – A function that calls itself

---

## **Syntax of a Function**

```cpp
return_type function_name(parameters) {
    // body of the function
    return value; // (if return_type is not void)
}
```

---

## **Function Declaration (Prototype)**

Before using a function, it can be declared at the top:

```cpp
return_type function_name(parameter_list);
```

> This helps the compiler know the function signature before its actual definition.

---

## **Example: Function Without Parameters and No Return Value**

```cpp
#include <iostream>
using namespace std;

void greet() {
    cout << "Hello, welcome to C++ functions!" << endl;
}

int main() {
    greet(); // function call
    return 0;
}
```

---

## **Example: Function With Parameters and Return Value**

```cpp
#include <iostream>
using namespace std;

int add(int a, int b) {
    return a + b;
}

int main() {
    int result = add(5, 3); // function call with arguments
    cout << "Sum is: " << result;
    return 0;
}
```

---

## **Function with Default Arguments**

```cpp
#include <iostream>
using namespace std;

void display(string name = "Guest") {
    cout << "Hello, " << name << endl;
}

int main() {
    display("Brijesh");
    display();  // uses default argument
    return 0;
}
```

---

## **Recursive Function Example**

```cpp
#include <iostream>
using namespace std;

int factorial(int n) {
    if (n == 0) return 1;
    else return n * factorial(n - 1);
}

int main() {
    cout << "Factorial of 5 is: " << factorial(5);
    return 0;
}
```

---

## **Inline Function**

Used for small, frequently-used functions. Hint to compiler to replace function call with function code.

```cpp
#include <iostream>
using namespace std;

inline int square(int x) {
    return x * x;
}

int main() {
    cout << "Square of 4 is: " << square(4);
    return 0;
}
```

---

## Function Overloading

Multiple functions with the same name but different parameter types or counts.

```cpp
#include <iostream>
using namespace std;

int add(int a, int b) {
    return a + b;
}

double add(double a, double b) {
    return a + b;
}

int main() {
    cout << add(3, 4) << endl;     // calls int version
    cout << add(2.5, 3.5) << endl; // calls double version
    return 0;
}
```

---

### **1. Pass by Value**
* A **copy** of the actual parameter is passed.
* Changes made inside the function do **not affect** the original variable.

**Example:**

```cpp
void modify(int x) {
    x = 10;  // Only modifies the copy
}
```

---

### **2. Pass by Reference**
* The **actual variable itself** is passed using a reference (`&`).
* Changes made inside the function **do affect** the original variable.

**Example:**

```cpp
void modify(int &x) {
    x = 10;  // Modifies the original
}
```
**Example:**
## **1. Pass by Reference using `&`**

```cpp
#include <iostream>
using namespace std;

void modify(int &x) { // x is an alias to the original variable
    x = 10;  // This changes the original variable
}

int main() {
    int num = 5;
    modify(num); // Passes reference
    cout << "After modify(): " << num << endl; // Output: 10
    return 0;
}
```

---

## **2. Pass by Reference using `*` (Pointer)**

```cpp
#include <iostream>
using namespace std;

void modify(int *x) { // x is a pointer to the original variable
    *x = 20;  // Dereferencing changes the original variable
}

int main() {
    int num = 5;
    modify(&num); // Pass address of num
    cout << "After modify(): " << num << endl; // Output: 20
    return 0;
}
```
---
Here is your comparison in a neatly formatted table:

| **Aspect**                      | **Pass by Value**                                                          | **Pass by Reference**                                                        |
| ------------------------------- | -------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| **What is passed**              | A copy of a variable is passed.                                            | Either the address of the variable or a reference to the variable is passed. |
| **Effect on original variable** | Changes made inside the function do **not** affect the original variable.  | Changes made inside the function **do** affect the original variable.        |
| **Memory location**             | Actual and formal parameters are stored in **different** memory locations. | Actual and formal parameters share the **same** memory location.             |
| **Memory efficiency**           | Slightly **less memory efficient** due to duplication.                     | Slightly **more memory efficient** as no duplication of data occurs.         |



---
[⬅️ Control Structures](/ControlStructures.md)         |        [Pointers ➡️](/Pointers.md)
---
## **License**
This project is licensed under the MIT License.

---

Happy Coding!

