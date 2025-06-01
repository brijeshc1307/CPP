### **Friend Function in C++**

A **friend function** in C++ is a special function that is **not a member of a class**, but has **access to its private and protected members**.

---

## Why Use Friend Functions?

Sometimes, you need **external functions** to access **private data** of a class, especially when:

* You're performing operations involving **multiple classes**.
* You want to provide **operator overloading** (like `+`, `<<`, etc.).
* You want to **separate logic** from class definition.

---

## Syntax

Inside the class:

```cpp
friend return_type function_name(arguments);
```

---

## Simple Example

```cpp
#include <iostream>
using namespace std;

class Box {
private:
    int length;

public:
    Box(int l) : length(l) {}

    // Friend function declaration
    friend void showLength(Box b);
};

// Friend function definition (outside class)
void showLength(Box b) {
    cout << "Length is: " << b.length << endl;  // Accessing private member
}

int main() {
    Box b(10);
    showLength(b);  // Output: Length is: 10
    return 0;
}
```

---

## Key Points

| Feature                                    | Description |
| ------------------------------------------ | ----------- |
| Access to private/protected members        | Yes       |
| Member of the class?                       | No        |
| Uses `.` instead of `->` or direct access? | Yes       |
| Defined outside the class                  | Yes       |

---

## Example: Friend Function for Two Classes

```cpp
#include <iostream>
using namespace std;

class B;  // Forward declaration

class A {
private:
    int a;

public:
    A(int x) : a(x) {}
    friend void sum(A, B);
};

class B {
private:
    int b;

public:
    B(int y) : b(y) {}
    friend void sum(A, B);
};

// Friend function defined outside
void sum(A obj1, B obj2) {
    cout << "Sum is: " << obj1.a + obj2.b << endl;
}

int main() {
    A a1(5);
    B b1(7);
    sum(a1, b1);  // Output: Sum is: 12
    return 0;
}
```

---

## Friend Function vs Member Function

| Feature              | Member Function    | Friend Function          |
| -------------------- | ------------------ | ------------------------ |
| Inside class         | Yes                | No                       |
| Access to private    | Yes                | Yes                      |
| Needs object to call | Yes (`obj.func()`) | Not always (`func(obj)`) |

---

## Summary

* A **friend function** is not a class member but can access private/protected data.
* Declared with the `friend` keyword **inside the class**.
* Useful for:

  * Operator overloading
  * External operations involving private data
  * Working with multiple classes

---

