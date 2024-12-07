# Unions and Differences from Structures in C

Unions in C, like structures, are user-defined data types that allow you to group variables of different types under a single name. However, unions differ significantly in how memory is allocated and how their members are accessed. This chapter explores unions, their syntax, applications, and key differences from structures.

---

## 1. **What Is a Union?**

A **union** is a special data type in C where all members share the same memory location. Unlike a structure, which allocates separate memory for each member, a union allocates enough memory to hold the largest member. This memory-sharing characteristic makes unions suitable for situations where only one member is used at a time.

---

## 2. **Defining a Union**

### Syntax:
```c
union union_name {
    data_type member1;
    data_type member2;
    // More members
};
```

### Example:
```c
#include <stdio.h>

// Define a union
union Data {
    int i;
    float f;
    char str[20];
};
```

This union `Data` can store an integer (`i`), a float (`f`), or a string (`str`), but only one member can hold a valid value at any given time.

---

## 3. **Declaring and Initializing a Union**

### Declaration:
```c
union union_name variable_name;
```

### Initialization:
You can initialize the union at the time of declaration:
```c
union Data data = {10}; // Initializes the first member
```

### Example:
```c
#include <stdio.h>

union Data {
    int i;
    float f;
    char str[20];
};

int main() {
    union Data data;

    // Assign values to union members
    data.i = 10;
    printf("Integer: %d\n", data.i);

    data.f = 220.5;
    printf("Float: %.2f\n", data.f);

    snprintf(data.str, sizeof(data.str), "Hello");
    printf("String: %s\n", data.str);

    return 0;
}
```

**Output**:
```
Integer: 10
Float: 220.50
String: Hello
```

**Note**: When you assign a value to one member, the value of other members becomes undefined due to memory sharing.

---

## 4. **Accessing Union Members**

Union members are accessed using the dot operator (`.`) for variables or the arrow operator (`->`) for pointers.

### Example:
```c
#include <stdio.h>

union Data {
    int i;
    float f;
};

int main() {
    union Data data, *ptr;

    data.i = 10; // Access via variable
    printf("Value of i: %d\n", data.i);

    ptr = &data; // Access via pointer
    ptr->f = 220.5;
    printf("Value of f: %.2f\n", ptr->f);

    return 0;
}
```

**Output**:
```
Value of i: 10
Value of f: 220.50
```

---

## 5. **Key Differences Between Structures and Unions**

| Feature                  | Structure                     | Union                         |
|--------------------------|-------------------------------|-------------------------------|
| **Memory Allocation**    | Allocates separate memory for each member. | Allocates memory equal to the largest member. |
| **Access to Members**    | All members can hold valid values simultaneously. | Only one member can hold a valid value at a time. |
| **Size**                 | Sum of sizes of all members.  | Size of the largest member.   |
| **Use Case**             | Suitable for grouping related data that needs to be accessed simultaneously. | Suitable for memory-efficient storage of variables used one at a time. |

---

### Example: Memory Allocation
```c
#include <stdio.h>

struct StructureExample {
    int i;
    float f;
};

union UnionExample {
    int i;
    float f;
};

int main() {
    printf("Size of structure: %lu bytes\n", sizeof(struct StructureExample));
    printf("Size of union: %lu bytes\n", sizeof(union UnionExample));

    return 0;
}
```

**Output**:
```
Size of structure: 8 bytes
Size of union: 4 bytes
```

---

## 6. **Applications of Unions**

1. **Efficient Memory Usage**:
   - Unions are ideal for memory-constrained applications where multiple data types share the same memory space.

2. **Variant Data Handling**:
   - Unions can store data in different formats (e.g., integer and float) for the same variable, commonly used in embedded systems and hardware programming.

3. **Type Conversion**:
   - Unions can be used for bit-level operations and interpreting raw data in different formats.

---

### Example: Storing Variant Data
```c
#include <stdio.h>

union Variant {
    int i;
    float f;
    char str[20];
};

void printVariant(union Variant var, char type) {
    if (type == 'i') {
        printf("Integer: %d\n", var.i);
    } else if (type == 'f') {
        printf("Float: %.2f\n", var.f);
    } else if (type == 's') {
        printf("String: %s\n", var.str);
    }
}

int main() {
    union Variant var;

    var.i = 42;
    printVariant(var, 'i');

    var.f = 3.14;
    printVariant(var, 'f');

    snprintf(var.str, sizeof(var.str), "Hello Union");
    printVariant(var, 's');

    return 0;
}
```

**Output**:
```
Integer: 42
Float: 3.14
String: Hello Union
```

---

## 7. **Common Mistakes with Unions**

1. **Accessing Undefined Members**:
   - Only one member of a union can hold valid data. Accessing other members may lead to undefined behavior.

2. **Incorrect Memory Usage**:
   - Misusing the shared memory can cause logical errors in the program.

3. **Complex Structures**:
   - Avoid using unions for complex data types, as the memory-sharing mechanism can create confusion.

---

## 8. **Practice Exercises**

1. Define a union for storing data in different formats (integer, float, and string). Write a program to input and display data in each format.
2. Create a union for a sensor reading that can store temperature, pressure, or humidity. Write a program to input and display readings based on the type of data.
3. Compare the size of a structure and a union containing the same members and explain the differences.
4. Implement a union to simulate type conversion (e.g., converting a float to its bit representation as an integer).
5. Write a program to demonstrate memory sharing in a union by assigning values to different members and observing the results.

---

## 9. **Key Points to Remember**

1. A union allocates memory equal to its largest member, and all members share the same memory location.
2. Use the dot operator (`.`) or arrow operator (`->`) to access union members.
3. Only one member of a union can hold a valid value at a time.
4. Unions are memory-efficient but require careful management to avoid undefined behavior.
5. Structures are better suited for grouping data used simultaneously, while unions are ideal for storing variant data.

---

Unions provide a powerful and memory-efficient way to handle variant data in C programming. By understanding their differences from structures and applying them in appropriate scenarios, you can leverage unions to write more efficient and effective programs. In the next chapter, we will explore **bitwise operations in C**, a topic closely related to low-level data manipulation and unions.
