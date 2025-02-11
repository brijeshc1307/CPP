### **Constructor and Destructor 

---

## **1. Constructor in C++**  
A **constructor** is a special function that initializes an object when it is created.  

### **Key Features of a Constructor:**  
- **Same name as the class.**  
- **No return type (not even `void`).**  
- **Automatically invoked when an object is created.**  
- Can be **default, parameterized, or copy constructor**.

### **Example: Constructor in C++**  
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
### **Output:**  
```
Constructor called! a = 10
```

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

** Key Takeaways:**
  - **Constructor** is called automatically when an object is created.
  - **Destructor** is called when an object is destroyed.
  - Useful for **resource allocation and deallocation** (e.g., memory, file handling).  

---


## **License**
This project is licensed under the MIT License.

---

Happy Coding!
