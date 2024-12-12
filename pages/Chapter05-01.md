# Definition and Declaration of Functions

Functions are essential components of any C program. They allow you to modularize your code, improving readability, reusability, and maintainability. This chapter covers the **definition** and **declaration** of functions in C.

---

## 1. **What Are Functions?**

A function is a block of code designed to perform a specific task. Once defined, it can be executed (or "called") as many times as needed, with optional input values (parameters) and a result (return value).

### Advantages of Using Functions
- **Code Reusability**: Write once, use multiple times.
- **Modularity**: Break down large problems into manageable parts.
- **Ease of Maintenance**: Modify and debug smaller function blocks easily.
- **Improved Readability**: Programs are easier to understand.

---

## 2. **Function Declaration**

The **function declaration** (also called a function prototype) informs the compiler about the function’s name, return type, and parameters. It allows the function to be used in the program before it is defined.

### Syntax:
```c
return_type function_name(parameter_list);
```

- **`return_type`**: The type of value the function returns. Use `void` if the function does not return a value.
- **`function_name`**: The name of the function, which should be descriptive and follow naming conventions.
- **`parameter_list`**: A list of input parameters, each with a data type and name. If no parameters are needed, use `void`.

### Example:
```c
int add(int a, int b); // Function declaration
```

In this example:
- The function `add` returns an integer (`int`).
- It takes two parameters of type `int`.

---

## 3. **Function Definition**

The **function definition** provides the actual body of the function, containing the logic to be executed when the function is called.

### Syntax:
```c
return_type function_name(parameter_list) {
    // Function body
    return value; // Optional, only if return_type is not void
}
```

- **Function Body**: Contains the statements that define the functionality of the function.
- **Return Statement**: Specifies the value to return to the caller (if applicable).

### Example:
```c
int add(int a, int b) { // Function definition
    return a + b;       // Return the sum of a and b
}
```

---

## 4. **Function Call**

To execute a function, you **call** it by using its name and providing arguments that match its parameter list.

### Syntax:
```c
function_name(argument_list);
```

- **`argument_list`**: Values provided to the function when it is called.

### Example:
```c
#include <stdio.h>

// Function declaration
int add(int a, int b);

int main() {
    int result;

    // Function call
    result = add(10, 20);

    printf("The sum is: %d\n", result);
    return 0;
}

// Function definition
int add(int a, int b) {
    return a + b;
}
```

**Output**:
```
The sum is: 30
```

---

## 5. **Complete Program with Function Declaration, Definition, and Call**

### Example:
```c
#include <stdio.h>

// Function declaration
float calculateArea(float radius);

int main() {
    float radius, area;

    printf("Enter the radius of the circle: ");
    scanf("%f", &radius);

    // Function call
    area = calculateArea(radius);

    printf("The area of the circle is: %.2f\n", area);
    return 0;
}

// Function definition
float calculateArea(float radius) {
    return 3.14159 * radius * radius;
}
```

**Output**:
```
Enter the radius of the circle: 5
The area of the circle is: 78.54
```

---

## 6. **Void Functions**

A function with the return type `void` does not return a value. It is typically used for performing actions like displaying output.

### Example:
```c
#include <stdio.h>

// Function declaration
void greet(void);

int main() {
    greet(); // Function call
    return 0;
}

// Function definition
void greet(void) {
    printf("Hello, welcome to C programming!\n");
}
```

**Output**:
```
Hello, welcome to C programming!
```

---

## 7. **Key Points About Functions**

1. **Declaration vs. Definition**:
   - Declaration introduces the function to the compiler.
   - Definition contains the actual code for the function.

2. **Parameter and Argument Matching**:
   - The number, order, and types of parameters in the declaration must match the function call and definition.

3. **Return Type**:
   - Functions must return a value that matches the return type, except for `void` functions.

4. **Scope of Variables**:
   - Variables declared inside a function are local to that function and cannot be accessed outside it.

---

## 8. **Common Errors and Solutions**

| **Error**                          | **Cause**                                     | **Solution**                                 |
|------------------------------------|-----------------------------------------------|---------------------------------------------|
| Undefined reference to function    | Function is called without being declared     | Add a function declaration above the `main` function or use a header file. |
| Mismatched parameter types         | Function is called with arguments of the wrong type | Ensure the types of arguments match the parameter list in the declaration. |
| Missing return statement           | A function with a non-void return type lacks a return statement | Add a return statement that matches the return type. |

---

## 9. **Practice Exercises**

1. Write a program with a function `multiply` that takes two integers as parameters and returns their product.
2. Create a program that calculates the factorial of a number using a function.
3. Implement a function `isEven` that returns `1` if a number is even and `0` otherwise.

---

By understanding the declaration and definition of functions, you can modularize your code and make it reusable. In the next chapter, we will explore **function parameters and arguments**, including pass-by-value and pass-by-reference concepts.

# Here are the solutions to the exercises implemented in C:

---

### 1. Program with a function `multiply` that takes two integers as parameters and returns their product

```c
#include <stdio.h>

// Function to multiply two integers
int multiply(int a, int b) {
    return a * b;
}

int main() {
    int num1, num2;
    printf("Enter two integers: ");
    scanf("%d %d", &num1, &num2);
    printf("The product of %d and %d is: %d\n", num1, num2, multiply(num1, num2));
    return 0;
}
```

---

### 2. Program that calculates the factorial of a number using a function

```c
#include <stdio.h>

// Function to calculate the factorial
long long factorial(int n) {
    if (n == 0 || n == 1) {
        return 1;
    }
    return n * factorial(n - 1);
}

int main() {
    int num;
    printf("Enter a number to calculate its factorial: ");
    scanf("%d", &num);
    if (num < 0) {
        printf("Factorial is not defined for negative numbers.\n");
    } else {
        printf("The factorial of %d is: %lld\n", num, factorial(num));
    }
    return 0;
}
```

---

### 3. Program with a function `isEven` that returns 1 if a number is even and 0 otherwise

```c
#include <stdio.h>

// Function to check if a number is even
int isEven(int num) {
    return num % 2 == 0;
}

int main() {
    int number;
    printf("Enter a number: ");
    scanf("%d", &number);
    if (isEven(number)) {
        printf("%d is even.\n", number);
    } else {
        printf("%d is odd.\n", number);
    }
    return 0;
}
```

---

### Explanation:

1. **`multiply` Function**: This function takes two integers as parameters, multiplies them, and returns the product.
2. **Factorial Calculation**: A recursive function `factorial` calculates the factorial of a number. It handles the base case of 0 or 1 by returning 1.
3. **`isEven` Function**: This function checks if a number is divisible by 2. It returns `1` if true (even) and `0` otherwise (odd). 

These programs demonstrate the use of functions in C to modularize and simplify the logic for reusability.
