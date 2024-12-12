# String Handling in C

Strings in C are sequences of characters terminated by a **null character** (`'\0'`). They are stored as arrays of `char` data type. C provides several standard library functions for string manipulation, which makes handling strings easier and more efficient.

---

## 1. **What Is a String in C?**

A string is an array of characters ending with the null character (`'\0'`). The null character marks the end of the string and is automatically added when a string is initialized with double quotes.

### Example:
```c
char str[] = "Hello"; // Stored as {'H', 'e', 'l', 'l', 'o', '\0'}
```

---

## 2. **Declaring and Initializing Strings**

### Declaration:
```c
char string_name[size];
```

### Initialization:
1. **Direct Assignment**:
   ```c
   char str[] = "Hello";
   ```

2. **Character-by-Character Assignment**:
   ```c
   char str[6] = {'H', 'e', 'l', 'l', 'o', '\0'};
   ```

---

## 3. **Input and Output of Strings**

### 3.1 **Using `gets` and `puts`**

#### `gets`:
- Reads a line of text until a newline (`\n`) is encountered.
- Avoided in modern C due to security risks (buffer overflow).

#### `puts`:
- Prints a string followed by a newline.

#### Example:
```c
#include <stdio.h>

int main() {
    char str[100];

    printf("Enter a string: ");
    gets(str); // Read string
    printf("You entered: ");
    puts(str); // Print string

    return 0;
}
```

**Output**:
```
Enter a string: Hello, World!
You entered:
Hello, World!
```

---

### 3.2 **Using `scanf` and `printf`**

#### `scanf`:
- Reads input but stops at whitespace.

#### Example:
```c
#include <stdio.h>

int main() {
    char str[100];

    printf("Enter a string: ");
    scanf("%s", str); // Reads until space
    printf("You entered: %s\n", str);

    return 0;
}
```

**Input**: `Hello World`

**Output**:
```
You entered: Hello
```

---

## 4. **Common String Handling Functions**

C provides several functions in the `<string.h>` library for string manipulation.

### 4.1 **`strlen`**

- Returns the length of a string (excluding the null character).
- **Syntax**:
  ```c
  size_t strlen(const char *str);
  ```

#### Example:
```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[] = "Hello";

    printf("Length of the string: %lu\n", strlen(str));

    return 0;
}
```

**Output**:
```
Length of the string: 5
```

---

### 4.2 **`strcpy`**

- Copies one string to another.
- **Syntax**:
  ```c
  char *strcpy(char *dest, const char *src);
  ```

#### Example:
```c
#include <stdio.h>
#include <string.h>

int main() {
    char src[] = "Hello, World!";
    char dest[50];

    strcpy(dest, src);
    printf("Copied string: %s\n", dest);

    return 0;
}
```

**Output**:
```
Copied string: Hello, World!
```

---

### 4.3 **`strcat`**

- Concatenates (appends) one string to another.
- **Syntax**:
  ```c
  char *strcat(char *dest, const char *src);
  ```

#### Example:
```c
#include <stdio.h>
#include <string.h>

int main() {
    char str1[50] = "Hello, ";
    char str2[] = "World!";

    strcat(str1, str2);
    printf("Concatenated string: %s\n", str1);

    return 0;
}
```

**Output**:
```
Concatenated string: Hello, World!
```

---

### 4.4 **`strcmp`**

- Compares two strings lexicographically.
- **Returns**:
  - `0` if both strings are equal.
  - A positive value if the first string is greater.
  - A negative value if the first string is smaller.
- **Syntax**:
  ```c
  int strcmp(const char *str1, const char *str2);
  ```

#### Example:
```c
#include <stdio.h>
#include <string.h>

int main() {
    char str1[] = "Hello";
    char str2[] = "World";

    int result = strcmp(str1, str2);

    if (result == 0) {
        printf("Strings are equal.\n");
    } else if (result > 0) {
        printf("First string is greater.\n");
    } else {
        printf("First string is smaller.\n");
    }

    return 0;
}
```

**Output**:
```
First string is smaller.
```

---

### 4.5 **`strrev`** (Not Standard in C)

- Reverses a string.
- Available in some compilers (e.g., Turbo C).

#### Example:
```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[] = "Hello";

    printf("Original string: %s\n", str);
    strrev(str);
    printf("Reversed string: %s\n", str);

    return 0;
}
```

**Output**:
```
Original string: Hello
Reversed string: olleH
```

---

### 4.6 **`strncpy`**

- Copies up to `n` characters from one string to another.
- **Syntax**:
  ```c
  char *strncpy(char *dest, const char *src, size_t n);
  ```

#### Example:
```c
#include <stdio.h>
#include <string.h>

int main() {
    char src[] = "Hello, World!";
    char dest[50];

    strncpy(dest, src, 5); // Copy first 5 characters
    dest[5] = '\0'; // Add null terminator
    printf("Copied string: %s\n", dest);

    return 0;
}
```

**Output**:
```
Copied string: Hello
```

---

## 5. **Common Mistakes with Strings**

1. **Buffer Overflow**:
   - Writing beyond the array's size can cause undefined behavior.
   ```c
   char str[5];
   strcpy(str, "Hello, World!"); // Buffer overflow
   ```

2. **Uninitialized Strings**:
   - Strings must be initialized before use.

3. **Null Character**:
   - Always ensure the string ends with `'\0'`.

4. **Using `gets`**:
   - Avoid `gets` due to its inability to check buffer size. Use `fgets` instead.

---

## 6. **Practice Exercises**

1. Write a program to reverse a string without using library functions.
2. Create a program to check if a given string is a palindrome.
3. Implement a program to count the occurrences of a character in a string.
4. Write a program to compare two strings without using `strcmp`.
5. Create a program to concatenate two strings without using `strcat`.

---

## 7. **Key Points to Remember**

1. Strings in C are arrays of characters terminated by a null character (`'\0'`).
2. Use `<string.h>` for built-in string handling functions.
3. Always ensure sufficient memory is allocated for strings to prevent overflow.
4. Avoid deprecated functions like `gets` and prefer safer alternatives like `fgets`.

---

String handling in C is fundamental for text manipulation tasks and forms the basis for many higher-level operations. Mastering these concepts will prepare you for more advanced programming challenges. In the next chapter, we will explore **pointers**, a powerful feature of C that complements string manipulation.

## Here are the solutions to the exercises implemented in C:

---

### 1. Program to reverse a string without using library functions

```c
#include <stdio.h>

void reverseString(char str[]) {
    int length = 0;
    while (str[length] != '\0') {
        length++;
    }

    for (int i = 0, j = length - 1; i < j; i++, j--) {
        char temp = str[i];
        str[i] = str[j];
        str[j] = temp;
    }
}

int main() {
    char str[100];
    printf("Enter a string: ");
    scanf("%s", str);

    reverseString(str);
    printf("Reversed string: %s\n", str);

    return 0;
}
```

---

### 2. Program to check if a given string is a palindrome

```c
#include <stdio.h>
#include <stdbool.h>

bool isPalindrome(char str[]) {
    int length = 0;
    while (str[length] != '\0') {
        length++;
    }

    for (int i = 0, j = length - 1; i < j; i++, j--) {
        if (str[i] != str[j]) {
            return false;
        }
    }
    return true;
}

int main() {
    char str[100];
    printf("Enter a string: ");
    scanf("%s", str);

    if (isPalindrome(str)) {
        printf("The string is a palindrome.\n");
    } else {
        printf("The string is not a palindrome.\n");
    }

    return 0;
}
```

---

### 3. Program to count the occurrences of a character in a string

```c
#include <stdio.h>

int countOccurrences(char str[], char ch) {
    int count = 0;
    for (int i = 0; str[i] != '\0'; i++) {
        if (str[i] == ch) {
            count++;
        }
    }
    return count;
}

int main() {
    char str[100], ch;
    printf("Enter a string: ");
    scanf("%s", str);

    printf("Enter the character to count: ");
    scanf(" %c", &ch);

    int count = countOccurrences(str, ch);
    printf("The character '%c' occurs %d times in the string.\n", ch, count);

    return 0;
}
```

---

### 4. Program to compare two strings without using `strcmp`

```c
#include <stdio.h>

int compareStrings(char str1[], char str2[]) {
    int i = 0;
    while (str1[i] != '\0' && str2[i] != '\0') {
        if (str1[i] != str2[i]) {
            return str1[i] - str2[i];
        }
        i++;
    }

    if (str1[i] == '\0' && str2[i] == '\0') {
        return 0; // Strings are equal
    }

    return str1[i] - str2[i];
}

int main() {
    char str1[100], str2[100];
    printf("Enter the first string: ");
    scanf("%s", str1);
    printf("Enter the second string: ");
    scanf("%s", str2);

    int result = compareStrings(str1, str2);
    if (result == 0) {
        printf("The strings are equal.\n");
    } else if (result > 0) {
        printf("The first string is greater than the second.\n");
    } else {
        printf("The first string is less than the second.\n");
    }

    return 0;
}
```

---

### 5. Program to concatenate two strings without using `strcat`

```c
#include <stdio.h>

void concatenateStrings(char str1[], char str2[]) {
    int i = 0, j = 0;

    // Find the end of the first string
    while (str1[i] != '\0') {
        i++;
    }

    // Append the second string
    while (str2[j] != '\0') {
        str1[i] = str2[j];
        i++;
        j++;
    }

    // Null-terminate the result
    str1[i] = '\0';
}

int main() {
    char str1[200], str2[100];
    printf("Enter the first string: ");
    scanf("%s", str1);
    printf("Enter the second string: ");
    scanf("%s", str2);

    concatenateStrings(str1, str2);
    printf("Concatenated string: %s\n", str1);

    return 0;
}
```

---

### Summary:

1. **Reverse String**: Reverses the string in-place using two pointers.
2. **Palindrome Check**: Compares characters from both ends to determine if the string is a palindrome.
3. **Count Character Occurrences**: Counts occurrences of a specific character by iterating through the string.
4. **Compare Strings**: Compares strings character by character to determine lexicographical order.
5. **Concatenate Strings**: Appends one string to another by iterating through both.

These solutions demonstrate fundamental string manipulations without relying on standard library functions.
