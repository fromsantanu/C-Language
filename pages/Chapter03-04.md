## 4. **Assignment Operators**

Assignment operators are used to assign values to variables. They can also combine assignment with arithmetic or bitwise operations.

| Operator | Description                   | Example  | Equivalent To   |
|----------|-------------------------------|----------|-----------------|
| `=`      | Assignment                   | `a = b`  | `a = b`         |
| `+=`     | Add and assign               | `a += b` | `a = a + b`     |
| `-=`     | Subtract and assign          | `a -= b` | `a = a - b`     |
| `*=`     | Multiply and assign          | `a *= b` | `a = a * b`     |
| `/=`     | Divide and assign            | `a /= b` | `a = a / b`     |
| `%=`     | Modulus and assign           | `a %= b` | `a = a % b`     |

### Example:
```c
#include <stdio.h>

int main() {
    int a = 10;

    a += 5;
    printf("a += 5: %d\n", a);

    a -= 2;
    printf("a -= 2: %d\n", a);

    a *= 3;
    printf("a *= 3: %d\n", a);

    a /= 4;
    printf("a /= 4: %d\n", a);

    a %= 3;
    printf("a %= 3: %d\n", a);

    return 0;
}
```

---





