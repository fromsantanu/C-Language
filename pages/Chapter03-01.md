# C Operators

Operators in C are special symbols or keywords used to perform operations on variables and values. They are fundamental building blocks in any program, enabling arithmetic, logical, and bit-level manipulations. In this chapter, we’ll cover the most commonly used operators in C.

---

## 1. **Arithmetic Operators**

Arithmetic operators are used to perform basic mathematical operations like addition, subtraction, multiplication, division, and modulus.

| Operator | Description         | Example          | Result        |
|----------|---------------------|------------------|---------------|
| `+`      | Addition            | `a + b`          | Sum of `a` and `b` |
| `-`      | Subtraction         | `a - b`          | Difference of `a` and `b` |
| `*`      | Multiplication      | `a * b`          | Product of `a` and `b` |
| `/`      | Division            | `a / b`          | Quotient of `a` divided by `b` |
| `%`      | Modulus (Remainder) | `a % b`          | Remainder when `a` is divided by `b` |

### Example:
```c
#include <stdio.h>

int main() {
    int a = 10, b = 3;
    
    printf("Addition: %d\n", a + b);
    printf("Subtraction: %d\n", a - b);
    printf("Multiplication: %d\n", a * b);
    printf("Division: %d\n", a / b);
    printf("Modulus: %d\n", a % b);

    return 0;
}
```

---

