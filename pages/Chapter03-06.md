## 6. **Ternary (Conditional) Operator**

The ternary operator is a shorthand for if-else statements. It takes the form:
```c
condition ? expression1 : expression2;
```
- If the `condition` is true, `expression1` is executed.
- If the `condition` is false, `expression2` is executed.

### Example:
```c
#include <stdio.h>

int main() {
    int a = 10, b = 20;
    int max = (a > b) ? a : b;

    printf("The maximum value is: %d\n", max);

    return 0;
}
```

---

