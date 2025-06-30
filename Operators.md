##  Operators in C++

Operators are symbols that perform operations on variables and values. C++ supports various types of operators:

---

### 1. **Arithmetic Operators**

| Operator | Description         | Example |
| -------- | ------------------- | ------- |
| `+`      | Addition            | `a + b` |
| `-`      | Subtraction         | `a - b` |
| `*`      | Multiplication      | `a * b` |
| `/`      | Division            | `a / b` |
| `%`      | Modulus (remainder) | `a % b` |

**Example**:

```cpp
int a = 10, b = 3;
cout << a + b << endl;  // 13
cout << a % b << endl;  // 1
```

---

### 2. **Relational (Comparison) Operators**

| Operator | Description           | Example  |
| -------- | --------------------- | -------- |
| `==`     | Equal to              | `a == b` |
| `!=`     | Not equal to          | `a != b` |
| `>`      | Greater than          | `a > b`  |
| `<`      | Less than             | `a < b`  |
| `>=`     | Greater than or equal | `a >= b` |
| `<=`     | Less than or equal    | `a <= b` |

**Example**:

```cpp
cout << (a > b);  // Outputs 1 (true)
```

---

### 3. **Logical Operators**
```markdown
| Operator | Description | Example           |  
| -------- | ----------- | ----------------- | 
| `&&`     | Logical AND | `a > 5 && b < 10` |   
| `||`     | Logical OR  | `a > 5 || b < 10` |  
| `!`      | Logical NOT | `!(a == b)`       |
```

**Example**:

```cpp
if (a > 5 && b < 10) {
    cout << "Condition true";
}
```

---

### 4. **Assignment Operators**

| Operator | Description         | Example  |
| -------- | ------------------- | -------- |
| `=`      | Assign value        | `a = 5`  |
| `+=`     | Add and assign      | `a += 3` |
| `-=`     | Subtract and assign | `a -= 2` |
| `*=`     | Multiply and assign | `a *= 4` |
| `/=`     | Divide and assign   | `a /= 2` |
| `%=`     | Modulus and assign  | `a %= 3` |

---

### 5. **Increment/Decrement Operators**

| Operator | Description | Example        |
| -------- | ----------- | -------------- |
| `++`     | Increment   | `++a` or `a++` |
| `--`     | Decrement   | `--a` or `a--` |

**Example**:

```cpp
int x = 5;
cout << ++x;  // Outputs 6
cout << x--;  // Outputs 6 (then x becomes 5)
```

---

### 6. **Bitwise Operators**
```markdown
| Operator | Description | Example    |    
| -------- | ----------- | ---------- | 
| `&`      | Bitwise AND | `a & b`    |    
| `|`      | Bitwise OR  | `a | b`    |
| `^`      | Bitwise XOR | `a ^ b`    |    
| `~`      | Bitwise NOT | `~a`       |   
| `<<`     | Left shift  | `a << 1`   |    
| `>>`     | Right shift | `a >> 1`   |   
```
---

### 7. **Conditional (Ternary) Operator**

| Operator | Description             | Example         |
| -------- | ----------------------- | --------------- |
| `?:`     | Short if-else condition | `a > b ? a : b` |

**Example**:

```cpp
int max = (a > b) ? a : b;
```

---

### 8. **Sizeof Operator**

| Operator | Description          | Example       |
| -------- | -------------------- | ------------- |
| `sizeof` | Returns size of type | `sizeof(int)` |

---

### 9. **Typecast Operator**

| Operator | Description                  | Example               |
| -------- | ---------------------------- | --------------------- |
| `(type)` | Converts one type to another | `float f = (float)a;` |

---

### 10. **Pointer Operators**

| Operator | Description                    | Example |
| -------- | ------------------------------ | ------- |
| `*`      | Value at address (dereference) | `*ptr`  |
| `&`      | Address of a variable          | `&a`    |

---

## Example using multiple operators:

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 5, b = 3;
    int max = (a > b) ? a : b; // ternary
    cout << "Max: " << max << endl;
    cout << "Sum: " << a + b << endl;
    cout << "Bitwise AND: " << (a & b) << endl;
    return 0;
}
```

---

### Common Bitwise Operations and Their Logic:

  * **Checking if a number is odd/even:**

      * **Logic:** The least significant bit (LSB) of an odd number is always `1`, and for an even number, it's `0`.
      * **Formula:** `(n & 1)`
          * If `(n & 1)` evaluates to `1`, `n` is odd.
          * If `(n & 1)` evaluates to `0`, `n` is even.

  * **Setting a specific bit:**

      * **Logic:** Use Bitwise OR with a mask where only the target bit is `1`.
      * **Formula (set $k$-th bit from right, 0-indexed):** `n | (1 << k)`

  * **Clearing a specific bit:**

      * **Logic:** Use Bitwise AND with a mask where only the target bit is `0`.
      * **Formula (clear $k$-th bit from right, 0-indexed):** `n & (~(1 << k))`

  * **Toggling a specific bit:**

      * **Logic:** Use Bitwise XOR with a mask where only the target bit is `1`.
      * **Formula (toggle $k$-th bit from right, 0-indexed):** `n ^ (1 << k)`

  * **Checking if a specific bit is set:**

      * **Logic:** Use Bitwise AND with a mask where only the target bit is `1`. If the result is non-zero, the bit was set.
      * **Formula (check $k$-th bit from right, 0-indexed):** `(n >> k) & 1` or `(n & (1 << k))`

  * **Multiplying by $2^k$:**

      * **Logic:** Left shift `k` times.
      * **Formula:** `n << k`

  * **Dividing by $2^k$ (integer division):**

      * **Logic:** Right shift `k` times.
      * **Formula:** `n >> k`

  * **Converting uppercase to lowercase (for ASCII characters):**

      * **Logic:** The 6th bit (0-indexed from right) differentiates uppercase and lowercase letters in ASCII. Setting this bit converts uppercase to lowercase.
      * **Formula:** `char | (1 << 5)` (or `char | 32`)

  * **Converting lowercase to uppercase (for ASCII characters):**

      * **Logic:** Clearing the 6th bit (0-indexed from right) converts lowercase to uppercase.
      * **Formula:** `char & (~(1 << 5))` (or `char & (~32)`)
        
* **Checking if a number is a power of 2:**
    * **Logic:** A positive integer is a power of 2 if and only if it has exactly one bit set to `1` in its binary representation. For example, $4 (0100_2)$, $8 (1000_2)$, etc. Subtracting 1 from a power of 2 turns its set bit into `0` and all bits to its right into `1`s. For example, $8 (1000_2)$ becomes $7 (0111_2)$. When you `AND` a power of 2 with `(power_of_2 - 1)`, the result will be `0`.
    * **Formula:** `(n > 0) && ((n & (n - 1)) == 0)`
        * The `(n > 0)` part is essential because $0$ is not considered a power of 2, and `(0 & -1)` would also be $0$.

* **Counting the number of set bits (population count/Hamming weight):**
    * **Logic (Brian Kernighan's Algorithm):** This efficient algorithm repeatedly unsets the least significant set bit until the number becomes `0`. Each unsetting counts as one set bit. The operation `n & (n - 1)` clears the rightmost set bit in `n`.
    * **Formula:**
        ```
        count = 0
        while (n > 0):
            n = n & (n - 1)
            count = count + 1
        return count
        ```

* **Finding the position of the least significant set bit (LSB):**
    * **Logic:** The expression `n & (-n)` (using two's complement for `-n`) isolates the least significant set bit. This is because in two's complement, `-n` is equivalent to `~n + 1`. When you `AND` `n` with `~n + 1`, all bits cancel out except for the rightmost set bit of `n`.
    * **Formula (value of LSB):** `n & (-n)`
    * **Formula (position of LSB, 0-indexed):** This often requires `log2` or a loop.
        ```
        pos = 0
        val_lsb = n & (-n)
        while ((1 << pos) != val_lsb):
            pos = pos + 1
        return pos
        ```
        (Many languages have built-in functions for this, e.g., `__builtin_ctz` in GCC/Clang for "count trailing zeros").

* **Flipping all bits from a given position to the end (masking):**
    * **Logic:** Create a mask that has `1`s from the target position to the rightmost bit, and `0`s elsewhere. Then `XOR` the number with this mask.
    * **Formula (flip bits from $k$-th position to right, 0-indexed):** `n ^ ((1 << (k + 1)) - 1)`
        * `1 << (k + 1)` creates a number with a `1` at position `k+1` and `0`s elsewhere (e.g., if `k=2`, this is `1000_2`).
        * Subtracting `1` from it creates a mask with `1`s from `k` down to `0` (e.g., `1000_2 - 1 = 0111_2`).

* **Checking if two numbers have opposite signs:**
    * **Logic:** In two's complement, the most significant bit (MSB) indicates the sign (0 for positive, 1 for negative). If two numbers have opposite signs, their MSBs will be different. The XOR operation on the two numbers will result in a negative number (MSB `1`) if their signs were different.
    * **Formula:** `(x ^ y) < 0`

* **Absolute value without branching (for integers):**
    * **Logic:** This clever trick utilizes the properties of two's complement and right shifts.
        * For positive `n`, `n >> 31` (for a 32-bit int) is $0$. So `n ^ 0 - 0 = n`.
        * For negative `n`, `n >> 31` is $-1$ (all `1`s). Let `mask = n >> 31`.
        * `n ^ mask` flips all bits of `n` (effectively one's complement).
        * Adding `mask` (which is `-1` or all `1`s) to the result of `n ^ mask` completes the two's complement conversion, giving the absolute value.
    * **Formula (for 32-bit signed integer):**
        ```
        int mask = n >> 31; // Fills with 0s if positive, 1s if negative
        return (n ^ mask) - mask;
        ```
        * More generally, `(n + mask) ^ mask` is also a common form.

* **Swapping two numbers without a temporary variable:**
    * **Logic:** The XOR swap algorithm uses the property that `A ^ B ^ B = A` and `A ^ A = 0`.
    * **Formula:**
        ```
        a = a ^ b;
        b = a ^ b; // b = (original_a ^ original_b) ^ original_b = original_a
        a = a ^ b; // a = (original_a ^ original_b) ^ original_a = original_b
        ```

* **Getting the maximum or minimum of two numbers without branching:**
    * **Logic (for max):** This uses the sign bit after XORing. If `x >= y`, `x - y` is positive, so `(x - y) >> 31` is $0$. Then `x ^ 0 = x`. If `x < y`, `x - y` is negative, so `(x - y) >> 31` is $-1$. Then `x ^ -1` flips `x`'s bits, and `(x ^ -1) + y` leads to `y`. This is more complex than simple `max` functions.
    * **Formula (for max, assuming 32-bit signed int, more complex/less intuitive than `abs` one):**
        ```
        int diff = x - y;
        int sign_bit = (diff >> 31); // 0 if diff >= 0, -1 if diff < 0
        return x - (sign_bit & diff);
        ```
        * **Alternative Max (using `abs` trick):** `return y + ((x - y) & ((x - y) >> (sizeof(int) * 8 - 1)));` (This is quite dense and relies on specific bit patterns).
        * Often, the simple `(x > y ? x : y)` is preferred for clarity unless extreme performance is *provably* needed and the compiler cannot optimize the branch.

* **Isolating the rightmost `0` bit:**
    * **Logic:** This is less common but useful in specific algorithms. If `n` has a `0` bit, then `~n` will have a `1` bit at that position. `n | (~n + 1)` will set the rightmost `0` bit to `1` and clear bits to its right.
    * **Formula:** `~n & (n + 1)` (This isolates the rightmost `0` bit. E.g., for `01011_2`, `~n` is `10100_2`. `n+1` is `01100_2`. `~n & (n+1)` is `00100_2`)

* **Turning off the rightmost `1` bit:**
    * **Logic:** Same as Brian Kernighan's algorithm.
    * **Formula:** `n & (n - 1)`

* **Turning on the rightmost `0` bit:**
    * **Logic:** `OR` the number with its complement plus one.
    * **Formula:** `n | (n + 1)` (e.g., $5 (0101_2)$ -> $5+1=6 (0110_2)$. $0101_2 | 0110_2 = 0111_2 = 7$).

* **Clearing bits from LSB to $k$-th bit:**
    * **Logic:** Create a mask that has `0`s from the LSB up to the $k$-th bit and `1`s for all bits higher than $k$. Then `AND` with `n`.
    * **Formula:** `n & (~((1 << (k + 1)) - 1))` (This creates a mask like `...111000...000` where the `0`s are up to the $k$-th bit).

* **Clearing bits from $k$-th bit to MSB:**
    * **Logic:** Create a mask that has `1`s from LSB up to the $k$-th bit and `0`s for all bits higher than $k$. Then `AND` with `n`.
    * **Formula:** `n & ((1 << (k + 1)) - 1)` (This creates a mask like `000...0111...111` where the `1`s are up to the $k$-th bit).

### Important Considerations:

* **Signed vs. Unsigned Integers:** Bitwise operations behave differently with signed and unsigned integers, especially right shifts (`>>`). Unsigned right shifts (`>>>`) always fill with `0`s. Signed right shifts (`>>`) typically replicate the sign bit (arithmetic right shift).
* **Integer Size:** The number of bits in an integer (e.g., 32-bit, 64-bit) affects the results of operations like `~` (bitwise NOT) and shifts, as it determines the total bit pattern.
* **Compiler Optimizations:** Modern compilers are very good at optimizing code. Sometimes, a straightforward logical comparison or arithmetic operation might be optimized by the compiler into bitwise instructions, making manual bitwise tricks unnecessary for performance. Always profile if optimization is critical.
* **Readability:** Bitwise operations can be less readable than their conventional counterparts. Use them when they offer a clear performance advantage or are the most natural way to express a specific bit manipulation.

This extended list provides a more comprehensive overview of common bitwise operations and their underlying logic, which are essential tools in a programmer's arsenal.

---
Next: [Control Structures](/ControlStructures.md)
---
## **License**
This project is licensed under the MIT License.

---

Happy Coding!


