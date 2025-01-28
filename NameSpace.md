In C++, a **namespace** is a way to organize code and prevent name conflicts by grouping entities like classes, objects, and functions under a unique name. This is particularly useful in larger programs or when using libraries that might have similar naming conventions.

### Declaring a Namespace
Here’s how you can declare and use a namespace:

```cpp
#include <iostream>

namespace MyNamespace {
    int myVariable = 42;

    void myFunction() {
        cout << "Hello from MyNamespace!" << endl;
    }
}

int main() {
    // Accessing elements in the namespace
    cout << "myVariable: " << MyNamespace::myVariable << endl;
    MyNamespace::myFunction();
    return 0;
}
```

### Key Features of Namespaces
1. **Prevent Naming Conflicts**: Namespaces ensure that entities in different libraries or sections of code do not collide. For example:
   ```cpp
   namespace Lib1 {
       int value = 10;
   }
   
   namespace Lib2 {
       int value = 20;
   }
   int main() {
       cout << Lib1::value << endl; // Output: 10
       cout << Lib2::value << endl; // Output: 20
   }
   ```

2. **`using` Keyword**: You can bring a namespace or its specific members into the current scope using the `using` keyword.
   ```cpp
   using namespace MyNamespace; // All members of MyNamespace are accessible without qualification.
   cout << myVariable << endl; // No need for MyNamespace::
   myFunction();
   ```

   However, it's better to avoid `using namespace` in larger programs to prevent ambiguity.

3. **Nested Namespaces**: You can nest namespaces within one another.
   ```cpp
   namespace Outer {
       namespace Inner {
           void display() {
               std::cout << "Inside Inner Namespace" << std::endl;
           }
       }
   }
   int main() {
       Outer::Inner::display();
   }
   ```

4. **Anonymous Namespaces**: If you don't give a namespace a name, it is treated as unique to the file (internal linkage).
   ```cpp
   namespace {
       void hiddenFunction() {
           cout << "This function is hidden from other files." << endl;
       }
   }
   ```

5. **Namespace Aliases**: Create shorter names for namespaces.
   ```cpp
   namespace LongNamespaceName {
       int value = 100;
   }
   namespace LNN = LongNamespaceName;
   int main() {
       cout << LNN::value << endl; // Output: 100
   }
   ```

### Advantages of Namespaces
- **Avoids global scope pollution**.
- Helps **modularize** the code.
- Makes code **readable and maintainable**.

Namespaces are extensively used in libraries like the C++ Standard Library (`std`). For instance:
```cpp
#include <iostream>

int main() {
    cout << "Hello, World!" << endl;
    return 0;
}
```
Here, `std` is the namespace for the C++ standard library.
