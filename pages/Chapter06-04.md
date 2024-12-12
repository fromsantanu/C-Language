# Arrays as Function Arguments in C

In C, arrays can be passed to functions to allow manipulation of their elements within the function. This chapter explains how arrays are passed to functions, their behavior, and key considerations when working with arrays as function arguments.

---

## 1. **Passing Arrays to Functions**

When an array is passed to a function:
- The array's **base address** (pointer to the first element) is passed.
- The function operates on the original array, as changes made within the function affect the actual array.

---

### 1.1 **Syntax for Passing Arrays**

```c
void function_name(data_type array_name[], int size);
```

- **`data_type`**: The type of elements in the array.
- **`array_name`**: Name of the array parameter.
- **`size`**: An additional parameter specifying the size of the array (arrays do not inherently carry size information).

---

### 1.2 **Example: Passing an Array to a Function**

#### Example:
```c
#include <stdio.h>

void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int numbers[] = {1, 2, 3, 4, 5};
    int size = sizeof(numbers) / sizeof(numbers[0]);

    printf("Array elements: ");
    printArray(numbers, size);

    return 0;
}
```

**Output**:
```
Array elements: 1 2 3 4 5
```

In this example:
- The array `numbers` is passed to the `printArray` function.
- The size of the array is passed as an additional parameter to control the loop.

---

## 2. **Modifying an Array in a Function**

Since arrays are passed by reference, any changes made to the array elements within the function will reflect in the original array.

#### Example:
```c
#include <stdio.h>

void doubleElements(int arr[], int size) {
    for (int i = 0; i < size; i++) {
        arr[i] *= 2; // Double each element
    }
}

int main() {
    int numbers[] = {1, 2, 3, 4, 5};
    int size = sizeof(numbers) / sizeof(numbers[0]);

    printf("Original array: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", numbers[i]);
    }
    printf("\n");

    doubleElements(numbers, size);

    printf("Modified array: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", numbers[i]);
    }
    printf("\n");

    return 0;
}
```

**Output**:
```
Original array: 1 2 3 4 5
Modified array: 2 4 6 8 10
```

---

## 3. **Pointer Notation for Arrays in Functions**

Arrays can also be passed using pointers, as an array name itself acts as a pointer to its first element.

#### Syntax:
```c
void function_name(data_type *array_name, int size);
```

#### Example:
```c
#include <stdio.h>

void printArray(int *arr, int size) {
    for (int i = 0; i < size; i++) {
        printf("%d ", *(arr + i)); // Access elements using pointer arithmetic
    }
    printf("\n");
}

int main() {
    int numbers[] = {10, 20, 30, 40, 50};
    int size = sizeof(numbers) / sizeof(numbers[0]);

    printf("Array elements: ");
    printArray(numbers, size);

    return 0;
}
```

**Output**:
```
Array elements: 10 20 30 40 50
```

---

## 4. **Multi-Dimensional Arrays as Function Arguments**

Multi-dimensional arrays can also be passed to functions. The function must specify all but the first dimension size.

### Syntax:
```c
void function_name(data_type array_name[][columns], int rows);
```

#### Example: Passing a 2D Array
```c
#include <stdio.h>

void printMatrix(int matrix[][3], int rows) {
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < 3; j++) {
            printf("%d ", matrix[i][j]);
        }
        printf("\n");
    }
}

int main() {
    int matrix[2][3] = {
        {1, 2, 3},
        {4, 5, 6}
    };

    printf("Matrix elements:\n");
    printMatrix(matrix, 2);

    return 0;
}
```

**Output**:
```
Matrix elements:
1 2 3
4 5 6
```

---

## 5. **Best Practices for Passing Arrays**

1. **Pass the Size of the Array**:
   Always pass the array size to avoid out-of-bounds errors, as arrays in C do not carry size information.

2. **Use `const` for Read-Only Arrays**:
   If the array should not be modified, use the `const` keyword to enforce immutability.

   #### Example:
   ```c
   void printArray(const int arr[], int size) {
       for (int i = 0; i < size; i++) {
           printf("%d ", arr[i]);
       }
       printf("\n");
   }
   ```

3. **Avoid Hardcoding Dimensions**:
   For multi-dimensional arrays, prefer flexible functions that accept dimensions as parameters.

4. **Use Pointers for Flexibility**:
   Pointers provide an alternative way to pass arrays and enable dynamic memory allocation.

---

## 6. **Common Mistakes**

1. **Forgetting to Pass the Size**:
   - Leads to undefined behavior when accessing out-of-bounds indices.
   ```c
   void printArray(int arr[]) {
       // No size parameter; risk of out-of-bounds access
   }
   ```

2. **Modifying Read-Only Arrays**:
   - Using `const` helps prevent accidental modifications.

3. **Mismanaging Multi-Dimensional Arrays**:
   - Ensure all dimensions except the first are specified in the function declaration.

---

## 7. **Advantages of Passing Arrays to Functions**

1. **Efficiency**:
   - Passing by reference avoids copying the entire array.
2. **Modularity**:
   - Functions can operate on arrays, making the program modular and easier to debug.
3. **Flexibility**:
   - Arrays can be manipulated directly, reducing the need for temporary variables.

---

## 8. **Practice Exercises**

1. Write a function that takes an array of integers and returns the sum of its elements.
2. Implement a function to reverse an array in place.
3. Create a function to find the maximum and minimum values in an array.
4. Write a program that takes a 2D matrix and computes its transpose.
5. Create a function to merge two sorted arrays into a single sorted array.

---

## 9. **Key Points to Remember**

1. Arrays are passed to functions by reference, allowing direct manipulation of their elements.
2. Always pass the size of the array as a parameter to avoid undefined behavior.
3. Use `const` to protect read-only arrays from accidental modification.
4. For multi-dimensional arrays, specify all dimensions except the first in the function declaration.

---

Passing arrays as function arguments is a fundamental concept in C programming. It allows efficient manipulation of large datasets and forms the basis for many algorithms and data structures. In the next chapter, we will explore **pointers**, which provide even more flexibility in working with arrays and other data structures.

## Here are the solutions to the exercises implemented in C:

---

### 1. Function to calculate the sum of elements in an array

```c
#include <stdio.h>

int sumArray(int arr[], int size) {
    int sum = 0;
    for (int i = 0; i < size; i++) {
        sum += arr[i];
    }
    return sum;
}

int main() {
    int n;
    printf("Enter the number of elements in the array: ");
    scanf("%d", &n);

    int arr[n];
    printf("Enter %d elements: ", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    printf("The sum of the array elements is: %d\n", sumArray(arr, n));
    return 0;
}
```

---

### 2. Function to reverse an array in place

```c
#include <stdio.h>

void reverseArray(int arr[], int size) {
    for (int i = 0, j = size - 1; i < j; i++, j--) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}

int main() {
    int n;
    printf("Enter the number of elements in the array: ");
    scanf("%d", &n);

    int arr[n];
    printf("Enter %d elements: ", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    reverseArray(arr, n);

    printf("Reversed array: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    return 0;
}
```

---

### 3. Function to find the maximum and minimum values in an array

```c
#include <stdio.h>

void findMaxMin(int arr[], int size, int *max, int *min) {
    *max = arr[0];
    *min = arr[0];

    for (int i = 1; i < size; i++) {
        if (arr[i] > *max) {
            *max = arr[i];
        }
        if (arr[i] < *min) {
            *min = arr[i];
        }
    }
}

int main() {
    int n, max, min;
    printf("Enter the number of elements in the array: ");
    scanf("%d", &n);

    int arr[n];
    printf("Enter %d elements: ", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    findMaxMin(arr, n, &max, &min);

    printf("Maximum value: %d\n", max);
    printf("Minimum value: %d\n", min);
    return 0;
}
```

---

### 4. Program to compute the transpose of a 2D matrix

```c
#include <stdio.h>

void transposeMatrix(int rows, int cols, int mat[rows][cols], int transposed[cols][rows]) {
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            transposed[j][i] = mat[i][j];
        }
    }
}

int main() {
    int rows, cols;
    printf("Enter the number of rows and columns: ");
    scanf("%d %d", &rows, &cols);

    int mat[rows][cols], transposed[cols][rows];

    printf("Enter elements of the matrix:\n");
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            scanf("%d", &mat[i][j]);
        }
    }

    transposeMatrix(rows, cols, mat, transposed);

    printf("Transposed matrix:\n");
    for (int i = 0; i < cols; i++) {
        for (int j = 0; j < rows; j++) {
            printf("%d ", transposed[i][j]);
        }
        printf("\n");
    }
    return 0;
}
```

---

### 5. Function to merge two sorted arrays into a single sorted array

```c
#include <stdio.h>

void mergeSortedArrays(int arr1[], int size1, int arr2[], int size2, int result[]) {
    int i = 0, j = 0, k = 0;

    // Merge arrays while elements remain in both
    while (i < size1 && j < size2) {
        if (arr1[i] <= arr2[j]) {
            result[k++] = arr1[i++];
        } else {
            result[k++] = arr2[j++];
        }
    }

    // Copy remaining elements from arr1
    while (i < size1) {
        result[k++] = arr1[i++];
    }

    // Copy remaining elements from arr2
    while (j < size2) {
        result[k++] = arr2[j++];
    }
}

int main() {
    int n1, n2;

    printf("Enter the number of elements in the first sorted array: ");
    scanf("%d", &n1);
    int arr1[n1];
    printf("Enter %d sorted elements: ", n1);
    for (int i = 0; i < n1; i++) {
        scanf("%d", &arr1[i]);
    }

    printf("Enter the number of elements in the second sorted array: ");
    scanf("%d", &n2);
    int arr2[n2];
    printf("Enter %d sorted elements: ", n2);
    for (int i = 0; i < n2; i++) {
        scanf("%d", &arr2[i]);
    }

    int result[n1 + n2];
    mergeSortedArrays(arr1, n1, arr2, n2, result);

    printf("Merged sorted array: ");
    for (int i = 0; i < n1 + n2; i++) {
        printf("%d ", result[i]);
    }
    printf("\n");

    return 0;
}
```

---

### Summary:

1. **Sum of Array Elements**: Computes the sum of integers in the array.
2. **Reverse Array**: Reverses the array in place by swapping elements.
3. **Max and Min Values**: Finds the largest and smallest values using pointers.
4. **Matrix Transpose**: Computes the transpose of a 2D matrix.
5. **Merge Sorted Arrays**: Merges two sorted arrays into one, maintaining sorted order.

These programs cover common and important array manipulations in C.
