# Chapter: Defining and Declaring Structures in C

Structures in C are user-defined data types that allow grouping related variables of different types into a single entity. They provide a way to organize and manage complex data, enabling better readability, modularity, and efficiency in programs.

---

## 1. **What Is a Structure?**

A **structure** is a collection of variables (called members) of different data types grouped together under a single name. Structures are useful for representing real-world entities like employees, students, or products that require multiple attributes.

---

## 2. **Defining a Structure**

### Syntax:
```c
struct structure_name {
    data_type member1;
    data_type member2;
    // More members
};
```

### Key Points:
1. **`struct`**: Keyword used to define a structure.
2. **`structure_name`**: Name of the structure type.
3. **`member`**: Variables inside the structure, also known as fields or attributes.

---

### Example:
```c
#include <stdio.h>

// Define a structure
struct Student {
    int id;         // Member: Student ID
    char name[50];  // Member: Student name
    float marks;    // Member: Student marks
};
```

This structure groups three members: `id` (integer), `name` (string), and `marks` (float).

---

## 3. **Declaring Structure Variables**

Once a structure is defined, you can declare variables of that structure type.

### Syntax:
```c
struct structure_name variable_name;
```

### Example:
```c
#include <stdio.h>

struct Student {
    int id;
    char name[50];
    float marks;
};

int main() {
    struct Student s1; // Declare a structure variable
    return 0;
}
```

### Initialization During Declaration:
```c
struct Student s1 = {101, "Alice", 95.5};
```

---

## 4. **Accessing Structure Members**

To access a structure's members, use the **dot operator (`.`)**.

### Syntax:
```c
variable_name.member_name
```

### Example:
```c
#include <stdio.h>

struct Student {
    int id;
    char name[50];
    float marks;
};

int main() {
    struct Student s1;

    // Assign values to structure members
    s1.id = 101;
    s1.marks = 95.5;
    snprintf(s1.name, sizeof(s1.name), "Alice");

    // Access and print structure members
    printf("Student ID: %d\n", s1.id);
    printf("Student Name: %s\n", s1.name);
    printf("Student Marks: %.2f\n", s1.marks);

    return 0;
}
```

**Output**:
```
Student ID: 101
Student Name: Alice
Student Marks: 95.50
```

---

## 5. **Using Typedef with Structures**

The `typedef` keyword allows you to define an alias for the structure type, making it easier to use.

### Syntax:
```c
typedef struct {
    data_type member1;
    data_type member2;
    // More members
} alias_name;
```

### Example:
```c
#include <stdio.h>

typedef struct {
    int id;
    char name[50];
    float marks;
} Student;

int main() {
    Student s1; // No need to use 'struct' keyword

    s1.id = 102;
    s1.marks = 88.5;
    snprintf(s1.name, sizeof(s1.name), "Bob");

    printf("Student ID: %d\n", s1.id);
    printf("Student Name: %s\n", s1.name);
    printf("Student Marks: %.2f\n", s1.marks);

    return 0;
}
```

**Output**:
```
Student ID: 102
Student Name: Bob
Student Marks: 88.50
```

---

## 6. **Nested Structures**

Structures can contain other structures as members, enabling hierarchical organization of data.

### Example:
```c
#include <stdio.h>

struct Address {
    char city[50];
    int pin;
};

struct Student {
    int id;
    char name[50];
    float marks;
    struct Address addr; // Nested structure
};

int main() {
    struct Student s1;

    // Assign values to members
    s1.id = 103;
    s1.marks = 90.0;
    snprintf(s1.name, sizeof(s1.name), "Charlie");
    snprintf(s1.addr.city, sizeof(s1.addr.city), "New York");
    s1.addr.pin = 10001;

    // Print structure members
    printf("Student ID: %d\n", s1.id);
    printf("Student Name: %s\n", s1.name);
    printf("Student Marks: %.2f\n", s1.marks);
    printf("City: %s\n", s1.addr.city);
    printf("PIN: %d\n", s1.addr.pin);

    return 0;
}
```

**Output**:
```
Student ID: 103
Student Name: Charlie
Student Marks: 90.00
City: New York
PIN: 10001
```

---

## 7. **Array of Structures**

You can create an array of structures to store data for multiple entities.

### Example:
```c
#include <stdio.h>

struct Student {
    int id;
    char name[50];
    float marks;
};

int main() {
    struct Student students[3] = {
        {101, "Alice", 95.5},
        {102, "Bob", 88.5},
        {103, "Charlie", 90.0}
    };

    for (int i = 0; i < 3; i++) {
        printf("Student ID: %d\n", students[i].id);
        printf("Student Name: %s\n", students[i].name);
        printf("Student Marks: %.2f\n", students[i].marks);
        printf("\n");
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
Student Marks: 88.50

Student ID: 103
Student Name: Charlie
Student Marks: 90.00
```

---

## 8. **Pointers to Structures**

You can create pointers to structures to access and manipulate data efficiently.

### Syntax:
```c
struct structure_name *pointer_name;
pointer_name->member_name; // Use '->' to access members
```

### Example:
```c
#include <stdio.h>

struct Student {
    int id;
    char name[50];
    float marks;
};

int main() {
    struct Student s1 = {104, "Dave", 92.5};
    struct Student *ptr = &s1;

    printf("Student ID: %d\n", ptr->id);
    printf("Student Name: %s\n", ptr->name);
    printf("Student Marks: %.2f\n", ptr->marks);

    return 0;
}
```

**Output**:
```
Student ID: 104
Student Name: Dave
Student Marks: 92.50
```

---

## 9. **Common Mistakes**

1. **Uninitialized Members**:
   - Failing to initialize structure members can lead to undefined values.

2. **Overlooking Memory Size**:
   - Be cautious with large structures to avoid memory overhead.

3. **Improper Access**:
   - Confusing the use of `.` and `->` operators when working with pointers.

---

## 10. **Practice Exercises**

1. Define a structure for a book, including title, author, and price. Write a program to store and display details of three books.
2. Create a structure for a point in a 2D space. Write a program to calculate the distance between two points.
3. Define a structure for an employee with nested structures for address and department. Write a program to input and display employee details.
4. Write a program to sort an array of structures based on a specific field (e.g., student marks).
5. Implement a program to calculate the average marks of students using an array of structures.

---

## 11. **Key Points to Remember**

1. Structures group related variables of different types under one name.
2. Use the `typedef` keyword for simplicity when working with structures.
3. Nested structures allow hierarchical data representation.
4. Arrays of structures and pointers to structures enable efficient data management.

---

Defining and declaring structures in C is foundational for organizing and managing complex data efficiently. In the next chapter, we will explore **manipulating structures using pointers**, which further enhances their versatility in programming.
