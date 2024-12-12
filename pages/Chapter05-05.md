# Storage Classes in C

Storage classes in C define the **scope**, **lifetime**, **visibility**, and **default value** of variables. They control how variables are stored in memory, their accessibility, and their duration in the program.

In this chapter, we will explore the four storage classes in C: **auto**, **static**, **extern**, and **register**.

---

## 1. **What Are Storage Classes?**

Every variable in C is associated with a storage class that determines:
1. **Scope**: Where the variable can be accessed in the program.
2. **Lifetime**: How long the variable exists in memory.
3. **Visibility**: Where the variable is visible in the program.
4. **Default Value**: The initial value if not explicitly initialized.

---

## 2. **Types of Storage Classes**

### 2.1 **`auto` (Automatic Storage Class)**

- **Scope**: Local to the block in which it is declared.
- **Lifetime**: Exists only during the execution of the block.
- **Visibility**: Accessible only within the block.
- **Default Value**: Undefined (garbage value).

By default, all local variables are `auto`, so explicitly using the `auto` keyword is optional.

#### Syntax:
```c
auto data_type variable_name;
```

#### Example:
```c
#include <stdio.h>

void display() {
    auto int num = 10; // Local variable with automatic storage
    printf("Value of num: %d\n", num);
}

int main() {
    display();
    // num is not accessible here
    return 0;
}
```

---

### 2.2 **`static` (Static Storage Class)**

- **Scope**: Local to the block in which it is declared.
- **Lifetime**: Retains its value throughout the program's execution.
- **Visibility**: Accessible only within the block where it is declared.
- **Default Value**: Zero.

A `static` variable retains its value between function calls, unlike `auto` variables.

#### Syntax:
```c
static data_type variable_name;
```

#### Example: Retaining Value Between Function Calls
```c
#include <stdio.h>

void count() {
    static int num = 0; // Static variable
    num++;
    printf("Value of num: %d\n", num);
}

int main() {
    count(); // Output: 1
    count(); // Output: 2
    count(); // Output: 3
    return 0;
}
```

Here, the `static` variable `num` retains its value across multiple calls to the `count` function.

#### Example: Static Variable in a Loop
```c
#include <stdio.h>

void loopExample() {
    static int num = 5;
    printf("Static num: %d\n", num);
    num++;
}

int main() {
    for (int i = 0; i < 3; i++) {
        loopExample();
    }
    return 0;
}
```

**Output**:
```
Static num: 5
Static num: 6
Static num: 7
```

---

### 2.3 **`extern` (External Storage Class)**

- **Scope**: Global (accessible throughout the program).
- **Lifetime**: Exists for the entire duration of the program.
- **Visibility**: Accessible across files.
- **Default Value**: Zero.

The `extern` keyword is used to declare a global variable that is defined in another file or outside the current block.

#### Syntax:
```c
extern data_type variable_name;
```

#### Example: Sharing a Global Variable Between Functions
```c
#include <stdio.h>

int num = 10; // Global variable

void display() {
    extern int num; // Access the global variable
    printf("Value of num: %d\n", num);
}

int main() {
    display();
    return 0;
}
```

#### Example: Sharing Variables Across Files
**File 1: `file1.c`**
```c
#include <stdio.h>

int sharedVar = 42; // Global variable

void showSharedVar() {
    printf("Value of sharedVar: %d\n", sharedVar);
}
```

**File 2: `file2.c`**
```c
#include <stdio.h>

extern int sharedVar; // Access the global variable from file1.c

int main() {
    printf("Accessing sharedVar from file2: %d\n", sharedVar);
    return 0;
}
```

---

### 2.4 **`register` (Register Storage Class)**

- **Scope**: Local to the block in which it is declared.
- **Lifetime**: Exists only during the execution of the block.
- **Visibility**: Accessible only within the block.
- **Default Value**: Undefined (garbage value).

The `register` storage class hints to the compiler to store the variable in a CPU register for faster access. However, the compiler may ignore this hint.

#### Syntax:
```c
register data_type variable_name;
```

#### Example:
```c
#include <stdio.h>

void display() {
    register int i; // Requesting register storage
    for (i = 0; i < 5; i++) {
        printf("i = %d\n", i);
    }
}

int main() {
    display();
    return 0;
}
```

**Note**:
- A `register` variable cannot have its address taken (i.e., you cannot use `&` with it).
- Modern compilers optimize variable storage automatically, so explicit use of `register` is rare.

---

## 3. **Comparison of Storage Classes**

| Storage Class | Scope              | Lifetime                | Default Value  | Visibility              |
|---------------|--------------------|-------------------------|----------------|-------------------------|
| **`auto`**    | Local              | Until the block ends    | Undefined      | Within the block only   |
| **`static`**  | Local/Global       | Entire program          | Zero           | Local or file scope     |
| **`extern`**  | Global             | Entire program          | Zero           | Across multiple files   |
| **`register`**| Local              | Until the block ends    | Undefined      | Within the block only   |

---

## 4. **Best Practices for Using Storage Classes**

1. Use `auto` (default) for local variables unless you need a specific storage behavior.
2. Use `static` for:
   - Variables that should retain their value between function calls.
   - Variables that should be limited to file scope (for encapsulation).
3. Use `extern` to share global variables between files sparingly. Overuse of global variables can make debugging difficult.
4. Use `register` for performance-critical variables in loops or frequent computations, but rely on compiler optimizations in modern systems.

---

## 5. **Practice Exercises**

1. Write a program to demonstrate the difference between `auto` and `static` variables.
2. Create a program where a global variable is shared between two files using `extern`.
3. Implement a function that uses a `register` variable to optimize a loop for summing numbers.

---

Storage classes are an essential aspect of C programming that directly affect how variables behave in terms of scope, lifetime, and visibility. Understanding their use enables you to write efficient, modular, and maintainable programs. In the next chapter, we will explore **pointers**, another fundamental feature of C that gives programmers direct control over memory.

## Here are the solutions to the given exercises implemented in C:

---

### 1. Program to demonstrate the difference between auto and static variables

```c
#include <stdio.h>

void demonstrateVariables() {
    auto int auto_var = 0;   // Auto variable
    static int static_var = 0; // Static variable

    auto_var++;
    static_var++;

    printf("Auto variable: %d, Static variable: %d\n", auto_var, static_var);
}

int main() {
    printf("Calling the function multiple times to observe behavior:\n");
    for (int i = 1; i <= 3; i++) {
        printf("Function call %d:\n", i);
        demonstrateVariables();
    }
    return 0;
}
```

**Explanation**:
- **Auto variables** are initialized every time the function is called, so their values reset.
- **Static variables** retain their values between function calls.

---

### 2. Program where a global variable is shared between two files using `extern`

**File 1 (`file1.c`)**:
```c
#include <stdio.h>

// Declare the global variable
int sharedVar = 10;

// Function to modify the variable
void modifySharedVar() {
    sharedVar += 5;
    printf("Shared variable modified in file1: %d\n", sharedVar);
}
```

**File 2 (`file2.c`)**:
```c
#include <stdio.h>

// Use extern to access the global variable from file1
extern int sharedVar;

// Function to access and modify the global variable
void accessSharedVar() {
    printf("Shared variable accessed in file2: %d\n", sharedVar);
    sharedVar *= 2;
}
```

**Main file (`main.c`)**:
```c
#include <stdio.h>

// Declare functions from file1 and file2
void modifySharedVar();
void accessSharedVar();

int main() {
    printf("Initial value of shared variable: %d\n", sharedVar);

    modifySharedVar(); // Function from file1
    accessSharedVar(); // Function from file2

    printf("Final value of shared variable: %d\n", sharedVar);
    return 0;
}
```

**Compilation**:
```bash
gcc file1.c file2.c main.c -o shared_var_example
./shared_var_example
```

**Explanation**:
- The `extern` keyword allows `file2.c` to reference the `sharedVar` defined in `file1.c`.

---

### 3. Program using a register variable to optimize a loop for summing numbers

```c
#include <stdio.h>

int sumUsingRegister(int n) {
    register int sum = 0; // Register variable
    for (register int i = 1; i <= n; i++) {
        sum += i;
    }
    return sum;
}

int main() {
    int num;
    printf("Enter a number to find the sum of numbers from 1 to n: ");
    scanf("%d", &num);

    int result = sumUsingRegister(num);
    printf("Sum of numbers from 1 to %d: %d\n", num, result);
    return 0;
}
```

**Explanation**:
- **Register variables** are stored in CPU registers (if available), making access faster. This is particularly beneficial for loop counters or frequently accessed variables.

---

### Summary:

1. **Auto vs Static Variables**: Demonstrates how `auto` resets while `static` retains its value between function calls.
2. **Global Variable Sharing**: Shows how a variable defined in one file can be accessed in another using `extern`.
3. **Register Variable for Optimization**: Uses a `register` variable to optimize a summation loop for performance. 

These examples highlight key concepts of variable scope and storage classes in C.
