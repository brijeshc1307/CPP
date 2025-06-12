
### **String**

A **string** is a sequence of characters. C++ provides **two types of strings**:

---

## **1. C-Style Strings (Character Array)**

A **C-style string** is an array of characters terminated by a null character `'\0'`.

### Declaration & Initialization

```cpp
#include <iostream>
using namespace std;

int main() {
    char name[6] = "Alice"; // A-l-i-c-e-\0
    cout << "Name: " << name << endl;
    return 0;
}
```

### Notes:

* `char name[6]` includes 5 characters + 1 for `'\0'` (null terminator)
* You can also write: `char name[] = {'A','l','i','c','e','\0'};`

---

## **2. C++ Strings (Using `<string>` class)**

C++ Standard Library provides the `std::string` class which is more powerful and easier to use.
>String in cpp like 1 dimentional char array


### Example:

```cpp
#include <iostream>
#include <string>  // Required for std::string
using namespace std;

int main() {
    string name = "Brijesh";
    char lastname[20];
    string address;
    cin>>lastname>>address;
    cout << "Name is: " << name <<" "<<lastname<<" "<<address<<endl;

    // Operations
    cout << "Length Name: " << name.length() << endl;
    cout << "Size Name: " << name.size() << endl;
    //cout << "Length lastname: " << lastname.length() << endl;
    cout << "Length lastname: " << size(lastname) << endl;
    cout << "Length address: " << address.length() << endl;
    cout << "First char: " << name[0] << endl;

    name += " Chaudhary";  // Concatenation
    cout << "Full Name: " << name << endl;

    return 0;
}
```
Output
```
Name is: Brijesh chaudhary Ramnagar
Length Name: 7
Size Name: 7
Length lastname: 20
Length address: 8
First char: B
Full Name: Brijesh Chaudhary
```

### Key Functions:

| Function              | Description              | Time Complexity                                                        |
| --------------------- | ------------------------ | ---------------------------------------------------------------------- |
| `length()` / `size()` | Returns length of string | **O(1)**                                                               |
| `append()`            | Appends to the string    | **O(n)** *(n = size of appended string)*                               |
| `substr(start, len)`  | Returns substring        | **O(len)**                                                             |
| `find()`              | Searches substring       | **O(n \* m)** in worst case *(n = size of main string, m = substring)* |
| `compare()`           | Compares two strings     | **O(min(n, m))** *(n and m = lengths of strings)*                      |
| `c_str()`             | Returns C-style string   | **O(1)** *(returns pointer, no copy)*                                  |

---

## Types of Strings in C++

| Type                 | Description                                | Example                                        |
| -------------------- | ------------------------------------------ | ---------------------------------------------- |
| **Character Array**  | C-style string using array of `char`       | `char str[10] = "Hello";`                      |
| **std::string**      | C++ style string using `#include <string>` | `string s = "Hello";`                          |
| **Array of Strings** | Array that holds multiple strings          | `string names[3] = {"Ram", "Shyam", "Mohan"};` |

---

## Example: Array of Strings

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string fruits[3] = {"Apple", "Banana", "Mango"};

    for (int i = 0; i < 3; i++) {
        cout << "Fruit " << i + 1 << ": " << fruits[i] << endl;
    }

    return 0;
}
```

---

### Difference Between C-String vs C++ String

| Feature       | C-String (`char[]`) | C++ String (`std::string`) |
| ------------- | ------------------- | -------------------------- |
| Header Needed | None or `<cstring>` | `<string>`                 |
| Terminated By | `'\0'`              | Not required               |
| Easy to Use   | ❌                   | ✅                          |
| Dynamic Size  | ❌                   | ✅                          |

---
