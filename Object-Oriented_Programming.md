## **Object-Oriented Programming (OOP) in C++**
Object-Oriented Programming (OOP) is a programming paradigm based on objects that encapsulate data and behavior. It allows for better code organization, reusability, and scalability.

### **Key Features of OOP:**
- **Encapsulation** – Wrapping data and functions into a single unit (class).
- **Abstraction** – Hiding unnecessary details and exposing only relevant features.
- **Inheritance** – Creating new classes from existing ones to promote reusability.
- **Polymorphism** – Ability to take multiple forms (function and operator overloading).

---

### **Class**
A class is a blueprint for creating objects. It defines properties (data members) and behaviors (member functions).
>"Class is user defined datatype"

```cpp
#include <iostream>
using namespace std;

class Car {
public:
    string brand;
    int speed;

    void show() {
        cout << "Brand: " << brand << ", Speed: " << speed << " km/h" << endl;
    }
};
```

### **Object**
An object is an instance of a class. or Object is an entity which has behavior, state/properties.
Real life example: Camera, light, laptop, etc.
```cpp
int main() {
    Car c1;
    c1.brand = "Toyota";
    c1.speed = 120;
    c1.show();
    return 0;
}
```
--- 

### Size of Empty Class
```cpp
#include <iostream>
using namespace std;

class EmptyClass {}; // No data members

int main() {
    cout << "Size of EmptyClass: " << sizeof(EmptyClass) << " byte" << endl;
    return 0;
}
```
```
Size of EmptyClass: 1 byte
```

---

### Why Size of EmptyClass: 1 byte
### Reason: To Ensure Each Object Has a Unique Address

The C++ standard requires that **each object in memory has a unique address**. If an empty class had a size of 0, then two instances of that class could potentially occupy the same memory address, which would break this rule.

#### Example:

```cpp
class Empty {};

int main() {
    Empty e1, e2;
    std::cout << &e1 << "\n";
    std::cout << &e2 << "\n";
}
```

This prints **two different addresses**, so `e1` and `e2` can be treated as distinct objects.

To make this work, the compiler gives every instance of an empty class a **minimum size of 1 byte**—often called a **dummy byte**—even though there's no actual data.

---

###  Special Cases

1. **Empty Base Optimization (EBO)**:
   When an empty class is used as a **base class**, modern compilers can optimize it out to avoid wasting that 1 byte.

   ```cpp
   class Empty {};
   class Derived : public Empty {
       int x;
   };
   ```

   In this case, `sizeof(Derived)` might be just `4` (not `5`), because the compiler applies EBO.

2. **Standard Compliance**:
   The C++ standard (specifically \[C++11 and later]) allows this optimization for base classes, but still requires that **non-base empty objects must have a size of at least 1**.

---

### Summary

| Concept                   | Value                                    |
| ------------------------- | ---------------------------------------- |
| Size of empty class       | 1 byte                                   |
| Why not 0?                | To give unique addresses to objects      |
| Can compiler optimize it? | Yes, in case of empty base classes (EBO) |

---

### Size of a Class with data members

```cpp
#include <iostream>
using namespace std;

class Example {
    int a;       // 4 bytes
    double b;    // 8 bytes
    char c;      // 1 byte
};

int main() {
    cout << "Size of class Example: " << sizeof(Example) << " bytes" << endl;
    return 0;
}
```
```
Size of class Example: 24 bytes
```
### Explanation:

The output may not be exactly `4 + 8 + 1 = 13` bytes due to padding and alignment, which ensure efficient memory access. Depending on the compiler, the size could be 16 bytes or more.

It will likely be `24 bytes`, depending on the platform and compiler you're using—typically on a 64-bit system with standard alignment rules.


---


### Why 24 bytes? Let's break it down:

| Member | Type     | Size (bytes) | Alignment requirement |
| ------ | -------- | ------------ | --------------------- |
| `a`    | `int`    | 4            | 4 bytes               |
| `b`    | `double` | 8            | 8 bytes               |
| `c`    | `char`   | 1            | 1 byte                |



### Memory layout with alignment and padding:

1. `a` (int): 4 bytes — starts at offset 0.
2. **Padding (4 bytes)** — to align the next `double` to an 8-byte boundary.
3. `b` (double): 8 bytes — starts at offset 8.
4. `c` (char): 1 byte — starts at offset 16.
5. **Padding (7 bytes)** — to make the total size a multiple of the largest alignment requirement (8 bytes for `double`).



### Final layout:

| Offset | Field    | Size |
| ------ | -------- | ---- |
| 0      | int a    | 4    |
| 4      | padding  | 4    |
| 8      | double b | 8    |
| 16     | char c   | 1    |
| 17–23  | padding  | 7    |

**Total = 24 bytes**

### Note:
We can use `#pragma pack(1)` to change alignment, but it may lead to performance penalties due to misaligned access on some architectures.
---
example:
```cpp
#include <iostream>
using namespace std;

class Example {
    int* a;     // pointer: 4 bytes on 32-bit, 8 bytes on 64-bit
    double b;   // 8 bytes
    char c;     // 1 byte
};

int main() {
    cout << "Size of class Example: " << sizeof(Example) << " bytes" << endl;
    return 0;
}
```
Output
```
// 8+ 8+ 8 = 24
```

exapmle:
```cpp
#include <iostream>
using namespace std;

class Example {
    static int a;       // 4 bytes **4 bytes, but not counted in object size**
// static int a belongs to the class, not to any object of the class. So it is stored separately in static storage, and not part of the instance's memory layout. Therefore, sizeof(Example) only includes non-static data members (b and c) + padding.

    double b;           // 8 bytes //8
    char c;             // 1 byte // 8 
};

int main() {
    cout << "Size of class Example: " << sizeof(Example) << " bytes" << endl;
    return 0;
}
```
Output
```
8+8=16 bytes
```
---

### Code:

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    virtual void sound() {}
};

class Dog : public Animal {
public:
    void sound() override {}
};

class Cat : public Animal {
public:
    void sound() override {}
};

int main() {
    Animal obj;
    Dog obj1;
    Cat obj2;

    cout << "Size of Animal: " << sizeof(obj) << " bytes" << endl;
    cout << "Size of Dog: " << sizeof(obj1) << " bytes" << endl;
    cout << "Size of Cat: " << sizeof(obj2) << " bytes" << endl;

// OR

 Animal* obj = new Animal();
    Dog* obj1 = new Dog();
    Cat* obj2 = new Cat();

    cout << "Size of Animal: " << sizeof(*obj) << " bytes" << endl;
    cout << "Size of Dog: " << sizeof(*obj1) << " bytes" << endl;
    cout << "Size of Cat: " << sizeof(*obj2) << " bytes" << endl;

    // Clean up memory
    delete obj;
    delete obj1;
    delete obj2;


    return 0;
}
```

---

### Sample Output (on 64-bit system):

```bash
Size of Animal: 8 bytes
Size of Dog: 8 bytes
Size of Cat: 8 bytes
```

(If you run this on a 32-bit system, you might see `4 bytes` instead.)

---

### **Access Modifiers in C++**
Access modifiers in C++ control the visibility and accessibility of class members (variables and functions). They help in implementing **encapsulation** by restricting direct access to data.

### **Types of Access Modifiers**
C++ provides three types of access modifiers:

| Access Modifier | Scope | Accessible From |
|---------------|--------|-----------------|
| `public` | Anywhere | Inside and outside the class |
| `private` | Within the class | Only inside the same class |
| `protected` | Within the class and derived classes | Inside the same class and its subclasses |

---

### Example for `public`
```cpp
#include <iostream>
using namespace std;

class Person{
// Properties
public:
  int age;
  void show(){
    cout<<"Age : "<<age<<endl;
  }
  
  
};
int main() {
  // creation of object
  Person obj;
  
  // store input in age of the person
  cout << "Enter age: "; 
  cin>>obj.age;
  
  // call function 
  obj.show();
  
  return 0;
}
```
```
Enter age: 21
Age : 21
```

### Example for `private`
```cpp
#include <iostream>
using namespace std;

class Person {
private:
    int age;  // Private property (not accessible in derived classes)

public:
    // Constructor (optional)
    Person() : age(0) {}

    // Setter function to modify age
    void setAge(int a) {
        age = a;
    }

    // Getter function to access age
    int getAge() {
        return age;
    }
};

class Child : public Person {
public:
    void show(int a) {
        setAge(a);  // Use setter to modify private variable
        cout << "Age: " << getAge() << endl;  // Use getter to access private variable
    }
};

int main() {
    Child c; // Object of derived class

    // Input age of the person
    int inputAge;
    cout << "Enter age: ";
    cin >> inputAge;

    // Call show() function and pass age as an argument
    c.show(inputAge);

    return 0;
}
```
```
Enter age: 25
Age: 25
```

### Example for `protected`
```cpp

#include <iostream>
using namespace std;

class Person{
// Properties
protected:
  int age;
};

class Child:public Person{
  public:
  void show(int a){
    age=a;
    cout<<"Age : "<<age<<endl;
  }
};
int main() {
  int age;
  // creation of object
  Child c;
  
  // store input in age of the person
  cout << "Enter age: "; 
  cin>>age;
  
  // call child class and show function and pass age argument
  c.show(age);
  
  return 0;
}
```
```
Enter age: 20
Age : 20
```
---

### **Getter | Setter**
Getters and setters are used to access and modify private data members in a class. They help in **data encapsulation** and provide controlled access to variables. 
>कोई भी Value or Data memebr अगर private है तो Getter and Setter की help से acccess कर सकते है

---

### **Why Use Getters and Setters?**
  - **Encapsulation**: Protects data by restricting direct access.  
  - **Validation**: Ensures data integrity by applying conditions before setting values.  
  - **Read-Only or Write-Only Access**: Allows controlled access to data.  

---

### **Example of Getters and Setters**
### **Without Getters and Setters (Incorrect Approach)**
```cpp
class Student {
public:
    int rollNo;  // Bad practice: directly accessible
};

int main() {
    Student s;
    s.rollNo = 101;  // Direct modification
    cout << "Roll No: " << s.rollNo << endl;
    return 0;
}
```
```
Roll No: 101
```

**Issue:** No control over roll number; it can be changed freely.

---

### **Using Getters and Setters (Correct Approach)**
```cpp
#include <iostream>
using namespace std;

class Student {
private:
    int rollNo;  // Private data member

public:
    // Setter function (to set value)
    void setRollNo(int r) {
        if (r > 0)  // Validation check
            rollNo = r;
        else
            cout << "Invalid Roll Number!" << endl;
    }

    // Getter function (to get value)
    int getRollNo() {
        return rollNo;
    }
};

int main() {
    Student s;
    s.setRollNo(101);  // Setting value using setter
    cout << "Roll No: " << s.getRollNo() << endl;  // Getting value using getter
    return 0;
}
```
**Output:**
```
Roll No: 101
```
**Advantages:**  
- Prevents invalid roll numbers.  
- Restricts direct access to private variables.  

---

### **Read-Only and Write-Only Properties**
  - **Read-Only:** Provide only a getter (no setter).  
  - **Write-Only:** Provide only a setter (no getter).  

### **Read-Only Example**
```cpp
class Student {
private:
    int rollNo = 202;

public:
    int getRollNo() {  // No setter, making it read-only
        return rollNo;
    }
};

int main() {
    Student s;
    cout << "Roll No: " << s.getRollNo() << endl;
    return 0;
}
```

### **Write-Only Example**
```cpp
class Student {
private:
    int rollNo;

public:
    void setRollNo(int r) {  // No getter, making it write-only
        rollNo = r;
    }
};

int main() {
    Student s;
    s.setRollNo(101);
    // cout << s.getRollNo();  Error: No getter function
    return 0;
}
```

---

### **Getters and Setters in Inheritance**
```cpp
class Person {
protected:
    string name;

public:
    void setName(string n) {
        name = n;
    }

    string getName() {
        return name;
    }
};

class Student : public Person {
public:
    void show() {
        cout << "Student Name: " << getName() << endl;
    }
};

int main() {
    Student s;
    s.setName("Alice");
    s.show();
    return 0;
}
```
**Output:**
```
Student Name: Alice
```
---

### **Structure vs Class**

| Feature    | Description                                                                                                                                                            |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **class**  | Default access is **private**. Default inheritance is **private**. Supports member functions and OOP features. Commonly used for encapsulation and complex types.      |
| **struct** | Default access is **public**. Default inheritance is **public**. Also supports member functions and OOP features. Typically used for simple data grouping (POD types). |


### **Example class vs structure**
```cpp
#include <iostream>
using namespace std;

// Using struct (default access is public)
struct Student {
    string name;
    int age;

    void display() { 
        cout << "Struct - Name: " << name << ", Age: " << age << endl; 
    }
};

// Using class (default access is private)
class Person {
private:
    string name;
    int age;

public:
    // Constructor to initialize values
    Person(string n, int a) {
        name = n;
        age = a;
    }

    void display() { 
        cout << "Class - Name: " << name << ", Age: " << age << endl; 
    }
};

int main() {
    // Struct Example
    Student s1;
    s1.name = "Alice";  // Allowed (public by default)
    s1.age = 20;        // Allowed
    s1.display();

    // Class Example
    Person p1("Bob", 25);
    p1.display();  // Only accessible via a public method

    return 0;
}
```
```
Struct - Name: Alice, Age: 20
Class - Name: Bob, Age: 25
```

---
### **Normal Variable vs Object Variable**

## 1. **Normal Variable (Primitive or Simple Variable)**

### **Definition**:

A normal variable holds **simple data types** or **primitive values** such as integers, floats, booleans, or characters.

### **Example**:

```cpp
int x = 5;        
string name = "John"; 
float pi = 3.14;    
```

### **Characteristics**:

* Stores **single pieces of data**.
* Stored **directly** in memory.
* Not part of any class or object by default.
* Operations on them are typically **value-based**.

---

## 2. **Object Variable (Instance Variable / Reference Variable)**

### **Definition**:

An object variable is a **reference to an instance of a class**. It holds **objects**, not simple values.

### **Example**:

```cpp
#include <iostream>
#include <string>
using namespace std;

class Person {
public:
    string name;

    // Constructor
    Person(string n) {
        name = n;
    }

    void greet() {
        cout << "Hello, my name is " << name << endl;
    }
};

int main() {
    Person p1("Alice");   // Object variable (instance of class Person)
    p1.greet();

    int x = 10;           // Normal variable (primitive type)

    return 0;
}

```

### **Characteristics**:

* Stores **reference to an object**, not the object itself.
* Can access methods and attributes of the class.
* Can hold **complex data** (multiple fields, behaviors).
* Often used to **model real-world entities**.

---

### Normal Variable Vs Object Variable :

| Aspect                 | Normal Variable              | Object Variable                    |
| ---------------------- | ---------------------------- | ---------------------------------- |
| Stores                 | Actual data/value            | Reference to an object             |
| Data type              | Primitive (int, float, char) | Class/struct instance              |
| Memory location        | Usually stack                | Reference on stack, object in heap |
| Size                   | Fixed size                   | Size of pointer/reference          |
| Example                | `int x = 5;`                 | `Person p = new Person();`         |
| Can hold multiple data | No                           | Yes (attributes + methods)         |

---
[⬅️ Strings](/string.md)      |  [Constructors and Destructors, Encapsulations And Abstraction ➡️](/constructors_destructors.md)
---

## **License**
This project is licensed under the MIT License.

---

Happy Coding!


