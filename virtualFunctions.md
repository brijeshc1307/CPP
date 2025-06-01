### Virtual Functions

A **virtual function** in C++ is a **member function in a base class** that you expect to **override in derived classes**. It allows **runtime polymorphism** — i.e., the correct function is chosen at **run time**, based on the object type.

---

## Why Use Virtual Functions?

They allow you to:

* Call **derived class functions using base class pointers/references**.
* Achieve **dynamic dispatch** (runtime function resolution).
* Support **runtime polymorphism** — one interface, multiple behaviors.

---

## Syntax

```cpp
class Base {
public:
    virtual void show() {
        cout << "Base class" << endl;
    }
};
```

---

## Example: Without Virtual Function (Static Binding)

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    void show() {
        cout << "Base class" << endl;
    }
};

class Derived : public Base {
public:
    void show() {
        cout << "Derived class" << endl;
    }
};

int main() {
    Base* bptr;
    Derived d;
    bptr = &d;

    bptr->show();  // Output: Base class (not what you expected)
    return 0;
}
```

---

## Example: With Virtual Function (Dynamic Binding)

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void show() {  //  virtual keyword
        cout << "Base class" << endl;
    }
};

class Derived : public Base {
public:
    void show() override {  // optional 'override' for clarity
        cout << "Derived class" << endl;
    }
};

int main() {
    Base* bptr;
    Derived d;
    bptr = &d;

    bptr->show();  // Output: Derived class
    return 0;
}
```

---

## Key Concepts

| Feature                  | Description                         |
| ------------------------ | ----------------------------------- |
| Resolved at              | **Runtime**                         |
| Enables                  | **Polymorphism**                    |
| Requires                 | `virtual` keyword in base class     |
| Works via                | Pointers or references              |
| Overriding Function      | Must have **same signature**        |
| Virtual Table (`vtable`) | Internal mechanism used by compiler |

---

## Real-Life Analogy

* **Base class**: `Shape` with `draw()`
* **Derived classes**: `Circle`, `Rectangle` override `draw()`
* You can store different shapes in a `Shape*` array and call `draw()` without knowing the exact type.

```cpp
class Shape {
public:
    virtual void draw() {
        cout << "Drawing shape" << endl;
    }
};

class Circle : public Shape {
public:
    void draw() {
        cout << "Drawing circle" << endl;
    }
};

class Rectangle : public Shape {
public:
    void draw() {
        cout << "Drawing rectangle" << endl;
    }
};

int main() {
    Shape* s1 = new Circle();
    Shape* s2 = new Rectangle();

    s1->draw();  // Output: Drawing circle
    s2->draw();  // Output: Drawing rectangle

    delete s1;
    delete s2;
}
```

---

## Summary

| Term                 | Meaning                                     |
| -------------------- | ------------------------------------------- |
| `virtual`            | Declares a function as overridable          |
| Overriding           | Redefining a base function in derived class |
| Runtime Polymorphism | Function resolved at runtime                |
| Used with            | Base class pointers or references           |

---

##1. **Pure Virtual Functions and Abstract Classes**

### What is a Pure Virtual Function?

A **pure virtual function** is a virtual function that has **no definition in the base class** and **must** be overridden in derived classes.

### Syntax:

```cpp
class Base {
public:
    virtual void show() = 0;  // Pure virtual function
};
```

### Abstract Class:

* A class with **at least one pure virtual function**.
* You **cannot create an object** of an abstract class.

---

### Example:

```cpp
#include <iostream>
using namespace std;

class Shape {
public:
    virtual void draw() = 0;  // Pure virtual
};

class Circle : public Shape {
public:
    void draw() override {
        cout << "Drawing Circle" << endl;
    }
};

int main() {
    // Shape s;         Not allowed (abstract class)
    Circle c;
    c.draw();          // Output: Drawing Circle

    Shape* sp = new Circle();
    sp->draw();        // Output: Drawing Circle
    delete sp;
}
```

---

## 2. **Virtual Destructors**

### Why Use a Virtual Destructor?

If you delete a derived class object using a **base class pointer**, the base class destructor should be **virtual** to ensure **proper cleanup**.

---

### Without virtual destructor:

```cpp
class Base {
public:
    ~Base() { cout << "Base Destructor\n"; }
};

class Derived : public Base {
public:
    ~Derived() { cout << "Derived Destructor\n"; }
};

int main() {
    Base* b = new Derived();
    delete b;  // Only Base Destructor will be called
}
```

### With virtual destructor:

```cpp
class Base {
public:
    virtual ~Base() { cout << "Base Destructor\n"; }
};

class Derived : public Base {
public:
    ~Derived() { cout << "Derived Destructor\n"; }
};

int main() {
    Base* b = new Derived();
    delete b;  // Both destructors will be called
}
```

---

## 3. **vtable and vptr (Conceptual)**

* **vtable (virtual table)**: A hidden table created by the compiler to manage virtual functions.
* **vptr (virtual pointer)**: A hidden pointer in each object pointing to the class's vtable.
* When a virtual function is called, the vptr uses the vtable to call the correct function at runtime.

> You don’t need to manage this manually; the compiler handles it for you.

---

## Summary Table

| Concept               | Purpose                                          |
| --------------------- | ------------------------------------------------ |
| Pure Virtual Function | Forces derived classes to implement the function |
| Abstract Class        | Cannot be instantiated; used as base only        |
| Virtual Destructor    | Ensures proper cleanup of derived objects        |
| vtable / vptr         | Mechanism for runtime function dispatch          |

---

