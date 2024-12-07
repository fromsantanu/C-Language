# Recursion in C

Recursion is a powerful concept in programming where a function calls itself to solve a problem. It is particularly useful for problems that can be broken down into smaller, similar subproblems.

---

## 1. **What Is Recursion?**

A recursive function is a function that calls itself, either directly or indirectly, to perform a repetitive task. Each recursive call reduces the problem into smaller instances until it reaches a base condition, which stops further recursion.

---

## 2. **Key Components of Recursion**

### 2.1 **Base Case**
The base case defines when the recursion should stop. Without a base case, the function would keep calling itself indefinitely, leading to a stack overflow error.

### 2.2 **Recursive Case**
The recursive case is the part of the function where the recursion occurs, reducing the problem to a simpler form.

---

## 3. **How Recursion Works**

When a recursive function is called:
1. The current function execution is paused and stored on the **call stack**.
2. The recursive function executes, possibly calling itself again.
3. When the base case is reached, recursion stops, and the stored function calls on the stack are resolved in reverse order.

---

## 4. **Examples of Recursion**

### 4.1 **Factorial Calculation**

The factorial of a number \( n \) is defined as:
\[
n! = n \times (n - 1) \times (n - 2) \times \ldots \times 1
\]
With the base case:
\[
0! = 1
\]

#### Example:
```c
#include <stdio.h>

// Recursive function to calculate factorial
int factorial(int n) {
    if (n == 0) { // Base case
        return 1;
    }
    return n * factorial(n - 1); // Recursive case
}

int main() {
    int num = 5;
    printf("Factorial of %d is %d\n", num, factorial(num));
    return 0;
}
```

**Output**:
```
Factorial of 5 is 120
```

---

### 4.2 **Fibonacci Sequence**

The Fibonacci sequence is defined as:
\[
F(n) = F(n - 1) + F(n - 2)
\]
With base cases:
\[
F(0) = 0, \quad F(1) = 1
\]

#### Example:
```c
#include <stdio.h>

// Recursive function to calculate Fibonacci numbers
int fibonacci(int n) {
    if (n == 0) { // Base case
        return 0;
    }
    if (n == 1) { // Base case
        return 1;
    }
    return fibonacci(n - 1) + fibonacci(n - 2); // Recursive case
}

int main() {
    int terms = 10;

    printf("Fibonacci series up to %d terms:\n", terms);
    for (int i = 0; i < terms; i++) {
        printf("%d ", fibonacci(i));
    }
    printf("\n");

    return 0;
}
```

**Output**:
```
Fibonacci series up to 10 terms:
0 1 1 2 3 5 8 13 21 34
```

---

### 4.3 **Sum of Natural Numbers**

To find the sum of the first \( n \) natural numbers:
\[
S(n) = n + S(n - 1)
\]
With the base case:
\[
S(0) = 0
\]

#### Example:
```c
#include <stdio.h>

// Recursive function to calculate the sum of natural numbers
int sum(int n) {
    if (n == 0) { // Base case
        return 0;
    }
    return n + sum(n - 1); // Recursive case
}

int main() {
    int num = 10;
    printf("Sum of first %d natural numbers is %d\n", num, sum(num));
    return 0;
}
```

**Output**:
```
Sum of first 10 natural numbers is 55
```

---

## 5. **Types of Recursion**

### 5.1 **Direct Recursion**
A function directly calls itself.

#### Example:
```c
void func() {
    func(); // Direct recursion
}
```

### 5.2 **Indirect Recursion**
A function calls another function, which in turn calls the original function.

#### Example:
```c
#include <stdio.h>

void funcA(int n);
void funcB(int n);

void funcA(int n) {
    if (n > 0) {
        printf("A: %d\n", n);
        funcB(n - 1); // Call to another function
    }
}

void funcB(int n) {
    if (n > 0) {
        printf("B: %d\n", n);
        funcA(n - 1); // Call back to the original function
    }
}

int main() {
    funcA(3);
    return 0;
}
```

**Output**:
```
A: 3
B: 2
A: 1
```

---

## 6. **Advantages and Disadvantages of Recursion**

### Advantages:
1. Simplifies code for problems that are naturally recursive (e.g., factorial, Fibonacci, tree traversals).
2. Reduces the need for complex loop structures.

### Disadvantages:
1. **Performance**: Each recursive call requires additional memory for the call stack.
2. **Risk of Stack Overflow**: If the base case is not defined or not reachable, recursion can lead to infinite calls.
3. **Difficult to Debug**: Recursive functions can be harder to debug compared to iterative solutions.

---

## 7. **Recursion vs Iteration**

| Feature            | Recursion                          | Iteration                    |
|--------------------|------------------------------------|-----------------------------|
| **Definition**      | Function calls itself.             | Repeats code using loops.   |
| **Memory Usage**    | Uses stack memory for each call.   | Uses a single memory block. |
| **Complexity**      | Simplifies naturally recursive tasks. | Often more efficient for simple tasks. |
| **Risk**            | Stack overflow if not designed well. | No stack overflow.          |

---

## 8. **Practice Exercises**

1. Write a recursive function to calculate the greatest common divisor (GCD) of two numbers.
2. Implement a recursive function to reverse a string.
3. Create a program to find the height of a binary tree using recursion.
4. Write a program to solve the Towers of Hanoi problem using recursion.

---

## 9. **Best Practices for Recursion**

1. **Define a Base Case**: Ensure every recursive function has a reachable base case.
2. **Limit Depth**: Avoid deep recursion for problems that can be solved iteratively.
3. **Memoization**: Use memoization to optimize recursive functions like Fibonacci, where overlapping subproblems exist.
4. **Test Thoroughly**: Recursion can lead to subtle bugs; test edge cases carefully.

---

Recursion is a fundamental concept in C programming, enabling elegant solutions to complex problems. However, it must be used judiciously to avoid performance and memory issues. In the next chapter, we will explore **arrays**, a vital data structure in C that complements recursive and iterative programming techniques.
