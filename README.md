#include <stdio.h>
#include <string.h>

struct Book {
    char title[50];
    char author[50];
};
int main() {
    struct Book books[100];
    int count = 0;
    int choice;
 while (1) {
        printf("\n1. Add Book\n2. View Books\n3. Search Book by Title\n4. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        getchar(); 
if (choice == 1) {
            printf("Enter book title: ");
            fgets(books[count].title, sizeof(books[count].title), stdin);
            books[count].title[strcspn(books[count].title, "\n")] = '\0';
            printf("Enter author name: ");
            fgets(books[count].author, sizeof(books[count].author), stdin);
            books[count].author[strcspn(books[count].author, "\n")] = '\0'; count++;
            printf("Book added!\n");
        } else if (choice == 2) {
            if (count == 0) {
                printf("No books available.\n");
            } else {
                printf("Books in Library:\n");
                for (int i = 0; i < count; i++) {
                    printf("%d. %s by %s\n", i + 1, books[i].title, books[i].author);  }
            }
        } else if (choice == 3) {
            char search[50];
            int found = 0;
printf("Enter title to search: ");
            getchar();
            fgets(search, sizeof(search), stdin);
            search[strcspn(search, "\n")] = '\0';
 for (int i = 0; i < count; i++) {
                if (strcmp(search, books[i].title) == 0) {
                    printf("Found: %s by %s\n", books[i].title, books[i].author);
                    found = 1;
                }
            }
            if (!found) {
                printf("Book not found.\n");
            }
        } else if (choice == 4) {
            printf("Exiting...\n");
            break;
        } else {
            printf("Invalid choice.\n");
        }
    }

    return 0;
}
