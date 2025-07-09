### Lambda Expressions in C++ (Anonymous Functions)

**Lambda expressions** are **anonymous functions** (i.e., functions without a name) that can be defined **inline** within C++ code. Introduced in **C++11**, they help write **cleaner**, **shorter**, and more **functional-style code**, especially for STL algorithms.

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

## Summary

| Feature       | Description                          |
| ------------- | ------------------------------------ |
| Purpose       | Anonymous inline function            |
| Return Type   | Optional (auto-deduced)              |
| Useful With   | `sort`, `for_each`, `count_if`, etc. |
| Captures      | `[ ]` by value, `[&]` by reference   |
| Introduced in | C++11                                |

---

### Want:

* Capture default rules?
* Mutable lambdas?
* Lambdas with threads?


