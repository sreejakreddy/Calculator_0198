# Calculator_0198
C application that acts as a versatile calculator.
#include <stdio.h>
#include <math.h>

// Function declarations
void addition(int n, double numbers[]);
void subtraction(int n, double numbers[]);
void multiplication(int n, double numbers[]);
void division(int n, double numbers[]);
void square_root(double number);
void logarithm_value(double number);

int main() {
    int choice, n, i;
    double numbers[100], num;

    do {
        printf("\nCalculator Menu:\n");
        printf("1. Addition\n");
        printf("2. Subtraction\n");
        printf("3. Multiplication\n");
        printf("4. Division\n");
        printf("5. Square Root\n");
        printf("6. Logarithmic Value\n");
        printf("7. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        if (choice >= 1 && choice <= 4) {
            printf("Enter the number of numbers: ");
            scanf("%d", &n);
            printf("Enter the numbers: ");
            for (i = 0; i < n; i++) {
                scanf("%lf", &numbers[i]);
            }
        } else if (choice == 5 || choice == 6) {
            printf("Enter a number: ");
            scanf("%lf", &num);
        }

        switch (choice) {
            case 1:
                addition(n, numbers);
                break;
            case 2:
                subtraction(n, numbers);
                break;
            case 3:
                multiplication(n, numbers);
                break;
            case 4:
                division(n, numbers);
                break;
            case 5:
                square_root(num);
                break;
            case 6:
                logarithm_value(num);
                break;
            case 7:
                printf("Exiting the program.\n");
                break;
            default:
                printf("Invalid choice.\n");
        }
    } while (choice != 7);

    return 0;
}

// Function definitions
void addition(int n, double numbers[]) {
    double sum = 0;
    for (int i = 0; i < n; i++) {
        sum += numbers[i];
    }
    printf("Sum: %.2lf\n", sum);
}

void subtraction(int n, double numbers[]) {
    double result = numbers[0];
    for (int i = 1; i < n; i++) {
        result -= numbers[i];
    }
    printf("Difference: %.2lf\n", result);
}

void multiplication(int n, double numbers[]) {
    double product = 1;
    for (int i = 0; i < n; i++) {
        product *= numbers[i];
    }
    printf("Product: %.2lf\n", product);
}

void division(int n, double numbers[]) {
    double result = numbers[0];
    for (int i = 1; i < n; i++) {
        if (numbers[i] == 0) {
            printf("Error: Division by zero is not allowed.\n");
            return;
        }
        result /= numbers[i];
    }
    printf("Quotient: %.2lf\n", result);
}

void square_root(double number) {
    if (number < 0) {
        printf("Error: Square root of a negative number is not possible.\n");
    } else {
        printf("Square Root: %.2lf\n", sqrt(number));
    }
}

void logarithm_value(double number) {
    if (number <= 0) {
        printf("Error: Logarithm of zero or negative numbers is not defined.\n");
    } else {
        printf("Logarithmic Value: %.2lf\n", log(number));
    }
}

