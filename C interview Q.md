### 1. What is the difference between declaration and definition of a variable/function?

* **Declaration:** Tells the compiler about the variable's or function's name and type but does **not** allocate memory or provide the body (for functions). It informs the compiler about its existence.
  Example:

  ```c
  extern int x;      // Declaration of variable x
  int func(int);     // Declaration of function func
  ```

* **Definition:** Actually allocates memory (for variables) or provides the function body (for functions). It fully implements the variable or function.
  Example:

  ```c
  int x;             // Definition of variable x
  int func(int a) {  // Definition of function func
      return a + 1;
  }
  ```

---

### 2. What is scope of a variable? How are variables scoped in C?

* **Scope:** The region of the program where a variable is visible and can be accessed.

* In C, variables have different scopes:

  * **Block scope:** Variables declared inside a block `{}` are only accessible within that block.
  * **Function scope:** Labels used with `goto` have function scope.
  * **File scope (global):** Variables declared outside any function have global scope, accessible throughout the file and potentially other files if declared with `extern`.
  * **Function prototype scope:** Parameters in function declarations.

Example:

```c
int globalVar;      // Global scope

void func() {
    int localVar;   // Local/block scope
}
```

---

### 3. How will you print "Hello World" without semicolon?

You can avoid semicolon in `printf` using alternatives like `if` or loops.

Example:

```c
#include <stdio.h>

int main() {
    if (printf("Hello World\n")) {}
    return 0;
}
```

* Here, semicolon is part of `if` statement but not after `printf`.

---

### 4. Write down the smallest executable code?

Smallest valid C program:

```c
int main() { return 0; }
```

This compiles and runs without error.

---

### 5. What are entry control and exit control loops?

* **Entry control loop:** The condition is checked before the loop body executes.

  * Examples: `for`, `while` loops.
* **Exit control loop:** The condition is checked after the loop body executes at least once.

  * Example: `do-while` loop.

---

### 6. Why pre-processor directive does not have a semicolon at last?

Preprocessor directives (like `#include`, `#define`) are instructions to the compiler's preprocessor, **not actual C statements**, so they don’t require semicolons. They are handled before compilation.

---

### 7. What is the difference between including the header file within angular braces `< >` and double quotes `" "`?

* `<header.h>`: Search for the header file in the system directories (standard library).
* `"header.h"`: Search in the current directory first, then system directories.

---

### 8. Why does “type demotion” not exist instead of “type promotion”?

* **Type promotion** means converting a smaller type to a larger one to avoid data loss (e.g., `char` to `int`).
* **Type demotion** (losing data by converting larger to smaller) is avoided because it can cause data loss.
* Hence, only promotion is standard and automatic in C.

---

### 9. Difference between `#include` in C and `import` in Java?

* `#include` copies the entire contents of the specified file into the source file before compilation (preprocessor directive).
* `import` in Java tells the compiler where to find classes but does **not** copy code. Java uses packages and class loading.

---

### 10. What are local static variables? What is their use?

* Variables declared as `static` inside functions retain their value between function calls but are only visible inside the function.
* Useful for preserving state without using global variables.

Example:

```c
void func() {
    static int count = 0;
    count++;
    printf("%d\n", count);
}
```

---

### 11. Can we declare a variable with the same name in two different functions?

* Yes. Each function has its own scope, so variables with the same name in different functions do not interfere.

---

### 12. What are main characteristics of C language?

* Procedural language
* Efficient and fast
* Low-level memory access (pointers)
* Portable across platforms
* Supports structured programming
* Rich set of operators
* Modular programming support (functions)

---

### 13. What is the difference between `i++` and `++i`?

* `i++`: Post-increment — returns the original value, then increments.
* `++i`: Pre-increment — increments first, then returns the incremented value.

---

### 14. What is l-value?

* **l-value** refers to an expression that refers to a memory location and can appear on the left side of an assignment.

Example:
In `x = 5;`, `x` is an l-value.

---

### 15. How will you print numbers from 1 to 100 without using loop?

Using recursion:

```c
#include <stdio.h>

void printNumbers(int n) {
    if (n <= 100) {
        printf("%d\n", n);
        printNumbers(n + 1);
    }
}

int main() {
    printNumbers(1);
    return 0;
}
```

---

### 16. What is volatile keyword?

* Tells the compiler that the variable can be changed unexpectedly (e.g., by hardware or another thread), so it should **not optimize** by caching the value.

---

### 17. Can a variable be both const and volatile?

* Yes. `const volatile` means the variable is read-only from the program's perspective but can change outside the program’s control.

Example: hardware registers.

---

### 18. What happens if you use an uninitialized variable in C?

* Its value is **undefined** (garbage value), leading to unpredictable behavior.

---

### 19. What is `while(1)` and how does it work?

* An infinite loop because the condition is always true.
* It runs endlessly until broken explicitly (e.g., using `break`).

---

### 20. What is the difference between local and global variables in C and what happens when a local variable has the same name as a global variable?

* **Global variable:** Declared outside any function, accessible throughout the file.

* **Local variable:** Declared inside a function or block, accessible only there.

* When a local variable has the same name as a global variable, **local variable shadows** the global one inside its scope.


---

### 1. How can we create an infinite loop in C?

Several ways:

* Using `while`:

  ```c
  while(1) {
      // infinite loop
  }
  ```

* Using `for`:

  ```c
  for(;;) {
      // infinite loop
  }
  ```

* Using `do-while`:

  ```c
  do {
      // infinite loop
  } while(1);
  ```

---

### 2. What is type conversion, and difference between implicit conversion and explicit type casting?

* **Type conversion:** Changing one data type into another.

* **Implicit conversion (Type coercion):** Done automatically by the compiler.
  Example:

  ```c
  int i = 10;
  float f = i;  // int implicitly converted to float
  ```

* **Explicit type casting:** Programmer forces conversion using cast operator.
  Example:

  ```c
  float f = 3.14;
  int i = (int)f;  // explicitly cast float to int
  ```

---

### 3. What’s the difference between `=` and `==` in C?

* `=` is the **assignment** operator, assigns value to a variable.
* `==` is the **equality comparison** operator, checks if two values are equal.

---

### 4. Why can't we use reserved keywords as variable names?

* Keywords are **reserved** by the language for specific syntax (e.g., `int`, `if`, `return`).
* Using them as variable names causes syntax errors/conflicts.

---

### 5. What happens if we do not use `break` in switch statement?

* Control **falls through** to the next case(s) until a `break` or the end of switch is reached.
* Can cause unintended code execution.

---

### 6. What will this code print?
```cpp
#include <stdio.h>

int main() {
    int a=0;
    if(a=1) printf("zero\n");
    else printf("non zero\n");
    return 0;
}

```
Output
```
Zero
```
* a = 1 is assignment, not comparison.
* So condition becomes true (since a is now 1, no matter what value of a is before if condition), and hence it prints: zero.

---

### 7. What does this loop print?
```cpp
#include <stdio.h>

int main() {
    int i=0;
    while(i++ <3) printf("%d ",i);
    return 0;
}
```
Output
* i++ returns the current value, then increments.
* It prints: 1 2 3
```
1 2 3 
```

---

### 8. What is the result of this code?

```cpp
#include <stdio.h>

int main() {
    int x = 3;
    int y = ++x*2;
    printf("x: %d, y: %d",x,y);
    return 0;
}
````
Output
* ++x increments x to 4 first and then used in the expression.
* y = 4 * 2 -> y = 12
```
x: 4, y: 8
```

---

### 9. What is the final value of b?

```cpp
#include <stdio.h>

int main()
{
    int a = 0;
    int b = 0;
    if (a && b++)
        printf("hello\n");
    printf("%d", b);
    return 0;
}
````
Output

* a is 0 (false), & b is 0 (false), here b++ is not evaluated due to short-circuiting, as for any expression a && b, b will not be evaluated if a already turns out to be false because if a is false then, irrespective of any value of b the complete expression will always return to false.
* Output: 0, and "Hello" is not printed.
```
0
```

---

### 10. How are variables stored in memory and what is the role of data types?

* Variables are stored in **memory locations**; data types tell the compiler:

  * How much memory to allocate.
  * How to interpret the bits stored there (e.g., int, float).
* Different data types have different sizes (e.g., `int` usually 4 bytes, `char` 1 byte).

---

### 11. How does the if-else conditional work in C, and when is it better than switch?

* `if-else` evaluates a **boolean condition** and executes blocks accordingly.
* Better than `switch` when:

  * Conditions are ranges or complex expressions (not just equality).
  * You need to evaluate expressions or non-integer conditions.

---

### 12. Can you use `else` without `if` in C?

* **No**, `else` must follow an `if` statement.

---

### 13. What are the different types of operators in C?

* Arithmetic: `+`, `-`, `*`, `/`, `%`
* Relational: `==`, `!=`, `<`, `>`, `<=`, `>=`
* Logical: `&&`, `||`, `!`
* Bitwise: `&`, `|`, `^`, `~`, `<<`, `>>`
* Assignment: `=`, `+=`, `-=`, etc.
* Increment/Decrement: `++`, `--`
* Conditional (ternary): `?:`
* Comma operator: `,`
* sizeof operator

---

### 14. How does the switch statement work in C, and how is it different from if-else?

* `switch` compares an expression against multiple **constant** cases.
* `if-else` can use any conditional expression.
* `switch` is generally clearer for discrete values; `if-else` is more flexible.

---

### 15. What is the difference between break and continue statements in C?

* `break`: Exits the nearest loop or switch immediately.
* `continue`: Skips the rest of the current iteration and proceeds to next iteration of the loop.

---

### 16. What is the size of different data types in C and why does it matter?

Common sizes (may vary by system):

* `char`: 1 byte
* `int`: 4 bytes
* `float`: 4 bytes
* `double`: 8 bytes

Size matters for memory usage, alignment, and portability.

---

### 17. What is the role of the sizeof operator in C?

* Returns the size (in bytes) of a data type or variable at **compile-time**.
* Used to allocate memory or calculate buffer sizes.

Example:

```c
printf("%zu", sizeof(int));  // prints size of int
```

---

### 18. Can we use a char variable to store small numbers?

* Yes, `char` can store small integer values (typically -128 to 127 if signed).

---

### 19. What are different storage class specifiers in C?

* `auto`: Default for local variables (automatic storage).
* `register`: Hint to store variable in CPU register.
* `static`: Retains variable value between function calls or limits function/variable scope.
* `extern`: Declares a variable defined elsewhere (global).
* `typedef`: Creates type aliases (not storage class, but related).

---

### 20. What are static functions? What is their use?

* Functions declared with `static` have **internal linkage**, meaning they are visible **only within the file** they are declared.
* Used to hide functions from other files/modules, preventing name conflicts.

---
Alright! Here's a detailed explanation for each of your questions:

---

### 1. How to write your own sizeof operator?

You can mimic `sizeof` using a macro that calculates the difference between two pointers of the same type:

```c
#define my_sizeof(type) ((char *)(&type + 1) - (char *)(&type))
```

Explanation:

* `&type` gives address of the variable
* `&type + 1` points to the next element (like array indexing)
* Difference gives size in bytes

*Note:* This works for variables, not types directly. For types, you'd do:

```c
#define my_sizeof(type) ((size_t)(&((type *)0)[1]) - (size_t)(&((type *)0)[0]))
```

---

### 2. Why is C called a mid-level programming language?

* **Mid-level** because it combines features of both:

  * **Low-level:** Direct access to memory via pointers, hardware manipulation.
  * **High-level:** Structured programming, functions, abstractions.

Thus, it bridges between machine-level and high-level programming.

---

### 3. Why does `int a = 5 / 2;` give `2` instead of `2.5`?

* Both `5` and `2` are integers.
* Integer division truncates the decimal part.
* So, `5 / 2 = 2` (not 2.5).
* To get float result, cast at least one operand to float:

```c
float a = 5 / 2.0;  // or float a = (float)5 / 2;
```

---

### 4. What are preprocessor directives in C?

* Instructions executed **before compilation**.
* Start with `#`.
* Examples: `#include`, `#define`, `#ifdef`.
* Used to include files, macros, conditional compilation.

---

### 5. What are header files and their uses?

* Files containing **function prototypes**, macros, type definitions, constants.
* Included using `#include`.
* Helps share declarations across multiple source files.

Example: `stdio.h` declares `printf`, `scanf`.

---

### 6. What is the difference between macro and functions?

| Macro                                       | Function                        |
| ------------------------------------------- | ------------------------------- |
| Textual substitution by preprocessor        | Actual code executed at runtime |
| No type checking                            | Type checked                    |
| Can cause side effects (if used improperly) | Safer                           |
| Faster (no function call overhead)          | Slight overhead due to call     |
| Harder to debug                             | Easier to debug                 |

---

### 7. What is the use of static variables in C?

* Preserve value between function calls.
* Scope limited to block/function (if local static).
* Useful for counters or state retention without globals.

---

### 8. What is the difference between pass by value and pass by reference?

* **Pass by value:** Copy of variable passed; changes don’t affect original.
* **Pass by reference:** Address passed; changes affect original variable.

In C, pass by reference is simulated by passing pointers.

---

### 9. What is an auto keyword?

* Default storage class for local variables.
* Optional to specify; usually omitted.
* Variables stored on the stack and have automatic lifetime.

---

### 10. Write a program to print "Hello-World" without using a semicolon.

```c
#include <stdio.h>

int main() {
    if (printf("Hello-World\n")) {}
    return 0;
}
```

---

### 11. What is an extern keyword?

* Declares a variable/function defined in another file.
* Used for global variables shared across files.
* Tells compiler variable exists but defined elsewhere.

---

### 12. Explain format specifiers.

* Used in `printf` and `scanf` to specify variable type.
* Examples:

  * `%d` — integer
  * `%f` — float
  * `%c` — char
  * `%s` — string
  * `%lf` — double

---

### 13. What is the difference between `getc()`, `getchar()`, `getch()` and `getche()`?

| Function    | Description                                                  | Echoes Input?     | Standard C?           |
| ----------- | ------------------------------------------------------------ | ----------------- | --------------------- |
| `getc()`    | Reads a character from a file/stream                         | Depends on stream | Yes                   |
| `getchar()` | Reads a character from `stdin` (equivalent to `getc(stdin)`) | No                | Yes                   |
| `getch()`   | Reads a character without waiting for Enter, no echo         | No                | No (conio.h, Windows) |
| `getche()`  | Reads a character without waiting for Enter, echoes input    | Yes               | No (conio.h, Windows) |

---

### 14. Can we declare a function inside another function in C? If not, how do we mimic that behavior?

* **No**, C does not allow nested functions.
* Mimic using **static helper functions** or function pointers.

---

### 15. What is a syntax error vs a logical error in C?

* **Syntax error:** Violation of language grammar; caught by compiler.
* **Logical error:** Program compiles but produces incorrect results.

---

### 16. Why does `char c = 65;` print `A`?

* ASCII code for `A` is 65.
* Assigning 65 to `char` stores ASCII 'A'.
* Printing `c` with `%c` outputs 'A'.

---

### 17. What are pointers and when should we use pointers?

* Variables that store **memory addresses**.
* Used for dynamic memory, efficient array handling, function arguments (pass-by-reference), and data structures like linked lists.

---

### 18. What are static and dynamic memory allocations?

* **Static allocation:** Memory allocated at compile time (global/local variables).
* **Dynamic allocation:** Memory allocated at runtime using `malloc()`, `calloc()`, `realloc()`.

---

### 19. What is the difference between `malloc()` and `calloc()` in C?

| Function   | Initializes Memory?    | Arguments                        |
| ---------- | ---------------------- | -------------------------------- |
| `malloc()` | No (garbage values)    | Size in bytes                    |
| `calloc()` | Yes (initializes to 0) | Number of elements, size of each |

---

### 20. What do you mean by dangling pointers and how are dangling pointers different from memory leaks in C programming?

* **Dangling pointer:** Pointer pointing to memory that has been freed/deallocated. Using it causes undefined behavior.
* **Memory leak:** Allocated memory that is no longer accessible (no pointers pointing to it), causing wasted memory.


---

### 1. **What is a memory leak and how to avoid it?**

* **Memory Leak:** Happens when dynamically allocated memory is not freed, causing loss of access to that memory (still reserved but unusable).

  **Example:**

  ```c
  int *ptr = malloc(sizeof(int) * 100);
  // Forgot to free(ptr); — this is a memory leak
  ```

* **How to avoid:**

  * Always use `free()` after `malloc()`/`calloc()` when memory is no longer needed.
  * Use tools like **Valgrind** to detect leaks.
  * Set pointers to `NULL` after freeing to avoid dangling pointers.

---

### 2. **What is near, far, and huge pointers in C?**

* **These are specific to old 16-bit DOS compilers (like Turbo C)**
* **Near:** 16-bit address; points within current segment.
* **Far:** 32-bit address; can access any memory segment.
* **Huge:** Like far, but allows pointer arithmetic across segment boundaries.

> **Modern systems (32/64-bit) do not use these distinctions.**

---

### 3. **What is the use of the dereference `*` operator?**

* Used to access the **value** at the address a pointer holds.

```c
int a = 10;
int *ptr = &a;
printf("%d", *ptr);  // Output: 10
```

---

### 4. **What are NULL pointers in C?**

* A **null pointer** is a pointer that points to **nothing**.

```c
int *ptr = NULL;
```

* Helps in error-checking and avoiding dangling references.

---

### 5. **What is the difference between `&` and `*` in C?**

| Symbol | Meaning                        | Example         |
| ------ | ------------------------------ | --------------- |
| `&`    | Address-of operator            | `int *p = &x;`  |
| `*`    | Dereference (value-at-address) | `int val = *p;` |

---

### 6. **What are the four dynamic memory functions in C?**

1. `malloc()` – allocates uninitialized memory
2. `calloc()` – allocates zero-initialized memory
3. `realloc()` – changes size of previously allocated memory
4. `free()` – deallocates memory

---

### 7. **What happens if you don't `free()` dynamically allocated memory?**

* Leads to **memory leaks**.
* Can cause program to consume more memory over time → performance issues → crash.

---

### 8. **What is a function pointer in C? How is it used?**

* A pointer that points to a function instead of a variable.

```c
#include <stdio.h>

void greet() {
    printf("Hello!\n");
}

int main() {
    void (*fptr)() = greet; // function pointer
    fptr(); // calls greet()
    return 0;
}
```

* Useful for **callbacks**, **dynamic dispatch**, etc.

---

### 9. **What is the difference between:**

```c
const int *ptr;      // (1) pointer to const int
int * const ptr;     // (2) const pointer to int
const int * const ptr; // (3) const pointer to const int
```

| Declaration             | Meaning                                          |
| ----------------------- | ------------------------------------------------ |
| `const int *ptr`        | Cannot change the value pointed to.              |
| `int * const ptr`       | Cannot change the pointer (fixed address).       |
| `const int * const ptr` | Cannot change value or pointer (fully constant). |

---

### 10. **What are stack and heap areas?**

* **Stack:**

  * Stores local variables, function calls
  * Fast access, auto memory management
  * Limited size

* **Heap:**

  * Used for dynamic memory (`malloc`)
  * Manual management (`free`)
  * Larger and slower access

---

### 11. **What will be the result when we try to dereference NULL?**

```c
int *ptr = NULL;
printf("%d", *ptr);  // UNDEFINED BEHAVIOR – likely a crash
```

> Dereferencing a NULL pointer causes a **segmentation fault**.

---

### 12. **Write a code to show how one can use double pointers.**

```c
#include <stdio.h>

int main() {
    int a = 10;
    int *p = &a;
    int **pp = &p;

    printf("Value: %d\n", **pp);
    return 0;
}
```

---

### 13. **Will the below provided code successfully run?**

> (You mentioned code snippet was in original, but it's missing — please share if you'd like an analysis.)

---

### 14. **What will be the output of the below code?**

> (Same as above — please provide the code for specific output.)

---

### 15. **Write the code to show how one can use `realloc()` with `malloc()`:**

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *arr = (int *)malloc(2 * sizeof(int));

    arr[0] = 1;
    arr[1] = 2;

    // Resize to hold 4 integers
    arr = (int *)realloc(arr, 4 * sizeof(int));
    arr[2] = 3;
    arr[3] = 4;

    for (int i = 0; i < 4; i++) {
        printf("%d ", arr[i]);
    }

    free(arr);
    return 0;
}
```

---

### 16. **What is the difference between array and pointer?**

| Array                    | Pointer                           |
| ------------------------ | --------------------------------- |
| Fixed size               | Can be dynamically resized        |
| Name is constant address | Pointer can point to anything     |
| Stored in stack          | Can point to heap/stack variables |

---

### 17. **Difference between `++*p`, `*p++`, and `*++p`?**

* `++*p`: Increment the value pointed to by `p`.
* `*p++`: Dereference `p`, then increment the pointer.
* `*++p`: Increment the pointer, then dereference.

Example:

```c
int arr[] = {10, 20, 30};
int *p = arr;

++*p;    // arr[0] becomes 11
*p++;   // arr[0] (11), then p points to arr[1]
*++p;   // p now points to arr[2], dereference gives 30
```

---

### 18. **Explain Deep Copy and Shallow Copy with examples.**

* **Shallow Copy:** Copies address — both variables point to the same data.
* **Deep Copy:** Copies actual data — independent copies.

**Example:**

```c
int *a = malloc(sizeof(int));
*a = 5;

int *shallow = a;         // both point to same memory
int *deep = malloc(sizeof(int));
*deep = *a;               // copy the value
```

---

### 19. **What is the difference between an array and a string in C?**

| Array                   | String                           |
| ----------------------- | -------------------------------- |
| Can store any data type | Array of `char` ending with `\0` |
| Doesn't require null    | Strings must end with `'\0'`     |

Example:

```c
char arr[5] = {'H', 'e', 'l', 'l', 'o'};
char str[] = "Hello"; // includes '\0'
```

---

### 20. **How do arrays work in C?**

* Arrays are **contiguous memory blocks**.
* The name of the array acts as a pointer to its first element.
* Accessed via index or pointer arithmetic.

```c
int arr[3] = {10, 20, 30};
printf("%d", *(arr + 1)); // prints 20
```

---


### ✅ 1. **What is the purpose of the null character `('\0')` in strings?**

* `'\0'` is the **string terminator** in C.
* It marks the **end of a string**.
* C uses this to determine the string’s length and stop reading characters.

```c
char str[] = "Hello"; // stored as {'H','e','l','l','o','\0'}
```

---

### ✅ 2. **How are strings stored in memory?**

* As **contiguous** arrays of characters ending with a **null character** (`'\0'`).
* Each character occupies **1 byte**.

```c
char str[] = "Cat"; // 'C' | 'a' | 't' | '\0'
```

---

### ✅ 3. **Standard Library String Functions**

| Function   | Purpose                          |
| ---------- | -------------------------------- |
| `strlen()` | Returns length (excluding `'\0`) |
| `strcpy()` | Copy strings                     |
| `strcat()` | Concatenate strings              |
| `strcmp()` | Compare strings                  |
| `strchr()` | Find character in string         |
| `strstr()` | Find substring in string         |

---

### ✅ 4. **What happens when you access an array out of bounds?**

* **Undefined behavior** — may crash, access garbage data, or corrupt memory.
* No bounds checking in C.

---

### ✅ 5. **Difference between `strlen()` and `sizeof()` for strings**

| Function   | Returns                                  |
| ---------- | ---------------------------------------- |
| `strlen()` | Number of characters before `'\0'`       |
| `sizeof()` | Total size (including `'\0'` for arrays) |

```c
char str[] = "Hi";
printf("%lu %lu", strlen(str), sizeof(str)); // Output: 2 3
```

---

### ✅ 6. **How to convert a string to numbers in C**

Use these standard functions:

* `atoi()` – string to `int`
* `atof()` – string to `float`
* `strtol()`, `strtod()` – safer versions

Example:

```c
char s[] = "123";
int num = atoi(s);  // num = 123
```

---

### ✅ 7. **Reverse a String in C**

```c
void reverse(char *str) {
    int i = 0, j = strlen(str) - 1;
    while(i < j) {
        char tmp = str[i];
        str[i++] = str[j];
        str[j--] = tmp;
    }
}
```

---

### ✅ 8. **Count Number of Subarrays with Even Sum**

```c
int countEvenSumSubarrays(int arr[], int n) {
    int count = 0, sum = 0;
    int even = 1, odd = 0;

    for(int i = 0; i < n; i++) {
        sum += arr[i];
        if(sum % 2 == 0)
            count += even++;
        else
            count += odd++;
    }

    return count;
}
```

---

### ✅ 9. **Reverse Each Word in a Sentence**

```c
void reverseWord(char *start, char *end) {
    while(start < end) {
        char tmp = *start;
        *start++ = *end;
        *end-- = tmp;
    }
}

void reverseWords(char *str) {
    char *word_start = NULL;
    for (int i = 0; ; i++) {
        if ((str[i] != ' ') && (word_start == NULL))
            word_start = &str[i];
        else if ((str[i] == ' ' || str[i] == '\0') && word_start) {
            reverseWord(word_start, &str[i - 1]);
            word_start = NULL;
        }
        if (str[i] == '\0') break;
    }
}
```

---

### ✅ 10. **Find the Largest Element in an Array**

```c
int findMax(int arr[], int n) {
    int max = arr[0];
    for(int i = 1; i < n; i++)
        if(arr[i] > max)
            max = arr[i];
    return max;
}
```

---

### ✅ 11. **Check if a String is a Palindrome**

```c
int isPalindrome(char *str) {
    int i = 0, j = strlen(str) - 1;
    while(i < j)
        if(str[i++] != str[j--])
            return 0;
    return 1;
}
```

---

### ✅ 12. **Remove All Duplicate Characters (Keep First Occurrence)**

```c
void removeDuplicates(char *str) {
    int hash[256] = {0};
    int i, j = 0;
    for(i = 0; str[i]; i++) {
        if(!hash[(unsigned char)str[i]]) {
            hash[(unsigned char)str[i]] = 1;
            str[j++] = str[i];
        }
    }
    str[j] = '\0';
}
```

---

### ✅ 13. **Merge Two Arrays into a Third**

```c
void mergeArrays(int a[], int b[], int m, int n, int res[]) {
    for(int i = 0; i < m; i++) res[i] = a[i];
    for(int i = 0; i < n; i++) res[m + i] = b[i];
}
```

---

### ✅ 14. **Detect Unique Characters in a String (ASCII)**

```c
int hasUniqueChars(char *str) {
    int chars[256] = {0};
    for(int i = 0; str[i]; i++) {
        if(chars[(unsigned char)str[i]]++)
            return 0;  // Duplicate found
    }
    return 1;  // All unique
}
```

---

### ✅ 15. **Remove All Spaces in a String (In-place)**

```c
void removeSpaces(char *str) {
    int i = 0, j = 0;
    while(str[i]) {
        if(str[i] != ' ')
            str[j++] = str[i];
        i++;
    }
    str[j] = '\0';
}
```

---

### ✅ 16. **Convert Uppercase to Lowercase (Without Library)**

```c
void toLowercase(char *str) {
    for(int i = 0; str[i]; i++)
        if(str[i] >= 'A' && str[i] <= 'Z')
            str[i] += 32;
}
```

---

### ✅ 17. **Find Length of Longest Common Prefix**

```c
int longestCommonPrefix(char strs[][100], int n) {
    if(n == 0) return 0;
    int i = 0;
    while(1) {
        char c = strs[0][i];
        for(int j = 1; j < n; j++)
            if(strs[j][i] != c || c == '\0')
                return i;
        i++;
    }
}
```

---

### ✅ 18. **Detect Duplicates in Array in O(n) Time (Worst Case)**

Using Hashing:

```c
int hasDuplicate(int arr[], int n) {
    int hash[100001] = {0}; // Adjust size if needed
    for(int i = 0; i < n; i++) {
        if(hash[arr[i]]++)
            return 1;
    }
    return 0;
}
```

---

### ✅ 19. **Find the Second Largest Number**

```c
int secondLargest(int arr[], int n) {
    int first = INT_MIN, second = INT_MIN;
    for(int i = 0; i < n; i++) {
        if(arr[i] > first) {
            second = first;
            first = arr[i];
        } else if(arr[i] > second && arr[i] != first) {
            second = arr[i];
        }
    }
    return second;
}
```

---

### ✅ 20. **Sort 0s, 1s, and 2s (Dutch National Flag Problem)**

```c
void sort012(int arr[], int n) {
    int low = 0, mid = 0, high = n - 1;
    while(mid <= high) {
        switch(arr[mid]) {
            case 0:
                swap(&arr[low++], &arr[mid++]);
                break;
            case 1:
                mid++;
                break;
            case 2:
                swap(&arr[mid], &arr[high--]);
                break;
        }
    }
}
```

---


## 1. What is recursion in C and write a recursive code to compute factorial?

**Recursion** is when a function calls itself to solve a smaller instance of the same problem. A recursive function must have:

* A **base case** — a condition under which it stops calling itself.
* A **recursive step** — the function calls itself with a smaller/simpler argument, moving toward the base case.

**Example: Recursive factorial**

```c
#include <stdio.h>

// Recursive function to compute factorial of n
long factorial(int n) {
    if (n < 0) { 
        // error case, factorial not defined for negative
        return -1;
    }
    if (n == 0 || n == 1) {  // base case
        return 1;
    }
    return n * factorial(n - 1);  // recursive call
}

int main() {
    int num;
    printf("Enter a non-negative integer: ");
    if (scanf("%d", &num) != 1) {
        printf("Invalid input\n");
        return 1;
    }
    long result = factorial(num);
    if (result < 0) {
        printf("Factorial not defined for negative numbers\n");
    } else {
        printf("Factorial of %d is %ld\n", num, result);
    }
    return 0;
}
```

---

## 2. What is a stack overflow in recursion? How can it be avoided?

* **Stack overflow** in recursion happens when recursive calls are nested too deeply, consuming more stack memory than is available. Each function call uses some stack space (for parameters, local variables, return address). If recursion never reaches or is too far from its base case, or if too large inputs, the stack may “overflow” → crash / undefined behavior. ([Scaler][1])

**How to avoid stack overflow:**

* Make sure you have a correct **base case** that will be reached.
* Ensure that recursive calls move towards the base case (argument size reduces).
* Limit recursion depth; for large inputs use iterative solutions.
* Use **tail recursion** if possible (some compilers optimize tail recursion to avoid extra stack frames).
* Increase stack size (platform dependent) if deep recursion is required.
* Use dynamic data structures or explicit stacks rather than relying solely on function call stack.

---

## 3. Implement structure & union in C

Here are example uses of both:

```c
#include <stdio.h>

// Define a struct
struct Person {
    char name[50];
    int age;
    float height;
};

// Define a union
union Data {
    int i;
    float f;
    char str[20];
};

int main() {
    // Using struct
    struct Person p1;
    snprintf(p1.name, sizeof(p1.name), "Alice");
    p1.age = 30;
    p1.height = 5.5;

    printf("Person: %s, age %d, height %.1f\n", p1.name, p1.age, p1.height);

    // Using union
    union Data d;

    d.i = 42;
    printf("d.i = %d\n", d.i);

    d.f = 3.14159;
    printf("d.f = %f (Note: d.i is now undefined)\n", d.f);

    // If we write into str
    strncpy(d.str, "Hello", sizeof(d.str));
    printf("d.str = %s\n", d.str);

    return 0;
}
```

* `struct` allows you to group different data types; each member has its own storage.
* `union` shares memory: all members overlap; the size of the union is the size of its largest member. Only one member contains a meaningful value at any time.

---

## 4. How do you read a whole text file line by line in C?

You can use `fgets()` in a loop, for example:

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    FILE *fp = fopen("input.txt", "r");
    if (!fp) {
        perror("Failed to open file");
        return 1;
    }

    // Buffer big enough for one line
    char buffer[1024];
    while (fgets(buffer, sizeof(buffer), fp) != NULL) {
        // buffer contains one line (including newline if fits)
        printf("%s", buffer);
    }

    fclose(fp);
    return 0;
}
```

* `fgets(buffer, size, fp)` reads up to size-1 characters or until a newline or EOF, whichever comes first.
* It ensures you don’t overflow buffer if size is correct.

---

## 5. What is an r-value and l-value?

* **l-value** (locator value): an expression that refers to a memory location. It can appear on the left side of an assignment. Example: `x`, `arr[5]`, `*p` (if `p` points to valid memory), etc.
* **r-value**: An expression that has a value but does not necessarily refer to a memory location you can assign to. It's used on the right side of assignment. Example: `5`, `x + 3`, function return values (non-reference), etc.

Example:

```c
int x;
int *p;

x = 5;   // here x is an l-value; 5 is an r-value
*p = x;  // *p is an l-value (if p valid)
```

---

## 6. What is the `sleep()` function?

* `sleep()` is a function (in POSIX systems / Unix / Linux) that pauses the execution of the current thread/process for a number of seconds.
* Prototype: `unsigned int sleep(unsigned int seconds);`
* On Windows there’s `Sleep(milliseconds)` in `<windows.h>`.
* It returns number of seconds left if interrupted, or `0` if complete.

Example:

```c
#include <unistd.h>  // for POSIX systems

int main() {
    printf("Sleeping for 3 seconds...\n");
    sleep(3);
    printf("Awake!\n");
    return 0;
}
```

---

## 7. What are enumerations?

* `enum` in C is a user-defined type consisting of named integer constants.
* Helps give meaningful names to integer values.

Example:

```c
#include <stdio.h>

enum Color { RED, GREEN, BLUE, YELLOW };

int main() {
    enum Color c = GREEN;
    printf("c = %d\n", c);  // prints 1 (if RED = 0, GREEN = 1, etc.)
    return 0;
}
```

* You can assign custom integer values:

```c
enum Fruit { APPLE = 1, BANANA = 4, ORANGE = 10 };
```

---

## 8. Write a C program to print the Fibonacci series using recursion and without using recursion

**Recursion version:**

```c
#include <stdio.h>

int fib(int n) {
    if (n < 0) return -1;  // error
    if (n == 0) return 0;
    if (n == 1) return 1;
    return fib(n - 1) + fib(n - 2);
}

int main() {
    int n, i;
    printf("How many Fibonacci terms? ");
    scanf("%d", &n);
    for (i = 0; i < n; ++i) {
        printf("%d ", fib(i));
    }
    printf("\n");
    return 0;
}
```

**Non-recursion (iterative) version:**

```c
#include <stdio.h>

int main() {
    int n, i;
    printf("How many Fibonacci terms? ");
    if (scanf("%d", &n) != 1) return 1;

    if (n <= 0) return 0;
    int a = 0, b = 1;
    printf("%d ", a);
    if (n > 1) printf("%d ", b);

    for (i = 2; i < n; i++) {
        int next = a + b;
        printf("%d ", next);
        a = b;
        b = next;
    }
    printf("\n");
    return 0;
}
```

---

## 9. Write a C program to check whether a number is prime or not

```c
#include <stdio.h>
#include <stdbool.h>

bool isPrime(int n) {
    if (n <= 1) return false;
    if (n <= 3) return true;
    if (n % 2 == 0) return false;
    for (int i = 3; i * i <= n; i += 2) {
        if (n % i == 0) return false;
    }
    return true;
}

int main() {
    int num;
    printf("Enter an integer: ");
    if (scanf("%d", &num) != 1) return 1;
    if (isPrime(num))
        printf("%d is prime\n", num);
    else
        printf("%d is not prime\n", num);
    return 0;
}
```

---

## 10. How is source code different from object code?

* **Source code**: Human-readable code written in a programming language (C, etc.). What you write in `.c` files.
* **Object code**: The machine-code binary output by the compiler (after compilation), usually `.o` or `.obj` file. It's not human readable and is what gets linked to form the executable.

---

## 11. What will be the output of this code and why? (code snippet with increment function)

You didn’t provide the snippet here. If you share it, I can walk through it.

---

## 12. Explain modifiers

Modifiers in C are keywords that alter the properties of data types. Common modifiers:

* `signed` / `unsigned` — for integer types, to alter whether negative values are allowed.
* `short`, `long` — to change the size/range of integer types.
* `const` — variable can’t be changed after initialization.
* `volatile` — tells compiler variable may change outside of program's normal flow (e.g., hardware interrupts).
* `static` — multiple uses: for variables (lifetime / linkage), for functions (internal linkage), etc.

Example:

```c
unsigned long int x;
const volatile int status;
```

---

## 13. Write a program to check an Armstrong number

An Armstrong number (in base 10) is one equal to the sum of its own digits each raised to the power of the number of digits. Example: 153 = 1³ + 5³ + 3³.

```c
#include <stdio.h>
#include <math.h>

int main() {
    int num, original, remainder, n = 0;
    long sum = 0;

    printf("Enter an integer: ");
    scanf("%d", &num);
    original = num;

    // count digits
    for (original = num; original != 0; original /= 10) {
        n++;
    }

    original = num;
    while (original != 0) {
        remainder = original % 10;
        sum += pow(remainder, n);
        original /= 10;
    }

    if (sum == num)
        printf("%d is an Armstrong number.\n", num);
    else
        printf("%d is not an Armstrong number.\n", num);

    return 0;
}
```

---

## 14. Write a program to reverse a given number

```c
#include <stdio.h>

int main() {
    int num, reversed = 0, remainder;
    printf("Enter an integer: ");
    if (scanf("%d", &num) != 1) return 1;

    int original = num;
    // handle negative
    int negative = 0;
    if (num < 0) {
        negative = 1;
        num = -num;
    }

    while (num != 0) {
        remainder = num % 10;
        reversed = reversed * 10 + remainder;
        num /= 10;
    }

    if (negative) reversed = -reversed;
    printf("Reversed number of %d is %d\n", original, reversed);

    return 0;
}
```

---

## 15. Mention file operations in C

Operations related to file I/O using the C standard library:

* Opening a file: `fopen()`
* Closing a file: `fclose()`
* Reading from file: `fgetc(), fgets(), fread(), fscanf()`
* Writing to file: `fputc(), fputs(), fwrite(), fprintf()`
* Seeking in file: `fseek(), ftell(), rewind()`
* Error handling: `feof(), ferror()`

---

## 16. Write a Program to check whether a linked list is circular or not

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct Node {
    int data;
    struct Node *next;
} Node;

int isCircular(Node *head) {
    if (head == NULL) return 0;
    Node *slow = head, *fast = head;
    while (fast != NULL && fast->next != NULL) {
        slow = slow->next;
        fast = fast->next->next;
        if (slow == fast) return 1; // loop exists
    }
    return 0;
}

Node *newNode(int data) {
    Node *node = malloc(sizeof(Node));
    node->data = data;
    node->next = NULL;
    return node;
}

int main() {
    // Example: create circular linked list
    Node *head = newNode(1);
    head->next = newNode(2);
    head->next->next = newNode(3);
    head->next->next->next = head;  // making it circular

    if (isCircular(head))
        printf("List is circular\n");
    else
        printf("List is not circular\n");

    return 0;
}
```

---

## 17. Write a program to Merge two sorted linked lists

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct Node {
    int data;
    struct Node *next;
} Node;

Node *newNode(int d) {
    Node *n = malloc(sizeof(Node));
    n->data = d;
    n->next = NULL;
    return n;
}

Node *mergeSorted(Node *a, Node *b) {
    if (a == NULL) return b;
    if (b == NULL) return a;
    Node *result = NULL;

    if (a->data <= b->data) {
        result = a;
        result->next = mergeSorted(a->next, b);
    } else {
        result = b;
        result->next = mergeSorted(a, b->next);
    }
    return result;
}

void printList(Node *head) {
    while (head != NULL) {
        printf("%d ", head->data);
        head = head->next;
    }
    printf("\n");
}

int main() {
    // Example usage
    Node *a = newNode(1);
    a->next = newNode(3);
    a->next->next = newNode(5);

    Node *b = newNode(2);
    b->next = newNode(4);
    b->next->next = newNode(6);

    Node *merged = mergeSorted(a, b);
    printList(merged);  // should print: 1 2 3 4 5 6

    return 0;
}
```

---

## 18. What is the difference between `fread()` and `fscanf()` in C?

| Feature            | `fread()`                                                                                  | `fscanf()`                                                                       |
| ------------------ | ------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------- |
| Purpose            | Reads raw binary data (a block of bytes) from a file into a buffer.                        | Reads formatted text from a file according to a format specifier (like `scanf`). |
| Data type handling | No type formatting; you deal with raw memory, often with casting or interpreting the data. | Human-readable text parsing, converting text to numbers, strings etc.            |
| Best for           | Reading images, binary files, structured binary records.                                   | Reading configuration, whitespace‐separated text, parsed input.                  |
| Speed / overhead   | Usually faster for large binary reads since minimal parsing.                               | Slower due to parsing/formatting overhead.                                       |

Examples:

* Using `fread`:

```c
FILE *fp = fopen("binary.dat", "rb");
if (!fp) return 1;
struct Rec { int id; double value; };
struct Rec buffer[10];
size_t elements_read = fread(buffer, sizeof(struct Rec), 10, fp);
// e.g. use buffer[0]..buffer[elements_read-1]
fclose(fp);
```

* Using `fscanf`:

```c
FILE *fp = fopen("data.txt", "r");
if (!fp) return 1;
int a;
double d;
while (fscanf(fp, "%d %lf", &a, &d) == 2) {
    printf("a=%d, d=%.2f\n", a, d);
}
fclose(fp);
```

(These concepts are supported by standards and documented in places like IBM docs for `fread()` etc. ([IBM][2]))

---

## 19. How do you open a file in append mode? What happens if the file doesn't exist?

* Use `fopen()` with `"a"` or `"a+"` mode:

```c
FILE *fp = fopen("file.txt", "a");  // Append mode
if (!fp) {
    perror("Failed to open");
    return 1;
}
```

* `"a"`: Open for writing; data is appended to end. Writes always go to end of file.

* `"a+"`: Open for reading and writing; writing still appends.

* **If the file doesn’t exist**, `fopen(..., "a")` will try to create the file.

---

## 20. What is `typedef` in C?

* `typedef` allows you to define new names (aliases) for existing types. Makes code more readable or portable.

Example:

```c
typedef unsigned long ulong;
typedef struct Node {
    int data;
    struct Node *next;
} Node;

Node *head;  // instead of struct Node *head;
```

---

## 21. How do command-line arguments work in C? Give an example.

* C `main` can take two arguments:

```c
int main(int argc, char *argv[]) { ... }
```

* `argc` is the **argument count** (number of command-line tokens including program name).
* `argv` is array of C‐strings (char pointers), `argv[0]` is program name, `argv[1]` first argument, etc.

**Example:**

```c
#include <stdio.h>

int main(int argc, char *argv[]) {
    printf("Number of arguments: %d\n", argc);
    for (int i = 0; i < argc; i++) {
        printf("argv[%d] = %s\n", i, argv[i]);
    }
    return 0;
}
```

If you compile as `prog` and run:

```
./prog hello world 123
```

Output:

```
Number of arguments: 4
argv[0] = ./prog
argv[1] = hello
argv[2] = world
argv[3] = 123
```

---

## 22. What happens if you forget to close a file in C?

* The resources (file handles) associated with the file remain allocated until program termination.
* May result in:

  * File not flushed (buffered data not written) → data loss.
  * Resource leak (too many open files) → may hit OS limit.
* Typically, when the program ends, OS reclaims resources, but you shouldn’t rely on that.

---

