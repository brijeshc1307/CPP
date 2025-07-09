
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

## **0. String Manipulation**

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

### 1. **Reverse a String**

```cpp
void reverseString(string &s) {
    int l = 0, r = s.size() - 1;
    while (l < r) swap(s[l++], s[r--]);
}
```

### 2. **Check Palindrome**

```cpp
bool isPalindrome(const string &s) {
    int l = 0, r = s.size() - 1;
    while (l < r) {
        if (s[l++] != s[r--]) return false;
    }
    return true;
}
```

---

## **Searching & Matching Algorithms**

### 3. **Naive Pattern Matching**

```cpp
int naiveSearch(string txt, string pat) {
    int n = txt.length(), m = pat.length();
    for (int i = 0; i <= n - m; ++i) {
        int j = 0;
        for (; j < m; ++j)
            if (txt[i + j] != pat[j])
                break;
        if (j == m) return i; // pattern found at index i
    }
    return -1;
}
```

### 4. **KMP (Knuth–Morris–Pratt)**

```cpp
vector<int> computeLPS(string &pat) {
    int m = pat.length();
    vector<int> lps(m, 0);
    for (int i = 1, len = 0; i < m; ) {
        if (pat[i] == pat[len]) lps[i++] = ++len;
        else if (len != 0) len = lps[len - 1];
        else lps[i++] = 0;
    }
    return lps;
}

int kmpSearch(string txt, string pat) {
    vector<int> lps = computeLPS(pat);
    int i = 0, j = 0, n = txt.length(), m = pat.length();
    while (i < n) {
        if (txt[i] == pat[j]) ++i, ++j;
        if (j == m) return i - j; // match found
        else if (i < n && txt[i] != pat[j]) {
            if (j != 0) j = lps[j - 1];
            else ++i;
        }
    }
    return -1;
}
```

### 5. **Rabin-Karp (Hashing)**

```cpp
const int d = 256;
const int q = 101; // a prime

int rabinKarp(string txt, string pat) {
    int n = txt.size(), m = pat.size();
    int h = 1, p = 0, t = 0;

    for (int i = 0; i < m - 1; i++) h = (h * d) % q;

    for (int i = 0; i < m; i++) {
        p = (d * p + pat[i]) % q;
        t = (d * t + txt[i]) % q;
    }

    for (int i = 0; i <= n - m; i++) {
        if (p == t) {
            int j = 0;
            while (j < m && txt[i + j] == pat[j]) j++;
            if (j == m) return i;
        }
        if (i < n - m)
            t = (d * (t - txt[i] * h) + txt[i + m]) % q;
        if (t < 0) t += q;
    }
    return -1;
}
```

---

## **Hashing and Frequency**

### 6. **Character Frequency Count**

```cpp
vector<int> countChars(string &s) {
    vector<int> freq(26, 0);
    for (char c : s) freq[c - 'a']++;
    return freq;
}
```

### 7. **Check Anagram**

```cpp
bool isAnagram(string a, string b) {
    if (a.size() != b.size()) return false;
    vector<int> freq(26, 0);
    for (char c : a) freq[c - 'a']++;
    for (char c : b) freq[c - 'a']--;
    for (int x : freq) if (x != 0) return false;
    return true;
}
```

---

## **Substring and Subsequence**

### 8. **Longest Common Substring**

```cpp
int longestCommonSubstring(string s1, string s2) {
    int n = s1.size(), m = s2.size(), result = 0;
    vector<vector<int>> dp(n+1, vector<int>(m+1));
    for (int i = 1; i <= n; i++)
        for (int j = 1; j <= m; j++)
            if (s1[i-1] == s2[j-1])
                result = max(result, dp[i][j] = dp[i-1][j-1] + 1);
    return result;
}
```

### 9. **Longest Common Subsequence**

```cpp
int longestCommonSubseq(string s1, string s2) {
    int n = s1.size(), m = s2.size();
    vector<vector<int>> dp(n+1, vector<int>(m+1));
    for (int i = 1; i <= n; i++)
        for (int j = 1; j <= m; j++)
            if (s1[i-1] == s2[j-1])
                dp[i][j] = dp[i-1][j-1] + 1;
            else
                dp[i][j] = max(dp[i-1][j], dp[i][j-1]);
    return dp[n][m];
}
```

---

## **Prefix, Z-Algorithm, Manacher's**

### 10. **Z-Algorithm for Pattern Search (O(n))**

```cpp
vector<int> computeZ(string s) {
    int n = s.length(), l = 0, r = 0;
    vector<int> Z(n);
    for (int i = 1; i < n; ++i) {
        if (i <= r) Z[i] = min(r - i + 1, Z[i - l]);
        while (i + Z[i] < n && s[Z[i]] == s[i + Z[i]]) Z[i]++;
        if (i + Z[i] - 1 > r) l = i, r = i + Z[i] - 1;
    }
    return Z;
}
```

### 11. **Manacher’s Algorithm (Longest Palindromic Substring in O(n))**

```cpp
string longestPalindromicSubstring(string s) {
    string t = "@";
    for (char c : s) {
        t += "#";
        t += c;
    }
    t += "#$";

    int n = t.size(), center = 0, right = 0;
    vector<int> P(n);
    for (int i = 1; i < n - 1; ++i) {
        int mirror = 2 * center - i;
        if (i < right) P[i] = min(right - i, P[mirror]);

        while (t[i + 1 + P[i]] == t[i - 1 - P[i]]) P[i]++;
        if (i + P[i] > right) {
            center = i;
            right = i + P[i];
        }
    }

    int len = 0, idx = 0;
    for (int i = 1; i < n - 1; i++) {
        if (P[i] > len) {
            len = P[i];
            idx = i;
        }
    }
    return s.substr((idx - len) / 2, len);
}
```

---

##  **Other String Algorithms**

### 12. **Remove Consecutive Duplicates**

```cpp
string removeDuplicates(string s) {
    string res;
    for (char c : s) {
        if (res.empty() || res.back() != c)
            res.push_back(c);
    }
    return res;
}
```

### 13. **Lexicographically Smallest Subsequence**

```cpp
string smallestSubsequence(string s) {
    vector<int> last(26, 0);
    for (int i = 0; i < s.size(); ++i) last[s[i] - 'a'] = i;

    vector<bool> seen(26, false);
    string res;
    for (int i = 0; i < s.size(); ++i) {
        char c = s[i];
        if (seen[c - 'a']) continue;
        while (!res.empty() && res.back() > c && last[res.back() - 'a'] > i) {
            seen[res.back() - 'a'] = false;
            res.pop_back();
        }
        res += c;
        seen[c - 'a'] = true;
    }
    return res;
}
```

---
---
[⬅️ Arrays](/array.md)       | [Object-Oriented Programming (OOP) ➡️](/Object-Oriented_Programming.md)
---
## **License**
This project is licensed under the MIT License.

---

Happy Coding!

