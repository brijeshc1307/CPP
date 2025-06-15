Here's a **complete set of 25 C++ Object-Oriented Programming (OOP)** questions in **LeetCode-style**, divided into Easy, Medium, and Hard difficulty levels. Each question emphasizes core OOP concepts like encapsulation, inheritance, polymorphism, abstraction, constructors/destructors, access specifiers, virtual functions, operator overloading, etc.

---

## 🟢 **Easy (10 Questions)**

---

### **1. Design a Simple Bank Account Class**

**Problem:**

Design a `BankAccount` class with private members `accountNumber`, `balance`. Implement methods to deposit, withdraw, and get the balance.

**Class Signature:**

```cpp
class BankAccount {
public:
    BankAccount(int accountNumber, double balance);
    void deposit(double amount);
    void withdraw(double amount);
    double getBalance() const;
};
```

**Constraints:**

* Balance should never be negative.
* Deposits and withdrawals must be positive.

---

### **2. Circle Class with Area and Perimeter**

**Problem:**

Design a `Circle` class that stores the radius and has methods to compute the area and perimeter.

**Class Signature:**

```cpp
class Circle {
public:
    Circle(double radius);
    double getArea() const;
    double getPerimeter() const;
};
```

---

### **3. Student Information System**

**Problem:**

Create a `Student` class with `name`, `rollNo`, and `grade`. Use appropriate access specifiers.

**Class Signature:**

```cpp
class Student {
public:
    Student(std::string name, int rollNo, char grade);
    std::string getName() const;
    int getRollNo() const;
    char getGrade() const;
};
```

---

### **4. Constructor and Destructor Logging**

**Problem:**

Design a class `Logger` that prints messages when constructor and destructor are called.

```cpp
class Logger {
public:
    Logger();
    ~Logger();
};
```

---

### **5. Rectangle Class Using Encapsulation**

**Problem:**

Create a class `Rectangle` with private `length` and `width`. Include methods to set/get them and compute area.

```cpp
class Rectangle {
public:
    Rectangle(double length, double width);
    double getArea() const;
    void setLength(double length);
    void setWidth(double width);
};
```

---

### **6. Default and Parameterized Constructors**

**Problem:**

Create a class `Book` with default and parameterized constructors.

```cpp
class Book {
public:
    Book(); // default constructor
    Book(std::string title, std::string author);
    void display() const;
};
```

---

### **7. Constant Member Functions**

**Problem:**

Create a `Point` class with `x` and `y` and a method `distanceFromOrigin` that is a `const` method.

```cpp
class Point {
public:
    Point(double x, double y);
    double distanceFromOrigin() const;
};
```

---

### **8. Simple Class with Getter/Setter**

**Problem:**

Create a class `Car` with private members `make` and `year`. Provide getter and setter methods.

```cpp
class Car {
public:
    Car(std::string make, int year);
    std::string getMake() const;
    int getYear() const;
    void setMake(const std::string& make);
    void setYear(int year);
};
```

---

### **9. Class with Static Member**

**Problem:**

Design a class `Counter` with a static member that counts the number of objects created.

```cpp
class Counter {
public:
    Counter();
    static int getCount();
};
```

---

### **10. Simple Operator Overloading (+)**

**Problem:**

Create a `Complex` class and overload the `+` operator to add two complex numbers.

```cpp
class Complex {
public:
    Complex(double real, double imag);
    Complex operator+(const Complex& other) const;
    void display() const;
};
```

---

## 🟡 **Medium (10 Questions)**

---

### **11. Abstract Base Class for Shape**

**Problem:**

Design an abstract class `Shape` with pure virtual functions `getArea()` and `getPerimeter()`. Inherit and implement for `Circle` and `Rectangle`.

```cpp
class Shape {
public:
    virtual double getArea() const = 0;
    virtual double getPerimeter() const = 0;
    virtual ~Shape() = default;
};
```

---

### **12. Inheritance - Employee and Manager**

**Problem:**

Create a base class `Employee` and a derived class `Manager`. Add specific attributes for each and display function.

```cpp
class Employee {
public:
    Employee(std::string name, int id);
    virtual void display() const;
};

class Manager : public Employee {
public:
    Manager(std::string name, int id, int teamSize);
    void display() const override;
};
```

---

### **13. Copy Constructor**

**Problem:**

Implement a class `Person` with a custom copy constructor.

```cpp
class Person {
public:
    Person(std::string name);
    Person(const Person& other); // copy constructor
    void display() const;
};
```

---

### **14. Virtual Function for Polymorphism**

**Problem:**

Demonstrate runtime polymorphism using a base class `Animal` and derived classes `Dog` and `Cat`.

```cpp
class Animal {
public:
    virtual void speak() const;
    virtual ~Animal() = default;
};

class Dog : public Animal {
public:
    void speak() const override;
};

class Cat : public Animal {
public:
    void speak() const override;
};
```

---

### **15. Operator Overloading (==)**

**Problem:**

Overload the `==` operator for a `Point` class to compare if two points are equal.

```cpp
class Point {
public:
    Point(double x, double y);
    bool operator==(const Point& other) const;
};
```

---

### **16. Dynamic Memory Allocation in Class**

**Problem:**

Create a `String` class that manages its own memory using `new` and `delete`.

```cpp
class String {
public:
    String(const char* str);
    ~String();
    void display() const;
};
```

---

### **17. Friend Function**

**Problem:**

Create a class `Box` and a friend function `compareVolume` to compare volumes of two boxes.

```cpp
class Box {
private:
    double length, width, height;
public:
    Box(double l, double w, double h);
    friend bool compareVolume(const Box& b1, const Box& b2);
};
```

---

### **18. Private Inheritance**

**Problem:**

Demonstrate private inheritance using a `Timer` class and a `Stopwatch` class.

```cpp
class Timer {
public:
    void start();
    void stop();
};

class Stopwatch : private Timer {
public:
    void begin();
    void end();
};
```

---

### **19. Multiple Inheritance**

**Problem:**

Design a `Person`, `Worker`, and `Engineer` class using multiple inheritance.

```cpp
class Person {
protected:
    std::string name;
};

class Worker {
protected:
    int id;
};

class Engineer : public Person, public Worker {
public:
    Engineer(std::string name, int id);
    void display() const;
};
```

---

### **20. Abstract Interface for Logging**

**Problem:**

Design a `Logger` interface with a pure virtual method `log()`. Implement in `ConsoleLogger`.

```cpp
class Logger {
public:
    virtual void log(const std::string& message) = 0;
    virtual ~Logger() = default;
};

class ConsoleLogger : public Logger {
public:
    void log(const std::string& message) override;
};
```

---

## 🔴 **Hard (5 Questions)**

---

### **21. Deep Copy with Copy Constructor and Assignment Operator**

**Problem:**

Create a `SmartArray` class that implements deep copy through both copy constructor and assignment operator.

```cpp
class SmartArray {
public:
    SmartArray(int size);
    SmartArray(const SmartArray& other);
    SmartArray& operator=(const SmartArray& other);
    ~SmartArray();
    int& operator[](int index);
};
```

---

### **22. Overloading << Operator for Custom Class**

**Problem:**

Overload the `<<` operator to print a `Matrix` class.

```cpp
class Matrix {
public:
    Matrix(int rows, int cols);
    friend std::ostream& operator<<(std::ostream& out, const Matrix& m);
};
```

---

### **23. Virtual Destructor in Inheritance Chain**

**Problem:**

Create a base class `Base` and derived class `Derived`. Demonstrate proper destruction using virtual destructor.

```cpp
class Base {
public:
    virtual ~Base();
};

class Derived : public Base {
public:
    ~Derived();
};
```

---

### **24. CRTP (Curiously Recurring Template Pattern)**

**Problem:**

Use CRTP to implement a base class that logs method calls in derived class.

```cpp
template<typename Derived>
class LoggerBase {
public:
    void log(const std::string& message);
};

class MyClass : public LoggerBase<MyClass> {
public:
    void doSomething();
};
```

---

### **25. Abstract Factory Pattern with OOP**

**Problem:**

Design an abstract factory for creating `Button` and `Checkbox` widgets for `Windows` and `MacOS`.

```cpp
class Button {
public:
    virtual void render() = 0;
};

class Checkbox {
public:
    virtual void render() = 0;
};

class GUIFactory {
public:
    virtual Button
```
