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
---

## **7. Static vs Dynamic Binding**

* **Without `virtual`** → static binding (decided at compile-time).
* **With `virtual`** → dynamic binding (decided at runtime using vtable).

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

## 3. **vtable and vptr (Conceptual)**
In C++, **`vtable` (virtual table)** and **`vptr` (virtual pointer)** are mechanisms used to implement **runtime polymorphism** through **virtual functions**. These are essential components of the **dynamic dispatch** system in C++.

---

## Why `vtable` and `vptr` are needed

C++ supports **polymorphism**, which allows calling **derived class methods using base class pointers or references**. But this only works if those functions are declared **`virtual`** in the base class.

Example:

```cpp
class Base {
public:
    virtual void show() {
        std::cout << "Base show\n";
    }
};

class Derived : public Base {
public:
    void show() override {
        std::cout << "Derived show\n";
    }
};
```

Now:

```cpp
Base* ptr = new Derived();
ptr->show();  // Which function is called? Base::show or Derived::show?
```

Answer: `Derived::show()` — thanks to the **vtable** and **vptr**.

---

## What is `vtable`?

A **`vtable` (virtual table)** is a **compiler-generated** lookup table of function pointers. There is **one vtable per class** (if it has virtual functions).

The vtable holds addresses of the **virtual functions** that are available for a class.

### Example:

Suppose we have:

```cpp
class Base {
public:
    virtual void show() { std::cout << "Base\n"; }
    virtual void print() { std::cout << "Print Base\n"; }
};

class Derived : public Base {
public:
    void show() override { std::cout << "Derived\n"; }
};
```

Now:

* `Base`'s vtable:

  ```
  &Base::show
  &Base::print
  ```

* `Derived`'s vtable:

  ```
  &Derived::show   // overrides Base::show
  &Base::print     // inherited
  ```

So each class that has virtual functions gets its own **vtable**, with pointers to the appropriate function implementations.

---

## What is `vptr`?

Each **object of a class with virtual functions** contains a hidden pointer called a **`vptr`** (virtual pointer), which **points to the vtable of its class**.

* Set **automatically by the compiler** during object construction.
* Ensures that the correct virtual functions are called at runtime.

### Memory layout (simplified):

```cpp
class Base {
public:
    virtual void show();
};

Base obj;
```

Internally:

```
+--------+
|  vptr  |  ---> points to Base's vtable
+--------+
|  data  |
+--------+
```

Now, when a virtual function is called, like `obj.show()`, the compiler translates it roughly to:

```cpp
obj.vptr[0](/* obj as this */);
```

So it's dynamically resolved at runtime using the vptr.

---

## How polymorphism works with `vtable` and `vptr`

Example:

```cpp
Base* ptr = new Derived();
ptr->show();  // What happens?
```

Internally:

1. `Derived` object is created.
2. Its constructor sets the `vptr` to point to `Derived`'s vtable.
3. `ptr->show()` is called.
4. The compiler looks up `vptr->vtable[0]` and calls the function pointer.
5. That function pointer points to `Derived::show()` → it is called.

Thus, **runtime polymorphism is achieved**.

---

## Some Key Points

| Concept                  | Description                                                                          |
| ------------------------ | ------------------------------------------------------------------------------------ |
| **vtable**               | Table of function pointers per class with virtual functions                          |
| **vptr**                 | Pointer inside object, pointing to class’s vtable                                    |
| **Overriding**           | Derived class replaces base class function pointer in its vtable                     |
| **Virtual Destructor**   | Ensures base class vtable cleanup if deleted via base pointer                        |
| **Multiple Inheritance** | May have multiple `vptr`s per object if multiple base classes with virtual functions |
| **No virtual functions** | No vtable or vptr is generated by compiler                                           |
| **Size increase**        | Object size increases by size of pointer (usually 4/8 bytes) due to `vptr`           |

---

## Realistic Memory Example

```cpp
class A {
public:
    int x;
    virtual void foo() {}
};

class B : public A {
public:
    int y;
    void foo() override {}
};
```

Now:

```cpp
B b;
```

Memory layout (simplified):

```
+-------+------------+
| vptr  | points to B’s vtable
+-------+
| x     |
+-------+
| y     |
+-------+
```

---

## Caveats and Notes

* You **cannot see** the vtable/vptr directly in standard C++.
* It's **implementation-defined** — i.e., the exact details may vary between compilers (GCC, MSVC, Clang).
* You can often explore them using **debuggers**, or tools like **`objdump`**, or reading assembly.

---

## Summary

| Term       | Meaning                                                 |
| ---------- | ------------------------------------------------------- |
| `vtable`   | Class-level table storing virtual function addresses    |
| `vptr`     | Object-level pointer pointing to its class’s vtable     |
| Purpose    | Enable dynamic dispatch and polymorphism                |
| Created by | Compiler, automatically when virtual functions are used |
| Access     | Not directly accessible from C++ code                   |

---


