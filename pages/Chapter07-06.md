# Dynamic Memory Allocation in C

Dynamic memory allocation allows a program to request and manage memory at runtime. This capability is crucial for creating flexible and efficient programs, especially when dealing with data structures like arrays, linked lists, and trees. In C, the standard library provides functions for dynamic memory management: `malloc`, `calloc`, `realloc`, and `free`.

---

## 1. **What Is Dynamic Memory Allocation?**

Dynamic memory allocation refers to allocating memory during program execution rather than at compile time. The memory is allocated in the **heap**, and pointers are used to access and manage it.

### Key Functions:
1. **`malloc`**: Allocates uninitialized memory.
2. **`calloc`**: Allocates zero-initialized memory.
3. **`realloc`**: Resizes previously allocated memory.
4. **`free`**: Deallocates previously allocated memory.

---

## 2. **Memory Management Functions**

### 2.1 **`malloc` (Memory Allocation)**

- Allocates a specified number of bytes of memory.
- Does not initialize the memory.
- Returns a pointer to the first byte of the allocated memory, or `NULL` if the allocation fails.

#### Syntax:
```c
void *malloc(size_t size);
```

#### Example:
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *arr;
    int n = 5;

    // Allocate memory for 5 integers
    arr = (int *)malloc(n * sizeof(int));

    if (arr == NULL) {
        printf("Memory allocation failed.\n");
        return 1;
    }

    // Initialize and print the array
    for (int i = 0; i < n; i++) {
        arr[i] = i + 1;
        printf("%d ", arr[i]);
    }
    printf("\n");

    // Free the allocated memory
    free(arr);

    return 0;
}
```

**Output**:
```
1 2 3 4 5
```

---

### 2.2 **`calloc` (Contiguous Allocation)**

- Allocates memory for an array of elements and initializes them to zero.
- Returns a pointer to the allocated memory, or `NULL` if the allocation fails.

#### Syntax:
```c
void *calloc(size_t num, size_t size);
```

#### Example:
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *arr;
    int n = 5;

    // Allocate memory for 5 integers and initialize to 0
    arr = (int *)calloc(n, sizeof(int));

    if (arr == NULL) {
        printf("Memory allocation failed.\n");
        return 1;
    }

    // Print the array
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    // Free the allocated memory
    free(arr);

    return 0;
}
```

**Output**:
```
0 0 0 0 0
```

---

### 2.3 **`realloc` (Reallocation)**

- Resizes previously allocated memory to a new size.
- Can expand or shrink the memory block.
- Returns a pointer to the new memory block, or `NULL` if the reallocation fails.

#### Syntax:
```c
void *realloc(void *ptr, size_t size);
```

#### Example:
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *arr;
    int n = 5;

    // Allocate memory for 5 integers
    arr = (int *)malloc(n * sizeof(int));

    if (arr == NULL) {
        printf("Memory allocation failed.\n");
        return 1;
    }

    // Initialize the array
    for (int i = 0; i < n; i++) {
        arr[i] = i + 1;
    }

    // Resize the array to hold 10 integers
    n = 10;
    arr = (int *)realloc(arr, n * sizeof(int));

    if (arr == NULL) {
        printf("Memory reallocation failed.\n");
        return 1;
    }

    // Initialize the new elements
    for (int i = 5; i < n; i++) {
        arr[i] = i + 1;
    }

    // Print the array
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    // Free the allocated memory
    free(arr);

    return 0;
}
```

**Output**:
```
1 2 3 4 5 6 7 8 9 10
```

---

### 2.4 **`free` (Deallocation)**

- Frees previously allocated memory.
- Prevents memory leaks by releasing unused memory back to the system.

#### Syntax:
```c
void free(void *ptr);
```

#### Example:
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *arr = (int *)malloc(5 * sizeof(int));

    if (arr == NULL) {
        printf("Memory allocation failed.\n");
        return 1;
    }

    // Free the allocated memory
    free(arr);
    printf("Memory successfully freed.\n");

    return 0;
}
```

**Output**:
```
Memory successfully freed.
```

---

## 3. **Difference Between `malloc` and `calloc`**

| Feature        | `malloc`                       | `calloc`                      |
|----------------|--------------------------------|--------------------------------|
| **Initialization** | Does not initialize memory     | Initializes memory to zero      |
| **Parameters**     | Single parameter: size          | Two parameters: num, size       |
| **Use Case**       | Suitable for single allocations | Suitable for arrays or multiple blocks |

---

## 4. **Common Mistakes in Dynamic Memory Allocation**

1. **Uninitialized Pointers**:
   - Using pointers without proper initialization can lead to undefined behavior.

2. **Memory Leaks**:
   - Forgetting to `free` allocated memory leads to memory leaks.

3. **Double Free**:
   - Freeing the same memory twice can cause program crashes.

4. **Accessing Freed Memory**:
   - Dereferencing a pointer after freeing the memory causes undefined behavior.

5. **Allocation Failures**:
   - Always check if `malloc`, `calloc`, or `realloc` returns `NULL`.

---

## 5. **Advantages of Dynamic Memory Allocation**

1. **Flexible Memory Usage**:
   - Allocate memory as needed during runtime.

2. **Efficient Resource Management**:
   - Prevents wastage of memory by allocating exact sizes.

3. **Supports Complex Data Structures**:
   - Enables dynamic arrays, linked lists, trees, and graphs.

---

## 6. **Applications**

1. **Dynamic Arrays**:
   - Create arrays that grow or shrink based on user input.

2. **Linked Lists**:
   - Allocate memory for nodes dynamically.

3. **Memory-Intensive Programs**:
   - Manage memory efficiently in applications with large data requirements.

---

## 7. **Practice Exercises**

1. Write a program to dynamically allocate memory for an array of integers and initialize it with user input.
2. Implement a program to resize a dynamically allocated array using `realloc`.
3. Write a program to dynamically allocate memory for a 2D array using `malloc`.
4. Create a linked list where each node is dynamically allocated.
5. Implement a program that allocates memory for a string, accepts input, and resizes it if needed.

---

## 8. **Key Points to Remember**

1. Use `malloc` for uninitialized memory, `calloc` for zero-initialized memory, and `realloc` to resize memory.
2. Always check if memory allocation or reallocation is successful by verifying the returned pointer.
3. Free memory after use to avoid memory leaks.
4. Avoid using pointers after freeing the memory they point to.

---

Dynamic memory allocation is a cornerstone of efficient and flexible C programming. By mastering `malloc`, `calloc`, `realloc`, and `free`, you can write programs that dynamically adapt to their memory requirements. In the next chapter, we will explore **structures**, a feature that allows grouping related data in C programs.
