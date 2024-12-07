# Chapter: Array of Structures in C

An **array of structures** allows you to manage and store multiple instances of a structure in a single array. This is particularly useful when dealing with collections of entities that share the same set of attributes, such as students, employees, or products.

---

## 1. **What Is an Array of Structures?**

An **array of structures** is a collection of structure variables of the same type. Each element of the array represents an instance of the structure, and you can access their members using array indexing.

### Syntax:
```c
struct structure_name array_name[array_size];
```

---

## 2. **Defining and Using an Array of Structures**

### Example:
```c
#include <stdio.h>

// Define a structure for a student
struct Student {
    int id;
    char name[50];
    float marks;
};

int main() {
    // Declare an array of structures
    struct Student students[3];

    // Assign values to the array elements
    students[0].id = 101;
    snprintf(students[0].name, sizeof(students[0].name), "Alice");
    students[0].marks = 95.5;

    students[1].id = 102;
    snprintf(students[1].name, sizeof(students[1].name), "Bob");
    students[1].marks = 88.0;

    students[2].id = 103;
    snprintf(students[2].name, sizeof(students[2].name), "Charlie");
    students[2].marks = 92.3;

    // Print the array elements
    for (int i = 0; i < 3; i++) {
        printf("Student ID: %d\n", students[i].id);
        printf("Student Name: %s\n", students[i].name);
        printf("Student Marks: %.2f\n\n", students[i].marks);
    }

    return 0;
}
```

**Output**:
```
Student ID: 101
Student Name: Alice
Student Marks: 95.50

Student ID: 102
Student Name: Bob
Student Marks: 88.00

Student ID: 103
Student Name: Charlie
Student Marks: 92.30
```

---

## 3. **Input and Output for Array of Structures**

You can use loops to input and output data for an array of structures dynamically.

### Example:
```c
#include <stdio.h>

struct Student {
    int id;
    char name[50];
    float marks;
};

int main() {
    int n;
    printf("Enter the number of students: ");
    scanf("%d", &n);

    struct Student students[n];

    // Input data for each student
    for (int i = 0; i < n; i++) {
        printf("\nEnter details for student %d:\n", i + 1);
        printf("ID: ");
        scanf("%d", &students[i].id);
        printf("Name: ");
        scanf(" %[^\n]s", students[i].name);
        printf("Marks: ");
        scanf("%f", &students[i].marks);
    }

    // Output data for each student
    printf("\nStudent Details:\n");
    for (int i = 0; i < n; i++) {
        printf("ID: %d, Name: %s, Marks: %.2f\n", students[i].id, students[i].name, students[i].marks);
    }

    return 0;
}
```

**Sample Input/Output**:
```
Enter the number of students: 2

Enter details for student 1:
ID: 101
Name: Alice
Marks: 95.5

Enter details for student 2:
ID: 102
Name: Bob
Marks: 88.0

Student Details:
ID: 101, Name: Alice, Marks: 95.50
ID: 102, Name: Bob, Marks: 88.00
```

---

## 4. **Array of Structures with Functions**

You can pass an array of structures to functions to perform operations like sorting or searching.

### Example: Passing Array of Structures to a Function
```c
#include <stdio.h>

struct Student {
    int id;
    char name[50];
    float marks;
};

// Function to print student details
void printStudents(struct Student students[], int size) {
    for (int i = 0; i < size; i++) {
        printf("ID: %d, Name: %s, Marks: %.2f\n", students[i].id, students[i].name, students[i].marks);
    }
}

int main() {
    struct Student students[2] = {
        {101, "Alice", 95.5},
        {102, "Bob", 88.0}
    };

    printf("Student Details:\n");
    printStudents(students, 2);

    return 0;
}
```

**Output**:
```
Student Details:
ID: 101, Name: Alice, Marks: 95.50
ID: 102, Name: Bob, Marks: 88.00
```

---

## 5. **Dynamic Memory Allocation for Array of Structures**

Dynamic memory allocation can be used to create arrays of structures with a size determined at runtime.

### Example:
```c
#include <stdio.h>
#include <stdlib.h>

struct Student {
    int id;
    char name[50];
    float marks;
};

int main() {
    int n;
    printf("Enter the number of students: ");
    scanf("%d", &n);

    // Dynamically allocate memory for the array of structures
    struct Student *students = (struct Student *)malloc(n * sizeof(struct Student));

    // Input data for each student
    for (int i = 0; i < n; i++) {
        printf("\nEnter details for student %d:\n", i + 1);
        printf("ID: ");
        scanf("%d", &students[i].id);
        printf("Name: ");
        scanf(" %[^\n]s", students[i].name);
        printf("Marks: ");
        scanf("%f", &students[i].marks);
    }

    // Output data for each student
    printf("\nStudent Details:\n");
    for (int i = 0; i < n; i++) {
        printf("ID: %d, Name: %s, Marks: %.2f\n", students[i].id, students[i].name, students[i].marks);
    }

    // Free allocated memory
    free(students);

    return 0;
}
```

**Output**:
```
Enter the number of students: 2

Enter details for student 1:
ID: 101
Name: Alice
Marks: 95.5

Enter details for student 2:
ID: 102
Name: Bob
Marks: 88.0

Student Details:
ID: 101, Name: Alice, Marks: 95.50
ID: 102, Name: Bob, Marks: 88.00
```

---

## 6. **Sorting an Array of Structures**

You can sort an array of structures based on specific fields using sorting algorithms like bubble sort or built-in functions like `qsort`.

### Example: Sorting by Marks
```c
#include <stdio.h>
#include <stdlib.h>

struct Student {
    int id;
    char name[50];
    float marks;
};

// Comparison function for qsort
int compare(const void *a, const void *b) {
    struct Student *studentA = (struct Student *)a;
    struct Student *studentB = (struct Student *)b;
    return (studentA->marks < studentB->marks) - (studentA->marks > studentB->marks);
}

int main() {
    struct Student students[3] = {
        {101, "Alice", 95.5},
        {102, "Bob", 88.0},
        {103, "Charlie", 92.3}
    };

    // Sort array of structures
    qsort(students, 3, sizeof(struct Student), compare);

    printf("Sorted Student Details (by marks):\n");
    for (int i = 0; i < 3; i++) {
        printf("ID: %d, Name: %s, Marks: %.2f\n", students[i].id, students[i].name, students[i].marks);
    }

    return 0;
}
```

**Output**:
```
Sorted Student Details (by marks):
ID: 101, Name: Alice, Marks: 95.50
ID: 103, Name: Charlie, Marks: 92.30
ID: 102, Name: Bob, Marks: 88.00
```

---

## 7. **Common Mistakes**

1. **Uninitialized Array Elements**:
   - Ensure all members of each structure are properly initialized before use.

2. **Index Out-of-Bounds**:
   - Accessing indices outside the array size leads to undefined behavior.

3. **Memory Leaks**:
   - Free dynamically allocated arrays to prevent memory leaks.

4. **Incorrect Comparisons**:
   - Ensure correct comparison logic when sorting or searching.

---

## 8. **Practice Exercises**

1. Write a program to store and display details of `n` employees using an array of structures.
2. Implement a program to sort an array of structures representing books by their prices.
3. Create a program to find the student with the highest marks in an array of structures.
4. Write a program to calculate the average marks of students stored in an array of structures.
5. Implement dynamic memory allocation for an array of structures to store

 customer details.

---

## 9. **Key Points to Remember**

1. An array of structures allows you to manage multiple instances of a structure efficiently.
2. Use loops to input and output data for arrays of structures.
3. Pass arrays of structures to functions for modular operations like sorting and searching.
4. Use dynamic memory allocation for flexible array sizes at runtime.
5. Always initialize array elements and free allocated memory to avoid errors.

---

Arrays of structures provide a robust way to handle collections of related data in C programming. They form the foundation for managing complex datasets and are widely used in real-world applications. In the next chapter, we will explore **pointers to structures**, which further enhance the flexibility of working with structures in C.
