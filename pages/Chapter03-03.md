## 3. **Logical Operators**

Logical operators are used to combine multiple conditions.

| Operator | Description          | Example          | Result                          |
|----------|----------------------|------------------|---------------------------------|
| `&&`     | Logical AND          | `a && b`         | 1 if both `a` and `b` are true |
| `||`     | Logical OR           | `a || b`         | 1 if either `a` or `b` is true |
| `!`      | Logical NOT          | `!a`             | 1 if `a` is false, otherwise 0 |

### Example:
```c
#include <stdio.h>

int main() {
    int a = 1, b = 0;

    printf("a && b: %d\n", a && b);
    printf("a || b: %d\n", a || b);
    printf("!a: %d\n", !a);

    return 0;
}
```

---

