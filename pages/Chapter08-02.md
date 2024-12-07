# Nested Structures in C

Nested structures in C allow one structure to contain another structure as a member. This enables the creation of hierarchical data representations, which are essential for modeling complex real-world entities.

---

## 1. **What Are Nested Structures?**

A **nested structure** is a structure that contains another structure as one of its members. This allows data to be organized in a hierarchical or multi-level format, making it easier to manage related attributes.

---

## 2. **Defining Nested Structures**

### Syntax:
```c
struct OuterStructure {
    struct InnerStructure {
        // Members of the inner structure
    } inner_member;

    // Other members of the outer structure
};
```

### Example:
```c
#include <stdio.h>

// Define a nested structure
struct Address {
    char city[50];
    int pin;
};

struct Student {
    int id;
    char name[50];
    struct Address addr; // Nested structure
};
```

In this example, `Address` is a nested structure inside `Student`. The `Student` structure contains fields for the student's ID, name, and address.

---

## 3. **Accessing Members of Nested Structures**

You can access the members of a nested structure using the dot operator (`.`) for non-pointer variables and the arrow operator (`->`) for pointers.

### Syntax:
```c
outer_variable.inner_member.inner_member_field;
outer_pointer->inner_member.inner_member_field;
```

---

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
    struct Address addr;
};

int main() {
    struct Student s1;

    // Assign values to the nested structure
    s1.id = 101;
    snprintf(s1.name, sizeof(s1.name), "Alice");
    snprintf(s1.addr.city, sizeof(s1.addr.city), "New York");
    s1.addr.pin = 10001;

    // Access and print values
    printf("Student ID: %d\n", s1.id);
    printf("Student Name: %s\n", s1.name);
    printf("City: %s\n", s1.addr.city);
    printf("PIN: %d\n", s1.addr.pin);

    return 0;
}
```

**Output**:
```
Student ID: 101
Student Name: Alice
City: New York
PIN: 10001
```

---

## 4. **Using Typedef with Nested Structures**

You can simplify the usage of nested structures by using `typedef` to define aliases.

### Example:
```c
#include <stdio.h>

typedef struct {
    char city[50];
    int pin;
} Address;

typedef struct {
    int id;
    char name[50];
    Address addr; // Nested structure
} Student;

int main() {
    Student s1 = {102, "Bob", {"Los Angeles", 90001}};

    printf("Student ID: %d\n", s1.id);
    printf("Student Name: %s\n", s1.name);
    printf("City: %s\n", s1.addr.city);
    printf("PIN: %d\n", s1.addr.pin);

    return 0;
}
```

**Output**:
```
Student ID: 102
Student Name: Bob
City: Los Angeles
PIN: 90001
```

---

## 5. **Pointers to Nested Structures**

You can use pointers to access and modify members of nested structures.

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
    struct Address addr;
};

int main() {
    struct Student s1 = {103, "Charlie", {"Chicago", 60601}};
    struct Student *ptr = &s1;

    // Access nested structure using pointer
    printf("Student ID: %d\n", ptr->id);
    printf("Student Name: %s\n", ptr->name);
    printf("City: %s\n", ptr->addr.city);
    printf("PIN: %d\n", ptr->addr.pin);

    // Modify nested structure using pointer
    snprintf(ptr->addr.city, sizeof(ptr->addr.city), "Houston");
    ptr->addr.pin = 77001;

    printf("\nAfter modification:\n");
    printf("City: %s\n", ptr->addr.city);
    printf("PIN: %d\n", ptr->addr.pin);

    return 0;
}
```

**Output**:
```
Student ID: 103
Student Name: Charlie
City: Chicago
PIN: 60601

After modification:
City: Houston
PIN: 77001
```

---

## 6. **Nested Structures in Arrays**

You can use arrays of structures that contain nested structures to manage multiple entities.

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
    struct Address addr;
};

int main() {
    struct Student students[2] = {
        {101, "Alice", {"New York", 10001}},
        {102, "Bob", {"Los Angeles", 90001}}
    };

    for (int i = 0; i < 2; i++) {
        printf("Student ID: %d\n", students[i].id);
        printf("Student Name: %s\n", students[i].name);
        printf("City: %s\n", students[i].addr.city);
        printf("PIN: %d\n", students[i].addr.pin);
        printf("\n");
    }

    return 0;
}
```

**Output**:
```
Student ID: 101
Student Name: Alice
City: New York
PIN: 10001

Student ID: 102
Student Name: Bob
City: Los Angeles
PIN: 90001
```

---

## 7. **Common Mistakes**

1. **Uninitialized Nested Structures**:
   - Always initialize nested structures before accessing their members.

2. **Complex Syntax**:
   - Be mindful of using the correct operators (`.` or `->`) based on whether the structure is a pointer or not.

3. **Memory Overhead**:
   - Using nested structures can increase memory usage. Optimize by using pointers if the nested structure is large.

---

## 8. **Practice Exercises**

1. Define a structure for a company employee with nested structures for personal details (name, age) and work details (department, salary). Write a program to display employee details.
2. Create a nested structure to represent a library book, including fields for the book's title, author, and a nested structure for publication details (publisher name, year).
3. Write a program that uses pointers to access and modify members of a nested structure representing a car's make, model, and specifications.
4. Implement a program to store and print details of multiple customers, including their contact information using nested structures.
5. Create a structure for a sports team, including team details and a nested structure for the coach's details.

---

## 9. **Key Points to Remember**

1. Nested structures allow you to create hierarchical data representations.
2. Access nested structure members using the dot (`.`) or arrow (`->`) operator based on the type of variable.
3. Use `typedef` to simplify working with nested structures.
4. Arrays and pointers can be used with nested structures for managing multiple entities efficiently.

---

Nested structures are a powerful tool for organizing complex data in C. They enable the creation of detailed, hierarchical models that closely represent real-world scenarios. In the next chapter, we will explore **dynamic memory allocation for structures**, which allows creating and managing structures dynamically at runtime.
