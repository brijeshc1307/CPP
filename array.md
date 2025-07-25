In C++, **an array** is a collection of **elements of the same data type**, stored in **contiguous memory locations**. Arrays are used to store multiple values in a single variable, instead of declaring separate variables for each value.

---

### **Why Use Arrays?**

* To group related data together
* To reduce code complexity (especially when using loops)
* To access elements by index easily

---

## Declaration and Initialization of Arrays

```cpp
#include <iostream>
using namespace std;

int main() {
    int numbers[5] = {10, 20, 30, 40, 50};

    for (int i = 0; i < 5; i++) {
        cout << "Element at index " << i << " is " << numbers[i] << endl;
    }

    return 0;
}
```

### Output:

```
Element at index 0 is 10
Element at index 1 is 20
Element at index 2 is 30
Element at index 3 is 40
Element at index 4 is 50
```
>Note: ```int numbers[n];``` standard C++ में invalid है, क्योंकि C++ को array की size compile-time पर पता होनी चाहिए। Best practice नहीं मानी जाती। अगर आप run-time पर size लेना चाहते हैं, तो: 1. ```new``` और ```delete[]``` use करें (manual memory management) or 2. ```std::vector``` use करें (modern C++ approach)।

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin>>n;
    int numbers[n] = {10, 20, 30, 40, 50};

    for (int i = 0; i < n; i++) {
        cout << "Element at index " << i << " is " << numbers[i] << endl;
    }

    return 0;
}
```

### Output:

```
Element at index 0 is 10
Element at index 1 is 20
Element at index 2 is 30
Element at index 3 is 40
Element at index 4 is 50
```

---

## Types of Arrays in C++

| Type              | Description                                  | Example                   |
| ----------------- | -------------------------------------------- | ------------------------- |
| 1D Array          | One-dimensional, linear array                | `int arr[5];`             |
| 2D Array          | Matrix-like array (rows & columns)           | `int matrix[3][3];`       |
| Multi-D Array     | 3D or higher-dimensional arrays              | `int tensor[2][3][4];`    |
| Character Array   | Array of characters (like a string)          | `char name[10] = "John";` |
| Array of Pointers | Holds memory addresses                       | `int* ptrArr[5];`         |
| Dynamic Array     | Size can be set during runtime (heap memory) | `int* arr = new int[n];`  |

---

## 1. One-Dimensional Array

```cpp
int marks[4] = {90, 80, 85, 70};
```

---

## 2. Two-Dimensional Array

```cpp
int matrix[2][3] = {
    {1, 2, 3},
    {4, 5, 6}
};
```

### Access:

```cpp
cout << matrix[1][2];  // Output: 6
```

---

## 3. Multi-Dimensional Array (3D Example)

```cpp
int arr[2][2][2] = {
    { {1, 2}, {3, 4} },
    { {5, 6}, {7, 8} }
};
```

---

## 4. Character Array (C-style string)

```cpp
char name[6] = "Alice"; // Includes null character '\0'
```

---

## 5. Array of Pointers

```cpp
int a = 10, b = 20;
int* arr[2] = {&a, &b};
cout << *arr[1];  // Output: 20
```

---

## 6. Dynamic Array

```cpp
int n = 5;
int* arr = new int[n];

for (int i = 0; i < n; i++) {
    arr[i] = i + 1;
}

delete[] arr;  // Free the memory
```

---

## Key Points:

* Indexing starts from 0
* Size must be known at compile time for static arrays
* Use `new` and `delete` for dynamic memory allocation

---

### Common Matrix Formulas

| **Operation**             | **Formula (Math Notation)**                                                 | **Description**                                        |
| ------------------------- | --------------------------------------------------------------------------- | ------------------------------------------------------ |
| **Transpose**             | $A^T$                                                                       | Flip matrix $A$ over its diagonal                      |
| **Addition**              | $C = A + B$                                                                 | Add corresponding elements: $c_{ij} = a_{ij} + b_{ij}$ |
| **Subtraction**           | $C = A - B$                                                                 | Subtract corresponding elements                        |
| **Scalar Multiplication** | $B = kA$                                                                    | Multiply each element by scalar $k$                    |
| **Matrix Multiplication** | $C = AB$                                                                    | $c_{ij} = \sum_{k=1}^n a_{ik} \cdot b_{kj}$            |
| **Determinant (2×2)**     | $\det(A) = ad - bc$, for $A = \begin{bmatrix} a & b \\ c & d \end{bmatrix}$ | Scalar value representing the area/volume scale        |
| **Inverse (2×2)**         | $A^{-1} = \frac{1}{\det(A)} \begin{bmatrix} d & -b \\ -c & a \end{bmatrix}$ | Exists only if $\det(A) \neq 0$                        |
| **Identity Matrix**       | $I$, such that $AI = IA = A$                                                | Diagonal matrix with 1’s on diagonal                   |
| **Symmetric Matrix**      | $A = A^T$                                                                   | Equal to its own transpose                             |
| **Orthogonal Matrix**     | $A^T A = AA^T = I$                                                          | Inverse equals transpose                               |
| **Trace**                 | $\text{Tr}(A) = \sum_{i=1}^n a_{ii}$                                        | Sum of diagonal elements                               |
| **Rank**                  | $\text{rank}(A)$                                                            | Number of linearly independent rows/columns            |

---

###  1. **Matrix Transpose**

```cpp
for (int i = 0; i < rows; ++i) {
    for (int j = 0; j < cols; ++j) {
        transpose[j][i] = matrix[i][j];
    }
}
```

---

###  2. **Matrix Addition**

```cpp
for (int i = 0; i < rows; ++i) {
    for (int j = 0; j < cols; ++j) {
        result[i][j] = A[i][j] + B[i][j];
    }
}
```

---

###  3. **Matrix Subtraction**

```cpp
for (int i = 0; i < rows; ++i) {
    for (int j = 0; j < cols; ++j) {
        result[i][j] = A[i][j] - B[i][j];
    }
}
```

---

###  4. **Scalar Multiplication**

```cpp
for (int i = 0; i < rows; ++i) {
    for (int j = 0; j < cols; ++j) {
        result[i][j] = k * A[i][j];
    }
}
```

---

###  5. **Matrix Multiplication**

```cpp
for (int i = 0; i < rowsA; ++i) {
    for (int j = 0; j < colsB; ++j) {
        result[i][j] = 0;
        for (int k = 0; k < colsA; ++k) {
            result[i][j] += A[i][k] * B[k][j];
        }
    }
}
```

---

###  6. **Determinant (2x2 Matrix)**

```cpp
int det = (A[0][0] * A[1][1]) - (A[0][1] * A[1][0]);
```

---

###  7. **Inverse (2x2 Matrix)**

```cpp
float det = A[0][0] * A[1][1] - A[0][1] * A[1][0];
if (det != 0) {
    inverse[0][0] =  A[1][1] / det;
    inverse[0][1] = -A[0][1] / det;
    inverse[1][0] = -A[1][0] / det;
    inverse[1][1] =  A[0][0] / det;
}
```

---

###  8. **Identity Matrix (n x n)**

```cpp
for (int i = 0; i < n; ++i) {
    for (int j = 0; j < n; ++j) {
        I[i][j] = (i == j) ? 1 : 0;
    }
}
```

---

###  9. **Trace of a Square Matrix**

```cpp
int trace = 0;
for (int i = 0; i < n; ++i) {
    trace += matrix[i][i];
}
```

---

###  10. **Check Symmetric Matrix**

```cpp
bool isSymmetric = true;
for (int i = 0; i < n; ++i) {
    for (int j = 0; j < n; ++j) {
        if (matrix[i][j] != matrix[j][i]) {
            isSymmetric = false;
            break;
        }
    }
}
```

---
[⬅️ Pointers](/Pointers.md)        |  [Strings ➡️](/string.md) 
---
## **License**
This project is licensed under the MIT License.

---

Happy Coding!

