# **S.O.L.I.D Principles**

## **Overview**

The **S.O.L.I.D principles** are a set of five key guidelines for designing object-oriented software systems. These principles were:

* **First introduced** by the renowned computer scientist **Robert C. Martin**, commonly known as *Uncle Bob*.
* The **acronym "S.O.L.I.D"** was later coined by **Michael Feathers** to help remember the five principles.

These principles serve as a **foundation for writing clean, maintainable, and scalable object-oriented code**. They provide a **set of rules and best practices** that guide developers in designing class structures that are robust and easy to manage.

---

## **Why Use S.O.L.I.D?**

> **"To create understandable, readable, and testable code that many developers can collaboratively work on."**

By adhering to the S.O.L.I.D principles, teams can:

* Reduce complexity in codebases
* Enhance code readability and testability
* Make systems easier to maintain and extend
* Encourage better collaboration among developers

---

## **S – Single Responsibility Principle (SRP)**

> *A class should have only one reason to change.*

Every class should have a **single, well-defined responsibility**. This improves clarity, reduces coupling, and makes maintenance easier.


### Simple Idea:

Think of a **remote control**: one button for volume, one for channel. If one button did *everything*, it would be confusing.

### Good Example in Code:

```cpp
class Report {
public:
    std::string getText() {
        return "Report content";
    }
};

class ReportPrinter {
public:
    void print(const Report& report) {
        std::cout << report.getText() << std::endl;
    }
};
```
 **Why it's good:**

* `Report` handles report content.
* `ReportPrinter` only handles printing.
* **Each has a single responsibility.**

---

## **O – Open/Closed Principle (OCP)**

> **Code should be open for extension, but closed for modification.**

Systems should be designed so that new functionality can be **added without modifying existing code**, often achieved through abstraction and polymorphism.

### Simple Idea:

Imagine a **phone** where you can add new apps (extend) without opening the device (modifying it).

### Good Example in Code:

```cpp
class Shape {
public:
    virtual double area() = 0;
};

class Circle : public Shape {
    double radius;
public:
    Circle(double r) : radius(r) {}
    double area() override {
        return M_PI * radius * radius;
    }
};

class Square : public Shape {
    double side;
public:
    Square(double s) : side(s) {}
    double area() override {
        return side * side;
    }
};

void printArea(Shape* shape) {
    std::cout << shape->area() << std::endl;
}
```

 **Why it's good:**

* You can add new shapes (like Triangle) **without changing existing code**.

---

## **L – Liskov Substitution Principle (LSP)**

> **Subclasses should be usable wherever the base class is expected.**

 Objects of a subclass should be able to **replace objects of the superclass** without affecting the program’s behavior. This ensures that inheritance is used correctly.


### Simple Idea:

If a **bird** can fly, any specific bird (e.g., sparrow) should also fly. But a **penguin** can’t fly — so it **shouldn’t be a subclass of flying birds**.

### ❌ Bad Example:

```cpp
class Bird {
public:
    virtual void fly() {
        std::cout << "Flying" << std::endl;
    }
};

class Penguin : public Bird {
public:
    void fly() override {
        throw std::runtime_error("Penguins can't fly!");
    }
};
```

 **Problem:**
Penguin violates expectations of `Bird`. Code breaks if we assume all birds can fly.

✅ **Fix:**
Separate behavior using interfaces or base classes properly.

Split the hierarchy into **flying and non-flying birds** using interfaces or abstract base classes:

```cpp
#include <iostream>
#include <vector>
#include <memory>

// General bird interface
class IBird {
public:
    virtual void eat() = 0;
    virtual ~IBird() {}
};

// Interface for birds that can fly
class IFlyingBird : public IBird {
public:
    virtual void fly() = 0;
};

// Sparrow can fly
class Sparrow : public IFlyingBird {
public:
    void eat() override {
        std::cout << "Sparrow is eating.\n";
    }

    void fly() override {
        std::cout << "Sparrow is flying.\n";
    }
};

// Penguin cannot fly
class Penguin : public IBird {
public:
    void eat() override {
        std::cout << "Penguin is eating.\n";
    }

    // No fly() method — avoids violating LSP
};
```

---

### Usage Example:

```cpp
void makeBirdsFly(std::vector<IFlyingBird*> birds) {
    for (auto bird : birds) {
        bird->fly(); // Safe: only flying birds are passed
    }
}

int main() {
    Sparrow sparrow;
    Penguin penguin;

    // Only pass flying birds to makeBirdsFly
    std::vector<IFlyingBird*> flyingBirds = { &sparrow };
    makeBirdsFly(flyingBirds);

    // You can still use penguin elsewhere
    penguin.eat();

    return 0;
}
```

---

### Why This Fix Works:

* Now, only birds that **can actually fly** implement `IFlyingBird`.
* `Penguin` doesn’t pretend to fly, so no runtime errors or surprises.
* This design **respects LSP** by keeping behavior predictable and correct.

---

## **I – Interface Segregation Principle (ISP)**

> **Don’t force a class to implement things it doesn’t use.**

Favor **many small, specific interfaces** over one large, general-purpose interface. This helps keep implementations clean and focused.

###  Simple Idea:

Don’t make a **printer** class also handle scanning and faxing if it doesn’t need to.

### ❌ Bad Example:

```cpp
class Machine {
public:
    virtual void print() = 0;
    virtual void scan() = 0;
    virtual void fax() = 0;
};

class OldPrinter : public Machine {
public:
    void print() override {
        std::cout << "Printing..." << std::endl;
    }

    void scan() override {} // Useless
    void fax() override {}  // Useless
};
```

✅ Good Design:

```cpp
class IPrinter {
public:
    virtual void print() = 0;
};

class IScanner {
public:
    virtual void scan() = 0;
};

class OldPrinter : public IPrinter {
public:
    void print() override {
        std::cout << "Printing..." << std::endl;
    }
};
```

---

## **D – Dependency Inversion Principle (DIP)**

> **High-level modules should depend on abstractions, not concrete classes.**

Code should depend on **interfaces or abstract classes**, not on concrete implementations. This **reduces tight coupling** and increases flexibility.

### Simple Idea:

If you're making tea, you don't care which **brand of kettle** boils the water — just that it does the job.

### ❌ Bad Example:

```cpp
class LightBulb {
public:
    void turnOn() { std::cout << "Light ON\n"; }
};

class Switch {
    LightBulb bulb;
public:
    void operate() {
        bulb.turnOn();
    }
};
```

🚫 **Problem:** `Switch` is tightly coupled to `LightBulb`.

✅ Good Design:

```cpp
class ISwitchable {
public:
    virtual void turnOn() = 0;
};

class LightBulb : public ISwitchable {
public:
    void turnOn() override {
        std::cout << "Light ON\n";
    }
};

class Switch {
    ISwitchable* device;
public:
    Switch(ISwitchable* d) : device(d) {}
    void operate() {
        device->turnOn();
    }
};
```

---

##  Summary Table:

| Principle | Key Idea                           | Simple Example                           |
| --------- | ---------------------------------- | ---------------------------------------- |
| SRP       | One class = one job                | Separate `Report` and `Printer`          |
| OCP       | Extend without changing            | Add new `Shape` classes                  |
| LSP       | Subtypes work like base types      | Don’t make `Penguin` a flying `Bird`     |
| ISP       | Don’t force unnecessary methods    | Split `IMachine` into smaller interfaces |
| DIP       | Depend on interfaces, not concrete | `Switch` uses `ISwitchable`              |

---


