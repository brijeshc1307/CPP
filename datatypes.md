## Data Types in C++

>A Data Type specifies the type of data that a variable can store such as Integer, Float, Charecter, etc. 
In C++, data types are used to define the **type of data** a variable can hold. They are mainly categorized into:

### 1. **Primitive (Built-in) Data Types**

These are basic types provided by the language.

| Type     | Description                  | Example             |
| -------- | ---------------------------- | ------------------- |
| `int`    | Integer values               | `int a = 10;`       |
| `float`  | Single precision decimal     | `float b = 3.14f;`  |
| `double` | Double precision decimal     | `double c = 5.123;` |
| `char`   | Single character             | `char d = 'A';`     |
| `bool`   | Boolean (true or false)      | `bool e = true;`    |
| `void`   | No value (used in functions) | `void show();`      |

---

### 2. **Derived Data Types**

These are built from primitive types.

| Type        | Description                | Example                         |
| ----------- | -------------------------- | ------------------------------- |
| `Array`     | Collection of elements     | `int arr[5] = {1, 2, 3, 4, 5};` |
| `Pointer`   | Stores memory address      | `int *ptr = &a;`                |
| `Reference` | Alias for another variable | `int &ref = a;`                 |
| `Function`  | Block of reusable code     | `int add(int x, int y);`        |

---

### 3. **User-Defined Data Types**

These are created by the programmer for specific needs.

| Type      | Description                         | Example                             |
| --------- | ----------------------------------- | ----------------------------------- |
| `struct`  | Group of variables                  | `struct Person { int age; };`       |
| `union`   | Similar to struct but shared memory | `union Data { int i; float f; };`   |
| `enum`    | Enumerated constant values          | `enum Color { RED, GREEN, BLUE };`  |
| `class`   | Blueprint for objects (OOP)         | `class Car { public: int speed; };` |
| `typedef` | Alias name for data types           | `typedef unsigned int uint;`        |
| `using`   | Modern type alias (C++11+)          | `using uint = unsigned int;`        |

---

## Example Program:

```cpp
#include <iostream>
using namespace std;

struct Person {
    int age;
    char name[50];
};

int main() {
    // Primitive
    int a = 5;
    float b = 3.14f;
    char c = 'X';
    bool isActive = true;

    // Derived
    int arr[3] = {1, 2, 3};
    int *ptr = &a;

    // User-defined
    Person p1 = {25, "John"};

    cout << "Age: " << p1.age << ", Name: " << p1.name << endl;
    cout << "Value of a: " << a << ", via pointer: " << *ptr << endl;

    return 0;
}
```

---

## 📏 C++ Data Types and Their Sizes (in Bytes)

| **Category**  | **Data Type**    | **Size (Bytes)** | **Range (Approximate)**                              |
| ------------- | ---------------- | ---------------- | ---------------------------------------------------- |
| **Primitive** | `bool`           | 1                | `true` or `false`                                    |
|               | `char`           | 1                | -128 to 127 (ASCII)                                  |
|               | `unsigned char`  | 1                | 0 to 255                                             |
|               | `int`            | 4                | -2,147,483,648 to 2,147,483,647                      |
|               | `unsigned int`   | 4                | 0 to 4,294,967,295                                   |
|               | `short int`      | 2                | -32,768 to 32,767                                    |
|               | `unsigned short` | 2                | 0 to 65,535                                          |
|               | `long int`       | 4 or 8           | Platform dependent (usually same as `int` or larger) |
|               | `unsigned long`  | 4 or 8           | 0 to 4 billion+                                      |
|               | `long long int`  | 8                | ±9 quintillion approx.                               |
|               | `float`          | 4                | \~3.4e-38 to 3.4e+38                                 |
|               | `double`         | 8                | \~1.7e-308 to 1.7e+308                               |
|               | `long double`    | 8, 12, or 16     | Depends on compiler (wider precision)                |

---

## Notes:

* `sizeof(type)` in C++ can be used to check size at runtime.
* Sizes may differ based on compiler settings and architecture.
* `void` has no size; it means "no value" and is used for functions that don't return anything.

---
Here’s a clear and concise explanation of **data types**, **variables**, and **`const`** in **C++**, along with examples.

---

###  2. **Variables in C++**

* A **variable** is a name for a memory location to store a value.
* It must be declared with a data type before use.

#### Syntax:

```cpp
<data_type> <variable_name> = <value>;
```

#### Example:

```cpp
int age = 25;
float temperature = 36.6;
char grade = 'B';
```

#### Rules for Variable Names:

* Must start with a letter or underscore.
* Cannot use C++ keywords (like `int`, `return`, etc.)
* Case-sensitive (`Age` and `age` are different).

---

### 3. **`const` in C++**

* **`const`** is a keyword to declare **constants** (values that cannot change after initialization).

#### Syntax:

```cpp
const data_type variable_name = value;
```

#### Example:

```cpp
const float PI = 3.14;
```

Attempting to change `PI` later will cause a compile-time error.

---

### Example Code:

```cpp
#include <iostream>
using namespace std;

int main() {
    int age = 25;              // variable
    const float PI = 3.14;     // constant
    char grade = 'A';          // variable
    bool isAdult = true;       // variable

    cout << "Age: " << age << endl;
    cout << "PI: " << PI << endl;
    cout << "Grade: " << grade << endl;
    cout << "Is Adult: " << isAdult << endl;

    return 0;
}
```
---
[⬅️ Basics](/basics.md)        |         [Operators ➡️](/Operators.md) 
---

## **License**
This project is licensed under the MIT License.

---

Happy Coding!


