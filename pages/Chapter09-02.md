# Reading and Writing Files in C

File handling in C enables you to read from and write to files, providing a way to persist and manipulate data. This chapter covers the key functions for file operations, including `fopen`, `fclose`, `fread`, `fwrite`, `fscanf`, and `fprintf`.

---

## 1. **Overview of File I/O Functions**

### Functions for File Operations:
1. **`fopen`**: Opens a file in a specified mode.
2. **`fclose`**: Closes an open file.
3. **`fscanf`**: Reads formatted data from a file.
4. **`fprintf`**: Writes formatted data to a file.
5. **`fread`**: Reads binary data from a file.
6. **`fwrite`**: Writes binary data to a file.

---

## 2. **Opening and Closing Files**

### `fopen`
Opens a file for reading, writing, or appending.

#### Syntax:
```c
FILE *fopen(const char *filename, const char *mode);
```

### `fclose`
Closes an open file.

#### Syntax:
```c
int fclose(FILE *stream);
```

---

### Example:
```c
#include <stdio.h>

int main() {
    FILE *file;

    // Open a file for writing
    file = fopen("example.txt", "w");

    if (file == NULL) {
        printf("Error: Could not open file.\n");
        return 1;
    }

    printf("File opened successfully.\n");

    // Close the file
    fclose(file);
    printf("File closed successfully.\n");

    return 0;
}
```

---

## 3. **Writing Data to Files**

### `fprintf`
Writes formatted data to a file (similar to `printf`).

#### Syntax:
```c
int fprintf(FILE *stream, const char *format, ...);
```

### Example: Writing Text to a File
```c
#include <stdio.h>

int main() {
    FILE *file = fopen("example.txt", "w");

    if (file == NULL) {
        printf("Error: Could not open file.\n");
        return 1;
    }

    // Write data to the file
    fprintf(file, "Name: Alice\n");
    fprintf(file, "Age: 25\n");
    fprintf(file, "Score: 90.5\n");

    fclose(file);
    printf("Data written successfully.\n");

    return 0;
}
```

**Output in `example.txt`**:
```
Name: Alice
Age: 25
Score: 90.5
```

---

### `fwrite`
Writes binary data to a file.

#### Syntax:
```c
size_t fwrite(const void *ptr, size_t size, size_t count, FILE *stream);
```

### Example: Writing Binary Data
```c
#include <stdio.h>

int main() {
    FILE *file = fopen("binary.dat", "wb");
    int numbers[] = {10, 20, 30, 40, 50};

    if (file == NULL) {
        printf("Error: Could not open file.\n");
        return 1;
    }

    // Write binary data to the file
    fwrite(numbers, sizeof(int), 5, file);

    fclose(file);
    printf("Binary data written successfully.\n");

    return 0;
}
```

---

## 4. **Reading Data from Files**

### `fscanf`
Reads formatted data from a file (similar to `scanf`).

#### Syntax:
```c
int fscanf(FILE *stream, const char *format, ...);
```

### Example: Reading Text from a File
```c
#include <stdio.h>

int main() {
    FILE *file = fopen("example.txt", "r");
    char name[50];
    int age;
    float score;

    if (file == NULL) {
        printf("Error: Could not open file.\n");
        return 1;
    }

    // Read data from the file
    fscanf(file, "Name: %s\n", name);
    fscanf(file, "Age: %d\n", &age);
    fscanf(file, "Score: %f\n", &score);

    printf("Name: %s\n", name);
    printf("Age: %d\n", age);
    printf("Score: %.2f\n", score);

    fclose(file);

    return 0;
}
```

**Output**:
```
Name: Alice
Age: 25
Score: 90.50
```

---

### `fread`
Reads binary data from a file.

#### Syntax:
```c
size_t fread(void *ptr, size_t size, size_t count, FILE *stream);
```

### Example: Reading Binary Data
```c
#include <stdio.h>

int main() {
    FILE *file = fopen("binary.dat", "rb");
    int numbers[5];

    if (file == NULL) {
        printf("Error: Could not open file.\n");
        return 1;
    }

    // Read binary data from the file
    fread(numbers, sizeof(int), 5, file);

    // Print the data
    for (int i = 0; i < 5; i++) {
        printf("%d ", numbers[i]);
    }
    printf("\n");

    fclose(file);

    return 0;
}
```

**Output**:
```
10 20 30 40 50
```

---

## 5. **File Modes for Reading and Writing**

| Mode   | Description                                                                 |
|--------|-----------------------------------------------------------------------------|
| `"r"`  | Opens a file for reading. The file must exist.                              |
| `"w"`  | Opens a file for writing. Creates a new file or truncates an existing file. |
| `"a"`  | Opens a file for appending. Creates the file if it doesn't exist.           |
| `"r+"` | Opens a file for both reading and writing. The file must exist.             |
| `"w+"` | Opens a file for both reading and writing. Creates or truncates the file.   |
| `"a+"` | Opens a file for both reading and appending. Creates the file if it doesn't exist. |

---

## 6. **Common Mistakes**

1. **Not Closing Files**:
   - Always use `fclose` to release file handles and avoid resource leaks.

2. **Incorrect File Mode**:
   - Ensure the mode matches the intended operation (e.g., reading or writing).

3. **Overwriting Existing Files**:
   - Opening a file in `"w"` mode erases its contents. Use `"a"` or `"r+"` if you want to retain existing data.

4. **Error Checking**:
   - Always check the return value of `fopen`, `fread`, and `fwrite` to ensure the operation succeeded.

---

## 7. **Practice Exercises**

1. Write a program to read a list of student names and scores from a file and display them on the screen.
2. Create a program to write and read binary data for a structure representing an employee (name, ID, and salary).
3. Write a program to copy the contents of one file to another.
4. Implement a program to append data to an existing file without overwriting it.
5. Create a program to read formatted data from a file and calculate the average of numerical values.

---

## 8. **Key Points to Remember**

1. Use `fprintf` and `fscanf` for formatted text file operations.
2. Use `fwrite` and `fread` for binary file operations.
3. Always open files with the appropriate mode and check for errors.
4. Close all files with `fclose` to release resources.
5. Different file modes (`r`, `w`, `a`, etc.) serve specific purposes; use the correct one for your needs.

---

File handling is a critical feature in C that allows programs to interact with persistent storage. By mastering these functions, you can build applications that store, retrieve, and process data efficiently. In the next chapter, we will explore **random access to files**, enabling you to read and write data at specific file positions.
