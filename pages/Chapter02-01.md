## 1. **Variables and Data Types**

### 1.1 **Variables**

A **variable** in C is a named storage location in memory where data can be stored, modified, and retrieved during the execution of a program. Variables must be declared before use, and they can hold different types of data.

#### Syntax for Declaring a Variable:
```c
data_type variable_name;
```
For example:
```c
int age;
float height;
char grade;
```

#### Variable Naming Rules:
- The name must begin with a letter (a-z, A-Z) or an underscore (_).
- Subsequent characters can be letters, numbers, or underscores.
- C is **case-sensitive** (`age` and `Age` are different).
- Variable names cannot be C **keywords**.

### 1.2 **Data Types**

C provides various **data types** to store different types of data. Data types specify the size and type of data that can be stored in a variable.

#### Common Data Types:

| Data Type | Description                    | Size (bytes) | Example            |
|-----------|--------------------------------|--------------|--------------------|
| `int`     | Integer (whole number)         | 2 or 4       | `int age = 25;`    |
| `float`   | Floating-point number (decimal)| 4            | `float salary = 5000.50;` |
| `double`  | Double-precision floating-point| 8            | `double pi = 3.14159;`    |
| `char`    | Single character               | 1            | `char grade = 'A';`       |
| `_Bool`   | Boolean (true or false)        | 1            | `_Bool isValid = 1;`      |

- **Integers** (`int`): Used to store whole numbers, e.g., `5`, `-10`.
- **Floating-Point Numbers** (`float`, `double`): Used to store numbers with decimal points.
- **Characters** (`char`): Used to store single characters or symbols, e.g., `'A'`, `'z'`, `'3'`.
- **Boolean** (`_Bool`): Used to store values `0` (false) and `1` (true).

### Example Program:

```c
#include <stdio.h>

int main() {
    int age = 25;           // Integer
    float height = 5.9;     // Floating-point
    char grade = 'A';       // Character
    _Bool isValid = 1;      // Boolean

    printf("Age: %d\n", age);
    printf("Height: %.1f\n", height);
    printf("Grade: %c\n", grade);
    printf("Valid: %d\n", isValid);

    return 0;
}
```


