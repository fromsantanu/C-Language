# Function Arguments and Return Values

Functions in C are powerful tools for modular programming, and their effectiveness lies in how they interact with the rest of the program through **arguments** and **return values**. This chapter covers how to pass data to functions using arguments and retrieve results using return values.

---

## 1. **Function Arguments**

Arguments (or parameters) are variables passed to a function when it is called. They allow functions to operate on external data. There are two primary ways to pass arguments to a function:
- **Pass-by-Value**
- **Pass-by-Reference**

---

### 1.1 **Pass-by-Value**

In **pass-by-value**, a copy of the actual argument is passed to the function. Any changes made to the parameter inside the function do not affect the original variable.

#### Example:
```c
#include <stdio.h>

// Function to swap two numbers (incorrectly using pass-by-value)
void swap(int x, int y) {
    int temp = x;
    x = y;
    y = temp;
    printf("Inside swap function: x = %d, y = %d\n", x, y);
}

int main() {
    int a = 5, b = 10;

    printf("Before swap: a = %d, b = %d\n", a, b);
    swap(a, b);
    printf("After swap: a = %d, b = %d\n", a, b);

    return 0;
}
```

**Output**:
```
Before swap: a = 5, b = 10
Inside swap function: x = 10, y = 5
After swap: a = 5, b = 10
```

In this example, the values of `a` and `b` in the main function remain unchanged because only copies of their values are passed to `swap`.

---

### 1.2 **Pass-by-Reference**

In **pass-by-reference**, the memory address of the actual argument is passed to the function. This allows the function to directly modify the original variable.

#### Example:
```c
#include <stdio.h>

// Function to swap two numbers using pass-by-reference
void swap(int *x, int *y) {
    int temp = *x;
    *x = *y;
    *y = temp;
}

int main() {
    int a = 5, b = 10;

    printf("Before swap: a = %d, b = %d\n", a, b);
    swap(&a, &b); // Pass addresses of a and b
    printf("After swap: a = %d, b = %d\n", a, b);

    return 0;
}
```

**Output**:
```
Before swap: a = 5, b = 10
After swap: a = 10, b = 5
```

In this example, the values of `a` and `b` are successfully swapped because their addresses were passed to the function.

---

## 2. **Return Values**

A function can return a value to the caller using the `return` statement. The type of value returned must match the function's declared return type.

### 2.1 **Returning a Single Value**

A function can return one value at a time.

#### Example:
```c
#include <stdio.h>

// Function to calculate the square of a number
int square(int x) {
    return x * x;
}

int main() {
    int num = 5;
    int result = square(num); // Call the function and store the result

    printf("Square of %d is %d\n", num, result);

    return 0;
}
```

**Output**:
```
Square of 5 is 25
```

---

### 2.2 **Returning Multiple Values**

Since a function can only return a single value, returning multiple values can be achieved using pointers or structures.

#### Example: Returning Multiple Values Using Pointers
```c
#include <stdio.h>

// Function to calculate quotient and remainder
void calculate(int dividend, int divisor, int *quotient, int *remainder) {
    *quotient = dividend / divisor;
    *remainder = dividend % divisor;
}

int main() {
    int dividend = 10, divisor = 3, quotient, remainder;

    calculate(dividend, divisor, &quotient, &remainder);

    printf("Quotient: %d, Remainder: %d\n", quotient, remainder);

    return 0;
}
```

**Output**:
```
Quotient: 3, Remainder: 1
```

---

### 2.3 **Returning a Structure**

A structure can be used to encapsulate multiple values and return them from a function.

#### Example:
```c
#include <stdio.h>

// Define a structure
struct Result {
    int quotient;
    int remainder;
};

// Function to calculate quotient and remainder
struct Result calculate(int dividend, int divisor) {
    struct Result res;
    res.quotient = dividend / divisor;
    res.remainder = dividend % divisor;
    return res;
}

int main() {
    int dividend = 10, divisor = 3;
    struct Result result = calculate(dividend, divisor);

    printf("Quotient: %d, Remainder: %d\n", result.quotient, result.remainder);

    return 0;
}
```

**Output**:
```
Quotient: 3, Remainder: 1
```

---

## 3. **Void Functions**

Functions with a `void` return type do not return any value. These functions are generally used to perform actions like displaying output.

#### Example:
```c
#include <stdio.h>

// Function to display a message
void greet() {
    printf("Hello, welcome to C programming!\n");
}

int main() {
    greet(); // Call the function
    return 0;
}
```

**Output**:
```
Hello, welcome to C programming!
```

---

## 4. **Function Arguments and Default Behavior**

In C, function arguments can behave differently based on how they are passed:
- **Default Argument Values**: C does not support default argument values like some other languages (e.g., C++). However, you can simulate this behavior using function overloading or optional parameters through additional logic.
  
- **Variable Number of Arguments**: The `stdarg.h` library provides support for functions that accept a variable number of arguments (e.g., `printf`).

---

## 5. **Key Points**

1. **Argument Matching**:
   - The number, type, and order of arguments in the function call must match the function's declaration and definition.

2. **Pass-by-Value vs. Pass-by-Reference**:
   - Use **pass-by-value** when you don't want to modify the original variable.
   - Use **pass-by-reference** when you need to modify the original variable or return multiple values.

3. **Return Values**:
   - Functions must return a value matching their return type (except for `void` functions).

4. **Reusability**:
   - Design functions to perform specific tasks for better reusability and modularity.

---

## 6. **Practice Exercises**

1. Write a program with a function that takes two integers and returns their greatest common divisor (GCD).
2. Create a function that takes three integers and returns the largest among them.
3. Implement a program that calculates the area and perimeter of a rectangle using a function that returns multiple values.

---

By mastering function arguments and return values, you can design efficient and modular programs. In the next chapter, we will explore **recursion**, a powerful technique where a function calls itself to solve complex problems.
