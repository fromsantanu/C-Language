# Multi-Dimensional Arrays in C

In C, multi-dimensional arrays allow the storage and manipulation of data in a grid-like or tabular format. They extend the concept of one-dimensional arrays by adding additional dimensions, making them useful for working with matrices, tables, or higher-dimensional datasets.

---

## 1. **What Are Multi-Dimensional Arrays?**

A **multi-dimensional array** is an array of arrays, where each element is an array itself. The most commonly used type is the **two-dimensional array**, but arrays with three or more dimensions are also supported.

### Example:
A **two-dimensional array** can represent a table with rows and columns, while a **three-dimensional array** can represent a cube or 3D grid.

---

## 2. **Two-Dimensional Arrays**

A **two-dimensional array** is an array of arrays, often visualized as a table with rows and columns.

### 2.1 **Declaration and Initialization**

#### Syntax:
```c
data_type array_name[rows][columns];
```

#### Example:
```c
int matrix[3][4]; // Declares a 3x4 matrix
```

### Initialization:
You can initialize a two-dimensional array at the time of declaration.

#### Example:
```c
int matrix[3][3] = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```

You can omit the inner braces:
```c
int matrix[3][3] = {1, 2, 3, 4, 5, 6, 7, 8, 9};
```

---

### 2.2 **Accessing and Modifying Elements**

Elements in a two-dimensional array are accessed using two indices:
1. **Row index**
2. **Column index**

#### Syntax:
```c
array_name[row_index][column_index];
```

#### Example:
```c
#include <stdio.h>

int main() {
    int matrix[3][3] = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };

    // Accessing an element
    printf("Element at row 1, column 2: %d\n", matrix[1][2]); // Output: 5

    // Modifying an element
    matrix[2][2] = 10;
    printf("Modified element at row 2, column 2: %d\n", matrix[2][2]); // Output: 10

    return 0;
}
```

---

### 2.3 **Traversing a Two-Dimensional Array**

#### Example:
```c
#include <stdio.h>

int main() {
    int matrix[3][3] = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };

    printf("Matrix elements:\n");
    for (int i = 0; i < 3; i++) {         // Loop through rows
        for (int j = 0; j < 3; j++) {     // Loop through columns
            printf("%d ", matrix[i][j]);
        }
        printf("\n"); // New line after each row
    }

    return 0;
}
```

**Output**:
```
Matrix elements:
1 2 3
4 5 6
7 8 9
```

---

## 3. **Three-Dimensional Arrays**

A **three-dimensional array** can be visualized as an array of 2D tables, where each table is indexed by a third dimension.

### 3.1 **Declaration and Initialization**

#### Syntax:
```c
data_type array_name[size1][size2][size3];
```

#### Example:
```c
int cube[2][3][4]; // Declares a 2x3x4 array
```

### Initialization:
```c
int cube[2][2][2] = {
    {{1, 2}, {3, 4}},
    {{5, 6}, {7, 8}}
};
```

---

### 3.2 **Accessing Elements**

Access elements using three indices:
```c
array_name[first_index][second_index][third_index];
```

#### Example:
```c
#include <stdio.h>

int main() {
    int cube[2][2][2] = {
        {{1, 2}, {3, 4}},
        {{5, 6}, {7, 8}}
    };

    printf("Element at [1][1][1]: %d\n", cube[1][1][1]); // Output: 8

    return 0;
}
```

---

## 4. **Memory Layout of Multi-Dimensional Arrays**

Multi-dimensional arrays in C are stored in **row-major order**, meaning:
1. Elements in a row are stored consecutively in memory.
2. Entire rows are stored one after the other.

### Example:
For the array:
```c
int matrix[2][3] = {
    {1, 2, 3},
    {4, 5, 6}
};
```
The memory layout is:
```
1, 2, 3, 4, 5, 6
```

---

## 5. **Applications of Multi-Dimensional Arrays**

1. **Matrices**: Representing mathematical matrices for calculations.
2. **Grids**: Storing and manipulating game boards (e.g., tic-tac-toe).
3. **Data Tables**: Handling tabular data in rows and columns.
4. **3D Modeling**: Representing 3D objects in a grid format.
5. **Dynamic Programming**: Storing solutions to subproblems.

---

## 6. **Common Mistakes**

1. **Out-of-Bounds Access**:
   Accessing indices outside the array dimensions leads to undefined behavior.
   ```c
   int matrix[3][3];
   printf("%d", matrix[3][3]); // Error: Out-of-bounds access
   ```

2. **Uninitialized Arrays**:
   Multi-dimensional arrays not explicitly initialized may contain garbage values.

3. **Incorrect Indexing**:
   Ensure that row and column indices are in the correct order:
   ```c
   int matrix[3][3];
   matrix[2][1] = 5; // Correct
   matrix[1][2] = 5; // Correct
   ```

---

## 7. **Practice Exercises**

1. Write a program to add two 2D matrices of the same size.
2. Implement a program to transpose a 2D matrix.
3. Create a program to multiply two matrices.
4. Write a program to find the sum of all elements in a 3D array.
5. Implement a program to check if a given 2D array is symmetric (i.e., matrix is equal to its transpose).

---

## 8. **Key Points to Remember**

1. **Row-Major Order**: Multi-dimensional arrays are stored row by row in memory.
2. **Initialization**: Always initialize arrays to avoid garbage values.
3. **Nested Loops**: Use nested loops to traverse multi-dimensional arrays.
4. **Memory Use**: Be mindful of the memory requirements for large arrays.

---

Multi-dimensional arrays are powerful tools for handling complex data structures and performing operations like matrix calculations. Mastering these concepts lays the foundation for solving advanced computational problems. In the next chapter, we will delve into **strings in C**, which are implemented as character arrays.
