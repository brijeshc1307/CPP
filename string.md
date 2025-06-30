
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
Sure! Let's dive into **String Manipulation**, **Pattern Matching**, and **Hashing** in C++ — each explained clearly with **examples** and use-cases.

---

## **1. String Manipulation**

**String manipulation** refers to performing operations like insert, delete, replace, reverse, concatenate, etc., on strings.

### Example: Basic Manipulations in C++

```cpp
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;

int main() {
    string str = "hello";

    // Append
    str += " world";  // str = "hello world"

    // Insert
    str.insert(5, " beautiful"); // str = "hello beautiful world"

    // Replace
    str.replace(6, 9, "awesome"); // str = "hello awesome world"

    // Erase
    str.erase(5, 8); // str = "hello world"

    // Reverse
    reverse(str.begin(), str.end()); // str = "dlrow olleh"

    cout << "Final string: " << str << endl;
    return 0;
}
```

### Output:

```
Final string: dlrow olleh
```

---

## **2. Pattern Matching**

Used to search for a **substring** (pattern) in a main string (text).
Let’s explore both naive and efficient ways.

---

### A. Naive Pattern Matching (O(n × m))

Check every position of the text to see if the pattern matches.

```cpp
bool naiveMatch(string text, string pattern) {
    int n = text.size(), m = pattern.size();
    for (int i = 0; i <= n - m; i++) {
        int j = 0;
        while (j < m && text[i + j] == pattern[j]) j++;
        if (j == m) return true; // Pattern found
    }
    return false;
}
```

---

### B. KMP Algorithm (O(n + m))

Uses an LPS (Longest Prefix Suffix) array to avoid redundant comparisons.

```cpp
vector<int> buildLPS(string pattern) {
    int m = pattern.size();
    vector<int> lps(m, 0);
    int len = 0;

    for (int i = 1; i < m; ) {
        if (pattern[i] == pattern[len]) {
            lps[i++] = ++len;
        } else {
            if (len != 0)
                len = lps[len - 1];
            else
                lps[i++] = 0;
        }
    }
    return lps;
}

bool kmpMatch(string text, string pattern) {
    vector<int> lps = buildLPS(pattern);
    int i = 0, j = 0;
    while (i < text.size()) {
        if (text[i] == pattern[j]) {
            i++; j++;
        }
        if (j == pattern.size()) return true;
        else if (i < text.size() && text[i] != pattern[j]) {
            j = (j != 0) ? lps[j - 1] : 0;
        }
    }
    return false;
}
```

---

## **3. Hashing (Rolling Hash / Rabin-Karp)**

Hashing is used to **convert a string to a number**, making comparisons faster.

### Use-case: Detect Substring Fast

### Hash Function Example:

```cpp
typedef long long ll;
const int p = 31;         // Prime base
const int mod = 1e9 + 9;  // Large prime

ll stringHash(string s) {
    ll hash = 0, pow = 1;
    for (char c : s) {
        hash = (hash + (c - 'a' + 1) * pow) % mod;
        pow = (pow * p) % mod;
    }
    return hash;
}
```

### Example Use:

```cpp
string a = "abc";
string b = "abc";

if (stringHash(a) == stringHash(b)) {
    cout << "Strings are same" << endl;
}
```

> Rolling hash is used in **Rabin-Karp** to search for patterns in O(n) using precomputed hashes.

---

## Summary:

| **Topic**           | **Goal**                   | **Example**            | **Complexity**        |
| ------------------- | -------------------------- | ---------------------- | --------------------- |
| String Manipulation | Modify or edit strings     | Insert, erase, reverse | O(n)                  |
| Naive Matching      | Find pattern in text       | Check at each index    | O(n × m)              |
| KMP                 | Efficient pattern matching | Uses prefix table      | O(n + m)              |
| Hashing             | Fast string comparison     | Hash + Compare         | O(n), O(1) comparison |

---

---
[⬅️ Strings](/string.md)       | [Constructors and Destructors, Encapsulations And Abstraction ➡️](/constructors_destructors.md)
---
## **License**
This project is licensed under the MIT License.

---

Happy Coding!

