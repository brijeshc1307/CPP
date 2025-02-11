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
```"Class is user defined datatype"```
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
The output may not be exactly `4 + 8 + 1 = 13 bytes` because of **padding and alignment**, which ensures efficient memory access. Depending on the compiler, it could be **16 bytes** (or more).

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
Getters and setters are used to access and modify private data members in a class. They help in **data encapsulation** and provide controlled access to variables. ```कोई भी Value or Data memebr अगर private है तो Getter and Setter की help से acccess कर सकते है```

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

1. **Default Access Specifier**:
   - **Struct**: Members are public by default.
   - **Class**: Members are private by default.

2. **Inheritance**:
   - **Struct**: Can inherit from other structs or classes, but the default inheritance mode is public.
   - **Class**: Can inherit from other classes or structs, but the default inheritance mode is private.

3. **Use Case**:
   - **Struct**: Typically used for simpler data types, such as PODs (Plain Old Data).
   - **Class**: Used for complex types that include behavior (methods) along with data.

4. **Features**:
   - Both support constructors, destructors, member functions, and access specifiers.
   - Structs in C++ are nearly identical to classes apart from default access and inheritance mode.

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



## **License**
This project is licensed under the MIT License.

---

Happy Coding!


