## 3. **Constants and Literals**

A **constant** is a value that cannot be altered during the program's execution. C supports different types of constants such as integer, floating-point, character, and string constants.

### 3.1 **Types of Constants:**

- **Integer Constants**: Whole numbers, e.g., `10`, `-20`.
- **Floating-Point Constants**: Numbers with a fractional part, e.g., `3.14`, `-0.01`.
- **Character Constants**: A single character enclosed in single quotes, e.g., `'A'`, `'9'`.
- **String Constants (Literals)**: A sequence of characters enclosed in double quotes, e.g., `"Hello"`, `"C programming"`.

### 3.2 **Defining Constants in C:**

There are two ways to define constants in C:

1. Using the `#define` preprocessor directive.
2. Using the `const` keyword.

#### Example:
```c
#include <stdio.h>
#define PI 3.14159   // Defining a constant using #define

int main() {
    const int age = 30;   // Defining a constant using const keyword

    printf("The value of PI is: %f\n", PI);
    printf("The value of age is: %d\n", age);

    return 0;
}
```

In the above program, `PI` is defined as a constant using `#define`, while `age` is defined as a constant using `const`. Both values cannot be changed during program execution.


