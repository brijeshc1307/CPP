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

---
[⬅️ Control Structures](/ControlStructures.md)         |        [Pointers ➡️](/Pointers.md)
---
## **License**
This project is licensed under the MIT License.

---

Happy Coding!

