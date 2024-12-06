## 2. **Relational Operators**

Relational operators are used to compare two values. They return `1` (true) if the condition is satisfied and `0` (false) otherwise.

| Operator | Description       | Example   | Result          |
|----------|-------------------|-----------|-----------------|
| `==`     | Equal to          | `a == b`  | 1 if `a` equals `b`, otherwise 0 |
| `!=`     | Not equal to      | `a != b`  | 1 if `a` is not equal to `b`, otherwise 0 |
| `>`      | Greater than      | `a > b`   | 1 if `a` is greater than `b`, otherwise 0 |
| `<`      | Less than         | `a < b`   | 1 if `a` is less than `b`, otherwise 0 |
| `>=`     | Greater than or equal to | `a >= b` | 1 if `a` is greater than or equal to `b`, otherwise 0 |
| `<=`     | Less than or equal to    | `a <= b` | 1 if `a` is less than or equal to `b`, otherwise 0 |

### Example:
```c
#include <stdio.h>

int main() {
    int a = 5, b = 10;

    printf("a == b: %d\n", a == b);
    printf("a != b: %d\n", a != b);
    printf("a > b: %d\n", a > b);
    printf("a < b: %d\n", a < b);
    printf("a >= b: %d\n", a >= b);
    printf("a <= b: %d\n", a <= b);

    return 0;
}
```

---

