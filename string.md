
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

---

### **C++ `std::string` Functions**

| **Function**             | **Description**                                     | **Example**                    | **Time Complexity**   |
| ------------------------ | --------------------------------------------------- | ------------------------------ | --------------------- |
| `length()` / `size()`    | Returns number of characters in the string          | `str.length()`                 | O(1)                  |
| `empty()`                | Checks if string is empty                           | `str.empty()`                  | O(1)                  |
| `at(index)`              | Access character with bounds checking               | `str.at(2)`                    | O(1)                  |
| `[]`                     | Access character (no bounds check)                  | `str[2]`                       | O(1)                  |
| `append(str)`            | Adds str to the end of string                       | `str.append("World")`          | O(n) (n = str.size()) |
| `+`                      | Concatenates two strings                            | `str = str1 + str2`            | O(n + m)              |
| `substr(pos, len)`       | Returns substring starting at `pos` of length `len` | `str.substr(0, 5)`             | O(len)                |
| `find(str)`              | Finds first occurrence of `str`                     | `str.find("lo")`               | O(n \* m) worst-case  |
| `rfind(str)`             | Finds last occurrence of `str`                      | `str.rfind("l")`               | O(n \* m) worst-case  |
| `erase(pos, len)`        | Removes `len` chars from position `pos`             | `str.erase(2, 3)`              | O(n)                  |
| `insert(pos, str)`       | Inserts `str` at position `pos`                     | `str.insert(5, "Test")`        | O(n + m)              |
| `replace(pos, len, str)` | Replaces `len` chars at `pos` with `str`            | `str.replace(2, 3, "xyz")`     | O(n + m)              |
| `compare(str)`           | Compares two strings lexicographically              | `str.compare("Hello")`         | O(min(n, m))          |
| `c_str()`                | Returns C-style (null-terminated) char array        | `const char* c = str.c_str();` | O(1)                  |
| `swap(str2)`             | Swaps content with another string                   | `str1.swap(str2)`              | O(1)                  |
| `clear()`                | Removes all characters from the string              | `str.clear()`                  | O(1)                  |

### **Legend**

* `n` = length of the original string
* `m` = length of the string being added or searched

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
