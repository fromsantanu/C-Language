# Chapter: Loops in C (For, While, Do-While)

Loops are an essential part of programming that allow the repetition of a block of code multiple times based on a condition. In C, there are three types of loops: **for**, **while**, and **do-while**. Each loop has its own use case and structure.

---

## 1. **Why Use Loops?**

Loops are used when you need to perform repetitive tasks without writing the same code multiple times. For example:
- Printing numbers from 1 to 10.
- Calculating the sum of a series.
- Iterating over arrays.

---

## 2. **The `for` Loop**

The `for` loop is used when the number of iterations is known beforehand. It has three components:
1. **Initialization**: Sets the starting point of the loop.
2. **Condition**: Evaluated before each iteration; the loop continues if true.
3. **Update**: Modifies the loop variable after each iteration.

### Syntax:
```c
for (initialization; condition; update) {
    // Code to execute
}
```

### Example: Printing Numbers from 1 to 10
```c
#include <stdio.h>

int main() {
    for (int i = 1; i <= 10; i++) {
        printf("%d\n", i);
    }
    return 0;
}
```

**How It Works**:
1. The variable `i` is initialized to 1.
2. The condition `i <= 10` is checked.
3. If true, the loop body is executed, and `i` is incremented (`i++`).
4. This process repeats until the condition becomes false.

### Nested `for` Loop
You can nest `for` loops to handle multidimensional tasks, such as printing a pattern:
```c
#include <stdio.h>

int main() {
    for (int i = 1; i <= 3; i++) {
        for (int j = 1; j <= i; j++) {
            printf("* ");
        }
        printf("\n");
    }
    return 0;
}
```

**Output**:
```
* 
* * 
* * * 
```

---

## 3. **The `while` Loop**

The `while` loop is used when the number of iterations is not known beforehand but depends on a condition. The loop continues as long as the condition is true.

### Syntax:
```c
while (condition) {
    // Code to execute
}
```

### Example: Printing Numbers from 1 to 10
```c
#include <stdio.h>

int main() {
    int i = 1;

    while (i <= 10) {
        printf("%d\n", i);
        i++; // Increment to avoid infinite loop
    }

    return 0;
}
```

**How It Works**:
1. The condition `i <= 10` is checked.
2. If true, the loop body is executed.
3. The variable `i` is incremented, and the condition is checked again.

---

## 4. **The `do-while` Loop**

The `do-while` loop is similar to the `while` loop, but the condition is checked **after** the loop body is executed. This ensures the loop executes at least once, even if the condition is false.

### Syntax:
```c
do {
    // Code to execute
} while (condition);
```

### Example: Printing Numbers from 1 to 10
```c
#include <stdio.h>

int main() {
    int i = 1;

    do {
        printf("%d\n", i);
        i++; // Increment to avoid infinite loop
    } while (i <= 10);

    return 0;
}
```

**How It Works**:
1. The loop body is executed first.
2. The condition `i <= 10` is checked after each iteration.
3. If true, the loop repeats; otherwise, it exits.

---

## 5. **Comparison of Loops**

| Feature               | `for` Loop          | `while` Loop            | `do-while` Loop       |
|-----------------------|---------------------|-------------------------|-----------------------|
| **Use Case**          | Fixed iterations    | Unknown iterations      | At least one iteration |
| **Condition Check**   | Before each iteration | Before each iteration  | After each iteration  |
| **Syntax Simplicity** | Compact             | Flexible               | Flexible              |

---

## 6. **Control Statements in Loops**

### 6.1 **`break` Statement**
The `break` statement is used to terminate a loop prematurely.

Example:
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

### 6.2 **`continue` Statement**
The `continue` statement skips the rest of the current iteration and jumps to the next iteration.

Example:
```c
#include <stdio.h>

int main() {
    for (int i = 1; i <= 10; i++) {
        if (i == 5) {
            continue; // Skip when i == 5
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

---

## 7. **Examples and Use Cases**

### Example 1: Sum of Numbers from 1 to N
```c
#include <stdio.h>

int main() {
    int n, sum = 0;

    printf("Enter a number: ");
    scanf("%d", &n);

    for (int i = 1; i <= n; i++) {
        sum += i;
    }

    printf("Sum: %d\n", sum);
    return 0;
}
```

### Example 2: Factorial of a Number
```c
#include <stdio.h>

int main() {
    int n, factorial = 1;

    printf("Enter a number: ");
    scanf("%d", &n);

    for (int i = 1; i <= n; i++) {
        factorial *= i;
    }

    printf("Factorial: %d\n", factorial);
    return 0;
}
```

### Example 3: Infinite Loop
Be cautious with infinite loops; they occur when the condition never becomes false.

```c
#include <stdio.h>

int main() {
    int i = 1;

    while (1) { // Infinite loop
        printf("%d\n", i++);
        if (i > 10) break; // Exit condition
    }

    return 0;
}
```

---

## 8. **Practice Exercises**

1. Write a program to print the Fibonacci series up to a given number using a `for` loop.
2. Create a program that reverses a number using a `while` loop.
3. Write a program to check if a number is a palindrome using a `do-while` loop.
4. Use nested loops to print a multiplication table for numbers 1 through 5.

---

By understanding and mastering loops, you can efficiently handle repetitive tasks in your programs. Loops, combined with control statements, allow for flexible and powerful programming. In the next chapter, we will delve into **arrays**, a critical data structure in C.
