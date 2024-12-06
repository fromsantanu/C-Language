## 5. **Bitwise Operators**

Bitwise operators operate on the binary representation of integers.

| Operator | Description         | Example  | Result Explanation |
|----------|---------------------|----------|---------------------|
| `&`      | Bitwise AND         | `a & b`  | Binary AND operation |
| `|`      | Bitwise OR          | `a | b`  | Binary OR operation  |
| `^`      | Bitwise XOR         | `a ^ b`  | Binary XOR operation |
| `~`      | Bitwise NOT         | `~a`     | Binary complement    |
| `<<`     | Left shift          | `a << b` | Shift bits left      |
| `>>`     | Right shift         | `a >> b` | Shift bits right     |

### Example:
```c
#include <stdio.h>

int main() {
    int a = 5, b = 3; // Binary: a = 0101, b = 0011

    printf("a & b: %d\n", a & b);
    printf("a | b: %d\n", a | b);
    printf("a ^ b: %d\n", a ^ b);
    printf("~a: %d\n", ~a);
    printf("a << 1: %d\n", a << 1);
    printf("a >> 1: %d\n", a >> 1);

    return 0;
}
```

---


