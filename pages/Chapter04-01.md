# Chapter: If, If-Else, and Nested If-Else

Control flow statements in C allow programmers to make decisions based on certain conditions. The **if**, **if-else**, and **nested if-else** structures are fundamental decision-making constructs in C. In this chapter, we will explore these constructs with detailed explanations and examples.

---

## 1. **The `if` Statement**

The `if` statement evaluates a condition and executes the block of code inside it only if the condition is true (non-zero). If the condition is false (zero), the code block is skipped.

### Syntax:
```c
if (condition) {
    // Code to execute if the condition is true
}
```

### Example:
```c
#include <stdio.h>

int main() {
    int age = 18;

    if (age >= 18) {
        printf("You are eligible to vote.\n");
    }

    return 0;
}
```

In this example, the message is printed only if `age` is greater than or equal to 18.

---

## 2. **The `if-else` Statement**

The `if-else` statement provides two options:
- The `if` block executes if the condition is true.
- The `else` block executes if the condition is false.

### Syntax:
```c
if (condition) {
    // Code to execute if the condition is true
} else {
    // Code to execute if the condition is false
}
```

### Example:
```c
#include <stdio.h>

int main() {
    int number;

    printf("Enter a number: ");
    scanf("%d", &number);

    if (number % 2 == 0) {
        printf("The number is even.\n");
    } else {
        printf("The number is odd.\n");
    }

    return 0;
}
```

In this example, the program checks whether the input number is even or odd and executes the appropriate block.

---

## 3. **The `nested if-else` Statement**

When there are multiple conditions to check, `if-else` statements can be nested within one another. This is called a **nested if-else**.

### Syntax:
```c
if (condition1) {
    // Code to execute if condition1 is true
    if (condition2) {
        // Code to execute if condition2 is also true
    } else {
        // Code to execute if condition2 is false
    }
} else {
    // Code to execute if condition1 is false
}
```

### Example:
```c
#include <stdio.h>

int main() {
    int marks;

    printf("Enter your marks: ");
    scanf("%d", &marks);

    if (marks >= 90) {
        printf("Grade: A\n");
    } else if (marks >= 75) {
        printf("Grade: B\n");
    } else if (marks >= 50) {
        printf("Grade: C\n");
    } else {
        printf("Grade: F\n");
    }

    return 0;
}
```

In this example, the program determines the grade based on the marks entered by the user. The conditions are evaluated in sequence, and the first true condition executes its corresponding block.

---

## 4. **Key Points to Remember**
- **Curly Braces**: Always use `{}` for blocks even if the block has only one statement. This avoids confusion and errors during program expansion.
  
  Example:
  ```c
  if (a > b)
      printf("a is greater.\n"); // Without braces, only this line is part of the `if`
      printf("This line is always executed.\n"); // Not part of the `if` block
  ```

- **Chained Conditions**: Multiple `if-else` statements can be chained together to handle more complex decision-making processes.

- **Nested if-else**: While effective for multi-condition checking, nested statements can become difficult to read. In such cases, consider using other constructs like the `switch` statement.

---

## 5. **Comprehensive Example**
This program checks if a number is positive, negative, or zero:
```c
#include <stdio.h>

int main() {
    int number;

    printf("Enter a number: ");
    scanf("%d", &number);

    if (number > 0) {
        printf("The number is positive.\n");
    } else if (number < 0) {
        printf("The number is negative.\n");
    } else {
        printf("The number is zero.\n");
    }

    return 0;
}
```

---

## 6. **Using Logical Operators with If Statements**

Logical operators like `&&` (AND) and `||` (OR) can combine conditions in `if` statements for more complex decision-making.

### Example:
```c
#include <stdio.h>

int main() {
    int age = 20;
    char gender = 'M';

    if (age > 18 && gender == 'M') {
        printf("You are an adult male.\n");
    } else {
        printf("Condition not met.\n");
    }

    return 0;
}
```

---

## 7. **Practice Exercises**

1. Write a program to check if a number is divisible by both 3 and 5.
2. Create a program to determine if a given year is a leap year using nested `if` statements.
3. Write a program to find the largest of three numbers using `if-else` or nested `if-else`.

---

By understanding `if`, `if-else`, and `nested if-else` constructs, you can create programs that handle a variety of decision-making scenarios. In the next chapter, we will explore loops, which allow you to repeat actions based on conditions.
