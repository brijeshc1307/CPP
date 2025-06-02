
## **Polymorphism**

**Polymorphism** means **"many forms."** It allows objects of **different classes** to be treated **as objects of a common base class**, especially when using **inheritance**.
Real life Example: A man at the same time is a father, a husband, and an employee.
It enables:

* **Same interface, different behavior**
* **Code flexibility and reusability**

---

## Types of Polymorphism in C++:

| Type                          | Description                                 | Achieved Using                             |
| ----------------------------- | ------------------------------------------- | ------------------------------------------ |
| **Compile-Time Polymorphism** | Resolved at compile time                    | Function Overloading, Operator Overloading |
| **Run-Time Polymorphism**     | Resolved at runtime using virtual functions | Virtual Functions + Inheritance            |

---

## 1. **Compile-Time Polymorphism (Static Polymorphism)**

### a) Function Overloading

```cpp
#include <iostream>
using namespace std;

class Print {
public:
    void show(int i) {
        cout << "Integer: " << i << endl;
    }

    void show(string s) {
        cout << "String: " << s << endl;
    }
};

int main() {
    Print p;
    p.show(10);
    p.show("Hello");
    return 0;
}
```

---

### b) Operator Overloading

```cpp
#include <iostream>
using namespace std;

class Complex {
public:
    int real, imag;

    Complex(int r, int i) : real(r), imag(i) {}

    // Overload '+' operator
    Complex operator+(const Complex& obj) {
        return Complex(real + obj.real, imag + obj.imag);
    }

    void display() {
        cout << real << " + " << imag << "i" << endl;
    }
};

int main() {
    Complex c1(2, 3), c2(4, 5);
    Complex c3 = c1 + c2;
    c3.display();  // Output: 6 + 8i
    return 0;
}
```

---

## 2. **Run-Time Polymorphism (Dynamic polymorphism or Late Binding)**

### Using **Virtual Functions** and **Inheritance**

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    virtual void sound() {
        cout << "Animal makes a sound" << endl;
    }
};

class Dog : public Animal {
public:
    void sound() override {
        cout << "Dog barks" << endl;
    }
};

class Cat : public Animal {
public:
    void sound() override {
        cout << "Cat meows" << endl;
    }
};

void makeSound(Animal* a) {
    a->sound();  // Calls the appropriate overridden function
}

int main() {
    Dog d;
    Cat c;

    makeSound(&d);  // Output: Dog barks
    makeSound(&c);  // Output: Cat meows

    return 0;
}
```

---

## Why Use Run-Time Polymorphism?

* It allows **writing generic code**.
* You can have **a single interface (base class)**, and different behaviors based on object type.

---

## Real-Life Example of Polymorphism

### Scenario: **Payment System**

All payments share the same interface (`processPayment()`), but behave differently for each payment type.

### Code:

```cpp
#include <iostream>
using namespace std;

class Payment {
public:
    virtual void processPayment() {
        cout << "Processing generic payment..." << endl;
    }
};

class CreditCard : public Payment {
public:
    void processPayment() override {
        cout << "Processing credit card payment..." << endl;
    }
};

class PayPal : public Payment {
public:
    void processPayment() override {
        cout << "Processing PayPal payment..." << endl;
    }
};

class UPI : public Payment {
public:
    void processPayment() override {
        cout << "Processing UPI payment..." << endl;
    }
};

void makePayment(Payment* p) {
    p->processPayment();
}

int main() {
    CreditCard cc;
    PayPal pp;
    UPI upi;

    makePayment(&cc);   // Output: Processing credit card payment...
    makePayment(&pp);   // Output: Processing PayPal payment...
    makePayment(&upi);  // Output: Processing UPI payment...

    return 0;
}
```

---

## Summary

| Type         | Binding Time | How          | Example               |
| ------------ | ------------ | ------------ | --------------------- |
| Compile-Time | Compile Time | Overloading  | `void add(int, int)`  |
| Run-Time     | Runtime      | Virtual Func | `virtual void draw()` |

### Real-world takeaway:

* **Polymorphism = One Interface, Many Implementations.**
* It makes your code **scalable**, **flexible**, and **easy to extend**.

---
