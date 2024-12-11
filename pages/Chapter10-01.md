# `#define` and `#include` Directives in C

Preprocessor directives in C are instructions that are executed before the actual compilation of the code begins. Two of the most commonly used directives are `#define` and `#include`. This chapter covers their syntax, usage, and practical examples.

---

## 1. **What Is a Preprocessor Directive?**

Preprocessor directives are commands that provide instructions to the compiler’s preprocessor. These directives begin with a `#` symbol and do not end with a semicolon (`;`).

---

## 2. **The `#define` Directive**

The `#define` directive is used to define:
- **Constants**: Replace symbolic names with constant values.
- **Macros**: Create reusable code snippets with or without parameters.

---

### 2.1 **Defining Constants**

The `#define` directive can replace symbolic names with constant values throughout the program.

#### Syntax:
```c
#define NAME value
```

#### Example:
```c
#include <stdio.h>

#define PI 3.14159

int main() {
    float radius = 5.0;
    float area = PI * radius * radius;

    printf("Area of the circle: %.2f\n", area);
    return 0;
}
```

**Output**:
```
Area of the circle: 78.54
```

---

### 2.2 **Defining Macros**

Macros are reusable code snippets that may take parameters. The preprocessor replaces the macro with its definition before compilation.

#### Syntax:
```c
#define MACRO_NAME(parameters) expression
```

#### Example:
```c
#include <stdio.h>

#define SQUARE(x) ((x) * (x))

int main() {
    int num = 4;
    printf("Square of %d: %d\n", num, SQUARE(num));
    return 0;
}
```

**Output**:
```
Square of 4: 16
```

**Note**: Always use parentheses around macro parameters and expressions to avoid precedence issues.

---

### 2.3 **Undefining Macros**

You can remove a macro definition using the `#undef` directive.

#### Syntax:
```c
#undef MACRO_NAME
```

#### Example:
```c
#include <stdio.h>

#define GREETING "Hello, World!"
#undef GREETING

int main() {
    // The following line will cause an error because GREETING is undefined
    // printf("%s\n", GREETING);
    return 0;
}
```

---

### 2.4 **Predefined Macros**

C provides several predefined macros that are automatically defined by the compiler.

| Macro          | Description                                             |
|-----------------|---------------------------------------------------------|
| `__FILE__`     | Current file name                                       |
| `__LINE__`     | Current line number                                     |
| `__DATE__`     | Current date of compilation                             |
| `__TIME__`     | Current time of compilation                             |
| `__STDC__`     | Defined as `1` if the compiler conforms to the C standard |

#### Example:
```c
#include <stdio.h>

int main() {
    printf("File: %s\n", __FILE__);
    printf("Line: %d\n", __LINE__);
    printf("Date: %s\n", __DATE__);
    printf("Time: %s\n", __TIME__);
    return 0;
}
```

**Output**:
```
File: example.c
Line: 5
Date: Dec 11 2024
Time: 15:30:00
```

---

## 3. **The `#include` Directive**

The `#include` directive is used to include the contents of another file into the program during preprocessing. This is commonly used to include standard or user-defined header files.

---

### 3.1 **Including Standard Library Headers**

To include standard library headers, use angle brackets (`<>`).

#### Syntax:
```c
#include <header_name>
```

#### Example:
```c
#include <stdio.h>

int main() {
    printf("Hello, World!\n");
    return 0;
}
```

**Common Standard Headers**:
| Header   | Purpose                              |
|----------|--------------------------------------|
| `stdio.h`| Input/Output functions               |
| `stdlib.h`| General utilities (e.g., memory allocation)|
| `math.h` | Mathematical functions               |
| `string.h`| String manipulation functions       |

---

### 3.2 **Including User-Defined Files**

To include user-defined header files, use double quotes (`""`).

#### Syntax:
```c
#include "filename.h"
```

#### Example:
**Header File (`myheader.h`)**:
```c
#define GREETING "Welcome to C Programming!"
```

**Main File (`main.c`)**:
```c
#include <stdio.h>
#include "myheader.h"

int main() {
    printf("%s\n", GREETING);
    return 0;
}
```

**Output**:
```
Welcome to C Programming!
```

---

### 3.3 **Nested Includes**

Header files can include other headers, creating a dependency chain.

#### Example:
**`a.h`**:
```c
#include "b.h"
#define A "This is Header A"
```

**`b.h`**:
```c
#define B "This is Header B"
```

**Main File**:
```c
#include <stdio.h>
#include "a.h"

int main() {
    printf("%s\n", A);
    printf("%s\n", B);
    return 0;
}
```

**Output**:
```
This is Header A
This is Header B
```

---

## 4. **Guarding Against Multiple Inclusions**

To prevent multiple inclusions of the same header file, use include guards or `#pragma once`.

### Using Include Guards
```c
#ifndef HEADER_NAME_H
#define HEADER_NAME_H

// Header content here

#endif
```

### Using `#pragma once`
```c
#pragma once

// Header content here
```

**Note**: `#pragma once` is compiler-specific but widely supported.

---

## 5. **Combining `#define` and `#include`**

You can use both `#define` and `#include` together to create modular and reusable code.

### Example:
**Header File (`constants.h`)**:
```c
#define PI 3.14159
#define SQUARE(x) ((x) * (x))
```

**Main File (`main.c`)**:
```c
#include <stdio.h>
#include "constants.h"

int main() {
    float radius = 5.0;
    printf("Area of the circle: %.2f\n", PI * SQUARE(radius));
    return 0;
}
```

**Output**:
```
Area of the circle: 78.54
```

---

## 6. **Common Mistakes**

1. **Missing Include Guards**:
   - Omitting include guards in header files can cause multiple definition errors.
   
2. **Incorrect File Paths**:
   - Ensure file paths are correct when including user-defined headers.

3. **Unintended Macro Expansion**:
   - Be cautious with macro names to avoid unintended replacements.

4. **Overuse of Macros**:
   - Prefer `const`, `inline`, or `enum` over macros when possible for better type safety.

---

## 7. **Practice Exercises**

1. Create a header file to define constants for mathematical operations and include it in a program to calculate areas.
2. Write a program that demonstrates the use of macros with parameters.
3. Implement include guards in a user-defined header file.
4. Use predefined macros (`__FILE__`, `__LINE__`, etc.) to log debugging information.
5. Write a program to calculate the perimeter of different shapes using a combination of `#define` and `#include`.

---

## 8. **Key Points to Remember**

1. **`#define`**:
   - Used for defining constants and macros.
   - Avoids runtime overhead but lacks type checking.

2. **`#include`**:
   - Used to include standard or user-defined headers.
   - Modularizes code and enables reusability.

3. **Predefined Macros**:
   - Provide useful information like file name, line number, and compile-time details.

4. **Include Guards**:
   - Prevent multiple inclusions of the same header file.

---

By mastering the `#define` and `#include` directives, you can create more organized, efficient, and maintainable C programs. In the next chapter, we will explore **conditional compilation**, which allows you to control code inclusion based on specific conditions.
