## What is a Template in C++?

A **template** is a way to write **generic and reusable code** that works with **any data type**.

Instead of writing the same function or class for `int`, `float`, `double`, etc., you write one **template** and let the compiler generate the appropriate versions.

---

## Types of Templates

1. **Function Templates**
2. **Class Templates**

---

## 1. **Function Template Example**

```cpp
#include <iostream>
using namespace std;

// Template for a function that returns the maximum of two values
template <typename T>
T getMax(T a, T b) {
    return (a > b) ? a : b;
}

int main() {
    cout << getMax(5, 10) << endl;       // Works with int
    cout << getMax(3.5, 2.1) << endl;    // Works with double
    cout << getMax('a', 'z') << endl;    // Works with char

    return 0;
}
```

---

## 2. **Class Template Example**

```cpp
#include <iostream>
using namespace std;

// Template for a simple class holding a value
template <typename T>
class Box {
public:
    T value;

    Box(T val) {
        value = val;
    }

    void display() {
        cout << "Value: " << value << endl;
    }
};

int main() {
    Box<int> intBox(123);
    Box<string> strBox("Hello");

    intBox.display();  // Output: Value: 123
    strBox.display();  // Output: Value: Hello

    return 0;
}
```

---

## Summary:

| Feature                | Description                                                             |
| ---------------------- | ----------------------------------------------------------------------- |
| Purpose                | Write generic, reusable code                                            |
| `template<typename T>` | `T` is a placeholder for any data type                                  |
| Compiler Role          | Creates actual functions/classes during compilation based on types used |

