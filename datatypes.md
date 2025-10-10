## Data Types in C++

>A Data Type specifies the type of data that a variable can store such as Integer, Float, Charecter, etc. 
In C++, data types are used to define the **type of data** a variable can hold. They are mainly categorized into:

### 1. **Primitive (Built-in) Data Types**
>These are basic types provided by the language.

### 2. **Derived Data Types**
>These are built from primitive types.

### 3. **User-Defined Data Types**
>These are created by the programmer for specific needs.

### Data Types

| **Primitive (Built-in) Data Types** | **Derived Data Types** | **User-Defined Data Types** |
| ----------------------------------- | ---------------------- | --------------------------- |
| `int`                               | Array                  | `struct`                    |
| `float`,                            | Pointer                | `union`                     |
| `double`                            | Function               | `class`                     |
| `char`                              | Reference              | `enum`                      |
| `bool`                              |                        | `typedef`                   |
| `wchar_t` (wide character)          |                        | `using`                     |

---

## Example Program:

```cpp
#include <iostream>
using namespace std;

// User-defined: struct
struct Person {
    int age;
    char name[50];
};

// User-defined: union
union Data {
    int intValue;
    float floatValue;
};

// User-defined: class
class Rectangle {
public:
    int length;
    int width;
    int area() { return length * width; }
};

// User-defined: enum
enum Color { RED, GREEN, BLUE };

// User-defined: typedef
typedef unsigned int uint;

void greet() {  // Function (Derived)
    cout << "Hello from a function!" << endl;
}

int main() {
    // Primitive types
    int a = 5;
    float b = 3.14f;
    double d = 2.71828;
    char c = 'X';
    bool isActive = true;
    wchar_t w = L'✓';

    // Derived types
    int arr[3] = {1, 2, 3};     // Array
    int* ptr = &a;              // Pointer
    int& ref = a;               // Reference

    // Function call
    greet();

    // User-defined: struct
    Person p1 = {25, "John"};

    // User-defined: union
    Data data;
    data.intValue = 100;

    // User-defined: class
    Rectangle rect;
    rect.length = 10;
    rect.width = 5;

    // User-defined: enum
    Color myColor = GREEN;

    // User-defined: typedef
    uint score = 95;

    // Output all data
    cout << "Primitive types:\n";
    cout << "int: " << a << ", float: " << b << ", double: " << d << ", char: " << c << ", bool: " << isActive << endl;
    wcout << L"wchar_t: " << w << endl;

    cout << "\nDerived types:\n";
    cout << "Array: [" << arr[0] << ", " << arr[1] << ", " << arr[2] << "]\n";
    cout << "Pointer to a: " << *ptr << "\n";
    cout << "Reference to a: " << ref << "\n";

    cout << "\nUser-defined types:\n";
    cout << "Struct - Age: " << p1.age << ", Name: " << p1.name << endl;
    cout << "Union - intValue: " << data.intValue << endl;
    cout << "Class - Rectangle Area: " << rect.area() << endl;
    cout << "Enum - Color: " << myColor << " (GREEN = 1)\n";
    cout << "Typedef (uint) - Score: " << score << endl;

    return 0;
}
```
Output
```
Hello from a function!
Primitive types:
int: 5, float: 3.14, double: 2.71828, char: X, bool: 1
wchar_t: 

Derived types:
Array: [1, 2, 3]
Pointer to a: 5
Reference to a: 5

User-defined types:
Struct - Age: 25, Name: John
Union - intValue: 100
Class - Rectangle Area: 50
Enum - Color: 1 (GREEN = 1)
Typedef (uint) - Score: 95
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
### ASCII Code
* **ASCII (American Standard Code for Information Interchange)** assigns a numeric value (0–127) to each character.
* It includes:

  * **Control characters** (0–31, 127): e.g., `\n`, `\t`, backspace — mostly non-printable.
  * **Printable characters** (32–126): letters, digits, punctuation, symbols, and space.
* **Common ASCII Values:**

  * `'A'` to `'Z'` → 65 to 90
  * `'a'` to `'z'` → 97 to 122
  * `'0'` to `'9'` → 48 to 57
  * `Space` → 32
  * `Enter (newline)` → 10 (`\n`)
  * `Tab` → 9 (`\t`)
* In **C++**, you can:

  * Convert a **char to ASCII** using: `int code = (int)ch;`
  * Convert an **ASCII code to char** using: `char ch = (char)code;`

---

### **ASCII Table (Decimal, Char)**

| Dec | Char  | Dec | Char | Dec | Char | Dec | Char |
| --- | ----- | --- | ---- | --- | ---- | --- | ---- |
| 32  | Space | 41  | `)`  | 50  | `2`  | 59  | `;`  |
| 33  | `!`   | 42  | `*`  | 51  | `3`  | 60  | `<`  |
| 34  | `"`   | 43  | `+`  | 52  | `4`  | 61  | `=`  |
| 35  | `#`   | 44  | `,`  | 53  | `5`  | 62  | `>`  |
| 36  | `$`   | 45  | `-`  | 54  | `6`  | 63  | `?`  |
| 37  | `%`   | 46  | `.`  | 55  | `7`  | 64  | `@`  |
| 38  | `&`   | 47  | `/`  | 56  | `8`  | 65  | `A`  |
| 39  | `'`   | 48  | `0`  | 57  | `9`  | 66  | `B`  |
| 40  | `(`   | 49  | `1`  | 58  | `:`  | 67  | `C`  |

| Dec | Char | Dec | Char | Dec | Char | Dec | Char    |
| --- | ---- | --- | ---- | --- | ---- | --- | ------- |
| 68  | `D`  | 77  | `M`  | 86  | `V`  | 95  | `_`     |
| 69  | `E`  | 78  | `N`  | 87  | `W`  | 96  | `` ` `` |
| 70  | `F`  | 79  | `O`  | 88  | `X`  | 97  | `a`     |
| 71  | `G`  | 80  | `P`  | 89  | `Y`  | 98  | `b`     |
| 72  | `H`  | 81  | `Q`  | 90  | `Z`  | 99  | `c`     |
| 73  | `I`  | 82  | `R`  | 91  | `[`  | 100 | `d`     |
| 74  | `J`  | 83  | `S`  | 92  | `\`  | 101 | `e`     |
| 75  | `K`  | 84  | `T`  | 93  | `]`  | 102 | `f`     |
| 76  | `L`  | 85  | `U`  | 94  | `^`  | 103 | `g`     |

| Dec | Char | Dec | Char | Dec | Char | Dec | Char |    |
| --- | ---- | --- | ---- | --- | ---- | --- | ---- | -- |
| 104 | `h`  | 109 | `m`  | 114 | `r`  | 119 | `w`  |    |
| 105 | `i`  | 110 | `n`  | 115 | `s`  | 120 | `x`  |    |
| 106 | `j`  | 111 | `o`  | 116 | `t`  | 121 | `y`  |    |
| 107 | `k`  | 112 | `p`  | 117 | `u`  | 122 | `z`  |    |
| 108 | `l`  | 113 | `q`  | 118 | `v`  | 123 | `{`  |    |
|     |      |     |      |     |      | 124 | \`   | \` |
|     |      |     |      |     |      | 125 | `}`  |    |
|     |      |     |      |     |      | 126 | `~`  |    |

---

---
[⬅️ Basics](/basics.md)      |          [Operators ➡️](/Operators.md)
---

## **License**
This project is licensed under the MIT License.

---

Happy Coding!


