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

