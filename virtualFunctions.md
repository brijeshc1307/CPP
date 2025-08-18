## **1. What is the `virtual` keyword?**

In C++, the `virtual` keyword is used in a **base class** to tell the compiler:

> “If this function is called through a base class pointer or reference, determine which function to execute at **runtime** (dynamic dispatch), not at compile-time.”

It enables **runtime polymorphism** by creating a **virtual table (vtable)** mechanism.

---

## **2. Syntax**

```cpp
class Base {
public:
    virtual void show() {
        cout << "Base class show()" << endl;
    }
};
```
---
## **Virtual Function**
A **virtual function** in C++ is a member function in a base class that you expect to be **overridden** in derived classes.
It enables **runtime polymorphism** — meaning, the call to the function is resolved **at runtime**, not at compile-time.

It’s declared using the `virtual` keyword in the base class.

---

## **1. Why to use Virtual Function**
* To achieve dynamic polymorphism. Which is the ability to call Derived class function using Base class pointer or reference.

## **2. How to use Virtual Function**
* By declaring function as virtual in Base class and overriding that function in Derived class.
(Function signature should be same in Base and Dervied class)
* Declaring a function as virtual in Base class is enough, Derived class function need not to be declared virtual.
* Virtual functions should be accessed using pointer(*) or reference(&) of Base class type to achieve run time polymorphism.

---

## **3. Rules for `virtual` Keyword**

1. Can only be used with **member functions**.
2. Can’t be used with:

   * Static functions
   * Constructors
   * Friend functions
3. If a function is declared virtual in a base class, it **remains virtual** in all derived classes.
4. If not overridden in derived class, the **base version** is called.
5. If used with destructors, ensures correct destructor call sequence.

---

### **Why do we need Virtual Functions?**

Without virtual functions, C++ uses **static binding**:

```cpp
class Base {
public:
    void show() { cout << "Base class" << endl; }
};

class Derived : public Base {
public:
    void show() { cout << "Derived class" << endl; }
};

int main() {
    Base* b = new Derived();
    b->show(); // Output: Base class (not what we want)
}
```

Even though `b` points to a `Derived` object, it calls `Base::show()` because **binding happens at compile time**.

With virtual functions:

```cpp
class Base {
public:
    virtual void show() { cout << "Base class" << endl; }
};

class Derived : public Base {
public:
    void show() override { cout << "Derived class" << endl; }
};

int main() {
    Base* b = new Derived();
    b->show(); // Output: Derived class ✅
}
```

Now it’s **dynamic binding** — resolved at runtime using the **V-Table mechanism**.

---

## **3. How Virtual Functions Work Internally (V-Table & V-Pointer)**

When a class has a virtual function:

1. **V-Table (Virtual Table)** is created:

   * A lookup table storing function pointers for the class's virtual functions.
2. **V-Ptr (Virtual Pointer)** is added to each object:

   * Points to the class’s V-Table.

Execution:

* When a virtual function is called through a base pointer, the compiler uses the V-Pointer → V-Table → correct function address → executes it.

---

### **Rules & Properties of Virtual Functions**

* Must be a **member function** of a class.
* Can’t be **static** or **constructor**.
* Can be overridden in the derived class.
* If not overridden, base class version is called.
* You can call them through:

  * Base class pointer/reference to derived object.
* If declared in base, it remains virtual in all derived classes (even if `virtual` keyword not repeated).
* Virtual functions can be **pure virtual** (`= 0`) → makes class **abstract**.

---

### **Example: Normal Virtual Function**

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void display() {
        cout << "Display from Base" << endl;
    }
};

class Derived : public Base {
public:
    void display() override {
        cout << "Display from Derived" << endl;
    }
};

int main() {
    Base* ptr = new Derived();
    ptr->display(); // Runtime: Derived
    delete ptr;
}
```

---

### **b. Pure Virtual Functions (Abstract Classes)**

```cpp
class Shape {
public:
    virtual void draw() = 0; // Pure virtual function
};

class Circle : public Shape {
public:
    void draw() override {
        cout << "Drawing Circle" << endl;
    }
};

int main() {
    Shape* s = new Circle();
    s->draw();
    delete s;
}
```

If a class has **at least one** pure virtual function, it becomes **abstract** and cannot be instantiated.

---

### **c. Virtual Destructor**
* If we delete child class object through a pointer of parent class then it is undefined behaviour,
    if parent class doesn't have virtual destructor.
* If we fail to declare destructor as virtual in parent class then we endup having memory leak.

* "If a base class has virtual functions, **always** make its destructor virtual to ensure proper cleanup."

```cpp
class Base {
public:
    virtual ~Base() { cout << "Base destructor\n"; }
};

class Derived : public Base {
public:
    ~Derived() { cout << "Derived destructor\n"; }
};

int main() {
    Base* ptr = new Derived();
    delete ptr; 
    // Output:
    // Derived destructor
    // Base destructor
}
```

Without a virtual destructor, deleting through a base pointer will cause **undefined behavior**.

---

### **5. Performance Impact**

* Virtual functions add **one level of indirection** (V-Table lookup).
* Slightly slower than non-virtual calls.
* Object size increases due to V-Pointer.
* Negligible in most real-world cases compared to flexibility gained.

---

### **6. When to Use**

✅ Use when:

* You need **polymorphic behavior**.
* Base class defines a common interface, but implementations differ.

❌ Avoid when:

* Class is not meant to be inherited.
* Performance in tight loops is extremely critical.

---

## **7. Static vs Dynamic Binding**

* **Without `virtual`** → static binding (decided at compile-time).
* **With `virtual`** → dynamic binding (decided at runtime using vtable).

---
---


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

