Control structures in C++ are fundamental programming constructs that manage the flow of execution in a program. They are mainly categorized into **decision-making**, **looping**, and **branching** structures.

---

## 1. **Decision-Making Statements**

### a. **if Statement**

**Syntax:**

```cpp
if (condition) {
    // code to execute if condition is true
}
```

**Example:**

```cpp
int age = 20;
if (age >= 18) {
    cout << "You are eligible to vote.";
}
```

---

### b. **if-else Statement**

**Syntax:**

```cpp
if (condition) {
    // code if condition is true
} else {
    // code if condition is false
}
```

**Example:**

```cpp
int age = 16;
if (age >= 18) {
    cout << "Eligible to vote";
} else {
    cout << "Not eligible to vote";
}
```

---

### c. **else-if Ladder**

**Syntax:**

```cpp
if (condition1) {
    // code
} else if (condition2) {
    // code
} else {
    // default code
}
```

**Example:**

```cpp
int marks = 85;
if (marks >= 90) {
    cout << "Grade A";
} else if (marks >= 75) {
    cout << "Grade B";
} else {
    cout << "Grade C";
}
```

---

### d. **switch Statement**

**Syntax:**

```cpp
switch (expression) {
    case value1:
        // code
        break;
    case value2:
        // code
        break;
    default:
        // default code
}
```

**Example:**

```cpp
int day = 3;
switch (day) {
    case 1: cout << "Monday"; break;
    case 2: cout << "Tuesday"; break;
    case 3: cout << "Wednesday"; break;
    default: cout << "Invalid day";
}
```

---

## 2. **Looping Statements**

### a. **for Loop**

**Syntax:**

```cpp
for (initialization; condition; increment) {
    // code
}
```

**Example:**

```cpp
for (int i = 1; i <= 5; i++) {
    cout << i << " ";
}
```

---

### b. **while Loop**

**Syntax:**

```cpp
while (condition) {
    // code
}
```

**Example:**

```cpp
int i = 1;
while (i <= 5) {
    cout << i << " ";
    i++;
}
```

---

### c. **do-while Loop**

**Syntax:**

```cpp
do {
    // code
} while (condition);
```

**Example:**

```cpp
int i = 1;
do {
    cout << i << " ";
    i++;
} while (i <= 5);
```

---
## 2. **Range-Based For Loop (C++11 and later)**
```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> numbers = {10, 20, 30, 40, 50};
    // OR
    // int numbers[] = {10, 20, 30, 40, 50};

    // Range-based for loop
    for (int num : numbers) {
        cout << num << " ";
    }

    return 0;
}

```
Output
```
10 20 30 40 50 
```
---

## 3. **Branching Statements**

### a. **break Statement**

Used to exit a loop or switch statement early.

**Example:**

```cpp
for (int i = 1; i <= 10; i++) {
    if (i == 5) break;
    cout << i << " ";
}
```

---

### b. **continue Statement**

Skips the current iteration of a loop.

**Example:**

```cpp
for (int i = 1; i <= 5; i++) {
    if (i == 3) continue;
    cout << i << " ";
}
```

---

### c. **goto Statement**

**Note:** Use is discouraged in modern C++ due to readability issues.

**Syntax:**

```cpp
goto label;
// code
label:
// code
```

**Example:**

```cpp
int x = 1;
goto skip;
cout << "This will not print";
skip:
cout << "Goto used!";
```

---
[⬅️ Operators](/Operators.md)         |        [Functions ➡️](/functions.md)
---
## **License**
This project is licensed under the MIT License.

---

Happy Coding!

