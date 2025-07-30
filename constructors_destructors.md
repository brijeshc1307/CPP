## **1. Constructor in C++**  
A **constructor** is a special function that initializes an object when it is created.  
>Object creation time पर Invoke होता है, जब हम Constructor बनाते है तब Deafault Constructor call नहीं होता है वो Delete हो जाता है

### **Key Features of a Constructor:**  
- **Same name as the class.**  
- **No return type (not even `void`).**  
- **Automatically invoked when an object is created.**  
- Can be **default, parameterized, or copy constructor**.
  
### **Why use it?** 
- Auto-initializes members
- Makes code cleaner and safer
- Supports overloading for flexibility
- Required for const or reference members

### **Example: Constructor**  

```cpp
#include <iostream>
using namespace std;

class Example {
    int a;
public:
    // Constructor
    Example(int x) {  
        a = x;
        cout << "Constructor called! a = " << a << endl;
    }
};

int main() {
    Example obj(10);  // Constructor is called automatically
    return 0;
}
``` 
```
Constructor called! a = 10
```
### **Example: Default Constructor** 
Default Constructor – Takes no arguments.
```cpp
#include <iostream>
using namespace std;

class Example {
    int a;

public:
    // Default constructor
    Example() {
        a = 0;
        cout << "Default constructor called! a = " << a << endl;
    }
};

int main() {
    Example obj1;          // Default constructor
    return 0;
}
```

### **Example: Parametrized Constructor**  
Parameterized Constructor – Takes arguments to initialize data members.

```cpp
// C++ program to calculate the area of a wall

#include <iostream>
using namespace std;

// declare a class
class Wall {
  private:
    double length;
    double height;

  public:
    // parameterized constructor to initialize variables
    Wall(double len, double hgt) {
      length = len;
      height = hgt;
    }

    double calculateArea() {
      return length * height;
    }
};

int main() {
  // create object and initialize data members
  Wall wall1(10.5, 8.6);
  Wall wall2(8.5, 6.3);

  cout << "Area of Wall 1: " << wall1.calculateArea() << endl;
  cout << "Area of Wall 2: " << wall2.calculateArea();

  return 0;
}
```
```
Area of Wall 1: 90.3
Area of Wall 2: 53.55
```

### **Example: Copy Constructor**  
Copy Constructor – Creates a new object as a copy of an existing object.
```cpp
#include <iostream>
using namespace std;

// declare a class
class Wall {
  private:
    double length;
    double height;

  public:

    // initialize variables with parameterized constructor
    Wall(double len, double hgt) {
      length = len;
      height = hgt;
    }

    // copy constructor with a Wall object as parameter
    // copies data of the obj parameter
    Wall(Wall &obj) {
      length = obj.length;
      height = obj.height;
    }

    double calculateArea() {
      return length * height;
    }
};

int main() {
  // create an object of Wall class
  Wall wall1(10.5, 8.6);

  // copy contents of wall1 to wall2
  Wall wall2(wall1);
  //Wall wall2 = wall1;

  // print areas of wall1 and wall2
  cout << "Area of Wall 1: " << wall1.calculateArea() << endl;
  cout << "Area of Wall 2: " << wall2.calculateArea();

  return 0;
}
```
```
Area of Wall 1: 90.3
Area of Wall 2: 90.3
```

### **Example: Default, Parametrized, Copy Constructor**  
```cpp
#include <iostream>
using namespace std;

// Declare a class
class Wall {
private:
    double length;
    double height;

public:
    // Simple Constructor
    Wall() {
        cout << "Simple Constructor Called" << endl;
        length = 5;   // Assign default values
        height = 4;
        cout << "Simple Constructor - Length: " << length << ", Height: " << height << ", Area: " << calculateArea() << endl;
    }

    // Parameterized Constructor
    Wall(double len, double hgt) {
        cout << "Parameterized Constructor Called" << endl;
        length = len;
        height = hgt;
        cout << "Parameterized Constructor - Length: " << length << ", Height: " << height << ", Area: " << calculateArea() << endl;
    }

    // Copy Constructor
    Wall(Wall &obj) {
        cout << "Copy Constructor Called" << endl;
        length = obj.length;
        height = obj.height;
        cout << "Copy Constructor - Length: " << length << ", Height: " << height << ", Area: " << calculateArea() << endl;
    }

    double calculateArea() {
        return length * height;
    }
};

int main() {
    // Create an object and invoke simple constructor
    Wall wall;

    // Create an object using parameterized constructor
    Wall wall1(10.5, 8.6);

    // Create an object using copy constructor
    Wall wall2 = wall1;

    return 0;
}
```
```
Simple Constructor Called
Simple Constructor - Length: 5, Height: 4, Area: 20
Parameterized Constructor Called
Parameterized Constructor - Length: 10.5, Height: 8.6, Area: 90.3
Copy Constructor Called
Copy Constructor - Length: 10.5, Height: 8.6, Area: 90.3
```

OR
```cpp
#include <iostream>
using namespace std;

class Example {
    int a;

public:
    // Default constructor
    Example() {
        a = 0;
        cout << "Default constructor called! a = " << a << endl;
    }

    // Parameterized constructor
    Example(int x) {
        a = x;
        cout << "Parameterized constructor called! a = " << a << endl;
    }

    // Copy constructor
    Example(const Example &obj) {
        a = obj.a;
        cout << "Copy constructor called! a = " << a << endl;
    }

    // Optional: Function to display value of 'a'
    void display() {
        cout << "Value of a = " << a << endl;
    }
};

int main() {
    Example obj1;          // Default constructor
    Example obj2(10);      // Parameterized constructor
    Example obj3 = obj2;   // Copy constructor

    // Optional: Displaying values
    cout << "\nDisplaying values:\n";
    obj1.display();
    obj2.display();
    obj3.display();

    return 0;
}

```
Output
```
Default constructor called! a = 0
Parameterized constructor called! a = 10
Copy constructor called! a = 10

Displaying values:
Value of a = 0
Value of a = 10
Value of a = 10
```
---

### Shallow Copy Constructor
A shallow copy creates a new object, but **does not copy the inner (nested) objects**. Instead, it copies references to them.
* **Result:** Changes to nested objects in the copy **affect the original**.
* Only the top-level object is copied.
* Inner objects are **shared** between original and copy.
* Default copy constructor also know as Shallow Copy

>Shallow copy एक नया object बनाता है, लेकिन इसके अंदर मौजूद inner (nested) objects की कॉपी नहीं करता। इसके बजाय, वो उनके references (पते) को कॉपी करता है।
>Copy किए गए nested objects में बदलाव करने पर original object भी प्रभावित होता है।
>केवल top-level object की कॉपी बनती है।
>Inner objects original और copy के बीच साझा (shared) रहते हैं।
>C++ में जो default copy constructor होता है, वो आमतौर पर shallow copy करता है।

```cpp
#include <iostream>
using namespace std;

// Box Class
class box {
private:
	int length;
	int breadth;
	int height;

public:
	// Function that sets the dimensions
	void set_dimensions(int length1, int breadth1, int height1)
	{
		length = length1;
		breadth = breadth1;
		height = height1;
	}

	// Function to display the dimensions
	// of the Box object
	void show_data()
	{
		cout << " Length = " << length
			<< "\n Breadth = " << breadth
			<< "\n Height = " << height
			<< endl;
	}
};

// Driver Code
int main()
{
	// Object of class Box
	box B1, B3;

	// Set dimensions of Box B1
	B1.set_dimensions(14, 12, 16);
	B1.show_data();

	// When copying the data of object
	// at the time of initialization
	// then copy is made through
	// COPY CONSTRUCTOR
	box B2 = B1;
	B2.show_data();

	// When copying the data of object
	// after initialization then the
	// copy is done through DEFAULT
	// ASSIGNMENT OPERATOR
	B3 = B1;
	B3.show_data();

	return 0;
}
```
```
 Length = 14
 Breadth = 12
 Height = 16
 Length = 14
 Breadth = 12
 Height = 16
 Length = 14
 Breadth = 12
 Height = 16
```

### Deep Copy Constructor
A deep copy creates a new object **and** also copies **all nested objects** recursively.
* **Result:** Changes to nested objects in the copy **do not affect the original**.
* Both the top-level and inner objects are fully copied.
* Original and copied objects are **independent**.

>Deep copy एक नया object बनाता है और उसमें मौजूद सभी nested objects (अंदर के objects) को भी recursively कॉपी करता है।
>Copy किए गए nested objects में बदलाव का असर original object पर नहीं पड़ता।
>Top-level और अंदर के सभी objects की अलग-अलग कॉपी बनती है।
>Original और copied object एक-दूसरे से पूरी तरह स्वतंत्र (independent) होते हैं।


```cpp
// deep copy
#include <iostream>
using namespace std;

// Box Class
class box {
private:
	int length;
	int* breadth;
	int height;

public:
	// Constructor
	box()
	{
		breadth = new int;
	}

	// Function to set the dimensions
	// of the Box
	void set_dimension(int len, int brea, int heig)
	{
		length = len;
		*breadth = brea;
		height = heig;
	}

	// Function to show the dimensions
	// of the Box
	void show_data()
	{
		cout << " Length = " << length
			<< "\n Breadth = " << *breadth
			<< "\n Height = " << height
			<< endl;
	}

	// Parameterized Constructors for
	// for implementing deep copy
	box(box& sample)
	{
		length = sample.length;
		breadth = new int;
		*breadth = *(sample.breadth);
		height = sample.height;
	}

	// Destructors
	~box()
	{
		delete breadth;
	}
};

// Driver Code
int main()
{
	// Object of class first
	box first;

	// Set the dimensions
	first.set_dimension(12, 14, 16);

	// Display the dimensions
	first.show_data();

	// When the data will be copied then
	// all the resources will also get
	// allocated to the new object
	box second = first;

	// Display the dimensions
	second.show_data();

	return 0;
}
```
```
 Length = 12
 Breadth = 14
 Height = 16
 Length = 12
 Breadth = 14
 Height = 16
```
---

### **Copy Assignment Operator**

The **copy assignment operator** is used to assign the contents of one object to another **already existing** object of the same class.

**Syntax:**

```cpp
ClassName& operator=(const ClassName& other);
```

* It **overwrites** the contents of an object.
* It’s called **when you use `=` between two objects** of the same class **after they have been created**.
* You should define it **when your class manages dynamic memory** to prevent shallow copy issues.
* If you don’t define it, the compiler provides a **default copy assignment operator** that performs a **shallow copy** (bitwise copy of all members).

---

### **Example:**

```cpp
#include <iostream>
using namespace std;

class Person {
public:
    string* name;

    Person(string n) {
        name = new string(n);
    }

    // Copy constructor (deep copy)
    Person(const Person& other) {
        name = new string(*other.name);
    }

    // Copy assignment operator (deep copy)
    Person& operator=(const Person& other) {
        if (this != &other) {  // Prevent self-assignment
            delete name;  // Clean up old memory
            name = new string(*other.name);  // Allocate new memory and copy
        }
        return *this;
    }

    void show() {
        cout << *name << endl;
    }

    ~Person() {
        delete name;
    }
};

int main() {
    Person p1("John");
    Person p2("David");

    p2 = p1;  // copy assignment operator called

    *p2.name = "Michael";

    p1.show();  // Output: John
    p2.show();  // Output: Michael

    return 0;
}
```

---

### Key Points:

| Aspect                  | Explanation                                  |
| ----------------------- | -------------------------------------------- |
| Purpose                 | Assign values from one object to another     |
| Default behavior        | Shallow copy                                 |
| When to define manually | When class handles dynamic memory (pointers) |
| Return type             | Reference to the current object (`*this`)    |
| Self-assignment check   | `if (this != &other)` is important           |

---

## **2. Destructor in C++**  
A **destructor** is a special function that cleans up an object before it is destroyed.  

### **Key Features of a Destructor:**  
- **Same name as the class but prefixed with `~`** (tilde).  
- **No return type and no parameters.**  
- **Automatically called when an object goes out of scope or `delete` is used.**  
- **Used to free dynamically allocated memory or release resources.**

### **Example: Destructor in C++**  
```cpp
#include <iostream>
using namespace std;

class Example {
public:
    // Constructor
    Example() {
        cout << "Constructor called!" << endl;
    }

    // Destructor
    ~Example() {
        cout << "Destructor called!" << endl;
    }
};

int main() {
    Example obj;  // Constructor is called automatically
    return 0;     // Destructor is called when obj goes out of scope
}
```

### **Output:**  
```
Constructor called!
Destructor called!
```

---

## **When Are Constructor and Destructor Called?**  
| Event            | Constructor | Destructor |
|-----------------|-------------|------------|
| Object Created  | Called    | Not Called |
| Object Deleted  | Not Called | Called |
| Object Goes Out of Scope | Not Called | Called |

---

## **Example: Constructor and Destructor in Dynamic Memory**
```cpp
#include <iostream>
using namespace std;

class Example {
public:
    Example() { cout << "Constructor called!" << endl; }
    ~Example() { cout << "Destructor called!" << endl; }
};

int main() {
    Example* obj = new Example(); // Constructor called
    delete obj; // Destructor called
    return 0;
}
```
### **Output:**
```
Constructor called!
Destructor called!
```

---
### **Rule of 0, 3, and 5 in C++**

These are guidelines about when and how to define special member functions in **C++ classes** that manage **resources** (like memory, file handles, etc.).

---

## 1. **Rule of 0**

* **You don’t need to define any special functions manually.**
* Let the **compiler generate** everything: constructor, destructor, copy/move constructor, assignment operators.

### When to use:

* Your class **doesn't own any raw resources** (like raw pointers).
* You use **standard containers** (like `std::string`, `std::vector`, `std::unique_ptr`, etc.).

### Example:

```cpp
struct Person {
    std::string name;
    int age;
    // No need to define destructor, copy/move constructors
};
```

---

## 2. **Rule of 3**

If you define **any one** of the following:

* Copy constructor
* Copy assignment operator
* Destructor

**Then you should define all three.**

### When to use:

* Your class **manages a raw resource** (e.g., raw pointers, dynamic memory).

### Example:

```cpp
class MyClass {
    int* data;

public:
    MyClass() {
        data = new int[10];
    }

    // 1. Destructor
    ~MyClass() {
        delete[] data;
    }

    // 2. Copy Constructor
    MyClass(const MyClass& other) {
        data = new int[10];
        std::copy(other.data, other.data + 10, data);
    }

    // 3. Copy Assignment
    MyClass& operator=(const MyClass& other) {
        if (this != &other) {
            delete[] data;
            data = new int[10];
            std::copy(other.data, other.data + 10, data);
        }
        return *this;
    }
};
```

---

##  3. **Rule of 5** (C++11 and later)

If your class manages resources and you define:

* Copy constructor
* Copy assignment operator
* Destructor

Then also define:

* **Move constructor**
* **Move assignment operator**

###  When to use:

* To **optimize performance** by allowing move semantics instead of always copying.

###  Example (with move):

```cpp
class MyClass {
    int* data;

public:
    MyClass() {
        data = new int[10];
    }

    ~MyClass() {
        delete[] data;
    }

    MyClass(const MyClass& other) {
        data = new int[10];
        std::copy(other.data, other.data + 10, data);
    }

    MyClass& operator=(const MyClass& other) {
        if (this != &other) {
            delete[] data;
            data = new int[10];
            std::copy(other.data, other.data + 10, data);
        }
        return *this;
    }

    // Move Constructor
    MyClass(MyClass&& other) noexcept {
        data = other.data;
        other.data = nullptr;
    }

    // Move Assignment
    MyClass& operator=(MyClass&& other) noexcept {
        if (this != &other) {
            delete[] data;
            data = other.data;
            other.data = nullptr;
        }
        return *this;
    }
};
```

---

## Summary Table:

| Rule      | You Define...                    | When              | Purpose                            |
| --------- | -------------------------------- | ----------------- | ---------------------------------- |
| Rule of 0 | Nothing                          | No raw resources  | Rely on compiler-generated members |
| Rule of 3 | Copy ctor, copy assignment, dtor | Raw resource mgmt | Correct copying & destruction      |
| Rule of 5 | + Move ctor, move assignment     | C++11+            | Avoid unnecessary deep copies      |

---

## **3.Encapsulation in C++**

---

Encapsulation is the process of wrapping data and functions into a single unit (class) and restricting direct access to some of the object's components. It is used to protect data from unauthorized access and modification by using access specifiers like private, public, and protected.

>Data hiding | Information hiding wraping up data member and function. (Fully encapsulated class - all Data members private होता है)

---

### **Real-Life Example:**

**Example: Bank Account**

Imagine a **bank account**. You can **deposit** or **withdraw** money using specific methods, but you **cannot directly change** the balance from outside.

* **Balance** is kept **private**
* **Deposit** and **Withdraw** methods are **public**

This protects the account from invalid operations.

---

### **Code Example:**

```cpp
#include <iostream>
using namespace std;

class BankAccount {
private:
    double balance; // private data member

public:
    // Constructor
    BankAccount(double initialBalance) {
        if (initialBalance >= 0)
            balance = initialBalance;
        else
            balance = 0;
    }

    // Public method to deposit money
    void deposit(double amount) {
        if (amount > 0)
            balance += amount;
    }

    // Public method to withdraw money
    void withdraw(double amount) {
        if (amount > 0 && amount <= balance)
            balance -= amount;
        else
            cout << "Invalid withdraw amount" << endl;
    }

    // Public method to check balance
    double getBalance() {
        return balance;
    }
};

int main() {
    BankAccount myAccount(1000); // Create an account with ₹1000

    myAccount.deposit(500);      // Add ₹500
    myAccount.withdraw(200);     // Withdraw ₹200

    cout << "Current balance: ₹" << myAccount.getBalance() << endl;

    // myAccount.balance = 10000; //  Not allowed: balance is private

    return 0;
}
```
### **Output:**
```
Current balance: ₹1300
```

```cpp

#include <iostream>
using namespace std;

class Student {
private:
    string name;
    int age;
    int height;

public:
    // Setter for name
    void setName(string n) {
        name = n;
    }

    // Setter for age
    void setAge(int a) {
        if (a >= 0)
            age = a;
    }

    // Setter for height
    void setHeight(int h) {
        if (h >= 0)
            height = h;
    }

    // Getter for name
    string getName() {
        return name;
    }

    // Getter for age
    int getAge() {
        return age;
    }

    // Getter for height
    int getHeight() {
        return height;
    }
};

int main() {
    Student first;

    // Set values using setters
    first.setName("Brijesh");
    first.setAge(25);
    first.setHeight(170);

    // Get and display values using getters
    cout << "Name: " << first.getName() << endl;
    cout << "Age: " << first.getAge() << endl;
    cout << "Height: " << first.getHeight() << " cm" << endl;

    return 0;
}
```
### **Output:**
```
Name: Brijesh
Age: 25
Height: 170 cm
```
---

### **Benefits of Encapsulation:**

* Protects internal state of the object
* Improves security and control
* Makes the code modular and maintainable
* Enables data hiding
* If we want, wecan make class- "Read Only"
* Use for unit testing
---

## **4. Abstraction**

**Abstraction** is the process of **hiding the internal implementation** and showing only the **essential features** to the user. It lets you use complex systems easily without knowing how they work inside.

>Abstract means displaying only essential information and hiding the details. OR Implementation hiding and showing only the features.

---

### **Benefits of Encapsulation:**

* Only we can make changes to our data or function, and no one esle can.
* It makes the application secure by not allowing anyone else to see the background details.
* Increase the reuseabilty of the code.
* Avoides duplicate of our code
---

### **Real-Life Example: Sending an Email**

When we send an email:

* We write the email, enter the recipient, and click **Send**.
* We **don’t know** how the mail is converted to packets, how servers communicate, or how the message is routed and delivered.

That’s **abstraction** — the complex logic is hidden, and only necessary functions are exposed to the user.

---

### **C++ Code Example:**

```cpp
#include <iostream>
using namespace std;

// Abstract class
class EmailService {
public:
    // Pure virtual function (interface)
    virtual void sendEmail(string to, string message) = 0;
};

// Concrete class
class Gmail : public EmailService {
public:
    void sendEmail(string to, string message) override {
        // Internal logic is hidden from the user
        cout << "Sending email to: " << to << endl;
        cout << "Message: " << message << endl;
        cout << "Email sent successfully using Gmail!" << endl;
    }
};

int main() {
    EmailService* email = new Gmail();

    // User only uses exposed interface
    email->sendEmail("example@gmail.com", "Hello! This is an abstracted email system.");

    delete email;
    return 0;
}
```

---

### **Explanation:**

* `EmailService` is an **abstract class**.
* `sendEmail()` is a **pure virtual function** — it defines *what* needs to be done.
* `Gmail` class implements *how* the email is sent — this internal logic is **hidden**.
* The user just calls `sendEmail()`, without knowing the complex background operations.

---

###  **C++ Code Example (Using Abstract Class):**

```cpp
#include <iostream>
using namespace std;

// Abstract class (contains at least one pure virtual function)
class Animal {
public:
    virtual void makeSound() = 0; // pure virtual function
};

class Dog : public Animal {
public:
    void makeSound() override {
        cout << "Dog barks " << endl;
    }
};

class Cat : public Animal {
public:
    void makeSound() override {
        cout << "Cat meows " << endl;
    }
};

int main() {
    Animal* a1 = new Dog();
    Animal* a2 = new Cat();

    a1->makeSound();  // Output: Dog barks
    a2->makeSound();  // Output: Cat meows

    delete a1;
    delete a2;

    return 0;
}
```
---

###  **Key Concepts:**

* `Animal` is an **abstract class** (cannot be instantiated).
* `makeSound()` is a **pure virtual function**, which forces derived classes to provide their own implementation.
* This hides **how** `makeSound()` is implemented and only exposes **what** it does.

---
```cpp
#include <iostream>
using namespace std;

class A {
private:
    int a,b;
public:
    void set(int x, int y){
        a=x;
        b=y;
    }
    void show(){
        cout<<"a = "<<a<<endl;
        cout<<"b = "<<b<<endl;
    }
};

int main() {
    A obj;
    obj.set(10,20);
    obj.show();
    return 0;
}

```
### **Output:**
```
a = 10
b = 20
```

---
###  **Difference Between Abstraction and Encapsulation:**

| Feature      | Abstraction                      | Encapsulation                       |
| ------------ | -------------------------------- | ----------------------------------- |
| Focus        | Hides **implementation details** | Hides **data**                      |
| Achieved via | Abstract classes, interfaces     | Access specifiers (`private`, etc.) |
| Goal         | Show only necessary features     | Protect internal object state       |

---
[⬅️ Object-Oriented Programming (OOP)](/Object-Oriented_Programming.md)     |   [Inheritance ➡️](/Inheritance.md) 
---
## **License**
This project is licensed under the MIT License.

---

Happy Coding!
