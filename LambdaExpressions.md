### Lambda Expressions in C++ (Anonymous Functions)

**Lambda expressions** are **anonymous functions** (i.e., functions without a name) that can be defined **inline** within C++ code. Introduced in **C++11**, they help write **cleaner**, **shorter**, and more **functional-style code**, especially for STL algorithms.
>**Lambda expressions** वो ** (एनोनिमस) anonymous functions** होती हैं (यानि ऐसी functions जिनका कोई नाम नहीं होता) जिन्हें हम **C++ code के अंदर inline** define कर सकते हैं। इनकी शुरुआत **C++11** में हुई थी, और इनका उपयोग करने से हम **ज़्यादा साफ़, छोटे और functional-style के कोड** लिख सकते हैं — खासकर जब हम **STL algorithms** जैसे `sort`, `for_each`, `count_if` आदि के साथ काम करते हैं।

---

## Definition:

A **lambda expression** is a **function-like object** you can define inline using the following syntax:

```cpp
[ capture_list ] ( parameters ) -> return_type {
    // function body
}
```

---

## Components:

| Component        | Description                                             |
| ---------------- | ------------------------------------------------------- |
| `[capture_list]` | What external variables to capture (by value/reference) |
| `(parameters)`   | Arguments to the lambda (optional if none)              |
| `-> return_type` | Return type (optional — compiler can deduce)            |
| `{ body }`       | Function logic                                          |

---

## Simple Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    auto sayHello = []() {
        cout << "Hello from lambda!" << endl;
    };

    sayHello(); // call lambda
}
```

---

## Example with Parameters and Return:

```cpp
auto add = [](int a, int b) -> int {
    return a + b;
};

cout << "Sum: " << add(10, 20);  // Output: 30
```

---

## Capture External Variables:

```cpp
int x = 5, y = 10;

auto sum = [x, y]() {
    return x + y;
};

cout << "Sum: " << sum(); // 15
```

You can also capture by **reference**:

```cpp
int z = 100;

auto update = [&z]() {
    z += 50;
};

update();
cout << z; // 150
```

---

## Lambda with STL Algorithms:

Lambda shines with STL like `sort()`, `for_each()`, etc.

```cpp
#include <algorithm>
#include <vector>
#include <iostream>
using namespace std;

int main() {
    vector<int> v = {5, 2, 8, 1};

    sort(v.begin(), v.end(), [](int a, int b) {
        return a > b;  // descending order
    });

    for (int x : v)
        cout << x << " "; // Output: 8 5 2 1
}
```

---

## Practical Examples

### ➤ Counting with Condition

```cpp
int count_even = count_if(v.begin(), v.end(), [](int x) {
    return x % 2 == 0;
});
```

### ➤ Using with `for_each`

```cpp
for_each(v.begin(), v.end(), [](int x) {
    cout << x << " ";
});
```
---
IMP Questions 1.
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	[]()->{};
return 0;
}
```
```
error: expected type-specifier before ‘{’ token
5 |         []()->{};
```
Questions 2.
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	[](){};
return 0;
}
```
```
Status :Successfully executed
```
Questions 3.
```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 5, b = 10;

    // Lambda that captures a and b, takes two parameters x, y, and returns sum
    auto add = [a, b](int x, int y) -> int {
        cout << "Captured a: " << a << ", b: " << b << endl;
        cout << "Passed x: " << x << ", y: " << y << endl;
        return a + b + x + y;
    };

    cout << "Total Sum: " << add(3, 7) << endl;

    return 0;
}
```
Output
```
Captured a: 5, b: 10
Passed x: 3, y: 7
Total Sum: 25
```
---

## Summary

| Feature       | Description                          |
| ------------- | ------------------------------------ |
| Purpose       | Anonymous inline function            |
| Return Type   | Optional (auto-deduced)              |
| Useful With   | `sort`, `for_each`, `count_if`, etc. |
| Captures      | `[ ]` by value, `[&]` by reference   |
| Introduced in | C++11                                |

---




