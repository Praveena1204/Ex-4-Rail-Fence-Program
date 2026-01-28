```
Name: A. Praveena
Reg.no: 212224040247
```
# Ex-5 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```py
#include <stdio.h>
#include <string.h>

int main() {
    char str[1000];
    char rail[100][1000];
    int i, j, len, rails;
    int row = 0, dir = 1;

    printf("Enter a Secret Message:\n");
    fgets(str, sizeof(str), stdin);
    str[strcspn(str, "\n")] = '\0';   // Remove newline

    len = strlen(str);

    printf("Enter number of rails:\n");
    scanf("%d", &rails);

    // Initialize rail matrix
    for (i = 0; i < rails; i++)
        for (j = 0; j < len; j++)
            rail[i][j] = '\n';

    // Place characters in zig-zag manner
    for (j = 0; j < len; j++) {
        rail[row][j] = str[j];

        if (row == 0)
            dir = 1;
        else if (row == rails - 1)
            dir = -1;

        row += dir;
    }

    // Read encrypted message
    printf("Encrypted Message:\n");
    for (i = 0; i < rails; i++)
        for (j = 0; j < len; j++)
            if (rail[i][j] != '\n')
                printf("%c", rail[i][j]);

    printf("\n");
    return 0;
}

```
# OUTPUT
<img width="411" height="321" alt="image" src="https://github.com/user-attachments/assets/25302abb-d60b-44e8-b491-f9fe44078bec" />

# RESULT
The program is executed successfuly.
