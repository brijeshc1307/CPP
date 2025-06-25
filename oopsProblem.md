## 🟢 Easy – C++ OOP Questions

### **1. Design a Basic Point Class**

*Concepts: Encapsulation, Constructors, Getters/Setters*

**Problem Statement:**
Implement a class `Point` that represents a 2D point. The class should store `x` and `y` coordinates as private members. Provide a constructor to initialize the coordinates and public getter/setter methods to access and modify them.

**Class Signature:**

```cpp
class Point {
public:
    Point(int x_coord, int y_coord);
    int getX() const;
    int getY() const;
    void setX(int new_x);
    void setY(int new_y);
};
```

**Constraints:**

* `x` and `y` are integers in the range \[-1000, 1000].

**Example:**

```cpp
Point p(10, 20);
p.setX(15);
// p.getX() == 15
// p.getY() == 20
```

---
Solution:
```cpp
#include <iostream>
using namespace std;

class Point {
private:
    int x, y;

public:
    // Constructor
    Point(int x_coord, int y_coord) {
        x = x_coord;
        y = y_coord;
    }

    // Getters
    int getX() const {
        return x;
    }

    int getY() const {
        return y;
    }

    // Setters
    void setX(int new_x) {
        x = new_x;
    }

    void setY(int new_y) {
        y = new_y;
    }
};

int main() {
    Point p(5, 7);
    cout << "Initial point: (" << p.getX() << ", " << p.getY() << ")\n";

    p.setX(10);
    p.setY(15);
    cout << "Updated point: (" << p.getX() << ", " << p.getY() << ")\n";

    return 0;
}
````
Output:
```
Initial point: (5, 7)
Updated point: (10, 15)
```


### **2. Implement a Counter Class**

*Concepts: Static Members, Constructors, Destructors*

**Problem Statement:**
Create a `Counter` class that tracks the number of active instances. Increment a static counter in the constructor and decrement it in the destructor. Provide a static method to retrieve the current count.

**Class Signature:**

```cpp
class Counter {
public:
    Counter();
    ~Counter();
    static int getActiveCount();
};
```

**Constraints:**

* Destructors are correctly called when objects go out of scope.

**Example:**

```cpp
// Counter::getActiveCount() == 0
Counter c1; // == 1
Counter c2; // == 2
{
    Counter c3; // == 3
} // c3 destroyed => == 2
```
Solution:
```cpp
#include <iostream>
using namespace std;

class Counter {
private:
    static int activeCount;  // Static variable to track active instances

public:
    Counter() {
        ++activeCount;  // Increment on construction
    }

    ~Counter() {
        --activeCount;  // Decrement on destruction
    }

    static int getActiveCount() {
        return activeCount;
    }
};

// Initialize static member
int Counter::activeCount = 0;

int main() {
    cout << "Active: " << Counter::getActiveCount() << endl;  // 0

    Counter c1;
    cout << "Active: " << Counter::getActiveCount() << endl;  // 1

    {
        Counter c2, c3;
        cout << "Active: " << Counter::getActiveCount() << endl;  // c1 1+ c2 1+ c3 1 =1+1+1=3
    } // c2 and c3 go out of scope and are destroyed

    cout << "Active: " << Counter::getActiveCount() << endl;  // 3 -1 -1 =1

    return 0;
}

```
Output:
```
Active: 0
Active: 1
Active: 3
Active: 1
```
---

### **3. Simple Rectangle Inheritance**

*Concepts: Inheritance, Protected Members*

**Problem Statement:**
Create a base class `Shape` with protected members `width` and `height`. Then define a derived class `Rectangle` that uses these members and implements a method to compute area.

**Class Signature:**

```cpp
class Shape {
protected:
    int width;
    int height;
public:
    Shape(int w, int h);
};

class Rectangle : public Shape {
public:
    Rectangle(int w, int h);
    int getArea() const;
};
```

**Constraints:**

* `width`, `height` ∈ \[1, 1000]

**Example:**

```cpp
Rectangle r(5, 10);
// r.getArea() == 50
```
Solution:
```cpp
#include <iostream>
using namespace std;

// Base class
class Shape {
protected:
    int width;
    int height;

public:
    Shape(int w, int h) : width(w), height(h) {}  // Constructor definition
};

// Derived class
class Rectangle : public Shape {
public:
    Rectangle(int w, int h) : Shape(w, h) {}  // Constructor calling base class constructor

    int getArea() const {
        return width * height;  // Accessing protected members from base class
    }
};

int main() {
    Rectangle rect(10, 5);
    cout << "Area of rectangle: " << rect.getArea() << endl;

    return 0;
}
```
Output
```
Area of rectangle: 50
```
---

### **4. Overload Addition Operator for Point**

*Concepts: Operator Overloading*

**Problem Statement:**
Extend the `Point` class to support `+` operator. The addition should produce a new `Point` where x and y are the sum of the operands' respective coordinates.

**Class Signature:**

```cpp
class Point {
    // Existing members...
public:
    Point operator+(const Point& other) const;
};
```

**Constraints:**

* Coordinate addition results are within valid integer limits.

**Example:**

```cpp
Point p1(1, 2), p2(3, 4);
Point p3 = p1 + p2;
// p3.getX() == 4
// p3.getY() == 6
```
Solution:
```cpp
#include <iostream>
using namespace std;

class Point {
private:
    int x, y;

public:
    // Constructor
    Point(int xVal = 0, int yVal = 0) : x(xVal), y(yVal) {}

    // Getter methods
    int getX() const { return x; }
    int getY() const { return y; }

    // Overload + operator
    Point operator+(const Point& other) const {
        return Point(x + other.x, y + other.y);
    }
};

int main() {
    Point p1(1, 2);
    Point p2(3, 4);

    Point p3 = p1 + p2;

    cout << "p3.x = " << p3.getX() << ", p3.y = " << p3.getY() << endl;

    return 0;
}
```
Output
```
p3.x = 4, p3.y = 6
```
---

### **5. Book Class with const Method**

*Concepts: Const Correctness*

**Problem Statement:**
Design a class `Book` that contains private `title` and `author`. Provide a constructor and constant getter methods.

**Class Signature:**

```cpp
#include <string>

class Book {
private:
    std::string title;
    std::string author;
public:
    Book(const std::string& title, const std::string& author);
    std::string getTitle() const;
    std::string getAuthor() const;
};
```

**Constraints:**

* `title` and `author` length ∈ \[1, 50]

**Example:**

```cpp
Book b("The Great Gatsby", "F. Scott Fitzgerald");
// b.getTitle() == "The Great Gatsby"
```
Solution
```cpp
#include <iostream>
#include <string>
using namespace std;

class Book {
private:
    string title;
    string author;

public:
    // Constructor
    Book(const string& title, const string& author) {
        if (title.length() < 1 || title.length() > 50 || author.length() < 1 || author.length() > 50) {
            throw invalid_argument("Title and author must be between 1 and 50 characters.");
        }
        this->title = title;
        this->author = author;
    }

    // Constant getter methods
    string getTitle() const {
        return title;
    }

    string getAuthor() const {
        return author;
    }
};

int main() {
    try {
        Book b("The Great Gatsby", "F. Scott Fitzgerald");
        cout << "Title: " << b.getTitle() << endl;
        cout << "Author: " << b.getAuthor() << endl;
    } catch (const exception& e) {
        cerr << "Error: " << e.what() << endl;
    }

    return 0;
}
```
Output
```
Title: The Great Gatsby
Author: F. Scott Fitzgerald
```

---

### **6. Circle Class with Area Calculation**

*Concepts: Encapsulation, Simple Calculation*

**Problem Statement:**
Create a `Circle` class with a private `radius` member. Provide a constructor and a method to return the area.

**Class Signature:**

```cpp
#include <cmath>

class Circle {
private:
    double radius;
public:
    Circle(double r);
    double getArea() const;
};
```

**Constraints:**

* `radius` ∈ \[0.1, 1000.0]

**Example:**

```cpp
Circle c(5.0);
// c.getArea() ≈ 78.5398
```
Solution
```cpp
#include <iostream>
#include <cmath>
using namespace std;

class Circle {
private:
    double radius;

public:
    // Constructor with basic constraint check
    Circle(double r) {
        if (r >= 0.1 && r <= 1000.0) {
            radius = r;
        } else {
            radius = 0.1;  // fallback/default value if invalid input
            cout << "Invalid radius. Setting to minimum allowed value (0.1)." << endl;
        }
    }

    // Method to return area
    double getArea() const {
        return M_PI * radius * radius;
    }
};

int main() {
    Circle c(5.0);
    cout << "Area of circle: " << c.getArea() << endl;

    Circle c2(2000.0);  // Invalid input, fallback will be used
    cout << "Area of circle with fallback radius: " << c2.getArea() << endl;

    return 0;
}

```
Output
```
Area of circle: 78.5398
Invalid radius. Setting to minimum allowed value (0.1).
Area of circle with fallback radius: 0.0314159
```
---

### **7. Dog and Animal Classes (Overriding)**

*Concepts: Method Overriding (without virtual)*

**Problem Statement:**
Define a base class `Animal` with method `makeSound()`. Derive a class `Dog` that overrides the method to provide specific output. Do not use `virtual`.

**Class Signature:**

```cpp
#include <iostream>

class Animal {
public:
    void makeSound();
};

class Dog : public Animal {
public:
    void makeSound(); // Overrides Animal’s makeSound
};
```

**Constraints:**

* Focus on method hiding due to lack of virtual dispatch.

**Example:**

```cpp
Animal a;
Dog d;
// a.makeSound() prints "Generic animal sound."
// d.makeSound() prints "Woof!"
```
Solution
```cpp

#include <iostream>
#include <cmath>
using namespace std;

class Animal {
public:
    void makeSound() {
        cout << "Generic animal sound." << endl;
    }
};

class Dog : public Animal {
public:
    void makeSound() {  // Hides Animal's makeSound
        cout << "Woof!" << endl;
    }
};

int main() {
    Animal a;
    Dog d;

    a.makeSound();  // Output: Generic animal sound.
    d.makeSound();  // Output: Woof!

    Animal* ptr = &d;
    ptr->makeSound();  // Output: Generic animal sound. (Because no virtual function is used)

    return 0;
}

```
Output
```
Generic animal sound.
Woof!
Generic animal sound.
```

---

### **8. Wallet Class with Balance Handling**

*Concepts: Aggregation, Data Validation*

**Problem Statement:**
Design a `Wallet` class to handle a monetary balance. Implement deposit and withdrawal functions, ensuring withdrawals are allowed only if sufficient funds are available.

**Class Signature:**

```cpp
class Wallet {
private:
    double balance;
public:
    Wallet(double initial_balance = 0.0);
    void deposit(double amount);
    bool withdraw(double amount);
    double getBalance() const;
};
```

**Constraints:**

* `initial_balance`, `amount` ∈ \[0.0, 10000.0]

**Example:**

```cpp
Wallet w(100.0);
w.deposit(50.0);      // balance = 150.0
w.withdraw(75.0);     // success, balance = 75.0
w.withdraw(100.0);    // fails, balance = 75.0
```
Solution
```cpp
#include <iostream>
using namespace std;

class Wallet {
private:
    double balance;

public:
    // Constructor with initial balance check
    Wallet(double initial_balance = 0.0) {
        if (initial_balance >= 0.0 && initial_balance <= 10000.0)
            balance = initial_balance;
        else {
            balance = 0.0;
            cout << "Invalid initial balance. Setting to 0.0" << endl;
        }
    }

    // Deposit method with constraint check
    void deposit(double amount) {
        if (amount >= 0.0 && amount <= 10000.0)
            balance += amount;
        else
            cout << "Invalid deposit amount. Must be between 0.0 and 10000.0" << endl;
    }

    // Withdraw method with fund and constraint check
    bool withdraw(double amount) {
        if (amount < 0.0 || amount > 10000.0) {
            cout << "Invalid withdrawal amount. Must be between 0.0 and 10000.0" << endl;
            return false;
        }

        if (amount <= balance) {
            balance -= amount;
            return true;
        } else {
            cout << "Withdrawal failed: insufficient funds." << endl;
            return false;
        }
    }

    // Getter for balance
    double getBalance() const {
        return balance;
    }
};

int main() {
    Wallet w(100.0);
    w.deposit(50.0);     // balance = 150.0
    cout << "Balance: " << w.getBalance() << endl;

    bool success1 = w.withdraw(75.0);  // success
    cout << "Withdraw 75.0: " << (success1 ? "Success" : "Fail") << endl;
    cout << "Balance: " << w.getBalance() << endl;

    bool success2 = w.withdraw(100.0); // fail
    cout << "Withdraw 100.0: " << (success2 ? "Success" : "Fail") << endl;
    cout << "Balance: " << w.getBalance() << endl;

    return 0;
}

```
```
Balance: 150
Withdraw 75.0: Success
Balance: 75
Withdrawal failed: insufficient funds.
Withdraw 100.0: Fail
Balance: 75
```
---

### **9. Vector2D Class with Copy Constructor**

*Concepts: Constructors, Copy Semantics*

**Problem Statement:**
Implement a `Vector2D` class with a default constructor, a parameterized constructor, and a copy constructor.

**Class Signature:**

```cpp
class Vector2D {
private:
    double x_comp;
    double y_comp;
public:
    Vector2D();
    Vector2D(double x, double y);
    Vector2D(const Vector2D& other);

    double getX() const;
    double getY() const;
};
```

**Constraints:**

* `x`, `y` are double-precision numbers.

**Example:**

```cpp
Vector2D v1;              // x=0, y=0
Vector2D v2(3.0, 4.0);    // x=3, y=4
Vector2D v3 = v2;         // copy constructor
```
Solution
```cpp
#include <iostream>
using namespace std;

class Vector2D {
private:
    double x_comp;
    double y_comp;

public:
    // Default constructor
    Vector2D() : x_comp(0.0), y_comp(0.0) {}

    // Parameterized constructor
    Vector2D(double x, double y) : x_comp(x), y_comp(y) {}

    // Copy constructor
    Vector2D(const Vector2D& other) : x_comp(other.x_comp), y_comp(other.y_comp) {}

    // Getter for x component
    double getX() const {
        return x_comp;
    }

    // Getter for y component
    double getY() const {
        return y_comp;
    }
};

int main() {
    Vector2D v1;                  // Default constructor
    Vector2D v2(3.0, 4.0);        // Parameterized constructor
    Vector2D v3 = v2;             // Copy constructor

    cout << "v1: (" << v1.getX() << ", " << v1.getY() << ")" << endl;
    cout << "v2: (" << v2.getX() << ", " << v2.getY() << ")" << endl;
    cout << "v3: (" << v3.getX() << ", " << v3.getY() << ")" << endl;

    return 0;
}

```
Output
```
v1: (0, 0)
v2: (3, 4)
v3: (3, 4)
```

---

### **10. Check if a Custom List is Empty**

*Concepts: Basic Class Design, Aggregation*

**Problem Statement:**
Create a class `MyList` that can store a small number of integers. Implement `add(int)` and `isEmpty()` methods.

**Class Signature:**

```cpp
#include <vector>

class MyList {
private:
    std::vector<int> data;
public:
    MyList();
    void add(int value);
    bool isEmpty() const;
};
```

**Constraints:**

* Store up to 10 integers internally.

**Example:**

```cpp
MyList list;
list.isEmpty(); // true
list.add(42);
list.isEmpty(); // false
```
Solution
```cpp
#include <iostream>
#include <vector>
using namespace std;

class MyList {
private:
    std::vector<int> data;

public:
    // Default constructor
    MyList() {}

    // Add an integer if the size limit is not reached
    void add(int value) {
        if (data.size() < 10) {
            data.push_back(value);
        } else {
            cout << "List is full. Cannot add more than 10 elements." << endl;
        }
    }

    // Check if the list is empty
    bool isEmpty() const {
        return data.empty();
    }
};

int main() {
    MyList list;

    cout << "Is list empty? " << (list.isEmpty() ? "Yes" : "No") << endl;  // true

    list.add(42);
    cout << "Is list empty? " << (list.isEmpty() ? "Yes" : "No") << endl;  // false

    return 0;
}

```
Output
```
Is list empty? Yes
Is list empty? No
```
---

### **11. Design a Simple Bank Account Class**

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


Solution
```cpp
#include <iostream>
using namespace std;

class BankAccount {
private:
    int accountNumber;
    double balance;

public:
    BankAccount(int accountNumber, double balance) {
        this->accountNumber = accountNumber;
        // Ensure initial balance is not negative
        this->balance = (balance >= 0) ? balance : 0;
    }

    void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        } else {
            cout << "Deposit amount must be positive!" << endl;
        }
    }

    void withdraw(double amount) {
        if (amount <= 0) {
            cout << "Withdraw amount must be positive!" << endl;
        } else if (amount > balance) {
            cout << "Insufficient balance!" << endl;
        } else {
            balance -= amount;
        }
    }

    double getBalance() const {
        return balance;
    }
};

int main() {
    BankAccount obj(100, 200);
    obj.deposit(300);
    cout << "After deposit, balance = " << obj.getBalance() << endl;

    obj.withdraw(50);
    cout << "After withdrawal, balance = " << obj.getBalance() << endl;

    // Try invalid operations
    obj.deposit(-10);    // Should print warning
    obj.withdraw(1000);  // Should print insufficient balance
    obj.withdraw(-30);   // Should print warning

    return 0;
}
```
Output
```
After deposit, balance = 500
After withdrawal, balance = 450
Deposit amount must be positive!
Insufficient balance!
Withdraw amount must be positive!
```

---

### **12. Circle Class with Area and Perimeter**

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
Solution
```cpp
#include <iostream>
#include <cmath>  // for M_PI
using namespace std;

class Circle {
private:
    double radius;

public:
    Circle(double radius) {
        if (radius >= 0)
            this->radius = radius;
        else {
            cout << "Invalid radius! Setting to 0." << endl;
            this->radius = 0;
        }
    }

    double getArea() const {
        return M_PI * radius * radius;
    }

    double getPerimeter() const {
        return 2 * M_PI * radius;
    }
};

int main() {
    Circle obj(25);
    cout << "Area of Circle = " << obj.getArea() << endl;
    cout << "Perimeter of Circle = " << obj.getPerimeter() << endl;

    return 0;
}

```
Output
```
Area of Circle = 1963.5
Perimeter of Circle = 157.08
```

---

### **13. Student Information System**

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
Solution
```cpp
#include <iostream>
using namespace std;

class Student {
private: 
    string name;
    int rollNo;
    char grade;

public:
    Student(const string& name, int rollNo, char grade) {
        this->name = name;
        this->rollNo = rollNo;
        this->grade = grade;
    }

    string getName() const {
        return name;
    }

    int getRollNo() const {
        return rollNo;
    }

    char getGrade() const {
        return grade;
    }
};

int main() {
    Student obj("Brijesh", 16, 'A');
    cout << "Name: " << obj.getName() << endl;
    cout << "Roll No: " << obj.getRollNo() << endl;
    cout << "Grade: " << obj.getGrade() << endl;

    return 0;
}

```
Output
```
Name: Brijesh
Roll No: 16
Grade: A
```
---

### **14. Constructor and Destructor Logging**

**Problem:**

Design a class `Logger` that prints messages when constructor and destructor are called.

```cpp
class Logger {
public:
    Logger();
    ~Logger();
};
```
Solution
```cpp
#include <iostream>
using namespace std;

class Logger {
public:
    Logger(){
        cout<<"Constructor called"<<endl;
    }
    ~Logger(){
        cout<<"Destructor called"<<endl;
    }
};

int main() {
    Logger obj;
    return 0;
}

```
Output
```
Constructor called
Destructor called
```
Solution updated only main function, To see the destructor call more clearly (especially in more complex programs), we can add a block scope
```cpp
int main() {
    {
        Logger obj;
    } // Destructor called here
    cout << "Exited block" << endl;
    return 0;
}
````
Output
```
Constructor called
Destructor called
Exited block
```

---

### **15. Rectangle Class Using Encapsulation**

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
Solution
```cpp
#include <iostream>
using namespace std;

class Rectangle {
private:
    double length;
    double width;

public:
    Rectangle(double length, double width) {
        // Use setters for validation
        setLength(length);
        setWidth(width);
    }

    double getArea() const {
        return length * width;
    }

    void setLength(double length) {
        if (length >= 0)
            this->length = length;
        else
            cout << "Length must be non-negative!" << endl;
    }

    void setWidth(double width) {
        if (width >= 0)
            this->width = width;
        else
            cout << "Width must be non-negative!" << endl;
    }

    double getLength() const {
        return length;
    }

    double getWidth() const {
        return width;
    }
};

int main() {
    Rectangle obj(20, 50);
    cout << "Initial area (valid values): " << obj.getArea() << endl;

    Rectangle obj1(-20, 50); // Length invalid
    cout << "Area with invalid length: " << obj1.getArea() << endl;

    obj.setLength(10);
    cout << "After setting length to 10, area: " << obj.getArea() << endl;

    obj.setWidth(20);
    cout << "After setting width to 20, area: " << obj.getArea() << endl;

    obj.setLength(-5); // Should be rejected
    obj.setWidth(-10); // Should be rejected

    return 0;
}

```
Output
```
Initial area (valid values): 1000
Length must be non-negative!
Area with invalid length: 0
After setting length to 10, area: 500
After setting width to 20, area: 200
Length must be non-negative!
Width must be non-negative!
```
---

### **16. Default and Parameterized Constructors**

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
Solution
```cpp
#include <iostream>
using namespace std;

class Book {
private:
    string title;
    string author;

public:
    // Default constructor
    Book() {
        title = "Unknown";
        author = "Unknown";
        cout << "Default constructor called" << endl;
    }

    // Parameterized constructor
    Book(string title, string author) {
        this->title = title;
        this->author = author;
    }

    void display() const {
        cout << "Title of Book: " << title << ", Author of Book: " << author << endl;
    }
};

int main() {
    Book obj;             // default constructor called
    obj.display();        // should now show "Unknown"
    
    Book obj1("CPP", "Brijesh");  // parameterized constructor called
    obj1.display();      

    return 0;
}

```
Output
```
Default constructor called
Title of Book: Unknown, Author of Book: Unknown
Title of Book: CPP, Author of Book: Brijesh
```
---

### **17. Constant Member Functions**

**Problem:**

Create a `Point` class with `x` and `y` and a method `distanceFromOrigin` that is a `const` method.

```cpp
class Point {
public:
    Point(double x, double y);
    double distanceFromOrigin() const;
};
```
Solution
```cpp
#include <iostream>
#include <cmath>
using namespace std;

class Point {
private:
    double x;
    double y;

public:
    Point(double x, double y) {
        this->x = x;
        this->y = y;
    }

    double distanceFromOrigin() const {
        return sqrt(x * x + y * y);
    }
};

int main() {
    Point obj(10, 20);
    cout << "Distance from origin: " << obj.distanceFromOrigin() << endl;
    return 0;
}

```
Output
```
Distance from origin: 22.3607
```
---

### **18. Simple Class with Getter/Setter**

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
Solution
```cpp
#include <iostream>
using namespace std;

class Car {
private:
    string make;
    int year;

public:
    // Constructor
    Car(string make, int year) {
        this->make = make;
        this->year = year;
    }

    // Getter for make
    string getMake() const {
        return make;
    }

    // Getter for year
    int getYear() const {
        return year;
    }

    // Setter for make
    void setMake(const string& make) {
        this->make = make;
    }

    // Setter for year
    void setYear(int year) {
        this->year = year;
    }
};

int main() {
    // Creating object using constructor
    Car myCar("Toyota", 2015);

    // Display initial details
    cout << "Make: " << myCar.getMake() << ", Year: " << myCar.getYear() << endl;

    // Update car details
    myCar.setMake("Honda");
    myCar.setYear(2020);

    // Display updated details
    cout << "Updated Make: " << myCar.getMake() << ", Updated Year: " << myCar.getYear() << endl;

    return 0;
}

```
Output
```
Make: Toyota, Year: 2015
Updated Make: Honda, Updated Year: 2020
```
---

### **19. Class with Static Member**

**Problem:**

Design a class `Counter` with a static member that counts the number of objects created.

```cpp
class Counter {
public:
    Counter();
    static int getCount();
};
```
Solution
```cpp
#include <iostream>
using namespace std;

class Counter {
private:
    static int count;  // Static member to hold number of objects

public:
    // Constructor increments count whenever an object is created
    Counter() {
        count++;
    }

    // Static method to access the count
    static int getCount() {
        return count;
    }
};

// Initialize the static member outside the class
int Counter::count = 0;

int main() {
    Counter c1;
    Counter c2;
    Counter c3;

    cout << "Number of Counter objects created: " << Counter::getCount() << endl;

    return 0;
}

```
Output
```
Number of Counter objects created: 3
```
---

### **20. Simple Operator Overloading (+)**

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
Solution
```cpp
#include <iostream>
using namespace std;

class Complex {
private:
    double real;
    double imag;

public:
    // Constructor
    Complex(double real, double imag) {
        this->real = real;
        this->imag = imag;
    }

    // Overload + operator
    Complex operator+(const Complex& other) const {
        return Complex(real + other.real, imag + other.imag);
    }

    // Display the complex number
    void display() const {
        cout << real;
        if (imag >= 0)
            cout << " + " << imag << "i";
        else
            cout << " - " << -imag << "i";
        cout << endl;
    }
};

int main() {
    Complex c1(3.5, 2.0);
    Complex c2(1.5, 4.5);

    Complex c3 = c1 + c2;  // Uses overloaded + operator

    cout << "First Complex number: ";
    c1.display();

    cout << "Second Complex number: ";
    c2.display();

    cout << "Sum: ";
    c3.display();

    return 0;
}

```
Output
```
First Complex number: 3.5 + 2i
Second Complex number: 1.5 + 4.5i
Sum: 5 + 6.5i
```
---

## 🟡 Medium – C++ OOP Questions

---

### **21. Shape Hierarchy with Polymorphism**

**Concepts:** Virtual Functions, Abstract Class, Polymorphism

**Problem Statement:**
Design an abstract base class `Shape` with a pure virtual function `getArea()`. Derive two concrete classes: `Circle` and `Rectangle`. Each class should implement `getArea()` using the appropriate formula. Demonstrate runtime polymorphism using a `std::vector<Shape*>`.

**Class Signature:**

```cpp
#include <cmath>

class Shape {
public:
    virtual double getArea() const = 0; // Pure virtual function
    virtual ~Shape() {} // Virtual destructor
};

class Circle : public Shape {
private:
    double radius;
public:
    Circle(double r);
    double getArea() const override;
};

class Rectangle : public Shape {
private:
    double width;
    double height;
public:
    Rectangle(double w, double h);
    double getArea() const override;
};
```

**Constraints:**

* `radius`, `width`, `height` are positive doubles.

**Example:**

```cpp
std::vector<Shape*> shapes;
shapes.push_back(new Circle(5.0));
shapes.push_back(new Rectangle(4.0, 6.0));
for (Shape* s : shapes) {
    std::cout << s->getArea() << std::endl;
}
// Don't forget to delete allocated memory.
```

---

### **22. Custom Exception for BankAccount**

**Concepts:** Exception Handling, Custom Exceptions

**Problem Statement:**
Create a `BankAccount` class with a `withdraw` method. If the withdrawal amount exceeds the available balance, throw a custom `InsufficientFundsException`.

**Class Signature:**

```cpp
#include <string>
#include <stdexcept>

class InsufficientFundsException : public std::runtime_error {
public:
    InsufficientFundsException(const std::string& msg);
};

class BankAccount {
private:
    double balance;
    std::string accountNumber;
public:
    BankAccount(const std::string& accNum, double initial_balance);
    void withdraw(double amount);
    double getBalance() const;
};
```

**Constraints:**

* `balance`, `amount` ≥ 0

**Example:**

```cpp
BankAccount acc("12345", 100.0);
try {
    acc.withdraw(150.0);
} catch (const InsufficientFundsException& e) {
    std::cout << e.what() << std::endl;
}
```

---

### **23. Overload Output Stream Operator for Point**

**Concepts:** Operator Overloading, Friend Functions

**Problem Statement:**
Extend the `Point` class to support output streaming by overloading the `<<` operator. Format the output as `(x, y)`.

**Class Signature:**

```cpp
#include <iostream>

class Point {
private:
    int x_coord;
    int y_coord;
public:
    Point(int x = 0, int y = 0);
    friend std::ostream& operator<<(std::ostream& os, const Point& p);
};
```

**Example:**

```cpp
Point p(10, 20);
std::cout << p; // Output: (10, 20)
```

---

### **24. Deep vs. Shallow Copy in Dynamic Array**

**Concepts:** Copy Constructor, Assignment Operator, Deep Copy

**Problem Statement:**
Implement a `DynamicArray` class that allocates memory on the heap. Provide a destructor, copy constructor, and copy assignment operator to ensure deep copying.

**Class Signature:**

```cpp
class DynamicArray {
private:
    int* data;
    int size;
public:
    DynamicArray(int s);
    ~DynamicArray();
    DynamicArray(const DynamicArray& other);
    DynamicArray& operator=(const DynamicArray& other);
    int& operator[](int index);
    int getSize() const;
};
```

**Constraints:**

* `size` ∈ \[1, 1000]

**Example:**

```cpp
DynamicArray arr1(5);
arr1[0] = 10;
DynamicArray arr2 = arr1;
arr2[0] = 20;
// arr1[0] should still be 10
```

---

### **25. Employee Hierarchy with Virtual Destructors**

**Concepts:** Virtual Destructors, Inheritance

**Problem Statement:**
Create a base class `Employee` with a virtual destructor. Derive `Manager` and `Engineer`, each printing a message in their destructor. Show that deleting objects via base class pointers calls correct destructors.

**Class Signature:**

```cpp
#include <iostream>
#include <string>

class Employee {
public:
    Employee(const std::string& name);
    virtual ~Employee();
protected:
    std::string name_;
};

class Manager : public Employee {
public:
    Manager(const std::string& name);
    ~Manager();
};

class Engineer : public Employee {
public:
    Engineer(const std::string& name);
    ~Engineer();
};
```

**Example:**

```cpp
Employee* emp1 = new Manager("Alice");
Employee* emp2 = new Engineer("Bob");
delete emp1; // Should call Manager -> Employee
delete emp2; // Should call Engineer -> Employee
```

---

### **26. Vehicle and Car with Polymorphism**

**Concepts:** Pure Virtual Functions, Virtual Methods

**Problem Statement:**
Define an abstract class `Vehicle` with a pure virtual method `startEngine()`. Derive `Car` and override `startEngine()` and a virtual method `drive()`.

**Class Signature:**

```cpp
class Vehicle {
public:
    virtual void startEngine() = 0;
    virtual void drive();
    virtual ~Vehicle() {}
};

class Car : public Vehicle {
public:
    void startEngine() override;
    void drive() override;
};
```

**Example:**

```cpp
Vehicle* myCar = new Car();
myCar->startEngine(); // Output: Car engine started.
myCar->drive();       // Output: Car is driving.
delete myCar;
```

---

### **27. Singleton Logger**

**Concepts:** Design Pattern - Singleton

**Problem Statement:**
Implement a thread-safe `Logger` class using the Singleton pattern. Prevent direct instantiation and copying. Provide a `log()` method to write messages.

**Class Signature:**

```cpp
#include <string>
#include <iostream>

class Logger {
private:
    Logger() {}
    Logger(const Logger&) = delete;
    Logger& operator=(const Logger&) = delete;

public:
    static Logger& getInstance();
    void log(const std::string& message);
};
```

**Example:**

```cpp
Logger& logger = Logger::getInstance();
logger.log("App started.");
```

---

### **28. Operator Overload for Money**

**Concepts:** Operator Overloading (Comparison)

**Problem Statement:**
Create a class `Money` that stores a double amount. Overload the `==` and `<` operators to compare `Money` objects.

**Class Signature:**

```cpp
class Money {
private:
    double amount;
public:
    Money(double val);
    bool operator==(const Money& other) const;
    bool operator<(const Money& other) const;
};
```

**Example:**

```cpp
Money m1(100.50), m2(50.25), m3(100.50);
// (m1 == m3) → true
// (m2 < m1)  → true
// (m1 < m2)  → false
```

---

### **29. Abstract Factory for UI Elements**

**Concepts:** Factory Method Pattern

**Problem Statement:**
Implement an abstract `Button` class and concrete classes `WindowsButton` and `MacButton`. Define a factory interface `GUIFactory` and implement platform-specific factories.

**Class Signature:**

```cpp
class Button {
public:
    virtual void render() = 0;
    virtual ~Button() {}
};

class WindowsButton : public Button {
public:
    void render() override;
};

class MacButton : public Button {
public:
    void render() override;
};

class GUIFactory {
public:
    virtual Button* createButton() = 0;
    virtual ~GUIFactory() {}
};

class WindowsFactory : public GUIFactory {
public:
    Button* createButton() override;
};

class MacFactory : public GUIFactory {
public:
    Button* createButton() override;
};
```

**Example:**

```cpp
GUIFactory* factory = new WindowsFactory();
Button* btn = factory->createButton();
btn->render(); // Output: Rendering a Windows button.
delete btn;
delete factory;
```

---

### **30. Checking Account Using Protected Inheritance**

**Concepts:** Protected Access Specifier, Inheritance

**Problem Statement:**
Create a base class `Account` with a protected balance. Implement deposit and get\_balance methods. Derive `CheckingAccount` that can withdraw funds by accessing balance directly.

**Class Signature:**

```cpp
class Account {
protected:
    double balance;
public:
    Account(double initial_balance = 0.0);
    void deposit(double amount);
    double get_balance() const;
};

class CheckingAccount : public Account {
public:
    CheckingAccount(double initial_balance = 0.0);
    void withdraw(double amount);
};
```

**Example:**

```cpp
CheckingAccount acc(200.0);
acc.withdraw(100.0);    // balance = 150.0
// acc.get_balance() == 150.0
```

---

### **31. Abstract Base Class for Shape**

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

### **32. Inheritance - Employee and Manager**

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

### **33. Copy Constructor**

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

### **34. Virtual Function for Polymorphism**

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

### **35. Operator Overloading (==)**

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

### **36. Dynamic Memory Allocation in Class**

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

### **37. Friend Function**

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

### **38. Private Inheritance**

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

### **39. Multiple Inheritance**

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

### **40. Abstract Interface for Logging**

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

## 🔴 Hard – C++ OOP Questions

---

### **41. Deep Copy with Copy Constructor and Assignment Operator**

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

### **42. Overloading << Operator for Custom Class**

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

### **43. Virtual Destructor in Inheritance Chain**

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

### **44. CRTP (Curiously Recurring Template Pattern)**

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

### **45. Abstract Factory Pattern with OOP**

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
---

### **46. Implementing a Polymorphic Collection and Iteration**

**Topic**: Polymorphism, Iterators, Memory Management
**Difficulty**: Medium

### **Problem Statement**

Design a class named `ShapeCollection` that manages a collection of pointers to polymorphic `Shape` objects (assume the classes `Shape`, `Circle`, and `Rectangle` are already defined).

Your task is to implement the following functionalities:

* Add a shape to the collection via `void addShape(Shape* s);`
* Compute the total area of all shapes using `double getTotalArea() const;`
* Provide simple iteration through the collection using:

  * `int size() const;`
  * `Shape* getShapeAt(int index) const;`

Ensure that your implementation handles memory management properly—i.e., all dynamically allocated shapes should be deleted in the destructor.

### **Class Skeleton**

```cpp
#include <vector>

class ShapeCollection {
private:
    std::vector<Shape*> shapes;

public:
    ShapeCollection();
    ~ShapeCollection();  // Responsible for memory cleanup
    void addShape(Shape* s);
    double getTotalArea() const;
    int size() const;
    Shape* getShapeAt(int index) const;
};
```

### **Constraints**

* The `Shape` class must be polymorphic (contain at least one virtual function).
* Ensure safe deallocation of shapes.
* Avoid raw pointer misuse (RAII encouraged if possible in extensions).

### **Usage Example**

```cpp
ShapeCollection collection;
collection.addShape(new Circle(3.0));
collection.addShape(new Rectangle(2.0, 5.0));
std::cout << collection.getTotalArea();  // Output: Sum of areas

for (int i = 0; i < collection.size(); ++i) {
    std::cout << collection.getShapeAt(i)->getArea() << std::endl;
}
```

---

### **47. Advanced Smart Pointer Usage with Custom Deleters**

**Topic**: Smart Pointers, Resource Management, Exception Safety
**Difficulty**: Medium

### **Problem Statement**

You are provided with a `Resource` class simulating a costly system resource. Your task is to implement a function `void manageResource(int id);` that:

* Acquires a `Resource` object,
* Performs operations with it, and
* Ensures safe release using `std::unique_ptr` with a custom deleter.

The custom deleter should:

* Use the default deleter for **even** `id`s.
* Print a custom message **before** deleting the object for **odd** `id`s.

### **Class Definition**

```cpp
class Resource {
public:
    int id;
    Resource(int id);
    ~Resource();
    void doSomething();
};
```

### **Function Signature**

```cpp
void manageResource(int id);
```

### **Constraints**

* Must use `std::unique_ptr` with a lambda-based custom deleter.
* Resource cleanup must be exception-safe.

### **Usage Example**

```cpp
manageResource(1); // Uses custom deleter with message
manageResource(2); // Uses default delete
```

---

### **48. Implementing the Visitor Pattern for Shapes**

**Topic**: Design Patterns (Visitor), Polymorphism, Encapsulation
**Difficulty**: Hard

### **Problem Statement**

Extend your `Shape` hierarchy to support the **Visitor Design Pattern**. You will:

1. Define an abstract class `ShapeVisitor` with `visit()` methods for both `Circle` and `Rectangle`.
2. Implement two visitors:

   * `AreaCalculatorVisitor`: Computes area.
   * `PerimeterCalculatorVisitor`: Computes perimeter.
3. Add an `accept()` method to each shape, which will call the appropriate `visit()` method.

### **Core Interface Modifications**

```cpp
class ShapeVisitor {
public:
    virtual void visit(Circle& circle) = 0;
    virtual void visit(Rectangle& rectangle) = 0;
    virtual ~ShapeVisitor() = default;
};

class Shape {
public:
    virtual double getArea() const = 0;
    virtual void accept(ShapeVisitor& visitor) = 0;
    virtual ~Shape() = default;
};
```

### **Example Use Case**

```cpp
Circle c(5.0);
Rectangle r(4.0, 6.0);

AreaCalculatorVisitor areaVisitor;
c.accept(areaVisitor);
r.accept(areaVisitor);
std::cout << areaVisitor.getTotalArea();

PerimeterCalculatorVisitor perimeterVisitor;
c.accept(perimeterVisitor);
r.accept(perimeterVisitor);
std::cout << perimeterVisitor.getTotalPerimeter();
```

---

### **49. Implementing a Generic Singly Linked List**

**Topic**: Templates, Memory Management, Operator Overloading
**Difficulty**: Medium

### **Problem Statement**

Create a templated singly linked list class named `LinkedList<T>` that supports:

* Adding a value (`add(T value)`),
* Removing a value (`remove(T value)`),
* Accessing a value at a specific index (`get(int index)`),
* Printing the list using the overloaded `<<` operator.

Ensure safe memory management (no leaks) and throw `std::out_of_range` for invalid indices.

### **Class Structure**

```cpp
template <typename T>
struct Node {
    T data;
    Node* next;
    Node(T val) : data(val), next(nullptr) {}
};

template <typename T>
class LinkedList {
private:
    Node<T>* head;
    int count;

public:
    LinkedList();
    ~LinkedList();
    void add(T value);
    bool remove(T value);
    T get(int index) const;
    int size() const;

    template <typename U>
    friend std::ostream& operator<<(std::ostream& os, const LinkedList<U>& list);
};
```

### **Example Usage**

```cpp
LinkedList<int> intList;
intList.add(10);
intList.add(20);
intList.add(30);
std::cout << intList << std::endl; // Output: [10, 20, 30]

intList.remove(20);
std::cout << intList << std::endl; // Output: [10, 30]

int val = intList.get(0);          // val = 10
intList.get(5);                    // Throws std::out_of_range
```

---

### **50. Runtime Type Information and Safe Downcasting**

**Topic**: RTTI, `dynamic_cast`, Polymorphism
**Difficulty**: Medium

### **Problem Statement**

Write a function `void processShape(Shape* s);` that safely downcasts a base pointer `Shape*` to either `Circle*` or `Rectangle*`. Based on the actual type, it should call the appropriate detail-printing method.

If the object is neither type, print a generic message indicating the shape is unknown or unsupported.

### **Required Methods in Derived Classes**

```cpp
class Circle : public Shape {
public:
    void printCircleDetails() const {
        std::cout << "This is a Circle with radius: " << radius << std::endl;
    }
};

class Rectangle : public Shape {
public:
    void printRectangleDetails() const {
        std::cout << "This is a Rectangle with width: " << width
                  << ", height: " << height << std::endl;
    }
};
```

### **Function Implementation**

```cpp
void processShape(Shape* s);
```

### **Usage Example**

```cpp
Shape* c = new Circle(7.0);
Shape* r = new Rectangle(8.0, 9.0);

processShape(c); // Output: Circle details
processShape(r); // Output: Rectangle details

delete c;
delete r;
```

---


