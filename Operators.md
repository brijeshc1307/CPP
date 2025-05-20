##  Operators in C++

Operators are symbols that perform operations on variables and values. C++ supports various types of operators:

---

### 1. **Arithmetic Operators**

| Operator | Description         | Example |
| -------- | ------------------- | ------- |
| `+`      | Addition            | `a + b` |
| `-`      | Subtraction         | `a - b` |
| `*`      | Multiplication      | `a * b` |
| `/`      | Division            | `a / b` |
| `%`      | Modulus (remainder) | `a % b` |

**Example**:

```cpp
int a = 10, b = 3;
cout << a + b << endl;  // 13
cout << a % b << endl;  // 1
```

---

### 2. **Relational (Comparison) Operators**

| Operator | Description           | Example  |
| -------- | --------------------- | -------- |
| `==`     | Equal to              | `a == b` |
| `!=`     | Not equal to          | `a != b` |
| `>`      | Greater than          | `a > b`  |
| `<`      | Less than             | `a < b`  |
| `>=`     | Greater than or equal | `a >= b` |
| `<=`     | Less than or equal    | `a <= b` |

**Example**:

```cpp
cout << (a > b);  // Outputs 1 (true)
```

---

### 3. **Logical Operators**

| Operator | Description | Example           |            |         |   |         |
| -------- | ----------- | ----------------- | ---------- | ------- | - | ------- |
| `&&`     | Logical AND | `a > 5 && b < 10` |            |         |   |         |
| \`       |             | \`                | Logical OR | \`a > 5 |   | b < 2\` |
| `!`      | Logical NOT | `!(a == b)`       |            |         |   |         |

**Example**:

```cpp
if (a > 5 && b < 10) {
    cout << "Condition true";
}
```

---

### 4. **Assignment Operators**

| Operator | Description         | Example  |
| -------- | ------------------- | -------- |
| `=`      | Assign value        | `a = 5`  |
| `+=`     | Add and assign      | `a += 3` |
| `-=`     | Subtract and assign | `a -= 2` |
| `*=`     | Multiply and assign | `a *= 4` |
| `/=`     | Divide and assign   | `a /= 2` |
| `%=`     | Modulus and assign  | `a %= 3` |

---

### 5. **Increment/Decrement Operators**

| Operator | Description | Example        |
| -------- | ----------- | -------------- |
| `++`     | Increment   | `++a` or `a++` |
| `--`     | Decrement   | `--a` or `a--` |

**Example**:

```cpp
int x = 5;
cout << ++x;  // Outputs 6
cout << x--;  // Outputs 6 (then x becomes 5)
```

---

### 6. **Bitwise Operators**

| Operator | Description | Example    |     |     |
| -------- | ----------- | ---------- | --- | --- |
| `&`      | Bitwise AND | `a & b`    |     |     |
| \`       | \`          | Bitwise OR | \`a | b\` |
| `^`      | Bitwise XOR | `a ^ b`    |     |     |
| `~`      | Bitwise NOT | `~a`       |     |     |
| `<<`     | Left shift  | `a << 1`   |     |     |
| `>>`     | Right shift | `a >> 1`   |     |     |

---

### 7. **Conditional (Ternary) Operator**

| Operator | Description             | Example         |
| -------- | ----------------------- | --------------- |
| `?:`     | Short if-else condition | `a > b ? a : b` |

**Example**:

```cpp
int max = (a > b) ? a : b;
```

---

### 8. **Sizeof Operator**

| Operator | Description          | Example       |
| -------- | -------------------- | ------------- |
| `sizeof` | Returns size of type | `sizeof(int)` |

---

### 9. **Typecast Operator**

| Operator | Description                  | Example               |
| -------- | ---------------------------- | --------------------- |
| `(type)` | Converts one type to another | `float f = (float)a;` |

---

### 10. **Pointer Operators**

| Operator | Description                    | Example |
| -------- | ------------------------------ | ------- |
| `*`      | Value at address (dereference) | `*ptr`  |
| `&`      | Address of a variable          | `&a`    |

---

## Example using multiple operators:

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 5, b = 3;
    int max = (a > b) ? a : b; // ternary
    cout << "Max: " << max << endl;
    cout << "Sum: " << a + b << endl;
    cout << "Bitwise AND: " << (a & b) << endl;
    return 0;
}
```

---
## **License**
This project is licensed under the MIT License.

---

Happy Coding!

