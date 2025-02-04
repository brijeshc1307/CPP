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
```txt "Class is user defined datatype"```
Size of empty class is 1 byte.

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

### **Getter | Setter**
Getters and setters are used to access and modify private data members in a class. They help in **data encapsulation** and provide controlled access to variables.

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
