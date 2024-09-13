## 3. **Structure of a C Program**

Every C program follows a specific structure that allows for efficient compilation and execution. A typical C program consists of various components, including preprocessor directives, a main function, and user-defined functions. Here is the basic structure of a C program:

### Example C Program

```c
#include <stdio.h> // Preprocessor directive to include standard I/O functions

// Function declaration
int add(int, int);

int main() {
    // Variable declaration
    int num1, num2, sum;
    
    // Taking user input
    printf("Enter two integers: ");
    scanf("%d %d", &num1, &num2);
    
    // Function call to add numbers
    sum = add(num1, num2);
    
    // Printing the result
    printf("Sum: %d\n", sum);
    
    return 0; // Returning 0 indicates the program executed successfully
}

// Function definition
int add(int a, int b) {
    return a + b;
}
```

### Components of a C Program

1. **Preprocessor Directives**: These are commands that are processed before the actual compilation begins. They usually begin with `#` (hash symbol). For example, `#include <stdio.h>` includes the Standard Input/Output library, which allows the use of functions like `printf()` and `scanf()`.

2. **Main Function (`main()`)**: The `main()` function is the starting point of any C program. The program's execution begins here. It contains the logic of the program and may call other functions.

3. **Variable Declaration**: In C, all variables must be declared before they are used. This specifies the data type (e.g., `int`, `float`) and allocates memory for the variables.

4. **Input/Output Functions**: Functions like `printf()` and `scanf()` are used for displaying output and taking input from the user, respectively. These functions are part of the `stdio.h` library.

5. **Function Definition**: C supports the use of user-defined functions, which allow dividing a program into smaller, manageable parts. In the example, the `add()` function is defined to add two numbers.

6. **Return Statement**: The `return` statement in the `main()` function returns a value to the operating system. A return value of `0` typically indicates successful execution.

### Execution Flow

The execution of a C program follows this flow:
1. The program begins execution from the `main()` function.
2. The preprocessor directives are handled before compilation.
3. The code inside the `main()` function is executed, including any function calls.
4. If functions are called, their definitions are executed as part of the program.
5. The program ends when the `main()` function finishes executing, returning a value to the operating system.

This simple structure, coupled with its features and portability, makes C one of the most widely used and enduring programming languages across industries and platforms.

