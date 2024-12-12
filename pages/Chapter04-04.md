# Break, Continue, and Goto Statements

Control flow statements like `break`, `continue`, and `goto` in C allow you to manage the flow of program execution. These statements can interrupt the normal sequence of execution to handle specific scenarios, such as skipping an iteration, exiting a loop, or jumping to a specific location in the program.

---

## 1. **The `break` Statement**

The `break` statement is used to terminate a loop or a `switch` statement immediately. Once executed, it exits the loop or `switch`, and the control moves to the next statement after the loop or `switch`.

### Syntax:
```c
break;
```

### Use Cases:
1. To exit a loop prematurely based on a condition.
2. To terminate a `switch` statement.

### Example: Using `break` in a Loop
```c
#include <stdio.h>

int main() {
    for (int i = 1; i <= 10; i++) {
        if (i == 5) {
            break; // Exit the loop when i == 5
        }
        printf("%d\n", i);
    }
    return 0;
}
```

**Output**:
```
1
2
3
4
```

Here, the loop exits when `i` reaches 5, skipping further iterations.

### Example: Using `break` in a `switch` Statement
```c
#include <stdio.h>

int main() {
    int choice;

    printf("Enter a number (1-3): ");
    scanf("%d", &choice);

    switch (choice) {
        case 1:
            printf("You selected Option 1.\n");
            break;
        case 2:
            printf("You selected Option 2.\n");
            break;
        case 3:
            printf("You selected Option 3.\n");
            break;
        default:
            printf("Invalid choice!\n");
    }

    return 0;
}
```

---

## 2. **The `continue` Statement**

The `continue` statement skips the rest of the current iteration of a loop and jumps to the next iteration. Unlike `break`, it does not terminate the loop but skips only the remaining code in the current iteration.

### Syntax:
```c
continue;
```

### Use Cases:
1. To skip specific iterations in a loop.
2. To bypass part of the loop body when a condition is met.

### Example: Skipping a Specific Iteration
```c
#include <stdio.h>

int main() {
    for (int i = 1; i <= 10; i++) {
        if (i == 5) {
            continue; // Skip the iteration when i == 5
        }
        printf("%d\n", i);
    }
    return 0;
}
```

**Output**:
```
1
2
3
4
6
7
8
9
10
```

Here, the value `5` is skipped, but the loop continues for other values.

### Example: Using `continue` in a `while` Loop
```c
#include <stdio.h>

int main() {
    int i = 0;

    while (i < 10) {
        i++;
        if (i % 2 == 0) {
            continue; // Skip even numbers
        }
        printf("%d\n", i);
    }
    return 0;
}
```

**Output**:
```
1
3
5
7
9
```

---

## 3. **The `goto` Statement**

The `goto` statement allows you to jump to a labeled part of the program. While powerful, its use is discouraged as it can make the program flow hard to understand and debug.

### Syntax:
```c
goto label;
// Code block
label:
// Code to execute after jumping
```

### Use Cases:
1. To jump to a specific part of the code in exceptional cases.
2. To create a rudimentary form of error handling.

### Example: Using `goto` to Exit Nested Loops
```c
#include <stdio.h>

int main() {
    for (int i = 1; i <= 3; i++) {
        for (int j = 1; j <= 3; j++) {
            if (i == 2 && j == 2) {
                goto exit; // Exit both loops
            }
            printf("i = %d, j = %d\n", i, j);
        }
    }

exit:
    printf("Exited nested loops.\n");
    return 0;
}
```

**Output**:
```
i = 1, j = 1
i = 1, j = 2
i = 1, j = 3
i = 2, j = 1
Exited nested loops.
```

### Example: Using `goto` for Error Handling
```c
#include <stdio.h>

int main() {
    int num;

    printf("Enter a positive number: ");
    scanf("%d", &num);

    if (num < 0) {
        goto error; // Jump to error handling code
    }

    printf("You entered: %d\n", num);
    return 0;

error:
    printf("Error: Negative number entered!\n");
    return 1;
}
```

---

## 4. **Comparison of `break`, `continue`, and `goto`**

| Feature              | `break`                       | `continue`                  | `goto`                       |
|----------------------|-------------------------------|-----------------------------|-----------------------------|
| **Function**         | Exits a loop or `switch`      | Skips current iteration     | Jumps to a specific label   |
| **Scope**            | Limited to loops and `switch` | Limited to loops            | Can jump anywhere in scope  |
| **Use Case**         | Exiting loops or `switch`     | Skipping specific iterations | Exceptional cases           |
| **Impact on Code**   | Controlled                   | Controlled                  | Can make code difficult to debug |

---

## 5. **Best Practices**

1. Use `break` and `continue` judiciously to improve readability and efficiency.
2. Avoid using `goto` unless absolutely necessary; prefer structured programming constructs like loops and functions.
3. Ensure the use of `break` in `switch` statements to prevent fall-through.
4. Comment well when using `goto` to make the control flow clear.

---

## 6. **Practice Exercises**

1. Write a program to find the first number divisible by 7 between 1 and 100 using a loop with `break`.
2. Create a program that skips printing multiples of 3 between 1 and 20 using `continue`.
3. Implement a program with nested loops that exits both loops using `goto` when a specific condition is met.

---

In this chapter, we explored `break`, `continue`, and `goto` statements and their use cases. While they are powerful tools for managing program flow, they should be used with caution to ensure code clarity and maintainability. In the next chapter, we will delve into **functions**, which enable code modularity and reusability.

## Here are the solutions to the given exercises implemented in C:

---

### 1. Program to find the first number divisible by 7 between 1 and 100 using a loop with `break`

```c
#include <stdio.h>

void findFirstDivisibleBy7() {
    for (int i = 1; i <= 100; i++) {
        if (i % 7 == 0) {
            printf("The first number divisible by 7 between 1 and 100 is: %d\n", i);
            break;
        }
    }
}

int main() {
    findFirstDivisibleBy7();
    return 0;
}
```

---

### 2. Program to skip printing multiples of 3 between 1 and 20 using `continue`

```c
#include <stdio.h>

void skipMultiplesOf3() {
    printf("Numbers between 1 and 20 excluding multiples of 3:\n");
    for (int i = 1; i <= 20; i++) {
        if (i % 3 == 0) {
            continue;
        }
        printf("%d ", i);
    }
    printf("\n");
}

int main() {
    skipMultiplesOf3();
    return 0;
}
```

---

### 3. Program with nested loops that exits both loops using `goto` when a specific condition is met

```c
#include <stdio.h>

void nestedLoopsWithGoto() {
    for (int i = 1; i <= 5; i++) {
        for (int j = 1; j <= 5; j++) {
            printf("i = %d, j = %d\n", i, j);
            if (i == 3 && j == 3) {
                printf("Exiting both loops at i = %d, j = %d\n", i, j);
                goto exit_loops;
            }
        }
    }
exit_loops:
    printf("Exited both loops.\n");
}

int main() {
    nestedLoopsWithGoto();
    return 0;
}
```

---

### Explanation:

1. **Find First Divisible by 7**: The `for` loop iterates from 1 to 100, checks for divisibility by 7, and exits using `break` once the condition is met.
2. **Skip Multiples of 3**: The `continue` statement skips the rest of the loop body when a multiple of 3 is encountered, effectively not printing those numbers.
3. **Nested Loops with `goto`**: The `goto` statement is used to jump out of both loops when `i` and `j` reach a specific condition (`i == 3 && j == 3`).

These programs demonstrate the use of `break`, `continue`, and `goto` effectively in different contexts.
