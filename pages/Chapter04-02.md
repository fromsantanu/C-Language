# Chapter: Switch-Case Statements

The `switch` statement in C is a multi-way decision-making construct that simplifies complex `if-else` ladders. It is used to test a variable against a list of possible values, executing the corresponding block of code for the matching case.

---

## 1. **Introduction to Switch-Case Statements**

A `switch` statement compares the value of an expression to multiple case labels. When a match is found, the corresponding code block is executed. If no match is found, an optional `default` block can be executed.

### Syntax:
```c
switch (expression) {
    case constant1:
        // Code to execute if expression == constant1
        break;
    case constant2:
        // Code to execute if expression == constant2
        break;
    // More cases...
    default:
        // Code to execute if no cases match
}
```

### Key Points:
1. **Expression**: Must evaluate to an integer or a character.
2. **Case Labels**: Should be unique constants (integer or character).
3. **Break Statement**: Prevents the execution from "falling through" to subsequent cases.
4. **Default**: Executes if no matching case is found. It is optional but recommended.

---

## 2. **How Switch-Case Works**

1. The `expression` inside the `switch` statement is evaluated.
2. The program compares the result of the expression with each `case` label.
3. If a match is found, the corresponding code block is executed until a `break` statement or the end of the switch is reached.
4. If no match is found, the `default` block (if present) is executed.

---

## 3. **Example: Basic Switch-Case**

This program prints the day of the week based on user input:
```c
#include <stdio.h>

int main() {
    int day;

    printf("Enter a number (1-7): ");
    scanf("%d", &day);

    switch (day) {
        case 1:
            printf("Monday\n");
            break;
        case 2:
            printf("Tuesday\n");
            break;
        case 3:
            printf("Wednesday\n");
            break;
        case 4:
            printf("Thursday\n");
            break;
        case 5:
            printf("Friday\n");
            break;
        case 6:
            printf("Saturday\n");
            break;
        case 7:
            printf("Sunday\n");
            break;
        default:
            printf("Invalid input! Please enter a number between 1 and 7.\n");
    }

    return 0;
}
```

### Explanation:
- The user inputs a number.
- The `switch` statement matches the number to a `case` and prints the corresponding day.
- The `default` block handles invalid input.

---

## 4. **Switch-Case with Characters**

The `switch` statement can also be used with character values.

### Example:
```c
#include <stdio.h>

int main() {
    char grade;

    printf("Enter your grade (A, B, C, D, F): ");
    scanf(" %c", &grade); // Note the space before %c to consume any leftover newline character

    switch (grade) {
        case 'A':
            printf("Excellent!\n");
            break;
        case 'B':
            printf("Good Job!\n");
            break;
        case 'C':
            printf("Fair Performance.\n");
            break;
        case 'D':
            printf("Needs Improvement.\n");
            break;
        case 'F':
            printf("Failed.\n");
            break;
        default:
            printf("Invalid grade!\n");
    }

    return 0;
}
```

---

## 5. **Switch-Case Without Break (Fall-Through)**

If the `break` statement is omitted, execution "falls through" to the next case, executing all subsequent cases until a `break` or the end of the `switch` is reached.

### Example:
```c
#include <stdio.h>

int main() {
    int number;

    printf("Enter a number (1-3): ");
    scanf("%d", &number);

    switch (number) {
        case 1:
            printf("One\n");
        case 2:
            printf("Two\n");
        case 3:
            printf("Three\n");
        default:
            printf("Invalid or no break used!\n");
    }

    return 0;
}
```

### Output for Input `1`:
```
One
Two
Three
Invalid or no break used!
```

**Note**: Fall-through can be useful in specific scenarios but should generally be avoided as it may lead to unexpected behavior.

---

## 6. **Nested Switch-Case**

Switch statements can be nested inside one another to handle more complex scenarios.

### Example:
```c
#include <stdio.h>

int main() {
    int menu;
    int subMenu;

    printf("Main Menu:\n1. Food\n2. Drinks\nEnter your choice: ");
    scanf("%d", &menu);

    switch (menu) {
        case 1:
            printf("Food Menu:\n1. Pizza\n2. Burger\nEnter your choice: ");
            scanf("%d", &subMenu);

            switch (subMenu) {
                case 1:
                    printf("You chose Pizza.\n");
                    break;
                case 2:
                    printf("You chose Burger.\n");
                    break;
                default:
                    printf("Invalid food choice!\n");
            }
            break;

        case 2:
            printf("Drinks Menu:\n1. Coke\n2. Water\nEnter your choice: ");
            scanf("%d", &subMenu);

            switch (subMenu) {
                case 1:
                    printf("You chose Coke.\n");
                    break;
                case 2:
                    printf("You chose Water.\n");
                    break;
                default:
                    printf("Invalid drinks choice!\n");
            }
            break;

        default:
            printf("Invalid main menu choice!\n");
    }

    return 0;
}
```

---

## 7. **Advantages and Limitations of Switch-Case**

### Advantages:
1. Simplifies the code by replacing complex `if-else` ladders.
2. Improves readability when multiple conditions are tested for equality.
3. Can be more efficient than `if-else` in certain cases as compilers optimize switch statements.

### Limitations:
1. The `expression` in a switch must be an integer or character (e.g., no floating-point or string comparisons).
2. It is less flexible than `if-else` for handling complex conditions or ranges of values.

---

## 8. **Practice Exercises**

1. Write a program to display the name of the month based on a number input (1 for January, 2 for February, etc.).
2. Create a calculator program using `switch` to perform basic operations (`+`, `-`, `*`, `/`) based on user input.
3. Implement a menu-driven program for a library system that allows users to borrow or return books using nested `switch`.

---

In this chapter, we explored the `switch-case` statement, a powerful tool for decision-making in C programs. In the next chapter, we will discuss **loops**, which allow repeating actions efficiently.
