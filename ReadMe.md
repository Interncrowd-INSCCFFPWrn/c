#include <stdio.h>
#include <string.h>

#define MAX_BIRTHDAYS 10

struct Birthday {
    char name[50];
    int day;
    int month;
    int year;
};

void searchBirthday(struct Birthday birthdays[], int count, const char* name) {
    int found = 0;
    for (int i = 0; i < count; i++) {
        if (strcmp(birthdays[i].name, name) == 0) {
            printf("Birthday found:\n");
            printf("Name: %s\n", birthdays[i].name);
            printf("Date: %d/%d/%d\n", birthdays[i].day, birthdays[i].month, birthdays[i].year);
            found = 1;
            break;
        }
    }
    if (!found) {
        printf("Birthday not found for %s\n", name);
    }
}

void listBirthdaysByMonth(struct Birthday birthdays[], int count, int month) {
    printf("Birthdays in month %d:\n", month);
    int found = 0;
    for (int i = 0; i < count; i++) {
        if (birthdays[i].month == month) {
            printf("Name: %s\n", birthdays[i].name);
            printf("Date: %d/%d/%d\n", birthdays[i].day, birthdays[i].month, birthdays[i].year);
            found = 1;
        }
    }
    if (!found) {
        printf("No birthdays found in month %d\n", month);
    }
}

int main() {
    struct Birthday birthdays[MAX_BIRTHDAYS];
    int count = 0;

    // Add birthdays
    strcpy(birthdays[count].name, "Avani");
    birthdays[count].day = 22;
    birthdays[count].month = 5;
    birthdays[count].year = 2002;
    count++;

    strcpy(birthdays[count].name, "Mahima");
    birthdays[count].day = 10;
    birthdays[count].month = 8;
    birthdays[count].year = 2002;
    count++;

    strcpy(birthdays[count].name, "Tanmai");
    birthdays[count].day = 06;
    birthdays[count].month = 7;
    birthdays[count].year = 2006;
    count++;

    strcpy(birthdays[count].name, "Janvi");
    birthdays[count].day = 26;
    birthdays[count].month = 2;
    birthdays[count].year = 20022;
    count++;

    strcpy(birthdays[count].name, "Tanisha");
    birthdays[count].day = 20;
    birthdays[count].month = 7;
    birthdays[count].year = 2003;
    count++;

    // Display menu
    int choice;
    do {
        printf("\n--- Birthday Manager ---\n");
        printf("1. Search birthday by name\n");
        printf("2. List birthdays by month\n");
        printf("3. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1: {
                char name[50];
                printf("Enter name to search: ");
                scanf("%s", name);
                searchBirthday(birthdays, count, name);
                break;
            }
            case 2: {
                int month;
                printf("Enter month (1-12): ");
                scanf("%d", &month);
                listBirthdaysByMonth(birthdays, count, month);
                break;
            }
            case 3:
                printf("Exiting the program. Goodbye!\n");
                break;
            default:
                printf("Invalid choice. Please try again.\n");
                break;
        }
    } while (choice != 3);

    return 0;
}