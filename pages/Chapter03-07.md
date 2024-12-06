## 7. **Increment and Decrement Operators**

Increment (`++`) and decrement (`--`) operators are used to increase or decrease a variable's value by 1.

| Operator | Description                   | Example  | Equivalent To |
|----------|-------------------------------|----------|---------------|
| `++a`    | Pre-increment                 | `++a`    | `a = a + 1`   |
| `a++`    | Post-increment                | `a++`    | `a = a + 1`   |
| `--a`    | Pre-decrement                 | `--a`    | `a = a - 1`   |
| `a--`    | Post-decrement                | `a--`    | `a = a - 1`   |

### Example:
```c
#include <stdio.h>

int main() {
    int a = 5;

    printf("Pre-increment: %d\n", ++a);
    printf("Post-increment: %d\n", a++);
    printf("After post-increment: %d\n", a);

    printf("Pre-decrement: %d\n", --a);
    printf("Post-decrement: %d\n", a--);
    printf("After post-decrement: %d\n", a);

    return 0;
}
```

---

In this chapter, we covered the most

 commonly used operators in C, which form the basis for writing complex programs. Understanding these operators will allow you to perform calculations, comparisons, and manipulations effectively in your C programs. In the next chapter, we will dive into control structures, which help manage the flow of your program.

