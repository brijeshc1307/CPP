### **Constructor and Destructor 

---

## **1. Constructor in C++**  
A **constructor** is a special function that initializes an object when it is created.  
```Object creation time पर Invoke होता है, जब हम Constructor बनाते है तब Deafault Constructor call नहीं होता है वो Delete हो जाता है```
### **Key Features of a Constructor:**  
- **Same name as the class.**  
- **No return type (not even `void`).**  
- **Automatically invoked when an object is created.**  
- Can be **default, parameterized, or copy constructor**.

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

### **Example: Parametrized Constructor**  
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

### **Example: Shallow Copy Constructor**  
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
	void set_dimensions(int length1, int breadth1,
						int height1)
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

### **Example: Deep Copy Constructor**  
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
	void set_dimension(int len, int brea,
					int heig)
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
