# One-Dimensional Arrays in C

An **array** is a collection of variables of the same type stored in contiguous memory locations. In C, arrays are used to store and manipulate a collection of data, making it easier to work with multiple values. This chapter focuses on **one-dimensional arrays**, their declaration, initialization, and operations.

---

## 1. **What Is a One-Dimensional Array?**

A **one-dimensional array** is a list of elements, all of the same type, accessed using a single index.

### Key Characteristics:
1. **Fixed Size**: The size of the array is defined at the time of declaration and cannot be changed.
2. **Indexing**: Array elements are indexed starting from `0`.
3. **Homogeneous Elements**: All elements in the array are of the same data type.

---

## 2. **Declaration and Initialization**

### 2.1 **Declaring an Array**

To declare an array, specify:
1. The type of elements.
2. The array name.
3. The size of the array (number of elements).

#### Syntax:
```c
data_type array_name[size];
```

#### Example:
```c
int numbers[5];  // Declares an array of 5 integers
float grades[10]; // Declares an array of 10 floating-point numbers
```

### 2.2 **Initializing an Array**

You can initialize an array at the time of declaration using curly braces `{}`.

#### Example:
```c
int numbers[5] = {10, 20, 30, 40, 50}; // Initializes all 5 elements
```

If fewer values are provided, the remaining elements are initialized to `0`:
```c
int numbers[5] = {10, 20}; // Remaining elements are 0
```

You can also omit the size during initialization:
```c
int numbers[] = {10, 20, 30, 40, 50}; // Size is inferred as 5
```

---

## 3. **Accessing and Modifying Array Elements**

Array elements are accessed using their **index**. The index starts at `0` and goes up to `size - 1`.

### Syntax:
```c
array_name[index];
```

#### Example:
```c
#include <stdio.h>

int main() {
    int numbers[5] = {10, 20, 30, 40, 50};

    // Access and print array elements
    printf("First element: %d\n", numbers[0]);
    printf("Last element: %d\n", numbers[4]);

    // Modify an element
    numbers[2] = 100; // Change the third element
    printf("Modified third element: %d\n", numbers[2]);

    return 0;
}
```

**Output**:
```
First element: 10
Last element: 50
Modified third element: 100
```

---

## 4. **Array Operations**

### 4.1 **Traversing an Array**

To access all elements in an array, use a loop.

#### Example:
```c
#include <stdio.h>

int main() {
    int numbers[5] = {10, 20, 30, 40, 50};

    printf("Array elements:\n");
    for (int i = 0; i < 5; i++) {
        printf("%d ", numbers[i]);
    }

    return 0;
}
```

**Output**:
```
Array elements:
10 20 30 40 50
```

---

### 4.2 **Finding the Sum of Array Elements**

#### Example:
```c
#include <stdio.h>

int main() {
    int numbers[5] = {10, 20, 30, 40, 50};
    int sum = 0;

    for (int i = 0; i < 5; i++) {
        sum += numbers[i];
    }

    printf("Sum of array elements: %d\n", sum);
    return 0;
}
```

**Output**:
```
Sum of array elements: 150
```

---

### 4.3 **Finding the Maximum Element**

#### Example:
```c
#include <stdio.h>

int main() {
    int numbers[5] = {10, 20, 30, 40, 50};
    int max = numbers[0];

    for (int i = 1; i < 5; i++) {
        if (numbers[i] > max) {
            max = numbers[i];
        }
    }

    printf("Maximum element: %d\n", max);
    return 0;
}
```

**Output**:
```
Maximum element: 50
```

---

### 4.4 **Reversing an Array**

#### Example:
```c
#include <stdio.h>

int main() {
    int numbers[5] = {10, 20, 30, 40, 50};

    printf("Reversed array:\n");
    for (int i = 4; i >= 0; i--) {
        printf("%d ", numbers[i]);
    }

    return 0;
}
```

**Output**:
```
Reversed array:
50 40 30 20 10
```

---

## 5. **Common Mistakes**

1. **Out-of-Bounds Access**:
   Accessing an index outside the array size leads to undefined behavior.
   ```c
   int numbers[5];
   printf("%d", numbers[5]); // Error: Index out of bounds
   ```

2. **Uninitialized Arrays**:
   Local arrays not explicitly initialized contain garbage values.

3. **Fixed Size**:
   Arrays have a fixed size. Dynamic resizing requires dynamic memory allocation (e.g., using pointers).

---

## 6. **Applications of One-Dimensional Arrays**

1. **Storing and Manipulating Data**:
   - Test scores, temperatures, and sales data.
   
2. **Implementing Algorithms**:
   - Sorting, searching, and mathematical computations.

3. **Handling Strings**:
   - Arrays of characters are used to represent strings.

---

## 7. **Practice Exercises**

1. Write a program to find the average of elements in a one-dimensional array.
2. Implement a program to find the smallest element in an array.
3. Write a program to count the number of occurrences of a specific value in an array.
4. Create a program to shift all elements of an array to the right by one position.
5. Implement a program to merge two one-dimensional arrays into a single array.

---

## 8. **Key Points to Remember**

1. **Fixed Size**: Arrays in C have a fixed size, declared at the time of initialization.
2. **Indexing**: Array indices start at `0`.
3. **Homogeneous Elements**: All elements must be of the same data type.
4. **Initialization**: If not initialized explicitly, array elements may contain garbage values.
5. **Boundaries**: Always ensure array access is within bounds to avoid undefined behavior.

---

One-dimensional arrays are fundamental in C programming, allowing efficient storage and manipulation of data. In the next chapter, we will explore **multi-dimensional arrays**, which enable working with more complex data structures like matrices.

## Here are the solutions to the exercises implemented in C:

---

### 1. Program to find the average of elements in a one-dimensional array

```c
#include <stdio.h>

double findAverage(int arr[], int size) {
    int sum = 0;
    for (int i = 0; i < size; i++) {
        sum += arr[i];
    }
    return (double)sum / size;
}

int main() {
    int n;
    printf("Enter the number of elements: ");
    scanf("%d", &n);

    int arr[n];
    printf("Enter %d elements: ", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    double average = findAverage(arr, n);
    printf("The average of the elements is: %.2f\n", average);
    return 0;
}
```

---

### 2. Program to find the smallest element in an array

```c
#include <stdio.h>

int findSmallest(int arr[], int size) {
    int smallest = arr[0];
    for (int i = 1; i < size; i++) {
        if (arr[i] < smallest) {
            smallest = arr[i];
        }
    }
    return smallest;
}

int main() {
    int n;
    printf("Enter the number of elements: ");
    scanf("%d", &n);

    int arr[n];
    printf("Enter %d elements: ", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    int smallest = findSmallest(arr, n);
    printf("The smallest element is: %d\n", smallest);
    return 0;
}
```

---

### 3. Program to count the number of occurrences of a specific value in an array

```c
#include <stdio.h>

int countOccurrences(int arr[], int size, int value) {
    int count = 0;
    for (int i = 0; i < size; i++) {
        if (arr[i] == value) {
            count++;
        }
    }
    return count;
}

int main() {
    int n, value;
    printf("Enter the number of elements: ");
    scanf("%d", &n);

    int arr[n];
    printf("Enter %d elements: ", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    printf("Enter the value to count: ");
    scanf("%d", &value);

    int occurrences = countOccurrences(arr, n, value);
    printf("The value %d occurs %d times in the array.\n", value, occurrences);
    return 0;
}
```

---

### 4. Program to shift all elements of an array to the right by one position

```c
#include <stdio.h>

void shiftRight(int arr[], int size) {
    int last = arr[size - 1];
    for (int i = size - 1; i > 0; i--) {
        arr[i] = arr[i - 1];
    }
    arr[0] = last;
}

int main() {
    int n;
    printf("Enter the number of elements: ");
    scanf("%d", &n);

    int arr[n];
    printf("Enter %d elements: ", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    shiftRight(arr, n);

    printf("Array after shifting right: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    return 0;
}
```

---

### 5. Program to merge two one-dimensional arrays into a single array

```c
#include <stdio.h>

void mergeArrays(int arr1[], int size1, int arr2[], int size2, int result[]) {
    for (int i = 0; i < size1; i++) {
        result[i] = arr1[i];
    }
    for (int i = 0; i < size2; i++) {
        result[size1 + i] = arr2[i];
    }
}

int main() {
    int n1, n2;
    printf("Enter the number of elements in the first array: ");
    scanf("%d", &n1);
    int arr1[n1];
    printf("Enter %d elements for the first array: ", n1);
    for (int i = 0; i < n1; i++) {
        scanf("%d", &arr1[i]);
    }

    printf("Enter the number of elements in the second array: ");
    scanf("%d", &n2);
    int arr2[n2];
    printf("Enter %d elements for the second array: ", n2);
    for (int i = 0; i < n2; i++) {
        scanf("%d", &arr2[i]);
    }

    int mergedArray[n1 + n2];
    mergeArrays(arr1, n1, arr2, n2, mergedArray);

    printf("Merged array: ");
    for (int i = 0; i < n1 + n2; i++) {
        printf("%d ", mergedArray[i]);
    }
    printf("\n");

    return 0;
}
```

---

### Summary:

1. **Average of Elements**: Computes the average by summing all elements and dividing by the size of the array.
2. **Smallest Element**: Iterates through the array to find the smallest element.
3. **Count Occurrences**: Counts how many times a specified value appears in the array.
4. **Shift Elements Right**: Moves each element to the next index, with the last element wrapping around to the first index.
5. **Merge Arrays**: Combines two arrays into a single array by copying their elements sequentially.

These exercises demonstrate practical array manipulations in C.
