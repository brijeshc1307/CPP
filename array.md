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

## **2. Static Arrays**

### Definition:

Fixed-size arrays where the size is known at compile-time.

### Use:

Efficient for small data sets with known size.

### Example:

```cpp
int arr[100]; // Static array of size 100
```

---

## **3. Prefix Sums**

### Definition:

An array where each element at index `i` stores the sum of the array elements from index `0` to `i`.

### Use:

Used to quickly calculate sum of subarrays in O(1) after O(n) preprocessing.

### Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[] = {1, 2, 3, 4, 5};
    int n = 5;
    int prefix[n];
    prefix[0] = arr[0];
    for (int i = 1; i < n; i++) {
        prefix[i] = prefix[i - 1] + arr[i];
    }
    int l = 1, r = 3; // sum from index 1 to 3
    int sum = prefix[r] - (l > 0 ? prefix[l - 1] : 0);
    cout << "Sum from " << l << " to " << r << " is " << sum;
    return 0;
}
```

---

## **4. Kadane’s Algorithm (Maximum Subarray Sum)**

### Definition:

Algorithm to find the maximum sum of a contiguous subarray in O(n) time.

### Use:

Useful in dynamic programming and stock market-related problems.

### Example:

```cpp
#include <iostream>
#include <algorithm>
using namespace std;

int main() {
    int arr[] = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
    int n = sizeof(arr) / sizeof(arr[0]);
    int maxSoFar = arr[0], maxEndingHere = arr[0];
    
    for (int i = 1; i < n; i++) {
        maxEndingHere = max(arr[i], maxEndingHere + arr[i]);
        maxSoFar = max(maxSoFar, maxEndingHere);
    }
    cout << "Maximum subarray sum is " << maxSoFar;
    return 0;
}
```

---

## **5. Dutch National Flag Algorithm**

### Definition:

An algorithm to sort an array of 0s, 1s, and 2s in a single pass.

### Use:

Optimized sorting for three types of elements.

### Example:

```cpp
#include <iostream>
using namespace std;

void sortColors(int arr[], int n) {
    int low = 0, mid = 0, high = n - 1;
    while (mid <= high) {
        if (arr[mid] == 0)
            swap(arr[low++], arr[mid++]);
        else if (arr[mid] == 1)
            mid++;
        else
            swap(arr[mid], arr[high--]);
    }
}

int main() {
    int arr[] = {2, 0, 2, 1, 1, 0};
    int n = 6;
    sortColors(arr, n);
    for (int i = 0; i < n; i++) cout << arr[i] << " ";
    return 0;
}
```

---

## **6. Two Pointer Technique**

### Definition:

Using two pointers (indices) to scan the array from different directions.

### Use:

Useful in problems involving pairs or triplets, especially in sorted arrays.

### Example:

**Find if a pair exists with a given sum**

```cpp
#include <iostream>
#include <algorithm>
using namespace std;

bool hasPairWithSum(int arr[], int n, int target) {
    sort(arr, arr + n);
    int left = 0, right = n - 1;
    while (left < right) {
        int sum = arr[left] + arr[right];
        if (sum == target) return true;
        else if (sum < target) left++;
        else right--;
    }
    return false;
}

int main() {
    int arr[] = {1, 4, 45, 6, 10, -8};
    int target = 16;
    int n = sizeof(arr) / sizeof(arr[0]);
    cout << (hasPairWithSum(arr, n, target) ? "Yes" : "No");
    return 0;
}
```

---

## **7. Sliding Window Technique**

### Definition:

A technique to maintain a "window" of elements and slide it over the array to optimize time complexity.

### Use:

Efficient for problems involving subarrays like max sum, averages, or distinct elements.

### Example:

**Find max sum of subarray of size k**

```cpp
#include <iostream>
using namespace std;

int maxSum(int arr[], int n, int k) {
    int maxSum = 0, windowSum = 0;

    for (int i = 0; i < k; i++)
        windowSum += arr[i];
    
    maxSum = windowSum;

    for (int i = k; i < n; i++) {
        windowSum += arr[i] - arr[i - k];
        maxSum = max(maxSum, windowSum);
    }

    return maxSum;
}

int main() {
    int arr[] = {100, 200, 300, 400};
    int k = 2;
    int n = sizeof(arr) / sizeof(arr[0]);
    cout << "Maximum sum of subarray of size " << k << " is " << maxSum(arr, n, k);
    return 0;
}
```

---

## Common Problems Involving Arrays:

1. **Reverse an array**
2. **Find the missing number in array**
3. **Check if array is a palindrome**
4. **Find the majority element (Moore's Voting)**
5. **Merge two sorted arrays**
6. **Find the first repeating element**
7. **Longest subarray with given sum**
8. **Find all subarrays with 0 sum**
9. **Move all zeroes to end**
10. **Rotate array by k positions**

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
[⬅️ Smart Pointers](/smartPointers.md)        |  [Strings ➡️](/string.md) 
---
## **License**
This project is licensed under the MIT License.

---

Happy Coding!

