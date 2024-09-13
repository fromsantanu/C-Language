## 4. **Input and Output in C (`printf` and `scanf`)**

### 4.1 **The `printf()` Function**

The `printf()` function is used to display output on the console. It prints formatted text and variables to the standard output (typically the screen).

#### Syntax of `printf()`:
```c
printf("format string", variables);
```

The **format string** contains text and format specifiers that represent the variables you want to print.

#### Common Format Specifiers:
- `%d` or `%i` : Integer
- `%f`         : Float
- `%lf`        : Double
- `%c`         : Character
- `%s`         : String

### Example:
```c
#include <stdio.h>

int main() {
    int age = 25;
    float height = 5.9;
    char grade = 'A';

    printf("Age: %d\n", age);
    printf("Height: %.1f\n", height);
    printf("Grade: %c\n", grade);

    return 0;
}
```

In this example, `%d` is used for printing an integer (`age`), `%f` is for floating-point numbers (`height`), and `%c` is for characters (`grade`).

### 4.2 **The `scanf()` Function**

The `scanf()` function is used to take input from the user. It reads data from standard input (usually the keyboard) and assigns it to variables.

#### Syntax of `scanf()`:
```c
scanf("format string", &variables);
```

Note that the `&` (address-of operator) is used before variable names in `scanf()` to provide the address where the input should be stored.

### Example:
```c
#include <stdio.h>

int main() {
    int age;
    float height;

    // Taking input from the user
    printf("Enter your age: ");
    scanf("%d", &age);

    printf("Enter your height: ");
    scanf("%f", &height);

    // Displaying the input
    printf("You entered age: %d and height: %.1f\n", age, height);

    return 0;
}
```

In this program, the user is prompted to enter their age and height, which are then stored in the `age` and `height` variables using the `scanf()` function.

### Key Points:
- Use the `&` operator with variables in `scanf()` to provide the memory address.
- Always ensure the format specifier matches the data type of the variable.

---

In this chapter, we introduced some of the most basic concepts of C programming. Understanding variables, data types, keywords, constants, literals, and the `printf()` and `scanf()` functions will enable you to begin writing simple C programs. In the next chapter, we will explore control structures, including conditional statements and loops, which will help you to manage the flow of execution in your programs.
