## **Inheritance**

**Inheritance** allows a class (**derived class**) to **inherit** properties and behaviors (data members and member functions) from another class (**base class**).

### Purpose:

* **Code Reusability** – reuse existing code.
* **Extend Functionality** – add new features without modifying base class.
* **Achieve Polymorphism** – especially in C++ using virtual functions.

---

## Syntax:

```cpp
class Base {
    // members
};

class Derived : access_modifier Base {
    // additional members
};
```

Where `access_modifier` can be `public`, `protected`, or `private`.

---

## Types of Inheritance in C++

1. **Single Inheritance**
2. **Multilevel Inheritance**
3. **Multiple Inheritance**
4. **Hierarchical Inheritance**
5. **Hybrid Inheritance**

---

## 1. **Single Inheritance**

One derived class inherits from one base class.

### Example:

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    void eat() {
        cout << "Eating..." << endl;
    }
};

class Dog : public Animal {
public:
    void bark() {
        cout << "Barking..." << endl;
    }
};

int main() {
    Dog d;
    d.eat();   // Inherited from Animal
    d.bark();  // Defined in Dog
    return 0;
}
```

---

## 2. **Multilevel Inheritance**

A class is derived from a class which is also derived from another class.

```cpp
class Animal {
public:
    void eat() {
        cout << "Eating..." << endl;
    }
};

class Dog : public Animal {
public:
    void bark() {
        cout << "Barking..." << endl;
    }
};

class Puppy : public Dog {
public:
    void weep() {
        cout << "Weeping..." << endl;
    }
};
```

---

## 3. **Multiple Inheritance**

A class inherits from **more than one base class**.

```cpp
class A {
public:
    void displayA() {
        cout << "Class A" << endl;
    }
};

class B {
public:
    void displayB() {
        cout << "Class B" << endl;
    }
};

class C : public A, public B {
public:
    void displayC() {
        cout << "Class C" << endl;
    }
};
```

> *Note:* Be cautious with ambiguity (like two base classes having same function name). Use **scope resolution** or **virtual inheritance** to resolve it.

---

## 4. **Hierarchical Inheritance**

Multiple classes inherit from a single base class.

```cpp
class Animal {
public:
    void eat() {
        cout << "Eating..." << endl;
    }
};

class Dog : public Animal {
public:
    void bark() {
        cout << "Barking..." << endl;
    }
};

class Cat : public Animal {
public:
    void meow() {
        cout << "Meowing..." << endl;
    }
};
```

---

## 5. **Hybrid Inheritance**

Combination of two or more types of inheritance (can lead to **diamond problem**, solved using virtual base classes).

---

## Access Modifiers in Inheritance

| Base Class Access | `public` Inheritance | `protected` Inheritance | `private` Inheritance |
| ----------------- | -------------------- | ----------------------- | --------------------- |
| `public`          | public in derived    | protected in derived    | private in derived    |
| `protected`       | protected in derived | protected in derived    | private in derived    |
| `private`         | Not accessible       | Not accessible          | Not accessible        |

---

## Virtual Functions and Polymorphism (Advanced)

Used with inheritance for **runtime polymorphism**.

```cpp
class Animal {
public:
    virtual void sound() {
        cout << "Animal sound" << endl;
    }
};

class Dog : public Animal {
public:
    void sound() override {
        cout << "Bark" << endl;
    }
};

void makeSound(Animal* a) {
    a->sound();  // Calls derived class function if virtual
}
```

---

## Summary

* **Inheritance** lets a class reuse features of another class.
* It supports **code reuse**, **extensibility**, and **polymorphism**.
* **Access specifiers** and **types of inheritance** determine how members are inherited.
* Use **virtual functions** for polymorphism in inheritance hierarchies.

---

